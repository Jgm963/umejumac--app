<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería de Productos con IA y Firestore</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Configuración de la fuente Inter y estilos -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f9fb;
        }
        /* Definir colores primarios basados en indigo/yellow de Tailwind */
        .text-primary { color: #4F46E5; } /* Indigo-600 */
        .bg-primary { background-color: #4F46E5; }
        .hover\:bg-primary-dark:hover { background-color: #4338CA; } /* Indigo-700 */
        .text-yellow { color: #F59E0B; } /* Amber-500 */
    </style>
    <!-- Font Awesome para el icono de papelera -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body class="p-4 md:p-8">

    <header class="text-center mb-12">
        <h1 class="text-4xl font-extrabold text-gray-900 mb-2">🛍️ Tienda Impulse IA </h1>
        <p class="text-xl text-gray-600">Catálogo dinámico impulsado por Gemini y Firestore</p>
    </header>

    <!-- DEBUG: Información de Sesión (Importante para verificar el estado de la autenticación) -->
    <div id="auth-status" class="text-center mb-8 text-sm font-mono p-3 rounded-xl transition duration-300 bg-white shadow-md border border-gray-100">
        <span class="text-gray-500">Iniciando sesión...</span>
    </div>

    <!-- Controles de Administración (Para añadir un producto de ejemplo) -->
    <div id="admin-controls" class="mb-10 p-5 bg-white rounded-2xl shadow-xl max-w-lg mx-auto hidden">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Añadir Nuevo Producto de Ejemplo</h2>
        <p class="text-sm text-gray-600 mb-4">Usa esta sección para añadir un producto a la galería pública (ID de Colección: <code class="bg-gray-100 p-1 rounded">products</code>).</p>
        <button id="add-product-btn" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-3 px-4 rounded-xl transition duration-300 shadow-lg shadow-indigo-200 focus:outline-none focus:ring-4 focus:ring-indigo-500 focus:ring-opacity-50">
            ➕ Añadir Producto Demo
        </button>
    </div>

    <h2 class="text-3xl font-bold text-gray-800 mb-6 text-center">Nuestros Productos</h2>

    <!-- Galería de Productos (Contenedor Dinámico) -->
    <div id="product-gallery" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
        <!-- Los productos se inyectarán aquí -->
    </div>

    <!-- Indicador de Carga Inicial -->
    <div id="loading-spinner" class="text-center mt-12 text-gray-600">
        <svg class="animate-spin h-10 w-10 text-indigo-500 mx-auto" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
            <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
        </svg>
        <p class="mt-3 text-lg">Cargando productos de Firestore...</p>
    </div>

    <!-- Modal de Mensaje/Confirmación Personalizado -->
    <div id="custom-modal" class="hidden fixed inset-0 bg-gray-900 bg-opacity-75 flex items-center justify-center p-4 z-50">
        <div class="bg-white p-6 rounded-xl shadow-2xl max-w-sm w-full transform transition-all scale-100 opacity-100">
            <h3 id="modal-title" class="text-xl font-bold text-gray-800 mb-4">Mensaje</h3>
            <p id="modal-message" class="text-gray-600 mb-6"></p>
            <div id="modal-actions" class="flex justify-end space-x-3">
                <button id="modal-cancel-btn" class="px-4 py-2 text-sm font-medium text-gray-700 bg-gray-200 rounded-lg hover:bg-gray-300 transition duration-150 hidden">Cancelar</button>
                <button id="modal-close-btn" class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-2 px-4 rounded-lg transition duration-300">Aceptar</button>
            </div>
        </div>
    </div>


    <!-- Script de Firebase y Lógica de la Aplicación -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, addDoc, onSnapshot, collection, query, serverTimestamp, updateDoc, deleteDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Establecer el nivel de log para depuración de Firestore
        setLogLevel('Debug');

        // --- CONSTANTES Y GLOBALES ---
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
        
        const API_KEY = ""; 
        const GEMINI_API_URL = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${API_KEY}`;
        
        let app, db, auth;
        let currentUserId = null;
        let isAuthReady = false;

        // --- REFERENCIAS DOM ---
        const authStatusEl = document.getElementById('auth-status');
        const galleryEl = document.getElementById('product-gallery');
        const loadingSpinnerEl = document.getElementById('loading-spinner');
        const adminControlsEl = document.getElementById('admin-controls');
        const addProductBtn = document.getElementById('add-product-btn');
        const modalEl = document.getElementById('custom-modal');
        const modalTitleEl = document.getElementById('modal-title');
        const modalMessageEl = document.getElementById('modal-message');
        const modalCloseBtn = document.getElementById('modal-close-btn');
        const modalCancelBtn = document.getElementById('modal-cancel-btn');
        const modalActionsEl = document.getElementById('modal-actions');


        // --- UTILIDADES DE MODAL ---
        
        /** Muestra un modal de mensaje o confirmación personalizado. */
        const showModal = (title, message, isConfirmation = false, onConfirm = () => {}) => {
            modalTitleEl.textContent = title;
            modalMessageEl.textContent = message;
            
            // Reemplazar listeners para evitar duplicados
            const newCloseBtn = modalCloseBtn.cloneNode(true);
            modalCloseBtn.parentNode.replaceChild(newCloseBtn, modalCloseBtn);
            
            if (isConfirmation) {
                modalCancelBtn.classList.remove('hidden');
                newCloseBtn.textContent = "Confirmar"; // Cambiar texto para confirmación
                
                // Reemplazar listeners de Confirmar y Cancelar
                const newCancelBtn = modalCancelBtn.cloneNode(true);
                modalCancelBtn.parentNode.replaceChild(newCancelBtn, modalCancelBtn);

                newCloseBtn.onclick = () => {
                    modalEl.classList.add('hidden');
                    onConfirm();
                };
                newCancelBtn.onclick = () => {
                    modalEl.classList.add('hidden');
                };
            } else {
                modalCancelBtn.classList.add('hidden');
                newCloseBtn.textContent = "Aceptar";
                newCloseBtn.onclick = () => {
                    modalEl.classList.add('hidden');
                };
            }

            modalEl.classList.remove('hidden');
        };

        /** Construye la ruta a la colección pública de productos. */
        const getProductsCollectionPath = () => {
            // Colección pública: /artifacts/{appId}/public/data/products
            return `artifacts/${appId}/public/data/products`;
        };

        // --- LÓGICA FIREBASE: INICIALIZACIÓN Y AUTENTICACIÓN ---

        try {
            if (Object.keys(firebaseConfig).length > 0) {
                app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);
            } else {
                showModal("Error de Configuración", "La configuración de Firebase no se ha cargado correctamente.");
                throw new Error("Firebase config is missing.");
            }
        } catch (error) {
            console.error("Error al inicializar Firebase:", error);
            // Si falla la inicialización, la aplicación no funcionará correctamente.
        }

        /** Maneja el proceso de autenticación. */
        const setupAuth = async () => {
            try {
                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }
            } catch (error) {
                console.error("Error de autenticación:", error);
                showModal("Error de Autenticación", "No se pudo iniciar sesión. " + error.message);
                authStatusEl.innerHTML = `<span class="text-red-600 font-bold">❌ Error de Auth: ${error.message}</span>`;
            }
        };

        /** Listener para el estado de autenticación. */
        onAuthStateChanged(auth, (user) => {
            isAuthReady = true;
            if (user) {
                currentUserId = user.uid;
                authStatusEl.innerHTML = `
                    <span class="text-gray-900 font-bold">Conectado como:</span>
                    <span class="text-indigo-600 break-all">${currentUserId}</span>
                    <br>
                    <span class="text-xs text-gray-500">Colección: ${getProductsCollectionPath()}</span>
                `;
                adminControlsEl.classList.remove('hidden'); 
                listenToProducts(); 
            } else {
                currentUserId = null;
                authStatusEl.innerHTML = `<span class="text-red-600 font-bold">Desconectado. Intentando iniciar sesión anónimamente...</span>`;
                setupAuth(); 
            }
        });


        // --- LÓGICA LLM: GENERACIÓN DE DESCRIPCIONES (Update) ---

        /** Genera una descripción de producto usando la API de Gemini. */
        const generateDescription = async (productId, productName, productCategory, buttonEl) => {
            buttonEl.disabled = true;
            const originalText = buttonEl.innerHTML;
            buttonEl.innerHTML = `
                <svg class="animate-spin h-4 w-4 mr-2 inline" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                    <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                    <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                </svg>
                Generando...
            `;

            try {
                const systemPrompt = "Actúa como un redactor profesional de comercio electrónico. Genera una descripción de producto concisa, atractiva y profesional (máximo 2 frases) para el siguiente artículo, centrándote en sus características y atractivo. Usa un tono entusiasta.";
                const userQuery = `Nombre del artículo: ${productName}. Categoría: ${productCategory}.`;

                const payload = {
                    contents: [{ parts: [{ text: userQuery }] }],
                    systemInstruction: { parts: [{ text: systemPrompt }] },
                };

                const maxRetries = 3;
                let attempt = 0;
                let response;

                while (attempt < maxRetries) {
                    try {
                        response = await fetch(GEMINI_API_URL, {
                            method: 'POST',
                            headers: { 'Content-Type': 'application/json' },
                            body: JSON.stringify(payload)
                        });

                        if (response.ok) break; 
                        else throw new Error(`Error HTTP: ${response.status}`);
                    } catch (error) {
                        attempt++;
                        if (attempt >= maxRetries) throw error;
                        const delay = Math.pow(2, attempt) * 1000; 
                        await new Promise(resolve => setTimeout(resolve, delay));
                    }
                }

                const result = await response.json();
                const text = result.candidates?.[0]?.content?.parts?.[0]?.text;

                if (text) {
                    const productRef = doc(db, getProductsCollectionPath(), productId);
                    await updateDoc(productRef, {
                        description: text,
                        lastGenerated: serverTimestamp()
                    });
                    showModal("Éxito de IA", "Descripción generada y actualizada en la base de datos.");
                } else {
                    showModal("Error de IA", "No se pudo generar la descripción. La respuesta de la API fue incompleta.");
                }

            } catch (error) {
                console.error("Error al generar la descripción:", error);
                showModal("Error Grave", `Fallo al comunicarse con la IA. Mensaje: ${error.message}`);
            } finally {
                buttonEl.disabled = false;
                buttonEl.innerHTML = originalText;
            }
        };

        // --- LÓGICA FIRESTORE: PRODUCTOS (Read, Create, Delete) ---
        
        /** Maneja la eliminación de un producto (Delete). */
        const deleteProduct = (productId, productName) => {
            showModal(
                "Confirmar Eliminación",
                `¿Estás seguro de que deseas eliminar permanentemente el producto "${productName}"?`,
                true, // Es una confirmación
                async () => {
                    try {
                        const productRef = doc(db, getProductsCollectionPath(), productId);
                        await deleteDoc(productRef);
                        showModal("Eliminado", `Producto "${productName}" eliminado con éxito.`);
                    } catch (error) {
                        console.error("Error al eliminar el producto:", error);
                        showModal("Error de Eliminación", "No se pudo eliminar el producto. Revisa los permisos.");
                    }
                }
            );
        };


        /** Renderiza la galería de productos. */
        const renderProducts = (products) => {
            loadingSpinnerEl.classList.add('hidden');
            let html = '';

            if (products.length === 0) {
                galleryEl.innerHTML = `
                    <div class="col-span-full text-center p-8 bg-white rounded-xl shadow-inner border border-dashed border-gray-300">
                        <p class="text-xl font-semibold text-gray-700">No hay productos en la galería.</p>
                        <p class="text-gray-500 mt-2">Usa el botón "Añadir Producto Demo" arriba para comenzar.</p>
                    </div>
                `;
                return;
            }

            products.forEach(product => {
                const descriptionText = product.description.trim() || 'No hay descripción. ¡Genera una con IA!';
                const lastGeneratedTime = product.lastGenerated ? new Date(product.lastGenerated.seconds * 1000).toLocaleString() : 'Nunca';

                html += `
                    <div id="product-${product.id}" class="bg-white rounded-3xl shadow-xl hover:shadow-2xl transition duration-300 overflow-hidden border border-gray-100">
                        <div class="h-48 bg-gray-200 flex items-center justify-center p-4 relative">
                            <img src="${product.imageUrl}" alt="${product.name}" onerror="this.onerror=null; this.src='https://placehold.co/400x400/4F46E5/ffffff?text=${encodeURIComponent(product.name)}'" class="object-cover h-full w-full rounded-2xl">
                            <!-- Botón de Eliminar (Delete) -->
                            <button 
                                id="del-btn-${product.id}"
                                data-id="${product.id}"
                                data-name="${product.name}"
                                class="absolute top-3 right-3 bg-red-500 hover:bg-red-600 text-white p-2 rounded-full shadow-lg transition duration-150 transform hover:scale-110"
                                aria-label="Eliminar producto"
                            >
                                <i class="fas fa-trash-alt text-sm"></i>
                            </button>
                        </div>
                        <div class="p-6">
                            <div class="flex justify-between items-start mb-3">
                                <h3 class="text-xl font-bold text-gray-900 leading-tight">${product.name}</h3>
                                <span class="text-2xl font-extrabold text-primary">${product.price.toFixed(2)}€</span>
                            </div>
                            <p class="text-gray-500 text-sm italic mb-4">${descriptionText}</p>
                            <button 
                                id="gen-btn-${product.id}"
                                data-id="${product.id}"
                                data-name="${product.name}"
                                data-category="${product.category || 'general'}"
                                class="w-full text-xs bg-yellow-500 hover:bg-yellow-600 text-white font-semibold py-2 rounded-xl transition duration-300 flex items-center justify-center shadow-md">
                                🤖 Generar Descripción con IA
                            </button>
                            <p class="text-xs text-gray-400 mt-2 text-center">Última Gen: ${lastGeneratedTime}</p>
                        </div>
                    </div>
                `;
            });
            
            galleryEl.innerHTML = html;

            // Añadir event listeners dinámicamente
            products.forEach(product => {
                const genBtn = document.getElementById(`gen-btn-${product.id}`);
                if (genBtn) {
                    genBtn.addEventListener('click', () => {
                        generateDescription(product.id, product.name, product.category || 'general', genBtn);
                    });
                }

                const delBtn = document.getElementById(`del-btn-${product.id}`);
                if (delBtn) {
                    delBtn.addEventListener('click', () => {
                        deleteProduct(product.id, product.name);
                    });
                }
            });
        };

        /** Escucha los productos en tiempo real desde Firestore. */
        const listenToProducts = () => {
            if (!db) return console.error("Firestore no está inicializado.");
            
            const productsCollectionRef = collection(db, getProductsCollectionPath());
            const q = query(productsCollectionRef);

            onSnapshot(q, (snapshot) => {
                try {
                    const products = [];
                    snapshot.forEach(doc => {
                        products.push({ id: doc.id, ...doc.data() });
                    });
                    
                    products.sort((a, b) => a.name.localeCompare(b.name));
                    renderProducts(products);
                } catch (error) {
                    console.error("Error al procesar snapshot de productos:", error);
                    showModal("Error de Base de Datos", "No se pudieron cargar los datos. Revisa la consola.");
                }
            }, (error) => {
                console.error("Error al escuchar productos:", error);
                showModal("Error de Conexión", "Fallo en la conexión a Firestore.");
                loadingSpinnerEl.classList.add('hidden');
                galleryEl.innerHTML = `<p class="col-span-full text-center text-red-600 mt-8">Error: No se pudo conectar a la base de datos.</p>`;
            });
        };

        // --- LÓGICA PARA AÑADIR PRODUCTOS DEMO (Create) ---

        const productMocks = [
            { name: "Cámara Ultra 4K", category: "Electrónica", price: 349.99, imageUrl: "https://placehold.co/400x400/0891b2/ffffff?text=Camara+4K" },
            { name: "Taza de Café Galáctica", category: "Hogar", price: 15.50, imageUrl: "https://placehold.co/400x400/9333ea/ffffff?text=Taza+Espacial" },
            { name: "Auriculares Inalámbricos Pro", category: "Audio", price: 89.99, imageUrl: "https://placehold.co/400x400/dc2626/ffffff?text=Auriculares+Inalambricos" },
            { name: "Esterilla de Yoga Ecológica", category: "Deportes", price: 45.00, imageUrl: "https://placehold.co/400x400/15803d/ffffff?text=Esterilla+Yoga" }
        ];

        let productIndex = 0;

        addProductBtn.addEventListener('click', async () => {
            if (!db) {
                showModal("Error", "La base de datos no está inicializada.");
                return;
            }

            const productData = productMocks[productIndex % productMocks.length];
            productIndex++;
            productData.name = `${productData.name} #${productIndex}`; 
            productData.description = '';
            productData.createdAt = serverTimestamp();

            try {
                await addDoc(collection(db, getProductsCollectionPath()), productData);
                showModal("¡Producto Añadido!", `El producto "${productData.name}" ha sido añadido a la galería.`);
            } catch (error) {
                console.error("Error al añadir producto:", error);
                showModal("Error", "No se pudo añadir el producto demo a Firestore.");
            }
        });

    </script>
</body>
</html>
