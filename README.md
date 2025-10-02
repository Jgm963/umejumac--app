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
        /* Ajuste específico para la portada del libro */
        .cover-placeholder {
            height: 180px; /* Altura fija para la portada del libro */
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 1rem;
            text-align: center;
        }
        /* Estilo para el título del libro en el placeholder */
        .cover-placeholder span {
            font-size: 1.25rem;
            line-height: 1.4;
            display: block;
            max-height: 100%;
            overflow: hidden;
            word-break: break-word;
        }
        
        /* Contenedor de la imagen real */
        .cover-image {
            height: 180px;
            width: 100%;
            object-fit: cover; /* Asegura que la imagen cubra el área sin deformarse */
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
        
        /* Contenedor del Logo 'M' que ahora incluye texto y es clickeable */
        .logo-click-area {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            transition: all 0.2s;
            padding: 0.25rem; /* Pequeño padding para el área de click */
            border-radius: 0.5rem;
        }
        .logo-click-area:hover {
            background-color: rgba(255, 255, 255, 0.1); /* Ligero fondo al pasar el ratón */
        }

        /* Estilo para RESALTAR la imagen/botón del logo 'M' */
        #logo-image {
            /* Fondo amarillo para asegurar visibilidad si la imagen falla */
            background-color: #ffcc00; 
            border: 2px solid #ffcc00; /* Borde de acento */
            border-radius: 0.5rem; /* Bordes redondeados */
            padding: 4px; 
            transition: all 0.2s ease-in-out;
            box-shadow: 0 0 8px rgba(255, 204, 0, 0.7); /* Sombra que resalta */
        }
        .logo-click-area:hover #logo-image {
            transform: scale(1.05); /* Ligeramente más grande al pasar el mouse/tocar */
            box-shadow: 0 0 12px rgba(255, 204, 0, 1);
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
        
        /* ====================================
           ESTILOS DEL LOGO PERSONALIZADO (Modal)
           ==================================== */
        .custom-logo-container {
            width: 100%;
            max-width: 250px;
            margin: 0 auto;
            background-color: white; /* Fondo blanco */
            border: 2px solid #003366; /* Borde azul marino */
        }
        .logo-m {
            /* M Negra sobre fondo blanco */
            font-size: 7rem;
            line-height: 1;
            font-weight: 900;
            color: #000000; /* Negro */
            text-shadow: none; /* Sin sombra */
        }
        .logo-acronym {
            font-size: 1rem;
            font-weight: 500;
            color: #444;
            margin-top: -5px; /* Ajuste visual */
        }
        .acronym-highlight {
            font-weight: 900;
            color: #003366; /* Azul marino para resaltar E J M R */
            font-size: 1.1rem;
            padding: 0 2px;
        }
        .autonomy-concept {
            font-size: 1.2rem; /* Un poco más grande para destacar */
            font-weight: 900;
            color: #000000; /* ¡Negro! */
            margin-top: 10px; /* Separación de las iniciales */
            border-top: 2px solid #003366; /* Línea de separación */
            padding-top: 8px;
            width: 90%; /* Ancho para la línea */
        }
        /* Nuevo estilo para ETAE: Menor tamaño y color rojo sutil */
        .etae-concept {
            font-size: 0.8rem;
            font-weight: 700;
            color: #dc2626; /* Rojo sutil (red-600) */
            margin-top: 5px; 
            padding-bottom: 5px;
            width: 90%;
            border-bottom: 1px solid #e5e7eb; /* Línea divisoria muy ligera */
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
                <!-- Texto descriptivo ahora MÁS VISIBLE -->
                <p class="text-yellow-300 text-sm mt-1 font-extrabold">Ver Logo (Pulsa)</p>
            </div>
            
            <nav class="flex flex-wrap justify-center sm:justify-end space-x-3 sm:space-x-6 text-sm font-medium">
                <!-- Enlaces de navegación -->
                <a href="#" class="nav-link hover:text-gray-300 transition py-1" data-target="asesoria" onclick="showView('asesoria')">Asesoría</a>
                <a href="#" class="nav-link hover:text-gray-300 transition py-1" data-target="bienes" onclick="showView('bienes')">Bienes y Servicios</a>
                <a href="#" class="nav-link hover:text-gray-300 transition font-bold py-1 cursor-pointer" data-target="gallery" onclick="showView('gallery')">Ventas</a>
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
                <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">Añadir Nuevo Producto (Venta)</h3>
                <form id="product-form" class="space-y-4">
                    <input type="text" id="product-title" placeholder="Título (Ej: Autonomy Concept | Equipo Quirúrgico)" required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    <input type="text" id="product-author" placeholder="Autor o Formato (Ej: EJMR | Modelo 2024)" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    
                    <!-- CAMPO CLAVE PARA IMAGEN (ACEPTA ID DE ARCHIVO SUBIDO o URL externa) -->
                    <input type="text" id="product-image-url" 
                        placeholder="Pega aquí el ID o URL de la imagen subida (Ej: uploaded:nombre.png-ID_completo)" 
                        title="Para usar una imagen subida: haz clic en el archivo, copia su ID completo y pégalo aquí."
                        class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    <!-- /CAMPO CLAVE PARA IMAGEN -->
                        
                    <textarea id="product-description" rows="2" placeholder="Descripción breve..." required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500 resize-none"></textarea>
                    <input type="number" step="0.01" id="product-price" placeholder="Precio (Ej: 25.00)" required class="w-full p-3 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    
                    <div class="flex space-x-3">
                        <!-- Botón de guardar: Inicialmente deshabilitado. Se habilitará con la autenticación de Firebase. -->
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

    <!-- Modal de Confirmación para Eliminar (Existente) -->
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
    
    <!-- ====================================
         MODAL DEL LOGO PERSONALIZADO
         ==================================== -->
    <div id="logo-modal" class="fixed inset-0 bg-gray-900 bg-opacity-80 hidden items-center justify-center p-4 z-50 transition-opacity duration-300" onclick="hideLogoModal()">
        <div class="bg-white rounded-xl p-6 sm:p-8 shadow-2xl max-w-lg w-full relative transform scale-95 opacity-0 transition-all duration-300" onclick="event.stopPropagation()">
            
            <!-- TÍTULO CENTRADO -->
            <div class="text-center mb-6">
                <h3 class="text-2xl font-extrabold text-blue-800">
                    UMÉJUMAC
                </h3>
                <p class="text-sm font-medium text-gray-500">
                    Unidad Médica Jurídica Morales AC
                </p>
            </div>

            <!-- Contenedor del Logo de Fantasía (Diseño SVG/CSS) -->
            <div class="flex flex-col items-center justify-center text-center mb-6 p-4 rounded-xl bg-white">
                
                <!-- Letra M Grande (Negra sobre blanco) -->
                <div class="custom-logo-container border-2 border-gray-300 rounded-xl p-4 flex flex-col items-center shadow-lg">
                    <div class="logo-m font-extrabold">M</div>

                    <!-- Acrónimo EJMR -->
                    <div class="logo-acronym">
                        <span class="acronym-highlight">E</span>dgar <span class="acronym-highlight">J</span>osé <span class="acronym-highlight">M</span>orales <span class="acronym-highlight">R</span>oa
                    </div>

                    <!-- Autonomy Concept -->
                    <div class="autonomy-concept">
                        Autonomy Concept
                    </div>
                    
                    <!-- NUEVO ELEMENTO: ETAE -->
                    <div class="etae-concept">
                        ETAE: Equipo de Trabajo de Alta Efectividad
                    </div>
                </div>
            </div>

            <!-- BOTÓN DE CERRAR MODAL (Ajustado a más pequeño y centrado) -->
            <div class="flex justify-center mt-6"> 
                <button onclick="hideLogoModal()" class="w-auto py-2 px-6 bg-red-600 text-white font-semibold rounded-lg hover:bg-red-700 transition duration-150 text-sm">
                    Cerrar Ventana
                </button>
            </div>
            
        </div>
    </div>

    <!-- Firebase SDKs -->
    <script type="module">
        // Importaciones de Firebase (Se cargan solo si están definidas)
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        // NOTA: Se ha corregido la importación para incluir addDoc, el cual es crucial para agregar nuevos documentos.
        import { getFirestore, doc, setDoc, onSnapshot, collection, query, serverTimestamp, deleteDoc, updateDoc, addDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        
        // Comprobar si las variables de Canvas/Firebase están definidas.
        const firebaseConfigExists = typeof __firebase_config !== 'undefined' && Object.keys(JSON.parse(__firebase_config)).length > 0;
        
        if (firebaseConfigExists) {
            setLogLevel('Debug');
        }

        // Variables globales de Canvas
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = firebaseConfigExists ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

        let app, db, auth;
        let userId = null;
        let isAuthReady = false;
        // La bandera isStaticMode se usa para saber si estamos en GitHub Pages o Canvas
        let isStaticMode = !firebaseConfigExists; 

        
        // URL de Imagen por defecto para productos que no tienen imagen
        const DEFAULT_IMAGE_URL = "https://placehold.co/400x180/003366/FFFFFF?text=UMAJUMAC%20PRODUCTO%20N/A";

        // RUTA PÚBLICA DE FIREBASE
        const PRODUCTS_COLLECTION_PATH = `artifacts/${appId}/public/data/umemajuc_products`;


        // Referencias de elementos del DOM (Secciones)
        const VIEWS = document.querySelectorAll('.view');
        
        // Referencias de Navegación
        const NAV_ELEMENTS = document.querySelectorAll('[data-target]');
        const CARD_ELEMENTS = document.querySelectorAll('.main-section-card');
        
        // Referencias del Logo y Modal
        const LOGO_CLICK_AREA = document.querySelector('.logo-click-area'); 
        const LOGO_MODAL = document.getElementById('logo-modal');

        // Referencias del Formulario y Galería de Productos
        const ADD_BUTTON = document.getElementById('add-product-btn');
        const FORM_CONTAINER = document.getElementById('creation-form-container');
        const PRODUCT_FORM = document.getElementById('product-form');
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

            // Ocultar o mostrar el botón de agregar producto y desactivarlo en modo estático
            ADD_BUTTON.style.display = (targetViewId === 'products-gallery') ? 'block' : 'none';
            if (targetViewId === 'products-gallery' && isStaticMode) {
                // Deshabilitar el botón + Nuevo Producto en modo GitHub
                ADD_BUTTON.disabled = true; 
                ADD_BUTTON.textContent = 'Galería Estática (Solo Lectura)';
                // Mostrar mensaje de carga estática si la galería está vacía en modo estático
                if (PRODUCTS_CONTAINER.children.length === 0 || PRODUCTS_CONTAINER.querySelector('#empty-message')) {
                     PRODUCTS_CONTAINER.innerHTML = '<p class="text-center text-gray-500 col-span-full py-10">Cargando productos estáticos...</p>';
                     loadStaticProducts(); // Volver a cargar si es necesario
                }

            } else {
                 ADD_BUTTON.disabled = !isAuthReady; // Solo se habilita si hay autenticación
                 ADD_BUTTON.textContent = isAuthReady ? '+ Nuevo Producto' : 'Cargando Autenticación...';
            }
            
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
            
            if (event.target.tagName === 'BUTTON' && event.target.closest('.main-section-card')) {
                 targetElement = event.target.closest('.main-section-card');
            }

            targetView = targetElement.dataset.target;

            if (targetView) {
                showView(targetView);
            }
        };

        // --- Lógica del Modal del Logo ---
        window.showLogoModal = () => {
            LOGO_MODAL.classList.remove('hidden');
            LOGO_MODAL.classList.add('flex');
            setTimeout(() => {
                LOGO_MODAL.querySelector('div').classList.remove('scale-95', 'opacity-0');
            }, 10);
        };

        window.hideLogoModal = () => {
            LOGO_MODAL.querySelector('div').classList.add('scale-95', 'opacity-0');
            setTimeout(() => {
                LOGO_MODAL.classList.add('hidden');
                LOGO_MODAL.classList.remove('flex');
            }, 300); 
        };


        // --- 2. Inicialización y Autenticación de Firebase / Carga Estática ---

        const initializeFirebase = async () => {
            if (isStaticMode) {
                // Modo Estático (GitHub Pages): No Firebase, no Auth.
                userId = 'STATIC_USER_GH';
                isAuthReady = false; // El CRUD no está listo
                SAVE_BUTTON.disabled = true; 
                USER_INFO_ELEMENT.textContent = `Modo Estático (GitHub)`;
                USER_INFO_ELEMENT.classList.remove('hidden');
                // La carga estática se hará al mostrar la vista de galería
                return;
            }

            // Modo Dinámico (Canvas): Inicializar Firebase.
            try {
                app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);

                // Autenticar con el token proporcionado por Canvas o anónimamente
                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }

                // Configurar el listener de estado de autenticación
                onAuthStateChanged(auth, (user) => {
                    if (user) {
                        userId = user.uid;
                        isAuthReady = true;
                        SAVE_BUTTON.disabled = false;
                        ADD_BUTTON.textContent = '+ Nuevo Producto';
                        ADD_BUTTON.disabled = false;
                        USER_INFO_ELEMENT.textContent = `Sesión: ${userId.substring(0, 8)}...`;
                        USER_INFO_ELEMENT.classList.remove('hidden');
                        listenForProducts();
                    } else {
                        userId = null;
                        isAuthReady = false;
                        SAVE_BUTTON.disabled = true;
                        ADD_BUTTON.textContent = 'Acceso Restringido';
                        ADD_BUTTON.disabled = true;
                        console.error("No se pudo autenticar al usuario.");
                        USER_INFO_ELEMENT.textContent = 'Sin Sesión';
                    }
                });

            } catch (error) {
                console.error("Error al inicializar Firebase o autenticar:", error);
                // Si falla la inicialización, se comporta como estático (con error)
                isStaticMode = true; 
                userId = 'ERROR_CONFIG';
                isAuthReady = false;
                SAVE_BUTTON.disabled = true;
                ADD_BUTTON.textContent = 'Error de Config.';
                ADD_BUTTON.disabled = true;
                USER_INFO_ELEMENT.textContent = 'Error de Config. Firebase';
            }
        };


        // --- DATA ESTÁTICA PARA MODO GITHUB PAGES (VISUALIZACIÓN) ---
        const STATIC_PRODUCTS = [
            // Se utiliza la imagen subida por el usuario para este producto
            { id: 'static-1', title: 'Autonomy Concept', author: 'Dr. Morales AC (EJMR)', description: 'Publicación clave sobre la autonomía profesional y gestión de riesgos médicos y legales.', price: 29.99, userId: 'STATIC_USER_GH', imageUrl: "uploaded:Imagen de WhatsApp 2025-10-01 a las 19.35.19_d1a48fa8.jpg-68106d3f-6ffc-469c-ad83-1067d2879e7f" },
            { id: 'static-2', title: 'Guía Legal Sanitaria 2024', author: 'UMÉJUMAC Editorial', description: 'Manual detallado sobre la normativa sanitaria y su aplicación en la práctica médica y administrativa.', price: 45.00, userId: 'STATIC_USER_GH', imageUrl: "https://placehold.co/400x180/ccff00/003366?text=NORMATIVA%20LEGAL" },
            { id: 'static-3', title: 'Servicio de Consultoría Premium', author: 'EJMR - Morales Roa', description: 'Acceso a un paquete de 10 horas de consultoría especializada en gestión hospitalaria y legal.', price: 199.99, userId: 'STATIC_USER_GH', imageUrl: "https://placehold.co/400x180/006699/FFFFFF?text=CONSULTORÍA%20VIP" },
        ];

        const loadStaticProducts = () => {
            const loadingElement = document.getElementById('loading-products');
            if (loadingElement) loadingElement.style.display = 'none';

            PRODUCTS_CONTAINER.innerHTML = '';
            
            // Renderizar los productos estáticos
            STATIC_PRODUCTS.forEach(product => {
                PRODUCTS_CONTAINER.appendChild(renderProduct(product));
            });
             PRODUCTS_CONTAINER.innerHTML += '<p class="text-center text-orange-600 col-span-full mt-4">Esta es una **Galería Estática** para visualización en GitHub. Para editar/guardar, acceda al editor de Canvas.</p>';
        };

        
        // --- 3. Renderizado de Productos y Corrección de Imagen ---
        
        const getImageUrl = (urlOrId) => {
            if (!urlOrId) return DEFAULT_IMAGE_URL;
            
            // Si es un ID de archivo subido, construye la URL interna
            if (urlOrId.startsWith('uploaded:')) {
                return `/_internal/content/${urlOrId}`;
            }

            // Si es una URL externa o el default, se devuelve tal cual.
            return urlOrId;
        };


        const renderProduct = (product) => {
            // El CRUD (Editar/Eliminar) solo está disponible en Canvas (no en modo estático) y si el usuario es el creador.
            const isOwner = isStaticMode ? false : product.userId === userId;
            
            const card = document.createElement('div');
            card.id = `product-${product.id}`;
            card.className = `book-card bg-white rounded-xl relative shadow-md fade-in flex flex-col`;

            // Resuelve el ID de Canvas a una URL válida o usa el placeholder
            const displayImageUrl = getImageUrl(product.imageUrl); 

            let coverContent = '';

            // Renderizar la imagen
            if (displayImageUrl && displayImageUrl !== DEFAULT_IMAGE_URL) {
                coverContent = `
                    <img 
                        src="${displayImageUrl}" 
                        alt="Portada de ${product.title}" 
                        class="cover-image rounded-t-xl" 
                        onerror="this.onerror=null; this.outerHTML='<div class=\\"cover-placeholder placeholder-img rounded-t-xl\\"><span>ERROR: No se pudo cargar la imagen</span></div>';"
                    />
                `;
            } else {
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
                    <!-- Título (Azul oscuro como en la imagen) -->
                    <h4 class="text-lg font-bold text-blue-800 mb-1">${product.title || 'Título del Producto'}</h4>
                    <!-- Autor / Formato -->
                    <p class="text-xs text-gray-500 mb-2">${product.author || 'Autor: N/A'}</p>
                    <!-- Descripción -->
                    <p class="text-sm text-gray-700 flex-grow mb-3">${product.description || 'Descripción: Reemplace este texto con información detallada.'}</p>
                    
                    <!-- Información de Creación/Propiedad (Solo en modo dinámico) -->
                    ${!isStaticMode ? `<p class="text-xs text-gray-400 mb-2">Creador: <span class="font-mono break-all">${product.userId.substring(0, 8)}...</span></p>` : ''}

                    <!-- Precio (Verde llamativo) -->
                    <div class="mt-auto">
                        <p class="price-text font-bold text-green-600">Precio: USD ${parseFloat(product.price).toFixed(2)}</p>
                    </div>

                    <!-- Botones de Acción (Solo si es el propietario y NO es modo estático) -->
                    ${(isOwner && !isStaticMode) ? `
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
            
            // Adjuntar eventos de edición y eliminación SOLO si es el propietario y NO es modo estático
            if (isOwner && !isStaticMode) {
                card.querySelector('.edit-btn')?.addEventListener('click', () => startEdit(product));
                card.querySelector('.delete-btn')?.addEventListener('click', () => showConfirmModal(product));
            }

            return card;
        };


        // --- 4. Escucha de Firestore (Solo en modo dinámico) ---
        const listenForProducts = () => {
            if (isStaticMode || !db) {
                // Si falla la carga de Firebase, carga la estática para la visualización en GitHub
                if (document.getElementById('products-gallery').style.display === 'block') {
                    loadStaticProducts();
                }
                return;
            }

            const productsRef = collection(db, PRODUCTS_COLLECTION_PATH);
            const q = query(productsRef); 

            onSnapshot(q, (snapshot) => {
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


        // --- 5. Lógica de CRUD y Modal (Solo en modo dinámico) ---
        
        const showForm = () => {
            if(isStaticMode || !isAuthReady) {
                 FORM_ERROR.textContent = 'Error: Sesión no autenticada.';
                 FORM_ERROR.classList.remove('hidden');
                 return;
            }
            FORM_CONTAINER.classList.remove('hidden');
            PRODUCTS_CONTAINER.scrollIntoView({ behavior: 'smooth', block: 'start' });
            TITLE_INPUT.focus();
        };

        const hideForm = () => {
            FORM_CONTAINER.classList.add('hidden');
            PRODUCT_FORM.reset();
            isEditing = false;
            editingProductId = null;
            
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
            editingProductId = product.id;
            
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
            
            if (isStaticMode || !isAuthReady || !userId) {
                FORM_ERROR.textContent = 'Error: Sesión no autenticada.';
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

                if (isEditing) {
                    // Si se está editando, usamos updateDoc en el documento existente
                    const docRef = doc(db, PRODUCTS_COLLECTION_PATH, editingProductId);
                    await updateDoc(docRef, productData);
                } else {
                    // Si es un nuevo producto, usamos addDoc (lo más simple)
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

        NAV_ELEMENTS.forEach(el => {
            el.addEventListener('click', handleNavigationClick);
        });

        CARD_ELEMENTS.forEach(card => {
            card.addEventListener('click', handleNavigationClick);
        });
        
        LOGO_CLICK_AREA.addEventListener('click', (e) => {
            e.stopPropagation(); 
            showLogoModal();
        });


        // Eventos del Formulario de Productos
        ADD_BUTTON.addEventListener('click', (e) => {
            e.stopPropagation(); 
            if (isStaticMode) return;
            // Al hacer clic, si está visible lo oculta, sino lo muestra (modo toggle)
            if (FORM_CONTAINER.classList.contains('hidden')) {
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
        
        LOGO_MODAL.addEventListener('click', (e) => {
            if (e.target === LOGO_MODAL) {
                hideLogoModal();
            }
        });


        // Iniciar la aplicación
        showView('main');
        initializeFirebase();

    </script>
</body>
</html>
