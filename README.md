<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMÉJUMAC: Soluciones Profesionales</title>
    <!-- Carga de Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Fuente Inter para estética */
        :root { font-family: 'Inter', sans-serif; }
        
        /* ====================================
           ESTILOS GENERALES Y DE NAVEGACIÓN
           ==================================== */

        /* Animaciones para transiciones suaves */
        .fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Clase general para ocultar las secciones (usamos 'view' como clase genérica) */
        .view {
            display: none;
        }
        
        /* Estilo para asegurar que las imágenes placeholder se vean bien */
        .placeholder-img {
            background-color: #003366;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.25rem;
            font-weight: 700;
        }

        /* Encabezado fijo y oscuro para simular el menú */
        .header-nav {
            background-color: #003366; /* Azul marino */
            color: white;
            position: sticky;
            top: 0;
            z-index: 20;
            box-shadow: 0 2px 4px 0 rgba(0,0,0,0.1);
        }
        
        /* Estilos de la tarjeta de Libro */
        .book-card {
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s, box-shadow 0.2s;
            overflow: hidden; 
        }
        .book-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }

        /* Estilo para las tarjetas de las secciones principales */
        .main-section-card {
            background-color: #f7f9fc;
            border-left: 5px solid #003366; /* Borde de color institucional */
            transition: all 0.3s;
            cursor: pointer; /* Indica que la tarjeta es clickeable */
        }
        .main-section-card:hover {
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transform: translateY(-5px);
            border-left: 5px solid #ffcc00; /* Borde de color de acento */
        }

    </style>
</head>
<body class="bg-gray-100 min-h-screen">

    <!-- Encabezado de Navegación Fijo -->
    <header class="header-nav p-4">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center">
            <div class="flex justify-between w-full sm:w-auto items-center mb-3 sm:mb-0">
                <h1 id="home-link" class="text-3xl font-extrabold tracking-wider cursor-pointer hover:text-gray-300 transition" data-target="main">UMÉJUMAC</h1>
            </div>
            
            <nav class="flex flex-wrap justify-center sm:justify-end space-x-3 sm:space-x-6 text-sm font-medium">
                <!-- Enlaces de navegación -->
                <a href="#" class="nav-link hover:text-gray-300 transition py-1" data-target="asesoria">Asesoría</a>
                <a href="#" class="nav-link hover:text-gray-300 transition py-1" data-target="bienes">Bienes y Servicios</a>
                <a href="#" class="nav-link hover:text-gray-300 transition font-bold py-1 cursor-pointer" data-target="gallery">Ventas</a>
                <!-- Botón para agregar un nuevo producto (Solo visible en la galería) -->
                <button id="add-product-btn" class="bg-white text-blue-800 hover:bg-gray-200 px-3 py-1 rounded-full transition duration-150 text-xs sm:text-sm mt-2 sm:mt-0" style="display: none;">
                    + Nuevo Producto
                </button>
            </nav>
        </div>
        <!-- Información de autenticación (muestra tu ID para referencia) -->
        <div id="user-info" class="text-xs text-center sm:text-right mt-2 mr-4 hidden sm:block"></div>
    </header>

    <div id="app-container" class="max-w-7xl mx-auto p-4 sm:p-8">

        <!-- ====================================
             1. VISTA PRINCIPAL (DEFAULT) 
             ==================================== -->
        <section id="main-view" class="view p-0 bg-transparent rounded-xl">
            <!-- Título Principal -->
            <div class="text-center mb-10 p-6 bg-white rounded-xl shadow-md">
                <h2 class="text-4xl font-extrabold text-blue-800 mb-2">Unidad Médica Jurídica Morales AC</h2>
                <p class="text-xl text-gray-700 max-w-4xl mx-auto">
                    Soluciones profesionales integrales en **Salud, Derecho y Comercio**.
                </p>
            </div>

            <!-- Contenedor de las 3 Secciones -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                
                <!-- SECCIÓN 1: Asesoría en salud colectiva -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" data-target="asesoria">
                    <h3 class="text-2xl font-bold text-blue-800 mb-3 flex items-center">
                        <span class="mr-3 text-yellow-500 text-3xl">1</span>
                        Asesoría en Salud Colectiva
                    </h3>
                    <p class="text-gray-600 mb-4">
                        Consultoría especializada en normatividad médica, legal y administrativa para entidades de salud.
                    </p>
                    <button class="bg-blue-100 text-blue-800 font-semibold py-2 px-4 rounded-lg text-sm hover:bg-blue-200 transition mt-2">
                        Ver Detalles
                    </button>
                </div>

                <!-- SECCIÓN 2: Bienes y Servicios -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" data-target="bienes">
                    <h3 class="text-2xl font-bold text-blue-800 mb-3 flex items-center">
                        <span class="mr-3 text-yellow-500 text-3xl">2</span>
                        Bienes y Servicios
                    </h3>
                    <p class="text-gray-600 mb-4">
                        Gestión y provisión de bienes diversos para cubrir necesidades operativas y logísticas.
                    </p>
                    <button class="bg-blue-100 text-blue-800 font-semibold py-2 px-4 rounded-lg text-sm hover:bg-blue-200 transition mt-2">
                        Ver Detalles
                    </button>
                </div>

                <!-- SECCIÓN 3: Productos de Venta -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" data-target="gallery">
                    <h3 class="text-2xl font-bold text-blue-800 mb-3 flex items-center">
                        <span class="mr-3 text-yellow-500 text-3xl">3</span>
                        Productos de Venta
                    </h3>
                    <p class="text-gray-600 mb-4">
                        Accede a nuestra colección de publicaciones, libros y materiales de apoyo exclusivos de UMÉJUMAC.
                    </p>
                    <button class="bg-yellow-500 text-blue-900 font-bold py-2 px-4 rounded-lg text-sm hover:bg-yellow-600 transition mt-2">
                        Explorar Galería
                    </button>
                </div>

            </div>
        </section>


        <!-- ====================================
             2. SECCIÓN: ASESORÍA EN SALUD COLECTIVA (VIEW)
             ==================================== -->
        <section id="asesoria-view" class="view bg-white p-6 rounded-xl shadow-lg">
            <h2 class="text-3xl font-extrabold text-blue-800 mb-4 border-b pb-2">Asesoría Especializada en Salud Colectiva</h2>
            <p class="text-lg text-gray-700 mb-8">
                Ofrecemos consultoría integral en normatividad, gestión de riesgos y optimización administrativa para instituciones de salud. Nuestro equipo combina experiencia médica y legal para garantizar el cumplimiento y la excelencia operativa.
            </p>

            <!-- Contenedor para fotos, trabajos en equipo o consultorías -->
            <div id="asesoria-content" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Ejemplo de contenido -->
                <div class="bg-gray-50 p-4 rounded-lg border border-blue-200">
                    <h4 class="font-semibold text-blue-700">Consultorías Regulatorias</h4>
                    <p class="text-sm text-gray-600">Revisión y ajuste de protocolos internos según la legislación vigente.</p>
                </div>
                <div class="bg-gray-50 p-4 rounded-lg border border-blue-200">
                    <h4 class="font-semibold text-blue-700">Trabajo en Equipo Multidisciplinario</h4>
                    <p class="text-sm text-gray-600">Casos complejos con enfoque médico-legal y administrativo.</p>
                </div>
                <div class="placeholder-img h-32 rounded-lg text-sm">Espacio para Foto de Equipo</div>
            </div>
            
        </section>


        <!-- ====================================
             3. SECCIÓN: BIENES Y SERVICIOS (VIEW)
             ==================================== -->
        <section id="bienes-view" class="view bg-white p-6 rounded-xl shadow-lg">
            <h2 class="text-3xl font-extrabold text-blue-800 mb-4 border-b pb-2">Provisión de Bienes y Servicios Diversos</h2>
            <p class="text-lg text-gray-700 mb-8">
                Nos encargamos de la gestión de bienes y la contratación de servicios esenciales, asegurando calidad y puntualidad para sus operaciones.
            </p>

            <!-- Contenedor para bienes, reuniones, logística o lo que sea -->
            <div id="bienes-content" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                 <!-- Ejemplo de contenido -->
                <div class="bg-gray-50 p-4 rounded-lg border border-blue-200">
                    <h4 class="font-semibold text-blue-700">Gestión de Logística</h4>
                    <p class="text-sm text-gray-600">Organización de reuniones y eventos corporativos con soporte completo.</p>
                </div>
                <div class="placeholder-img h-32 rounded-lg text-sm">Espacio para Foto de Reuniones</div>
                <div class="bg-gray-50 p-4 rounded-lg border border-blue-200">
                    <h4 class="font-semibold text-blue-700">Suministro de Materiales</h4>
                    <p class="text-sm text-gray-600">Provisión de insumos y materiales operativos no médicos.</p>
                </div>
            </div>
        </section>


        <!-- ====================================
             4. GALERÍA DE PRODUCTOS (VIEW)
             ==================================== -->
        <section id="products-gallery" class="view">
            <!-- Título sin la referencia "Punto 3" -->
            <h2 class="text-3xl font-extrabold text-gray-800 mb-6 text-center sm:text-left border-b pb-2">Galería de Productos Exclusivos</h2>

            <!-- Formulario de Creación Rápida (Inicialmente oculto) -->
            <div id="creation-form-container" class="bg-white p-6 rounded-xl shadow-xl mb-8 hidden fade-in">
                <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">Añadir Nuevo Producto (Libro)</h3>
                <form id="product-form" class="space-y-4">
                    <input type="text" id="product-title" placeholder="Título (Ej: Libro 1)" required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    <input type="text" id="product-author" placeholder="Autor o Formato (Ej: Juan Pérez | Formato Digital)" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    <textarea id="product-description" rows="2" placeholder="Descripción breve..." required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 resize-none"></textarea>
                    <input type="number" step="0.01" id="product-price" placeholder="Precio (Ej: 19.99)" required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    
                    <div class="flex space-x-3">
                        <button type="submit" id="save-button" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-4 rounded-xl transition duration-150 ease-in-out disabled:opacity-50">
                            Guardar Producto
                        </button>
                        <button type="button" id="cancel-button" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-semibold py-3 px-4 rounded-xl transition duration-150">
                            Cancelar
                        </button>
                    </div>
                    <p id="form-error-message" class="text-red-500 text-sm mt-2 hidden"></p>
                </form>
            </div>

            <!-- Galería de Productos -->
            <div id="products-container" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 2xl:grid-cols-6 gap-6">
                <p id="loading-products" class="text-center text-gray-500 col-span-full py-10">Cargando productos...</p>
            </div>
        </section>

    </div>

    <!-- Modal de Confirmación para Eliminar -->
    <div id="confirm-modal" class="fixed inset-0 bg-gray-600 bg-opacity-70 hidden items-center justify-center p-4 z-50">
        <div class="bg-white rounded-xl p-6 shadow-2xl max-w-sm w-full">
            <h3 class="text-lg font-bold text-gray-900 mb-4">Confirmar Eliminación</h3>
            <p id="modal-text" class="text-gray-700 mb-6">¿Estás seguro de que quieres eliminar este producto de la galería?</p>
            <div class="flex justify-end space-x-3">
                <button id="cancel-delete-button" class="px-4 py-2 text-sm font-medium text-gray-700 bg-gray-200 rounded-lg hover:bg-gray-300 transition">Cancelar</button>
                <button id="confirm-delete-button" class="px-4 py-2 text-sm font-medium text-white bg-red-600 rounded-lg hover:bg-red-700 transition">Eliminar</button>
            </div>
        </div>
    </div>

    <!-- Firebase SDKs -->
    <script type="module">
        // Importaciones de Firebase
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, setDoc, onSnapshot, collection, query, serverTimestamp, deleteDoc, updateDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        
        setLogLevel('Debug');

        // Variables globales de Canvas
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

        let app, db, auth;
        let userId = null;
        let isAuthReady = false;

        // RUTA PÚBLICA DE FIREBASE
        const PRODUCTS_COLLECTION_PATH = `artifacts/${appId}/public/data/umemajuc_products`;


        // Referencias de elementos del DOM (Secciones)
        // Se añade la clase 'view' a todas las secciones principales
        const VIEWS = document.querySelectorAll('.view');
        const MAIN_VIEW = document.getElementById('main-view');

        // Referencias de Navegación
        const NAV_ELEMENTS = document.querySelectorAll('[data-target]');
        const CARD_ELEMENTS = document.querySelectorAll('.main-section-card');
        
        // Formulario y Galería de Productos (Mantenidas)
        const ADD_BUTTON = document.getElementById('add-product-btn');
        const FORM_CONTAINER = document.getElementById('creation-form-container');
        const PRODUCT_FORM = document.getElementById('product-form');
        const TITLE_INPUT = document.getElementById('product-title');
        const AUTHOR_INPUT = document.getElementById('product-author');
        const DESC_INPUT = document.getElementById('product-description');
        const PRICE_INPUT = document.getElementById('product-price');
        const SAVE_BUTTON = document.getElementById('save-button');
        const CANCEL_BUTTON = document.getElementById('cancel-button');
        const FORM_ERROR = document.getElementById('form-error-message');
        const PRODUCTS_CONTAINER = document.getElementById('products-gallery').querySelector('.grid');
        const USER_INFO_ELEMENT = document.getElementById('user-info');
        const LOADING_PRODUCTS_ELEMENT = document.getElementById('loading-products');
        
        // Referencias del Modal de Confirmación
        const MODAL_ELEMENT = document.getElementById('confirm-modal');
        const CONFIRM_BUTTON = document.getElementById('confirm-delete-button');
        const CANCEL_DELETE_BUTTON = document.getElementById('cancel-delete-button');

        let productToDelete = null;
        let isEditing = false;
        let editingProductId = null;


        // --- 1. Lógica de Navegación de Vistas ---

        // Función central para mostrar una vista y ocultar las demás
        const showView = (viewId) => {
            let targetViewId;

            // 1. Normalizar el ID de la vista
            if (viewId === 'main') {
                targetViewId = 'main-view';
            } else if (viewId === 'gallery') {
                targetViewId = 'products-gallery'; 
            } else {
                targetViewId = `${viewId}-view`; 
            }

            let targetViewFound = false;
            
            VIEWS.forEach(view => {
                // Ocultar todas las secciones
                view.classList.remove('fade-in');
                view.style.display = 'none';

                if (view.id === targetViewId) {
                    // Mostrar la sección solicitada
                    view.style.display = 'block';
                    view.classList.add('fade-in');
                    targetViewFound = true;
                }
            });

            // Ocultar o mostrar el botón de agregar producto
            ADD_BUTTON.style.display = (targetViewId === 'products-gallery') ? 'block' : 'none';
            if (targetViewId !== 'products-gallery') {
                 hideForm(); // Ocultar el formulario si salimos de la galería
            }
            
            if (targetViewFound) {
                window.scrollTo(0, 0); // Desplazarse al inicio de la página al cambiar de vista
            } else {
                console.error(`Vista no encontrada para ID: ${viewId} (Buscando: ${targetViewId})`);
            }
        };

        // Manejador de eventos para todos los elementos con data-target
        const handleNavigationClick = (event) => {
            event.preventDefault(); 
            
            let targetView = null;
            let targetElement = event.currentTarget;
            
            // Si el elemento clickeado es un botón dentro de una tarjeta
            // necesitamos encontrar la tarjeta contenedora para obtener el data-target.
            if (event.target.tagName === 'BUTTON' && event.target.closest('.main-section-card')) {
                 targetElement = event.target.closest('.main-section-card');
            }

            // Intentar obtener el target del elemento actual o de su contenedor principal
            targetView = targetElement.dataset.target;

            if (targetView) {
                showView(targetView);
            }
        };


        // --- 2. Inicialización y Autenticación de Firebase (Sin cambios) ---

        const initializeFirebase = async () => {
            try {
                app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);

                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }

                onAuthStateChanged(auth, (user) => {
                    if (user) {
                        userId = user.uid;
                        isAuthReady = true;
                        USER_INFO_ELEMENT.textContent = `Sesión: ${userId.substring(0, 8)}...`;
                        USER_INFO_ELEMENT.classList.remove('hidden');
                        // Iniciar la escucha de datos solo después de autenticar
                        listenForProducts();
                    } else {
                        console.error("No se pudo autenticar al usuario.");
                    }
                });

            } catch (error) {
                console.error("Error al inicializar Firebase o autenticar:", error);
            }
        };


        // --- 3. Renderizado de Productos (Sin cambios) ---

        const renderProduct = (product) => {
            const isOwner = product.userId === userId;
            
            const card = document.createElement('div');
            card.id = `product-${product.id}`;
            card.className = `book-card bg-white rounded-xl relative shadow-md fade-in flex flex-col`;


            card.innerHTML = `
                <!-- Bloque de Portada (Placeholder Azul Marino) -->
                <div class="cover-placeholder placeholder-img rounded-t-xl">
                    <span>${product.title || 'Título N/A'}</span>
                </div>

                <!-- Contenido de Detalle -->
                <div class="p-4 flex flex-col flex-grow">
                    <!-- Título (Azul oscuro como en la imagen) -->
                    <h4 class="text-lg font-bold text-blue-800 mb-1">${product.title || 'Título del Producto'}</h4>
                    <!-- Autor / Formato -->
                    <p class="text-xs text-gray-500 mb-2">${product.author || 'Autor: N/A'}</p>
                    <!-- Descripción -->
                    <p class="text-sm text-gray-700 flex-grow mb-3">${product.description || 'Descripción: Reemplace este texto con información detallada.'}</p>
                    
                    <!-- Información de Creación/Propiedad (Visible para todos) -->
                    <p class="text-xs text-gray-400 mb-2">Creador: <span class="font-mono break-all">${product.userId.substring(0, 8)}...</span></p>

                    <!-- Precio (Verde llamativo) -->
                    <div class="mt-auto">
                        <p class="price-text">Precio: USD ${parseFloat(product.price).toFixed(2)}</p>
                    </div>

                    <!-- Botones de Acción (Solo si es el propietario) -->
                    ${isOwner ? `
                        <div class="flex mt-3 space-x-2">
                            <button class="edit-btn text-xs font-semibold text-blue-600 hover:text-blue-800 transition" data-id="${product.id}">
                                Editar
                            </button>
                            <button class="delete-btn text-xs font-semibold text-red-600 hover:text-red-800 transition" data-id="${product.id}">
                                Eliminar
                            </button>
                        </div>
                    ` : ''}
                </div>
            `;
            
            // Adjuntar eventos de edición y eliminación SOLO si es el propietario
            if (isOwner) {
                card.querySelector('.edit-btn')?.addEventListener('click', () => startEdit(product));
                card.querySelector('.delete-btn')?.addEventListener('click', () => showConfirmModal(product));
            }

            return card;
        };


        // --- 4. Escucha de Firestore (Sin cambios) ---
        const listenForProducts = () => {
            if (!db) return;

            const productsRef = collection(db, PRODUCTS_COLLECTION_PATH);
            const q = query(productsRef); 

            onSnapshot(q, (snapshot) => {
                // Asegurar que el elemento de carga se muestre/oculte correctamente
                const loadingElement = document.getElementById('loading-products');
                if (loadingElement) loadingElement.style.display = 'none';

                const products = [];
                snapshot.forEach(doc => {
                    products.push({ id: doc.id, ...doc.data() });
                });

                // Ordenar por fecha de creación descendente (los más nuevos primero)
                products.sort((a, b) => (b.createdAt?.seconds || 0) - (a.createdAt?.seconds || 0));

                PRODUCTS_CONTAINER.innerHTML = '';
                if (products.length === 0) {
                    // Mensaje neutral para la galería vacía
                    PRODUCTS_CONTAINER.innerHTML = '<p id="empty-message" class="text-center text-gray-500 p-6 bg-white rounded-xl shadow-inner col-span-full">La galería de productos está actualmente vacía. Utiliza el botón "+ Nuevo Producto" para añadir uno.</p>';
                } else {
                    products.forEach(product => {
                        PRODUCTS_CONTAINER.appendChild(renderProduct(product));
                    });
                }
            }, (error) => {
                console.error("Error al escuchar productos:", error);
                PRODUCTS_CONTAINER.innerHTML = `<p class="text-center text-red-500 p-6 col-span-full">Error al cargar datos: ${error.message}</p>`;
            });
        };


        // --- 5. Lógica de CRUD y Modal (Sin cambios) ---
        
        const showForm = () => {
            FORM_CONTAINER.classList.remove('hidden');
            PRODUCTS_CONTAINER.scrollIntoView({ behavior: 'smooth', block: 'start' });
            TITLE_INPUT.focus();
        };

        const hideForm = () => {
            FORM_CONTAINER.classList.add('hidden');
            PRODUCT_FORM.reset();
            isEditing = false;
            editingProductId = null;
            SAVE_BUTTON.textContent = 'Guardar Producto';
            FORM_ERROR.classList.add('hidden');
        };

        const startEdit = (product) => {
            isEditing = true;
            editingProductId = product.id;
            
            TITLE_INPUT.value = product.title || '';
            AUTHOR_INPUT.value = product.author || '';
            DESC_INPUT.value = product.description || '';
            PRICE_INPUT.value = parseFloat(product.price).toFixed(2); 
            
            SAVE_BUTTON.textContent = 'Actualizar Producto';
            showForm();
        };

        const saveProduct = async (e) => {
            e.preventDefault();
            
            if (!isAuthReady || !userId) {
                FORM_ERROR.textContent = 'Error: Sesión no autenticada.';
                FORM_ERROR.classList.remove('hidden');
                return;
            }

            const title = TITLE_INPUT.value.trim();
            const author = AUTHOR_INPUT.value.trim();
            const description = DESC_INPUT.value.trim();
            const price = parseFloat(PRICE_INPUT.value.trim());

            if (!title || !description || isNaN(price) || price < 0) {
                FORM_ERROR.textContent = 'Por favor, rellena todos los campos de forma válida.';
                FORM_ERROR.classList.remove('hidden');
                return;
            }
            
            SAVE_BUTTON.disabled = true;
            FORM_ERROR.classList.add('hidden');
            

            try {
                const productData = {
                    title,
                    author,
                    description,
                    price,
                    userId: userId, 
                };

                if (isEditing) {
                    const docRef = doc(db, PRODUCTS_COLLECTION_PATH, editingProductId);
                    await updateDoc(docRef, productData);
                } else {
                    const newDocRef = doc(collection(db, PRODUCTS_COLLECTION_PATH));
                    await setDoc(newDocRef, {
                        ...productData,
                        createdAt: serverTimestamp(),
                    });
                }
                
                hideForm();

            } catch (error) {
                console.error("Error al guardar el producto:", error);
                FORM_ERROR.textContent = `Error al guardar: ${error.message}`;
                FORM_ERROR.classList.remove('hidden');
            } finally {
                SAVE_BUTTON.disabled = false;
            }
        };

        const deleteProduct = async () => {
            if (!productToDelete) return;

            CONFIRM_BUTTON.disabled = true; // Deshabilitar el botón de confirmación
            CANCEL_DELETE_BUTTON.disabled = true; // Deshabilitar el botón de cancelar
            
            MODAL_ELEMENT.classList.add('hidden');
            MODAL_ELEMENT.classList.remove('flex');
            
            try {
                const docRef = doc(db, PRODUCTS_COLLECTION_PATH, productToDelete.id);
                await deleteDoc(docRef);

            } catch (error) {
                console.error("Error al eliminar el producto:", error);
                // Si ocurre un error, mostrarlo en el formulario de creación (aunque no esté visible)
                const errorDisplay = document.getElementById('form-error-message');
                if (errorDisplay) {
                    errorDisplay.textContent = `Error al eliminar: ${error.message}.`;
                    errorDisplay.classList.remove('hidden');
                }
            } finally {
                CONFIRM_BUTTON.disabled = false;
                CANCEL_DELETE_BUTTON.disabled = false;
                productToDelete = null;
            }
        };


        const showConfirmModal = (product) => {
            productToDelete = product; 
            MODAL_ELEMENT.classList.remove('hidden');
            MODAL_ELEMENT.classList.add('flex');
        };

        const hideConfirmModal = () => {
            MODAL_ELEMENT.classList.add('hidden');
            MODAL_ELEMENT.classList.remove('flex');
            productToDelete = null;
        };


        // --- 6. Event Listeners ---

        // Configurar listener para todos los elementos de navegación (barra superior)
        NAV_ELEMENTS.forEach(el => {
            el.addEventListener('click', handleNavigationClick);
        });

        // Configurar listener para las tarjetas principales (para hacerlas clickeables)
        CARD_ELEMENTS.forEach(card => {
            card.addEventListener('click', handleNavigationClick);
            
            // Eliminamos la detención de propagación aquí. La función handleNavigationClick
            // ahora es responsable de determinar el target correcto si se pulsa un botón.
            // Esto permite que el botón "Ver Detalles" funcione.
        });
        
        // Eventos del Formulario de Productos
        ADD_BUTTON.addEventListener('click', (e) => {
             // Detener propagación para evitar doble clic si se pulsa cerca de otro elemento
            e.stopPropagation(); 
            if (FORM_CONTAINER.classList.contains('hidden')) {
                hideForm(); // Resetear antes de mostrar
                showForm();
            } else {
                hideForm();
            }
        });
        CANCEL_BUTTON.addEventListener('click', hideForm);
        PRODUCT_FORM.addEventListener('submit', saveProduct);
        CONFIRM_BUTTON.addEventListener('click', deleteProduct);
        CANCEL_DELETE_BUTTON.addEventListener('click', hideConfirmModal);

        // Iniciar la aplicación: Primero la vista principal, luego Firebase
        showView('main');
        initializeFirebase();

    </script>
</body>
</html>
