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

        .fade-in { animation: fadeIn 0.5s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .view { display: none; }
        
        .placeholder-img {
            background-color: #003366;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.25rem;
            font-weight: 700;
        }

        .cover-placeholder {
            height: 180px; 
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 1rem;
            text-align: center;
        }
        
        .cover-placeholder span {
            font-size: 1.25rem;
            line-height: 1.4;
            display: block;
            max-height: 100%;
            overflow: hidden;
            word-break: break-word;
        }
        
        .cover-image {
            height: 180px;
            width: 100%;
            object-fit: cover; 
        }

        .header-nav {
            background-color: #003366; 
            color: white;
            position: sticky;
            top: 0;
            z-index: 20;
            box-shadow: 0 2px 4px 0 rgba(0,0,0,0.1);
        }
        
        .logo-click-area {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            transition: all 0.2s;
            padding: 0.25rem; 
            border-radius: 0.5rem;
        }
        .logo-click-area:hover {
            background-color: rgba(255, 255, 255, 0.1); 
        }

        #logo-image {
            background-color: #ffcc00; 
            border: 2px solid #ffcc00; 
            border-radius: 0.5rem; 
            padding: 4px; 
            transition: all 0.2s ease-in-out;
            box-shadow: 0 0 8px rgba(255, 204, 0, 0.7); 
        }
        .logo-click-area:hover #logo-image {
            transform: scale(1.05); 
            box-shadow: 0 0 12px rgba(255, 204, 0, 1);
        }
        
        .book-card {
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s, box-shadow 0.2s;
            overflow: hidden; 
        }
        .book-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }

        .main-section-card {
            background-color: #f7f9fc;
            border-left: 5px solid #003366; 
            transition: all 0.3s;
            cursor: pointer; 
        }
        .main-section-card:hover {
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transform: translateY(-5px);
            border-left: 5px solid #ffcc00; 
        }
        
        /* ====================================
           ESTILOS DEL LOGO PERSONALIZADO (Modal)
           ==================================== */
        .custom-logo-container {
            width: 100%;
            max-width: 250px;
            margin: 0 auto;
            background-color: white; 
            border: 2px solid #003366; 
        }
        .logo-m {
            font-size: 7rem;
            line-height: 1;
            font-weight: 900;
            color: #000000; 
            text-shadow: none; 
        }
        .logo-acronym {
            font-size: 1rem;
            font-weight: 500;
            color: #444;
            margin-top: -5px; 
        }
        .acronym-highlight {
            font-weight: 900;
            color: #003366; 
            font-size: 1.1rem;
            padding: 0 2px;
        }
        .autonomy-concept {
            font-size: 1.2rem; 
            font-weight: 900;
            color: #000000; 
            margin-top: 10px; 
            border-top: 2px solid #003366; 
            padding-top: 8px;
            width: 90%; 
        }
        .etae-concept {
            font-size: 0.8rem;
            font-weight: 700;
            color: #dc2626; 
            margin-top: 5px; 
            padding-bottom: 5px;
            width: 90%;
            border-bottom: 1px solid #e5e7eb; 
        }

    </style>
</head>
<body class="bg-gray-100 min-h-screen">

    <!-- Encabezado de Navegación Fijo -->
    <header class="header-nav p-4">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center">
            
            <!-- CONTENEDOR DE LOGO 'M' -->
            <div class="logo-click-area mb-3 sm:mb-0" onclick="showLogoModal()">
                <img 
                    src="https://placehold.co/40x40/ffcc00/003366?text=M" 
                    alt="Logo UMÉJUMAC (M) - Click para ver detalles" 
                    class="h-10 w-auto object-contain" 
                    id="logo-image"
                    onerror="this.onerror=null; this.src='https://placehold.co/40x40/ffcc00/003366?text=M';"
                >
                <p class="text-yellow-300 text-sm mt-1 font-extrabold">Ver Logo (Pulsa)</p>
            </div>
            
            <nav class="flex flex-wrap justify-center sm:justify-end space-x-3 sm:space-x-6 text-sm font-medium">
                <!-- Enlaces de navegación -->
                <a href="#" class="nav-link hover:text-gray-300 transition py-1" data-target="asesoria" onclick="showView('asesoria')">Asesoría</a>
                <a href="#" class="nav-link hover:text-gray-300 transition py-1" data-target="bienes" onclick="showView('bienes')">Bienes y Servicios</a>
                <a href="#" class="nav-link hover:text-gray-300 transition font-bold py-1 cursor-pointer" data-target="gallery" onclick="showView('gallery')">Ventas</a>
                <!-- Botón para agregar un nuevo producto (Solo visible en la galería) -->
                <button id="add-product-btn" class="bg-white text-blue-800 hover:bg-gray-200 px-3 py-1 rounded-full transition duration-150 text-xs sm:text-sm mt-2 sm:mt-0" style="display: none;">
                    Cargando...
                </button>
            </nav>
        </div>
        <!-- Información de autenticación y Modo -->
        <div class="flex justify-center sm:justify-end mt-2 mr-4 text-xs">
            <span id="system-status" class="px-2 py-0.5 rounded-full font-bold text-white bg-gray-500">Cargando Estado...</span>
            <span id="user-info" class="text-gray-300 ml-4 hidden sm:block"></span>
        </div>
    </header>

    <div id="app-container" class="max-w-7xl mx-auto p-4 sm:p-8">

        <!-- ====================================
             1. VISTA PRINCIPAL (DEFAULT) 
             ==================================== -->
        <section id="main-view" class="view p-0 bg-transparent rounded-xl">
            <!-- Título Principal RESTAURADO -->
            <div class="text-center mb-10 p-6 bg-white rounded-xl shadow-md">
                <h2 class="text-4xl font-extrabold text-blue-800 mb-2">Unidad Médica Jurídica Morales AC</h2>
                <p class="text-xl text-gray-700 max-w-4xl mx-auto">
                    Soluciones profesionales integrales en **Salud, Derecho y Comercio**.
                </p>
            </div>

            <!-- Contenedor de las 3 Secciones -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                
                <!-- SECCIÓN 1: Asesoría en salud colectiva -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" data-target="asesoria" onclick="showView('asesoria')">
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
                <div class="main-section-card p-6 rounded-xl shadow-lg" data-target="bienes" onclick="showView('bienes')">
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
                <div class="main-section-card p-6 rounded-xl shadow-lg" data-target="gallery" onclick="showView('gallery')">
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
            <h2 class="text-3xl font-extrabold text-gray-800 mb-6 text-center sm:text-left border-b pb-2">Galería de Productos Exclusivos</h2>

            <!-- Formulario de Creación Rápida (Inicialmente oculto) -->
            <div id="creation-form-container" class="bg-white p-6 rounded-xl shadow-xl mb-8 hidden fade-in">
                <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">Añadir Nuevo Producto (Venta)</h3>
                <form id="product-form" class="space-y-4">
                    <!-- Campo oculto para almacenar el ID de edición -->
                    <input type="hidden" id="editing-product-id">

                    <input type="text" id="product-title" placeholder="Título (Ej: Autonomy Concept | Equipo Quirúrgico)" required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    <input type="text" id="product-author" placeholder="Autor o Formato (Ej: EJMR | Modelo 2024)" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    
                    <!-- CAMPO CLAVE PARA IMAGEN -->
                    <input type="text" id="product-image-url" 
                        placeholder="Pega aquí el ID o URL de la imagen (Ej: uploaded:nombre.png-ID_completo)" 
                        title="Para usar una imagen subida: haz clic en el archivo, copia su ID completo y pégalo aquí."
                        class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    <!-- /CAMPO CLAVE PARA IMAGEN -->
                        
                    <textarea id="product-description" rows="2" placeholder="Descripción breve..." required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 resize-none"></textarea>
                    <input type="number" step="0.01" id="product-price" placeholder="Precio (Ej: 25.00)" required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    
                    <div class="flex space-x-3">
                        <!-- Botón de guardar: Inicialmente deshabilitado. Se habilita con la autenticación de Firebase. -->
                        <button type="submit" id="save-button" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-4 rounded-xl transition duration-150 ease-in-out disabled:opacity-50" disabled>
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
    
    <!-- MODAL DEL LOGO PERSONALIZADO -->
    <div id="logo-modal" class="fixed inset-0 bg-gray-900 bg-opacity-80 hidden items-center justify-center p-4 z-50 transition-opacity duration-300" onclick="hideLogoModal()">
        <div class="bg-white rounded-xl p-6 sm:p-8 shadow-2xl max-w-lg w-full relative transform scale-95 opacity-0 transition-all duration-300" onclick="event.stopPropagation()">
            
            <div class="text-center mb-6">
                <h3 class="text-2xl font-extrabold text-blue-800">UMÉJUMAC</h3>
                <p class="text-sm font-medium text-gray-500">Unidad Médica Jurídica Morales AC</p>
            </div>

            <div class="flex flex-col items-center justify-center text-center mb-6 p-4 rounded-xl bg-white">
                
                <div class="custom-logo-container border-2 border-gray-300 rounded-xl p-4 flex flex-col items-center shadow-lg">
                    <div class="logo-m font-extrabold">M</div>

                    <div class="logo-acronym">
                        <span class="acronym-highlight">E</span>dgar <span class="acronym-highlight">J</span>osé <span class="acronym-highlight">M</span>orales <span class="acronym-highlight">R</span>oa
                    </div>

                    <div class="autonomy-concept">
                        Autonomy Concept
                    </div>
                    
                    <div class="etae-concept">
                        ETAE: Equipo de Trabajo de Alta Efectividad
                    </div>
                </div>
            </div>

            <div class="flex justify-center mt-6"> 
                <button onclick="hideLogoModal()" class="w-auto py-2 px-6 bg-red-600 text-white font-semibold rounded-lg hover:bg-red-700 transition duration-150 text-sm">
                    Cerrar Ventana
                </button>
            </div>
            
        </div>
    </div>

    <!-- Firebase SDKs -->
    <script type="module">
        // Importaciones de Firebase 
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, onSnapshot, collection, query, serverTimestamp, deleteDoc, updateDoc, addDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        
        // ===============================================
        // LÓGICA DE DETECCIÓN DE MODO Y DEBUGGING CRÍTICO
        // ===============================================
        
        let firebaseConfigExists = false;
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        let configData = {};
        
        try {
            // 1. Verificar si la variable global existe
            if (typeof __firebase_config !== 'undefined') {
                // 2. Intentar parsear el JSON
                configData = JSON.parse(__firebase_config);
            }

            // 3. Verificar si el objeto parseado tiene contenido (ej: una clave apiKey)
            if (Object.keys(configData).length > 0 && configData.apiKey) {
                firebaseConfigExists = true;
                setLogLevel('Debug');
                console.log("SUCCESS: La configuración de Firebase fue encontrada y parseada correctamente. Modo DYNAMIC ON.");
            } else if (typeof __firebase_config !== 'undefined' && __firebase_config.length > 2) {
                 // Caso: existe pero es inválida o no tiene las claves principales
                 console.warn("WARNING: __firebase_config existe pero parece vacía o incompleta. Forzando Modo STATIC.");
            } else {
                 console.warn("WARNING: La variable __firebase_config no está definida. Forzando Modo STATIC.");
            }

        } catch (e) {
            console.error("FATAL ERROR: Falló al parsear __firebase_config JSON. Esto indica un problema de formato. Detalles:", e);
        }

        const firebaseConfig = firebaseConfigExists ? configData : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
        
        // Define el modo basado en la existencia de la config (CRITICAL LINE)
        let isStaticMode = !firebaseConfigExists; 
        
        console.log(`[UMAJUMAC DEBUG] Modo de Aplicación establecido: ${isStaticMode ? 'STATIC (Solo Lectura)' : 'DYNAMIC (CRUD Habilitado)'}`);


        let app, db, auth;
        let userId = null;
        let isAuthReady = false;
        
        // URL de Imagen por defecto para productos que no tienen imagen
        const DEFAULT_IMAGE_URL = "https://placehold.co/400x180/003366/FFFFFF?text=UMAJUMAC%20PRODUCTO%20N/A";

        // RUTA PÚBLICA DE FIREBASE
        const PRODUCTS_COLLECTION_PATH = `artifacts/${appId}/public/data/umemajuc_products`;


        // Referencias de elementos del DOM
        const VIEWS = document.querySelectorAll('.view');
        
        // Referencias de Formulario y Galería
        const ADD_BUTTON = document.getElementById('add-product-btn');
        const FORM_CONTAINER = document.getElementById('creation-form-container');
        const PRODUCT_FORM = document.getElementById('product-form');
        const EDITING_PRODUCT_ID_INPUT = document.getElementById('editing-product-id');
        const TITLE_INPUT = document.getElementById('product-title');
        const AUTHOR_INPUT = document.getElementById('product-author');
        const IMAGE_URL_INPUT = document.getElementById('product-image-url');
        const DESC_INPUT = document.getElementById('product-description');
        const PRICE_INPUT = document.getElementById('product-price');
        const SAVE_BUTTON = document.getElementById('save-button'); 
        const CANCEL_BUTTON = document.getElementById('cancel-button');
        const FORM_ERROR = document.getElementById('form-error-message');
        const PRODUCTS_CONTAINER = document.getElementById('products-gallery').querySelector('.grid');
        const USER_INFO_ELEMENT = document.getElementById('user-info');
        const SYSTEM_STATUS_ELEMENT = document.getElementById('system-status');
        const LOADING_PRODUCTS_ELEMENT = document.getElementById('loading-products');
        
        const MODAL_ELEMENT = document.getElementById('confirm-modal');
        const CONFIRM_BUTTON = document.getElementById('confirm-delete-button');
        const CANCEL_DELETE_BUTTON = document.getElementById('cancel-delete-button');

        let productToDelete = null;
        let isEditing = false;
        
        // --- 1. Lógica de Navegación de Vistas ---

        // Función central para mostrar una vista y ocultar las demás
        window.showView = (viewId) => { 
            let targetViewId;

            if (viewId === 'main') {
                targetViewId = 'main-view';
            } else if (viewId === 'gallery') {
                targetViewId = 'products-gallery'; 
            } else {
                targetViewId = `${viewId}-view`; 
            }

            let targetViewFound = false;
            
            VIEWS.forEach(view => {
                view.classList.remove('fade-in');
                view.style.display = 'none';

                if (view.id === targetViewId) {
                    view.style.display = 'block';
                    view.classList.add('fade-in');
                    targetViewFound = true;
                }
            });

            // Lógica del botón + Nuevo Producto
            ADD_BUTTON.style.display = (targetViewId === 'products-gallery') ? 'block' : 'none';
            if (targetViewId === 'products-gallery') {
                if (isStaticMode) {
                    ADD_BUTTON.disabled = true; 
                    ADD_BUTTON.textContent = 'Galería Estática (Solo Lectura)';
                    loadStaticProducts(); // Cargar estáticos si es el modo
                } else {
                    // Modo dinámico, la autenticación debe estar lista
                    ADD_BUTTON.disabled = !isAuthReady; 
                    ADD_BUTTON.textContent = isAuthReady ? '+ Nuevo Producto' : 'Conectando Base de Datos...';
                }
            }
            
            if (targetViewId !== 'products-gallery') {
                 hideForm(); // Ocultar el formulario si salimos de la galería
            }
            
            if (targetViewFound) {
                window.scrollTo(0, 0); // Desplazarse al inicio de la página al cambiar de vista
            }
        };

        // Lógica del Modal del Logo (se mantiene igual)
        window.showLogoModal = () => {
            const modalInner = document.querySelector('#logo-modal > div');
            if(modalInner) modalInner.classList.remove('scale-95', 'opacity-0');
            document.getElementById('logo-modal').classList.remove('hidden');
            document.getElementById('logo-modal').classList.add('flex');
        };

        window.hideLogoModal = () => {
            const modalInner = document.querySelector('#logo-modal > div');
            if(modalInner) modalInner.classList.add('scale-95', 'opacity-0');
            setTimeout(() => {
                document.getElementById('logo-modal').classList.add('hidden');
                document.getElementById('logo-modal').classList.remove('flex');
            }, 300); 
        };


        // --- 2. Inicialización y Autenticación de Firebase / Carga Estática ---
        const updateSystemStatus = (isDynamic, statusText, statusColor, userInfoText = '') => {
            SYSTEM_STATUS_ELEMENT.textContent = statusText;
            SYSTEM_STATUS_ELEMENT.className = `px-2 py-0.5 rounded-full font-bold text-white ${statusColor}`;
            USER_INFO_ELEMENT.textContent = userInfoText;
            USER_INFO_ELEMENT.classList.remove('hidden');
        };

        const initializeFirebase = async () => {
            if (isStaticMode) {
                // Modo Estático: No Firebase, no Auth.
                userId = 'STATIC_USER';
                isAuthReady = false; 
                SAVE_BUTTON.disabled = true; 
                updateSystemStatus(false, 'Modo Estático (Sin CRUD)', 'bg-red-500', 'Sin Base de Datos');
                loadStaticProducts();
                return;
            }

            // Modo Dinámico: Inicializar Firebase.
            try {
                app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);
                updateSystemStatus(true, 'Conectando...', 'bg-yellow-500', 'Autenticando usuario...');

                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }

                onAuthStateChanged(auth, (user) => {
                    if (user) {
                        userId = user.uid;
                        isAuthReady = true;
                        SAVE_BUTTON.disabled = false;
                        updateSystemStatus(true, 'Modo Dinámico ACTIVO', 'bg-green-600', `ID: ${userId.substring(0, 8)}...`);
                        listenForProducts();
                        // Actualiza el botón de la galería si la vista actual es la galería
                        if (document.getElementById('products-gallery').style.display === 'block') {
                             ADD_BUTTON.textContent = '+ Nuevo Producto';
                             ADD_BUTTON.disabled = false;
                        }

                    } else {
                        userId = null;
                        isAuthReady = false;
                        SAVE_BUTTON.disabled = true;
                        updateSystemStatus(false, 'Modo Dinámico (Error Auth)', 'bg-red-500', 'Se requiere autenticación');
                        ADD_BUTTON.textContent = 'Acceso Restringido';
                        ADD_BUTTON.disabled = true;
                    }
                });

            } catch (error) {
                console.error("Error al inicializar Firebase o autenticar:", error);
                isStaticMode = true; 
                userId = 'ERROR_AUTH';
                isAuthReady = false;
                SAVE_BUTTON.disabled = true;
                updateSystemStatus(false, 'Error de Conexión o Config.', 'bg-red-700', 'Volviendo a Modo Estático');
                loadStaticProducts();
            }
        };


        // --- DATA ESTÁTICA PARA MODO LECTURA ---
        const STATIC_PRODUCTS = [
            // Producto clave con la imagen subida
            { id: 'static-1', title: 'Autonomy Concept', author: 'Dr. Morales AC (EJMR)', description: 'Publicación clave sobre la autonomía profesional y gestión de riesgos médicos y legales.', price: 29.99, userId: 'STATIC_USER', imageUrl: "uploaded:Imagen de WhatsApp 2025-10-01 a las 19.35.19_d1a48fa8.jpg-68106d3f-6ffc-469c-ad83-1067d2879e7f" },
            { id: 'static-2', title: 'Guía Legal Sanitaria 2024', author: 'UMÉJUMAC Editorial', description: 'Manual detallado sobre la normativa sanitaria y su aplicación en la práctica médica y administrativa.', price: 45.00, userId: 'STATIC_USER', imageUrl: "https://placehold.co/400x180/ccff00/003366?text=NORMATIVA%20LEGAL" },
            { id: 'static-3', title: 'Servicio de Consultoría Premium', author: 'EJMR - Morales Roa', description: 'Acceso a un paquete de 10 horas de consultoría especializada en gestión hospitalaria y legal.', price: 199.99, userId: 'STATIC_USER', imageUrl: "https://placehold.co/400x180/006699/FFFFFF?text=CONSULTORÍA%20VIP" },
        ];

        const loadStaticProducts = () => {
            if (LOADING_PRODUCTS_ELEMENT) LOADING_PRODUCTS_ELEMENT.style.display = 'none';

            PRODUCTS_CONTAINER.innerHTML = '';
            
            STATIC_PRODUCTS.forEach(product => {
                PRODUCTS_CONTAINER.appendChild(renderProduct(product));
            });
             PRODUCTS_CONTAINER.innerHTML += '<p class="text-center text-orange-600 col-span-full mt-4 p-4 border border-orange-200 rounded-lg bg-orange-50">Esta es una **Galería Estática** para visualización. El botón de Agregar está deshabilitado. Para usar el CRUD, asegúrese de estar en el editor de Canvas.</p>';
        };

        
        // --- 3. Renderizado de Productos y Lógica de Imagen (se mantiene igual) ---
        
        const getImageUrl = (urlOrId) => {
            if (!urlOrId) return DEFAULT_IMAGE_URL;
            
            if (urlOrId.startsWith('uploaded:')) {
                return `/_internal/content/${urlOrId}`;
            }

            return urlOrId;
        };


        const renderProduct = (product) => {
            // El propietario es el usuario estático o el usuario actual, solo importa para botones de edición
            const isOwner = isStaticMode ? false : product.userId === userId;
            
            const card = document.createElement('div');
            card.id = `product-${product.id}`;
            card.className = `book-card bg-white rounded-xl relative shadow-md fade-in flex flex-col`;

            const displayImageUrl = getImageUrl(product.imageUrl); 

            let coverContent = `
                <img 
                    src="${displayImageUrl}" 
                    alt="Portada de ${product.title}" 
                    class="cover-image rounded-t-xl" 
                    onerror="this.onerror=null; this.src='${DEFAULT_IMAGE_URL}'; this.outerHTML='<div class=\\"cover-placeholder placeholder-img rounded-t-xl\\"><span>${product.title ? 'FALLO AL CARGAR: ' + product.title : 'IMAGEN N/A'}</span></div>';"
                />
            `;
            
            if (displayImageUrl === DEFAULT_IMAGE_URL) {
                 coverContent = `
                    <div class="cover-placeholder placeholder-img rounded-t-xl">
                        <span>${product.title || 'Título N/A'}</span>
                    </div>
                `;
            }


            card.innerHTML = `
                <!-- Bloque de Portada (Imagen o Placeholder) -->
                ${coverContent}

                <!-- Contenido de Detalle -->
                <div class="p-4 flex flex-col flex-grow">
                    <!-- Título -->
                    <h4 class="text-lg font-bold text-blue-800 mb-1">${product.title || 'Título del Producto'}</h4>
                    <!-- Autor / Formato -->
                    <p class="text-xs text-gray-500 mb-2">${product.author || 'Autor: N/A'}</p>
                    <!-- Descripción -->
                    <p class="text-sm text-gray-700 flex-grow mb-3">${product.description || 'Descripción: Reemplace este texto con información detallada.'}</p>
                    
                    <!-- Información de Creación/Propiedad (Solo en modo dinámico) -->
                    ${(!isStaticMode && product.userId) ? `<p class="text-xs text-gray-400 mb-2">Creador: <span class="font-mono break-all">${product.userId.substring(0, 8)}...</span></p>` : ''}

                    <!-- Precio -->
                    <div class="mt-auto">
                        <p class="price-text font-bold text-green-600">Precio: USD ${parseFloat(product.price).toFixed(2)}</p>
                    </div>

                    <!-- Botones de Acción (Solo si es el propietario y NO es modo estático) -->
                    ${(isOwner && !isStaticMode) ? `
                        <div class="flex mt-3 space-x-2">
                            <button class="edit-btn flex-1 text-xs font-semibold py-1.5 px-2 bg-yellow-500 text-white rounded-lg hover:bg-yellow-600 transition" data-id="${product.id}">
                                Editar
                            </button>
                            <button class="delete-btn flex-1 text-xs font-semibold py-1.5 px-2 bg-red-600 text-white rounded-lg hover:bg-red-700 transition" data-id="${product.id}">
                                Eliminar
                            </button>
                        </div>
                    ` : ''}
                </div>
            `;
            
            if (isOwner && !isStaticMode) {
                card.querySelector('.edit-btn')?.addEventListener('click', () => startEdit(product));
                card.querySelector('.delete-btn')?.addEventListener('click', () => showConfirmModal(product));
            }

            return card;
        };


        // --- 4. Escucha de Firestore (Solo en modo dinámico) ---
        const listenForProducts = () => {
            if (isStaticMode || !db) return;

            const productsRef = collection(db, PRODUCTS_COLLECTION_PATH);
            const q = query(productsRef); 

            onSnapshot(q, (snapshot) => {
                if (LOADING_PRODUCTS_ELEMENT) LOADING_PRODUCTS_ELEMENT.style.display = 'none';

                const products = [];
                snapshot.forEach(doc => {
                    products.push({ id: doc.id, ...doc.data() });
                });

                products.sort((a, b) => (b.createdAt?.seconds || 0) - (a.createdAt?.seconds || 0));

                PRODUCTS_CONTAINER.innerHTML = '';
                if (products.length === 0) {
                    PRODUCTS_CONTAINER.innerHTML = '<p id="empty-message" class="text-center text-gray-500 p-6 bg-white rounded-xl shadow-inner col-span-full">La galería de productos está actualmente vacía. Utiliza el botón "+ Nuevo Producto" para añadir uno.</p>';
                } else {
                    products.forEach(product => {
                        PRODUCTS_CONTAINER.appendChild(renderProduct(product));
                    });
                }
            }, (error) => {
                console.error("Error al escuchar productos de Firestore:", error);
                PRODUCTS_CONTAINER.innerHTML = `<p class="text-center text-red-500 p-6 col-span-full">Error al cargar datos de la base de datos: ${error.message}</p>`;
            });
        };


        // --- 5. Lógica de CRUD y Modal (Se mantiene igual, solo se valida el modo) ---
        
        const showForm = () => {
            if(isStaticMode || !isAuthReady) {
                 FORM_ERROR.textContent = 'ERROR: El modo dinámico no está activo. No se puede acceder al formulario.';
                 FORM_ERROR.classList.remove('hidden');
                 return;
            }
            FORM_CONTAINER.classList.remove('hidden');
            FORM_CONTAINER.scrollIntoView({ behavior: 'smooth', block: 'start' }); 
            TITLE_INPUT.focus();
        };

        const hideForm = () => {
            FORM_CONTAINER.classList.add('hidden');
            PRODUCT_FORM.reset();
            isEditing = false;
            EDITING_PRODUCT_ID_INPUT.value = ''; 
            
            if (isAuthReady) { 
                SAVE_BUTTON.disabled = false;
            } else {
                SAVE_BUTTON.disabled = true;
            }
            
            SAVE_BUTTON.textContent = 'Guardar Producto';
            FORM_ERROR.classList.add('hidden');
        };

        const startEdit = (product) => {
            if(isStaticMode || !isAuthReady) return;
            isEditing = true;
            EDITING_PRODUCT_ID_INPUT.value = product.id; 
            
            TITLE_INPUT.value = product.title || '';
            AUTHOR_INPUT.value = product.author || '';
            IMAGE_URL_INPUT.value = product.imageUrl || ''; 
            DESC_INPUT.value = product.description || '';
            PRICE_INPUT.value = parseFloat(product.price).toFixed(2); 
            
            SAVE_BUTTON.textContent = 'Actualizar Producto';
            showForm();
        };

        const saveProduct = async (e) => {
            e.preventDefault();
            
            const editingProductId = EDITING_PRODUCT_ID_INPUT.value;
            
            if (isStaticMode || !isAuthReady || !userId) {
                FORM_ERROR.textContent = 'Error: No tiene permisos para guardar o no está en modo dinámico.';
                FORM_ERROR.classList.remove('hidden');
                SAVE_BUTTON.disabled = true;
                return;
            }

            const title = TITLE_INPUT.value.trim();
            const author = AUTHOR_INPUT.value.trim();
            const imageUrl = IMAGE_URL_INPUT.value.trim(); 
            const description = DESC_INPUT.value.trim();
            const price = parseFloat(PRICE_INPUT.value.trim());

            if (!title || !description || isNaN(price) || price < 0) {
                FORM_ERROR.textContent = 'Por favor, rellena los campos de Título, Descripción y Precio de forma válida.';
                FORM_ERROR.classList.remove('hidden');
                return;
            }
            
            SAVE_BUTTON.disabled = true;
            FORM_ERROR.classList.add('hidden');
            

            try {
                const productData = {
                    title,
                    author,
                    imageUrl, 
                    description,
                    price,
                    userId: userId, 
                };

                if (isEditing && editingProductId) {
                    const docRef = doc(db, PRODUCTS_COLLECTION_PATH, editingProductId);
                    await updateDoc(docRef, productData);
                } else {
                    const productsRef = collection(db, PRODUCTS_COLLECTION_PATH);
                    await addDoc(productsRef, {
                        ...productData,
                        createdAt: serverTimestamp(), 
                    });
                }
                
                hideForm();

            } catch (error) {
                console.error("Error al guardar el producto:", error);
                FORM_ERROR.textContent = `Error al guardar: ${error.message}. Asegúrese de tener conexión a internet.`;
                FORM_ERROR.classList.remove('hidden');
            } finally {
                SAVE_BUTTON.disabled = false;
            }
        };

        const deleteProduct = async () => {
            if (isStaticMode || !productToDelete) return;

            CONFIRM_BUTTON.disabled = true; 
            CANCEL_DELETE_BUTTON.disabled = true; 
            
            MODAL_ELEMENT.classList.add('hidden');
            MODAL_ELEMENT.classList.remove('flex');
            
            try {
                const docRef = doc(db, PRODUCTS_COLLECTION_PATH, productToDelete.id);
                await deleteDoc(docRef);

            } catch (error) {
                console.error("Error al eliminar el producto:", error);
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
            if(isStaticMode) return;
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

        // Eventos de Navegación
        document.querySelectorAll('.nav-link, .main-section-card').forEach(el => {
             el.addEventListener('click', (e) => {
                const target = e.currentTarget.dataset.target;
                if(target && (!e.target.closest('button') || e.target.closest('a'))) {
                    e.preventDefault();
                    showView(target);
                }
             });
        });

        // Eventos del Formulario de Productos
        ADD_BUTTON.addEventListener('click', (e) => {
            e.stopPropagation(); 
            if (isStaticMode || !isAuthReady) return;

            // Modo Toggle: Ocultar si está visible, mostrar/editar si está oculto
            if (FORM_CONTAINER.classList.contains('hidden')) {
                // Al presionar +Nuevo Producto, siempre reseteamos y mostramos para añadir.
                hideForm(); 
                showForm();
            } else {
                hideForm();
            }
        });
        CANCEL_BUTTON.addEventListener('click', hideForm);
        PRODUCT_FORM.addEventListener('submit', saveProduct);
        CONFIRM_BUTTON.addEventListener('click', deleteProduct);
        CANCEL_DELETE_BUTTON.addEventListener('click', hideConfirmModal);
        
        // Cierre de modal al clickear fuera
        document.getElementById('logo-modal').addEventListener('click', (e) => {
            if (e.target.id === 'logo-modal') {
                hideLogoModal();
            }
        });

        // Iniciar la aplicación
        showView('main');
        initializeFirebase();

    </script>
</body>
</html>
