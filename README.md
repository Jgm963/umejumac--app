<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMÉJUMAC - Galería de Productos</title>
    <!-- Carga de Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Configuración de Colores Personalizados de Tailwind -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        // Definiciones de colores basadas en el código original para asegurar consistencia
                        'primary': '#4F46E5', // Indigo-600
                        'secondary': '#818CF8', // Indigo-400
                        'dark-blue': '#1F2937', // Dark Slate Gray
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8f8f8;
        }
        .product-card {
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body>

<!-- Navbar/Header Fijo -->
<nav class="bg-dark-blue shadow-lg fixed w-full top-0 z-40">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
            <!-- Logo -->
            <div class="flex-shrink-0 flex items-center">
                <div class="h-10 w-10 bg-yellow-500 rounded-full flex items-center justify-center text-xl font-bold text-dark-blue mr-3">M</div>
                <span class="text-white text-xl font-extrabold tracking-tight">UMÉJUMAC</span>
            </div>
            <!-- Menú de Navegación -->
            <div class="md:block">
                <div class="flex items-baseline space-x-4">
                    <a href="#" class="text-gray-300 hover:bg-primary hover:text-white px-3 py-2 rounded-md text-sm font-medium hidden sm:block">Asesoría</a>
                    <a href="#" class="text-gray-300 hover:bg-primary hover:text-white px-3 py-2 rounded-md text-sm font-medium hidden sm:block">Bienes y Servicios</a>
                    <button id="sales-button" class="bg-primary text-white px-3 py-2 rounded-md text-sm font-bold shadow-md hover:bg-secondary transition duration-150" onclick="toggleProductModal()">
                        Cargando Galería (CRUD)...
                    </button>
                </div>
            </div>
        </div>
    </div>
</nav>

<!-- Contenido Principal -->
<main class="max-w-7xl mx-auto pt-24 pb-8 px-4 sm:px-6 lg:px-8">
    <h1 class="text-4xl font-extrabold text-gray-900 mb-2 text-center">Galería de Publicaciones y Servicios Exclusivos</h1>
    <p class="text-center text-gray-500 mb-8">Gestión de productos en tiempo real con Firestore.</p>

    <!-- DEBUG: Información de Sesión (Importante para verificar el estado de la autenticación) -->
    <div id="auth-status" class="text-center mb-4 text-sm font-mono p-2 rounded-lg transition duration-300 hidden"></div>

    <!-- Galería de Productos (Contenedor Dinámico) -->
    <div id="product-gallery" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <!-- Los productos se inyectarán aquí -->
    </div>

    <!-- Indicador de Carga Inicial -->
    <div id="loading-spinner" class="text-center mt-12 text-gray-600">
        <svg class="animate-spin h-8 w-8 text-primary mx-auto" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
            <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
        </svg>
        <p class="mt-2">Cargando productos...</p>
    </div>
</main>

<!-- Modal para Agregar Nuevo Producto -->
<div id="product-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50 hidden">
    <div class="bg-white rounded-xl p-8 max-w-lg w-full shadow-2xl">
        <h2 class="text-2xl font-bold mb-6 text-gray-900">Agregar Nuevo Producto</h2>
        <form id="product-form">
            <!-- Título -->
            <div class="mb-4">
                <label for="title" class="block text-sm font-medium text-gray-700">Título del Producto</label>
                <input type="text" id="title" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary focus:ring-primary p-2 border" required>
            </div>
            <!-- Autor/Formato -->
            <div class="mb-4">
                <label for="author" class="block text-sm font-medium text-gray-700">Autor o Formato</label>
                <input type="text" id="author" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary focus:ring-primary p-2 border" required>
            </div>
            <!-- ID/URL de Imagen -->
            <div class="mb-4">
                <label for="image" class="block text-sm font-medium text-gray-700">ID de Imagen (Ej: uploaded:vvv.png-... o URL)</label>
                <input type="text" id="image" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary focus:ring-primary p-2 border" required>
            </div>
            <!-- Precio -->
            <div class="mb-4">
                <label for="price" class="block text-sm font-medium text-gray-700">Precio (USD)</label>
                <input type="number" step="0.01" id="price" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary focus:ring-primary p-2 border" required>
            </div>
            <!-- Descripción -->
            <div class="mb-6">
                <label for="description" class="block text-sm font-medium text-gray-700">Descripción Breve</label>
                <textarea id="description" rows="3" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary focus:ring-primary p-2 border" required></textarea>
            </div>

            <!-- Mensaje de Error/Éxito -->
            <p id="form-message" class="text-sm font-semibold mb-4"></p>

            <!-- Botones -->
            <div class="flex justify-end space-x-4">
                <button type="button" onclick="toggleProductModal()" class="px-4 py-2 text-sm font-medium text-gray-700 bg-gray-200 rounded-lg hover:bg-gray-300 transition duration-150">Cancelar</button>
                <button type="submit" class="bg-primary text-white px-4 py-2 rounded-lg text-sm font-medium shadow-md hover:bg-secondary transition duration-150">Guardar Producto</button>
            </div>
        </form>
    </div>
</div>

<!-- Generic Confirmation/Message Modal (Replaces alert() and prompt() logic) -->
<div id="custom-modal" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center p-4 z-[100] hidden">
    <div class="bg-white rounded-xl p-8 max-w-sm w-full shadow-2xl">
        <h3 id="modal-title" class="text-xl font-bold mb-4 text-gray-900">Mensaje del Sistema</h3>
        <p id="modal-message" class="text-gray-700 mb-6"></p>
        <div id="modal-actions" class="flex justify-end space-x-3">
            <button id="modal-cancel-btn" class="px-4 py-2 text-sm font-medium text-gray-700 bg-gray-200 rounded-lg hover:bg-gray-300 transition duration-150 hidden">Cancelar</button>
            <button id="modal-confirm-btn" class="bg-primary text-white px-4 py-2 rounded-lg text-sm font-medium shadow-md hover:bg-secondary transition duration-150">Aceptar</button>
        </div>
    </div>
</div>

<!-- Firebase SDKs -->
<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
    import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
    import { getFirestore, collection, onSnapshot, addDoc, doc, deleteDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
    import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

    // Configuración de Logging para Firebase
    setLogLevel('Debug');

    // 1. Inicialización Global y Referencias DOM
    let app;
    let db;
    let auth;
    let userId = 'anonimo';
    const salesButton = document.getElementById('sales-button');
    const galleryContainer = document.getElementById('product-gallery');
    const loadingSpinner = document.getElementById('loading-spinner');
    const authStatus = document.getElementById('auth-status');
    const formMessage = document.getElementById('form-message');
    const customModal = document.getElementById('custom-modal');
    const modalTitle = document.getElementById('modal-title');
    const modalMessage = document.getElementById('modal-message');
    const modalCancelBtn = document.getElementById('modal-cancel-btn');
    const modalConfirmBtn = document.getElementById('modal-confirm-btn');
    const modalActions = document.getElementById('modal-actions');


    // Rutas de Firestore (Pública para colaboración)
    const getProductsCollectionRef = (appId) => {
        if (!db) return null;
        // Colección pública: /artifacts/{appId}/public/data/products
        return collection(db, `artifacts/${appId}/public/data/products`);
    };

    // --- Lógica del Modal Personalizado (Reemplazo de alert/confirm/prompt) ---

    // Función genérica para mostrar mensajes o confirmaciones
    const showCustomModal = (title, message, isConfirmation, callback = () => {}) => {
        modalTitle.textContent = title;
        modalMessage.textContent = message;

        modalCancelBtn.classList.add('hidden');
        
        // Limpiar y clonar para evitar múltiples listeners
        const newConfirmBtn = modalConfirmBtn.cloneNode(true);
        modalConfirmBtn.parentNode.replaceChild(newConfirmBtn, modalConfirmBtn);
        
        customModal.classList.remove('hidden');

        if (isConfirmation) {
            modalCancelBtn.classList.remove('hidden');
            
            // Re-asignar listener de Cancelar
            const newCancelBtn = modalCancelBtn.cloneNode(true);
            modalCancelBtn.parentNode.replaceChild(newCancelBtn, modalCancelBtn);
            newCancelBtn.onclick = () => {
                customModal.classList.add('hidden');
            };

            // Listener de Confirmar
            newConfirmBtn.onclick = () => {
                customModal.classList.add('hidden');
                callback(true);
            };
        } else {
            // Modo Alerta/Mensaje (Solo botón Aceptar)
            newConfirmBtn.textContent = 'Aceptar';
            newConfirmBtn.onclick = () => {
                customModal.classList.add('hidden');
                callback(true);
            };
        }
    };
    
    // --- Fin Lógica del Modal Personalizado ---


    // 2. Lógica de Inicialización y Autenticación
    const initializeFirebase = async () => {
        try {
            // Variables inyectadas por el entorno de Canvas
            const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
            let firebaseConfig = null;
            const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

            if (typeof __firebase_config !== 'undefined' && __firebase_config) {
                try {
                    firebaseConfig = JSON.parse(__firebase_config);
                } catch (e) {
                    console.error("Error al parsear __firebase_config:", e);
                }
            }

            if (!firebaseConfig) {
                throw new Error("Configuración de Firebase no disponible.");
            }

            // Inicializar App y Servicios
            app = initializeApp(firebaseConfig);
            db = getFirestore(app);
            auth = getAuth(app);
            console.log("Firebase inicializado correctamente.");

            // Autenticación: Usar token de sesión o iniciar anónimamente
            if (initialAuthToken) {
                await signInWithCustomToken(auth, initialAuthToken);
                console.log("Autenticado con token de sesión.");
            } else {
                await signInAnonymously(auth);
                console.log("Autenticación anónima iniciada.");
            }

            // Listener del Estado de Autenticación
            onAuthStateChanged(auth, (user) => {
                if (user) {
                    userId = user.uid;
                    authStatus.textContent = `Sesión activa. Tu ID: ${userId}`;
                    authStatus.classList.remove('hidden', 'bg-red-100', 'text-red-600');
                    authStatus.classList.add('bg-green-100', 'text-green-600');
                    salesButton.textContent = '+ Nuevo Producto';
                    salesButton.disabled = false;
                    
                    // Una vez autenticado, cargar la galería
                    loadProductGallery(appId);
                } else {
                    handleStaticMode("Sesión no autenticada. Se cargan datos estáticos.");
                }
            });

        } catch (error) {
            console.error("Error crítico al inicializar o autenticar Firebase:", error);
            handleStaticMode(`ERROR CRÍTICO: ${error.message}`);
        }
    };

    const handleStaticMode = (message) => {
        // Activar modo estático (solo lectura)
        authStatus.textContent = message;
        authStatus.classList.remove('hidden', 'bg-green-100', 'text-green-600');
        authStatus.classList.add('bg-red-100', 'text-red-600');
        salesButton.textContent = 'Galería Estática (Solo Lectura)';
        salesButton.disabled = true;
        loadingSpinner.classList.add('hidden');
        displayStaticProducts(); // Mostrar productos estáticos
    }

    // 3. Carga de la Galería (onSnapshot)
    const loadProductGallery = (appId) => {
        const productsRef = getProductsCollectionRef(appId);
        if (!productsRef) return; // Salir si db no está inicializada

        onSnapshot(productsRef, (snapshot) => {
            loadingSpinner.classList.add('hidden'); // Ocultar spinner
            galleryContainer.innerHTML = ''; // Limpiar galería

            if (snapshot.empty) {
                galleryContainer.innerHTML = '<p class="col-span-full text-center text-gray-500 mt-8">No hay productos guardados. ¡Crea el primero!</p>';
                return;
            }

            snapshot.docs.forEach(doc => {
                const product = doc.data();
                product.id = doc.id;
                galleryContainer.appendChild(createProductCard(product));
            });
            
        }, (error) => {
            console.error("Error en onSnapshot (Firestore):", error);
            salesButton.textContent = 'ERROR de Conexión DB';
            loadingSpinner.classList.add('hidden');
            galleryContainer.innerHTML = '<p class="col-span-full text-center text-red-500 mt-8">Error al cargar la base de datos en tiempo real. Revisa la consola para más detalles.</p>';
        });
    };

    // 4. Creación de Tarjeta de Producto (HTML)
    const createProductCard = (product) => {
        const card = document.createElement('div');
        card.classList.add('product-card', 'bg-white', 'rounded-xl', 'shadow-lg', 'overflow-hidden', 'flex', 'flex-col');
        
        // Determinar la fuente de la imagen.
        const imageId = product.image && (product.image.startsWith('uploaded:') || product.image.startsWith('http')) 
            ? product.image 
            : `https://placehold.co/400x300/4F46E5/ffffff?text=${product.title ? product.title.substring(0, 10).toUpperCase() : 'IMG'}`;

        // Mostrar el botón de eliminar solo si el usuario actual es el creador o si se quiere dar acceso total para propósitos de prueba.
        // Aquí lo hacemos visible para todos los usuarios autenticados, ya que es una colección pública colaborativa.
        const deleteButton = `
            <button onclick="deleteProduct('${product.id}')" class="text-red-500 hover:text-red-700 text-sm font-medium transition duration-150">
                Eliminar
            </button>
        `;

        card.innerHTML = `
            <!-- Imagen -->
            <div class="h-48 overflow-hidden bg-gray-200 flex items-center justify-center">
                <img src="${imageId}" alt="${product.title}" class="w-full h-full object-cover" onerror="this.onerror=null;this.src='https://placehold.co/400x300/6B7280/ffffff?text=ERROR+IMG'">
            </div>
            <!-- Contenido -->
            <div class="p-5 flex flex-col flex-grow">
                <h3 class="text-xl font-bold text-dark-blue mb-1">${product.title}</h3>
                <p class="text-sm font-semibold text-primary mb-3">${product.author}</p>
                <p class="text-gray-600 text-sm mb-4 flex-grow">${product.description}</p>
                <div class="flex justify-between items-center mt-auto pt-3 border-t border-gray-100">
                    <span class="text-2xl font-extrabold text-green-600">$${product.price ? parseFloat(product.price).toFixed(2) : '0.00'}</span>
                    ${deleteButton}
                </div>
                <p class="text-xs text-gray-400 mt-2">Creado por: ${product.userId ? product.userId.substring(0, 8) + '...' : 'Desconocido'}</p>
            </div>
        `;
        return card;
    };

    // 5. Guardar Producto (Firestore)
    const saveProduct = async (event) => {
        event.preventDefault();
        formMessage.textContent = 'Guardando...';
        formMessage.classList.remove('text-red-500', 'text-green-500');
        formMessage.classList.add('text-gray-500');

        if (!db || !auth.currentUser) {
            formMessage.textContent = 'Error: Sesión no autenticada para guardar.';
            formMessage.classList.remove('text-gray-500');
            formMessage.classList.add('text-red-500');
            return;
        }

        const priceInput = document.getElementById('price').value;
        if (isNaN(parseFloat(priceInput))) {
            formMessage.textContent = 'Error: El precio debe ser un número válido.';
            formMessage.classList.remove('text-gray-500');
            formMessage.classList.add('text-red-500');
            return;
        }

        const productData = {
            title: document.getElementById('title').value,
            author: document.getElementById('author').value,
            image: document.getElementById('image').value.trim(),
            price: parseFloat(priceInput).toFixed(2),
            description: document.getElementById('description').value,
            createdAt: new Date().toISOString(), // Usar formato ISO para fecha
            userId: auth.currentUser.uid // Registrar quién lo creó
        };

        try {
            const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
            const productsRef = getProductsCollectionRef(appId);
            await addDoc(productsRef, productData);
            
            formMessage.textContent = 'Producto guardado con éxito. Galería actualizada.';
            formMessage.classList.remove('text-gray-500', 'text-red-500');
            formMessage.classList.add('text-green-500');
            
            document.getElementById('product-form').reset();
            setTimeout(() => {
                toggleProductModal(); // Cerrar modal después de 2 segundos
            }, 1500);

        } catch (error) {
            console.error("Error al añadir documento:", error);
            formMessage.textContent = `Error al guardar: ${error.message}`;
            formMessage.classList.remove('text-gray-500', 'text-green-500');
            formMessage.classList.add('text-red-500');
        }
    };
    
    // 6. Eliminar Producto (Firestore)
    // Se adjunta a window para ser llamado desde el HTML (onclick)
    window.deleteProduct = (productId) => {
        if (!db || !auth.currentUser) {
            showCustomModal(
                "Error de Permisos",
                "No está autenticado para eliminar productos.",
                false
            );
            return;
        }
        
        // Usar modal de confirmación personalizado
        showCustomModal(
            "Confirmar Eliminación",
            "¿Estás seguro de que deseas eliminar permanentemente esta publicación? Esta acción es irreversible y se reflejará inmediatamente en la galería.",
            true,
            async (confirmed) => {
                if (confirmed) {
                    try {
                        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
                        const docRef = doc(db, `artifacts/${appId}/public/data/products`, productId);
                        await deleteDoc(docRef);
                        console.log("Documento eliminado:", productId);
                        // onSnapshot se encargará de actualizar la UI
                    } catch (error) {
                        console.error("Error al eliminar documento:", error);
                        showCustomModal(
                            "Error de DB",
                            `No se pudo eliminar el producto: ${error.message}`,
                            false
                        );
                    }
                }
            }
        );
    };

    // 7. Modo Estático (Solo si falla la autenticación)
    const displayStaticProducts = () => {
        loadingSpinner.classList.add('hidden');
        galleryContainer.innerHTML = '';
        
        // Datos estáticos de ejemplo
        const staticProducts = [
            { id: 'static1', title: "Autonomy Concept", author: "Dr. Morales AC", image: 'https://placehold.co/400x300/2563eb/ffffff?text=Autonomia', description: "Publicación clave sobre la autonomía profesional y gestión de riesgos.", price: "29.99", userId: 'STATIC' },
            { id: 'static2', title: "Guía Legal Sanitaria 2024", author: "UMÉJUMAC Editorial", image: 'https://placehold.co/400x300/1d4ed8/ffffff?text=Guia+Legal', description: "Manual detallado sobre la normativa sanitaria y su aplicación en la práctica médica.", price: "45.00", userId: 'STATIC' },
            { id: 'static3', title: "Servicio de Consultoría Premium", author: "EJMR", image: 'https://placehold.co/400x300/103a7d/ffffff?text=Consultoria', description: "Acceso a un paquete de 10 horas de consultoría especializada en gestión hospitalaria.", price: "199.99", userId: 'STATIC' }
        ];

        staticProducts.forEach(product => {
            galleryContainer.appendChild(createProductCard(product));
        });
    };

    // 8. Funciones del Modal de Producto
    // Se adjunta a window para ser llamado desde el HTML (onclick)
    window.toggleProductModal = () => {
        const modal = document.getElementById('product-modal');
        if (modal.classList.contains('hidden')) {
            // Abrir modal, limpiar mensajes y formulario
            if (auth && auth.currentUser && !salesButton.disabled) {
                modal.classList.remove('hidden');
                formMessage.textContent = '';
                formMessage.classList.remove('text-red-500', 'text-green-500');
                document.getElementById('product-form').reset();
            } else {
                // Si el usuario no está autenticado o en modo estático, usar modal de mensaje
                showCustomModal(
                    "Acceso Restringido",
                    "No puedes agregar productos. La aplicación está en modo estático (solo lectura) debido a un error de autenticación o inicialización.",
                    false
                );
            }
        } else {
            modal.classList.add('hidden');
        }
    };

    // 9. Asignar Eventos y Arranque
    document.addEventListener('DOMContentLoaded', () => {
        document.getElementById('product-form').addEventListener('submit', saveProduct);
        initializeFirebase();
    });

</script>
</body>
</html>
