<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unidad Jurídica - Vista Principal</title>
    <!-- Carga de Tailwind CSS para un diseño responsive y moderno -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        // Configuración de colores corporativos
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'primary-dark': '#003366', // Azul oscuro (corporativo)
                        'accent-gold': '#ffcc00', // Amarillo/Oro (acento)
                        'bg-light': '#f7f9fc', // Fondo claro
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        /* Importación de fuente Inter */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

        /* ====================================
           ESTILOS GENERALES Y DE NAVEGACIÓN
           ==================================== */

        .fade-in { animation: fadeIn 0.5s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        /* CRÍTICO: Todas las vistas inician ocultas */
        .view { display: none; }
        
        /* Asegura que la vista activa se muestre */
        .view.active { display: block; }

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
            display: flex; 
            align-items: center;
            justify-content: center;
            height: 32px; 
            width: 32px;
        }
        .logo-click-area:hover #logo-image {
            transform: scale(1.05); 
            box-shadow: 0 0 12px rgba(255, 204, 0, 1);
        }
        
        /* Contenedor del texto UMEJUMAC y Pulsar */
        .logo-text-container {
            display: flex;
            flex-direction: column;
            align-items: flex-start; /* Alinea el texto a la izquierda dentro del contenedor */
            padding-left: 0.5rem; /* Pequeño espaciado del ícono M */
        }
        
        .logo-acronym {
            font-size: 1.25rem; /* text-xl */
            font-weight: 800; /* font-extrabold */
            color: #ffcc00; /* text-accent-gold */
            line-height: 1.2;
        }

        .logo-pulsar {
            font-size: 0.75rem; /* text-xs */
            font-weight: 700;
            color: #f7f9fc; /* color blanco/claro */
            margin-top: -0.25rem; /* Subir un poco para juntarlo con el acrónimo */
            line-height: 1.2;
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

        /* Estilos de Utilidad */
        .nav-btn {
            padding: 0.5rem 0.75rem; font-weight: 500; font-size: 0.875rem; 
            transition: all 0.2s; border-bottom: 3px solid transparent;
            text-align: center; line-height: 1.2;
        }
        .nav-btn.active {
            border-bottom: 3px solid #ffcc00; /* Borde activo dorado */
            background-color: rgba(255, 255, 255, 0.1);
        }
        .message-modal {
            position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%);
            z-index: 50; background-color: #003366; color: white;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3); border-radius: 0.5rem; padding: 1rem;
        }
        
        /* Estilos para la tarjeta de producto */
        .product-card {
            border-top: 4px solid #ffcc00;
            transition: all 0.2s;
        }
        .product-card:hover {
            box-shadow: 0 4px 10px rgba(0, 51, 102, 0.1);
            transform: translateY(-2px);
        }

        .product-image-container {
            width: 100%;
            height: 150px; 
            overflow: hidden;
            border-radius: 0.5rem;
            margin-bottom: 0.75rem;
            background-color: #f0f0f0;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .product-image {
            width: 100%;
            height: 100%;
            object-fit: cover; 
        }
        
        /* Estilos del Gestor de Archivos */
        .file-upload-box {
            border: 2px dashed #003366;
            background-color: #f0f8ff;
            transition: background-color 0.3s;
        }
        .file-upload-box:hover {
            background-color: #e0f2ff;
        }
    </style>
</head>
<body class="bg-bg-light min-h-screen font-sans">

    <!-- Mensaje de Notificación (Reemplazo de alert()) -->
    <div id="message-container" class="message-modal hidden">
        <div id="message-content" class="text-sm font-semibold"></div>
    </div>
    
    <!-- Modal para Agregar Productos de Venta -->
    <div id="add-product-modal" class="hidden fixed inset-0 bg-black bg-opacity-50 z-40 flex items-center justify-center fade-in">
        <div class="bg-white p-6 rounded-xl shadow-2xl max-w-lg w-full">
            <h2 class="text-2xl font-bold text-primary-dark mb-4 border-b pb-2">Registrar Nuevo Producto</h2>
            <form id="add-product-form">
                <!-- Campo 1: Nombre del Producto -->
                <div class="mb-4">
                    <label for="product-name" class="block text-sm font-medium text-gray-700">Nombre del Producto</label>
                    <input type="text" id="product-name" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-primary-dark focus:border-primary-dark">
                </div>
                
                <!-- Campo 2: Categoría -->
                <div class="mb-4">
                    <label for="product-category" class="block text-sm font-medium text-gray-700">Categoría</label>
                    <select id="product-category" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-primary-dark focus:border-primary-dark">
                        <option value="">Seleccione una categoría</option>
                        <option value="Libros">Libros/Publicaciones</option>
                        <option value="Instrumental">Instrumental Quirúrgico</option>
                        <option value="Bienes">Otros Bienes</option>
                        <option value="Servicios">Servicios Especializados</option>
                    </select>
                </div>

                <!-- Campo 3: Precio -->
                <div class="mb-4">
                    <label for="product-price" class="block text-sm font-medium text-gray-700">Precio (MXN)</label>
                    <input type="number" id="product-price" step="0.01" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-primary-dark focus:border-primary-dark" min="0">
                </div>
                
                <!-- Campo 4: URL de Imagen -->
                <div class="mb-4">
                    <label for="product-image-url" class="block text-sm font-medium text-gray-700">URL de la Imagen (Opcional)</label>
                    <input type="url" id="product-image-url" placeholder="Pegue aquí la URL obtenida en el Gestor de Archivos" class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-primary-dark focus:border-primary-dark">
                    <!-- Enlace para ir al gestor, útil para copiar la URL -->
                    <button type="button" onclick="switchView('archivo-manager'); toggleModal('add-product-modal');" class="mt-2 text-xs text-primary-dark hover:text-accent-gold font-semibold underline">
                        Ir al Gestor de Archivos para obtener URL
                    </button>
                </div>

                <!-- Campo 5: Descripción -->
                <div class="mb-6">
                    <label for="product-description" class="block text-sm font-medium text-gray-700">Descripción</label>
                    <textarea id="product-description" rows="3" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-primary-dark focus:border-primary-dark"></textarea>
                </div>

                <div class="flex justify-end space-x-3">
                    <button type="button" onclick="toggleModal('add-product-modal')" class="bg-gray-300 text-gray-800 p-2 rounded-lg font-semibold hover:bg-gray-400 transition">Cancelar</button>
                    <button type="submit" class="bg-primary-dark text-white p-2 rounded-lg font-semibold hover:bg-opacity-90 transition">Guardar Producto</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Header y Navegación Sticky -->
    <header class="header-nav">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16 sm:h-20">
                
                <!-- Logo M + UMEJUMAC + PULSAR -->
                <button class="logo-click-area flex-row space-x-2" onclick="switchView('principal')">
                    <div class="flex items-center space-x-2">
                        <!-- Icono M -->
                        <div id="logo-image">
                            <span class="text-primary-dark font-black text-xl">M</span>
                        </div>
                        <!-- Texto UMEJUMAC y Pulsar -->
                        <div class="logo-text-container hidden sm:flex">
                            <span class="logo-acronym">UMEJUMAC</span>
                            <span class="logo-pulsar">Pulsar</span>
                        </div>
                    </div>
                </button>

                <!-- Botones de Navegación (Solo las 3 vistas públicas) -->
                <nav class="flex space-x-2 sm:space-x-4 overflow-x-auto pb-1">
                    <button id="nav-btn-asesoria-detalle" data-view="asesoria-detalle" class="nav-btn text-white whitespace-nowrap" onclick="switchView('asesoria-detalle')">1. Asesoría en Salud Colectiva</button>
                    <button id="nav-btn-bienes-servicios-detalle" data-view="bienes-servicios-detalle" class="nav-btn text-white whitespace-nowrap" onclick="switchView('bienes-servicios-detalle')">2. Bienes y Servicios</button>
                    <button id="nav-btn-ventas-detalle" data-view="ventas-detalle" class="nav-btn text-white whitespace-nowrap" onclick="switchView('ventas-detalle')">3. Ventas de Producto</button>
                    <!-- EL BOTÓN DE GESTOR DE ARCHIVOS SE ELIMINÓ DE AQUÍ -->
                </nav>
            </div>
        </div>
    </header>

    <!-- Contenido Principal: Vistas -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- 1. VISTA PRINCIPAL (Hub Unificado) -->
        <section id="principal-view" class="view active fade-in">
            <div class="text-center mb-10 p-8 rounded-xl shadow-lg border-t-8 border-primary-dark bg-white">
                <h1 class="text-3xl sm:text-4xl font-extrabold text-primary-dark mb-2">
                    Unidad Médica Jurídica Morales AC
                </h1>
                <p class="text-lg text-gray-600 font-semibold">
                    Soluciones profesionales integrales en **Salud, Derecho y Comercio**.
                </p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                
                <!-- Tarjeta 1: Asesoría en Salud Colectiva -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" onclick="switchView('asesoria-detalle')">
                    <span class="text-4xl font-black text-primary-dark mb-2 block">1</span>
                    <h3 class="text-xl font-bold text-primary-dark">Asesoría en Salud Colectiva</h3>
                    <p class="text-gray-600 mt-2 text-sm">
                        Consultoría especializada en normatividad médica, legal y administrativa.
                    </p>
                    <span class="inline-block bg-indigo-100 text-indigo-800 text-xs font-semibold px-3 py-1 rounded-full mt-4">VER DETALLE</span>
                </div>

                <!-- Tarjeta 2: Bienes y Servicios -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" onclick="switchView('bienes-servicios-detalle')">
                    <span class="text-4xl font-black text-primary-dark mb-2 block">2</span>
                    <h3 class="text-xl font-bold text-primary-dark">Bienes y Servicios</h3>
                    <p class="text-gray-600 mt-2 text-sm">
                        Provisión y gestión de bienes y servicios.
                    </p>
                    <span class="inline-block bg-green-100 text-green-800 text-xs font-semibold px-3 py-1 rounded-full mt-4">VER DETALLE</span>
                </div>

                <!-- Tarjeta 3: Ventas de Producto -->
                <div class="main-section-card p-6 rounded-xl shadow-lg" onclick="switchView('ventas-detalle')">
                    <span class="text-4xl font-black text-primary-dark mb-2 block">3</span>
                    <h3 class="text-xl font-bold text-primary-dark">Ventas de Producto</h3>
                    <p class="text-gray-600 mt-2 text-sm">
                        Colección de publicaciones, instrumental y otros materiales.
                    </p>
                    <span class="inline-block bg-yellow-100 text-yellow-800 text-xs font-semibold px-3 py-1 rounded-full mt-4">VER DETALLE</span>
                </div>
            </div>
        </section>


        <!-- 2. VISTA DETALLE: Asesoría en Salud Colectiva -->
        <section id="asesoria-detalle-view" class="view fade-in">
            <!-- ... (Contenido de Asesoría en Salud Colectiva) ... -->
            <h1 class="text-3xl font-extrabold text-primary-dark mb-8 border-b-4 border-accent-gold pb-2">
                1. Asesoría en Salud Colectiva
            </h1>
            <button onclick="switchView('principal')" class="text-sm bg-gray-200 text-gray-800 p-2 rounded-lg mb-4 hover:bg-gray-300 transition">
                ← Volver a Vista Principal
            </button>
            <p class="text-lg text-gray-700 mb-6">Detalle del contenido de Asesoría.</p>
            

            <div class="placeholder-card bg-white p-8 rounded-xl shadow-lg border-t-8 border-primary-dark">
                <p class="text-2xl font-bold text-primary-dark">Servicios de Consultoría Legal y Normativa</p>
                <p class="text-gray-500 mt-2">Contenido pendiente de llenar.</p>
            </div>
        </section>

        <!-- 3. VISTA DETALLE: Bienes y Servicios -->
        <section id="bienes-servicios-detalle-view" class="view fade-in">
             <!-- ... (Contenido de Bienes y Servicios) ... -->
            <h1 class="text-3xl font-extrabold text-primary-dark mb-8 border-b-4 border-accent-gold pb-2">
                2. Bienes y Servicios
            </h1>
            <button onclick="switchView('principal')" class="text-sm bg-gray-200 text-gray-800 p-2 rounded-lg mb-4 hover:bg-gray-300 transition">
                ← Volver a Vista Principal
            </button>
            <p class="text-lg text-gray-700 mb-6">Detalle del contenido de Bienes y Servicios.</p>
            
            
            <div class="placeholder-card bg-white p-8 rounded-xl shadow-lg border-t-8 border-primary-dark">
                <p class="text-2xl font-bold text-primary-dark">Catálogo de Suministros Operativos</p>
                <p class="text-gray-500 mt-2">Información de bienes y provisión de servicios.</p>
            </div>
        </section>

        <!-- 4. VISTA DETALLE: Ventas de Producto (Dinámico con Firestore) -->
        <section id="ventas-detalle-view" class="view fade-in">
            <h1 class="text-3xl font-extrabold text-primary-dark mb-8 border-b-4 border-accent-gold pb-2">
                3. Ventas de Producto
            </h1>
            <button onclick="switchView('principal')" class="text-sm bg-gray-200 text-gray-800 p-2 rounded-lg mb-4 hover:bg-gray-300 transition">
                ← Volver a Vista Principal
            </button>
            <p class="text-lg text-gray-700 mb-6">Catálogo dinámico de publicaciones y otros bienes de UMEJUMAC.</p>
            
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-6 space-y-4 sm:space-y-0">
                <!-- Botón para abrir el modal de agregar producto -->
                <button onclick="toggleModal('add-product-modal')" class="w-full sm:w-auto text-sm bg-accent-gold text-primary-dark font-bold p-3 rounded-lg hover:bg-yellow-400 transition flex items-center justify-center sm:justify-start space-x-2 shadow-md">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path></svg>
                    <span>Agregar Nuevo Producto</span>
                </button>

                <!-- BOTÓN DE ACCESO AL GESTOR (ADMINISTRATIVO) -->
                <button onclick="switchView('archivo-manager')" class="w-full sm:w-auto text-sm bg-gray-600 text-white font-semibold p-3 rounded-lg hover:bg-gray-700 transition flex items-center justify-center sm:justify-start space-x-2 shadow-md">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-6l-2-2H5a2 2 0 00-2 2z"></path></svg>
                    <span>Gestor de Archivos (Admin)</span>
                </button>
            </div>

            <!-- Contenedor de la lista de productos (Cargado por JS) -->
            <div id="product-list-container" class="mt-4 grid grid-cols-1 md:grid-cols-2 gap-6">
                <p class="text-center text-gray-500 col-span-full" id="loading-message">Iniciando conexión. Si tarda, revise la consola.</p>
            </div>
        </section>

        <!-- 5. VISTA DETALLE: Gestor de Archivos (Upload con Firebase Storage) -->
        <!-- NOTA: Esta vista NO tiene botón de navegación principal -->
        <section id="archivo-manager-view" class="view fade-in">
            <h1 class="text-3xl font-extrabold text-primary-dark mb-8 border-b-4 border-accent-gold pb-2">
                Gestor de Archivos (Subida de Imágenes)
            </h1>
            <button onclick="switchView('ventas-detalle')" class="text-sm bg-gray-200 text-gray-800 p-2 rounded-lg mb-4 hover:bg-gray-300 transition">
                ← Volver a Ventas
            </button>
            <p class="text-lg text-gray-700 mb-6">Sube tus imágenes de producto aquí para obtener una **URL** que luego usarás para publicarlas en la sección de Ventas.</p>

            <div class="bg-white p-6 rounded-xl shadow-lg border-t-8 border-primary-dark">
                <h2 class="text-xl font-bold text-primary-dark mb-4">Subir Imagen</h2>
                
                <div class="file-upload-box p-6 rounded-lg text-center cursor-pointer mb-6">
                    <input type="file" id="file-input" accept="image/*" class="hidden">
                    <label for="file-input" class="block">
                        <svg class="mx-auto h-12 w-12 text-primary-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12"></path></svg>
                        <p class="mt-1 text-sm font-semibold text-gray-600">Haz clic para seleccionar o arrastra una imagen</p>
                        <p class="text-xs text-gray-500" id="file-name-display">Ningún archivo seleccionado.</p>
                    </label>
                </div>
                
                <button id="upload-btn" class="w-full bg-primary-dark text-white p-3 rounded-lg font-semibold hover:bg-opacity-90 transition disabled:opacity-50" disabled>
                    Subir Imagen y Generar URL
                </button>

                <!-- Barra de progreso (Oculta al inicio) -->
                <div id="progress-bar-container" class="mt-4 hidden">
                    <div class="text-sm font-medium text-primary-dark mb-1">Progreso de Subida: <span id="upload-percentage">0%</span></div>
                    <div class="w-full bg-gray-200 rounded-full h-2.5">
                        <div id="upload-progress" class="bg-accent-gold h-2.5 rounded-full" style="width: 0%"></div>
                    </div>
                </div>

                <!-- Resultado de la URL -->
                <div id="url-result-container" class="mt-6 p-4 bg-gray-100 border border-gray-300 rounded-lg hidden">
                    <p class="font-semibold text-primary-dark mb-2">URL Generada (Copia y pega en Ventas):</p>
                    <input type="text" id="generated-url-input" class="w-full p-2 text-sm bg-white border border-gray-400 rounded-md truncate" readonly>
                    <button onclick="copyToClipboard('generated-url-input')" class="mt-2 w-full bg-green-500 text-white p-2 rounded-lg text-sm font-semibold hover:bg-green-600 transition">
                        Copiar URL
                    </button>
                    <img id="uploaded-image-preview" src="" alt="Previsualización" class="mt-4 max-w-full h-32 object-contain mx-auto border rounded-md hidden">
                </div>

            </div>
        </section>

    </main>

    <!-- Lógica de la Aplicación y Firebase -->
    <script type="module">
        // Importaciones de Firebase
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot, query, setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { getStorage, ref, uploadBytesResumable, getDownloadURL } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-storage.js";


        // Variables Globales de Firebase
        let db;
        let auth;
        let storage;
        let appId;
        let userId;

        /**
         * Inicializa Firebase, autentica al usuario y carga los datos.
         */
        async function initFirebase() {
            setLogLevel('Debug'); // Habilitar logs de Firebase

            try {
                // 1. Configuración de la App ID y Firebase Config
                appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
                const firebaseConfig = JSON.parse(__firebase_config);

                // 2. Inicializar App y Servicios
                const app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);
                storage = getStorage(app); // Inicializar Firebase Storage

                // 3. Autenticación
                if (typeof __initial_auth_token !== 'undefined') { 
                    await signInWithCustomToken(auth, __initial_auth_token); 
                } else { 
                    await signInAnonymously(auth); 
                }
                
                userId = auth.currentUser?.uid || 'anonymous-user';
                console.log("Firebase inicializado. User ID:", userId);
                
                // 4. Iniciar la carga de productos
                loadProducts();

            } catch (error) {
                console.error("Error al inicializar Firebase o autenticar:", error);
                showMessage("Error al cargar la aplicación. Revise la consola.", 'error');
            }
        }

        /**
         * Maneja la subida de archivos a Firebase Storage.
         */
        async function uploadFile() {
            const fileInput = document.getElementById('file-input');
            const file = fileInput.files[0];
            const uploadBtn = document.getElementById('upload-btn');
            const urlResultContainer = document.getElementById('url-result-container');
            const progressBarContainer = document.getElementById('progress-bar-container');
            const uploadProgress = document.getElementById('upload-progress');
            const uploadPercentage = document.getElementById('upload-percentage');
            const generatedUrlInput = document.getElementById('generated-url-input');
            const uploadedImagePreview = document.getElementById('uploaded-image-preview');


            if (!file) {
                showMessage("Por favor, seleccione un archivo de imagen primero.", 'info');
                return;
            }

            uploadBtn.disabled = true;
            uploadBtn.textContent = 'Subiendo...';
            progressBarContainer.classList.remove('hidden');
            urlResultContainer.classList.add('hidden');
            uploadedImagePreview.classList.add('hidden');
            uploadProgress.style.width = '0%';
            uploadPercentage.textContent = '0%';
            generatedUrlInput.value = '';

            try {
                // Definir la ruta de almacenamiento: /sales_images/{userId}/imagen_timestamp
                const fileName = `${Date.now()}_${file.name}`;
                const storageRef = ref(storage, `sales_images/${userId}/${fileName}`);
                const uploadTask = uploadBytesResumable(storageRef, file);

                // Monitorear el progreso de la subida
                uploadTask.on('state_changed', 
                    (snapshot) => {
                        const progress = (snapshot.bytesTransferred / snapshot.totalBytes) * 100;
                        uploadProgress.style.width = progress + '%';
                        uploadPercentage.textContent = `${Math.round(progress)}%`;
                    }, 
                    (error) => {
                        console.error("Error de subida:", error);
                        showMessage("Error al subir el archivo: " + error.message, 'error');
                        progressBarContainer.classList.add('hidden');
                        uploadBtn.disabled = false;
                        uploadBtn.textContent = 'Subir Imagen y Generar URL';
                    }, 
                    async () => {
                        // Subida completada con éxito, obtener la URL de descarga
                        const downloadURL = await getDownloadURL(uploadTask.snapshot.ref);
                        
                        generatedUrlInput.value = downloadURL;
                        uploadedImagePreview.src = downloadURL;
                        
                        // Mostrar resultados
                        progressBarContainer.classList.add('hidden');
                        urlResultContainer.classList.remove('hidden');
                        uploadedImagePreview.classList.remove('hidden');
                        
                        showMessage("¡Subida exitosa! URL lista para copiar.", 'success');
                        
                        uploadBtn.disabled = false;
                        uploadBtn.textContent = 'Subir Otra Imagen';
                        fileInput.value = ''; // Resetear input de archivo
                        document.getElementById('file-name-display').textContent = 'Ningún archivo seleccionado.';
                    }
                );
            } catch (error) {
                console.error("Error en la subida:", error);
                showMessage("Ocurrió un error inesperado al subir el archivo.", 'error');
                progressBarContainer.classList.add('hidden');
                uploadBtn.disabled = false;
                uploadBtn.textContent = 'Subir Imagen y Generar URL';
            }
        }

        /**
         * Agrega un nuevo producto a la colección de ventas.
         */
        async function addProduct(event) {
            event.preventDefault(); // Previene el envío estándar del formulario
            
            const form = document.getElementById('add-product-form');
            const name = form.elements['product-name'].value;
            const category = form.elements['product-category'].value;
            const price = parseFloat(form.elements['product-price'].value);
            const description = form.elements['product-description'].value;
            const imageUrl = form.elements['product-image-url'].value; 

            if (!name || !category || isNaN(price) || !description) {
                showMessage("Por favor, complete todos los campos obligatorios.", 'info');
                return;
            }

            try {
                const productData = {
                    name: name,
                    category: category,
                    price: price,
                    description: description,
                    imageUrl: imageUrl.trim() || '', 
                    createdAt: Date.now(),
                    creatorId: userId,
                };
                
                // Ruta pública para datos compartidos
                const salesCollectionPath = `/artifacts/${appId}/public/data/sales_products`;
                
                await addDoc(collection(db, salesCollectionPath), productData);

                showMessage("Producto registrado exitosamente.", 'success');
                form.reset(); // Limpia el formulario
                toggleModal('add-product-modal'); // Cierra el modal

            } catch (e) {
                console.error("Error al agregar documento: ", e);
                showMessage("Error al guardar el producto. Intente de nuevo.", 'error');
            }
        }

        /**
         * Escucha cambios en tiempo real en la colección de productos y los muestra.
         */
        function loadProducts() {
            if (!db) return;

            const salesCollectionPath = `/artifacts/${appId}/public/data/sales_products`;
            const productsQuery = query(collection(db, salesCollectionPath));
            const listContainer = document.getElementById('product-list-container');
            const loadingMessage = document.getElementById('loading-message');

            onSnapshot(productsQuery, (snapshot) => {
                const products = [];
                snapshot.forEach((doc) => {
                    products.push({ id: doc.id, ...doc.data() });
                });

                // Ordenar por más reciente primero
                products.sort((a, b) => b.createdAt - a.createdAt);

                listContainer.innerHTML = ''; // Limpiar lista anterior

                if (products.length === 0) {
                    listContainer.innerHTML = '<p class="text-center text-gray-500 col-span-full">Aún no hay productos registrados. ¡Agregue el primero!</p>';
                } else {
                    products.forEach(product => {
                        listContainer.innerHTML += createProductCard(product);
                    });
                }
                
                if (loadingMessage) {
                    const existingLoadingMessage = document.getElementById('loading-message');
                    if (existingLoadingMessage) existingLoadingMessage.remove();
                }
            }, (error) => {
                console.error("Error al escuchar cambios en Firestore:", error);
                listContainer.innerHTML = '<p class="text-center text-red-500 col-span-full">Error al cargar productos.</p>';
            });
        }

        /**
         * Genera el HTML para una tarjeta de producto.
         */
        function createProductCard(product) {
            const formattedPrice = new Intl.NumberFormat('es-MX', { style: 'currency', currency: 'MXN' }).format(product.price);
            
            // Lógica para la imagen o el placeholder
            // Ejemplo de placeholder con color de la categoría
            const categoryInitial = product.category.substring(0, 1).toUpperCase();
            const placeholderImageUrl = `https://placehold.co/400x150/003366/ffcc00?text=${categoryInitial}P`;
            
            // Incluye el manejo de error para la imagen
            const imageHtml = product.imageUrl ? 
                `<img src="${product.imageUrl}" class="product-image" alt="Imagen de ${product.name}" onerror="this.onerror=null;this.src='${placeholderImageUrl}';" />` :
                `<img src="${placeholderImageUrl}" class="product-image" alt="Imagen no disponible" />`;

            let categoryColor = 'bg-gray-100 text-gray-700';

            switch(product.category) {
                case 'Libros':
                    categoryColor = 'bg-indigo-100 text-indigo-800';
                    break;
                case 'Instrumental':
                    categoryColor = 'bg-red-100 text-red-800';
                    break;
                default:
                    categoryColor = 'bg-green-100 text-green-800';
                    break;
            }

            return `
                <div class="product-card bg-white p-5 rounded-xl shadow-md flex flex-col">
                    <!-- Contenedor de Imagen -->
                    <div class="product-image-container">
                        ${imageHtml}
                    </div>
                    
                    <div>
                        <div class="flex items-center justify-between mb-2">
                            <span class="inline-block ${categoryColor} text-xs font-semibold px-3 py-1 rounded-full">${product.category}</span>
                        </div>
                        <h3 class="text-xl font-bold text-primary-dark mb-1">${product.name}</h3>
                        <p class="text-gray-600 text-sm h-12 overflow-hidden mb-3">${product.description}</p>
                    </div>
                    <div class="mt-auto pt-3 border-t border-gray-200 flex justify-between items-center">
                        <span class="text-2xl font-extrabold text-red-600">${formattedPrice}</span>
                        <button class="bg-primary-dark text-white text-xs font-semibold px-4 py-2 rounded-full hover:bg-opacity-90 transition">Ver Detalles</button>
                    </div>
                </div>
            `;
        }


        // Funciones de Utilidad (fuera del módulo para ser globales)
        window.switchView = function(viewId) {
            // Ocultar todas las vistas y remover la clase 'active' de los botones de navegación
            document.querySelectorAll('.view').forEach(view => {
                view.classList.remove('active');
            });
            // Solo los 3 botones públicos tienen la clase 'nav-btn'
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('active');
            });

            // Mostrar la vista seleccionada
            const targetView = document.getElementById(viewId + '-view');
            
            if (targetView) {
                targetView.classList.add('active');
            }
            
            // Activar el botón de navegación correspondiente (solo si es una vista de detalle pública)
            const targetBtn = document.getElementById('nav-btn-' + viewId);
            if (targetBtn) {
                targetBtn.classList.add('active');
            }
        }

        window.toggleModal = function(modalId) {
            const modal = document.getElementById(modalId);
            if (modal) {
                modal.classList.toggle('hidden');
            }
        }

        window.showMessage = function(message, type) {
            const container = document.getElementById('message-container');
            const content = document.getElementById('message-content');
            
            let bgColor = 'bg-primary-dark';
            if (type === 'success') {
                bgColor = 'bg-green-600';
            } else if (type === 'error') {
                bgColor = 'bg-red-600';
            } else if (type === 'info') {
                bgColor = 'bg-blue-600';
            }
            
            container.className = `message-modal ${bgColor}`;
            content.textContent = message;
            container.classList.remove('hidden');

            setTimeout(() => {
                container.classList.add('hidden');
            }, 3000);
        }

        window.copyToClipboard = function(elementId) {
            const copyText = document.getElementById(elementId);
            try {
                // Selecciona el texto en el input
                copyText.select();
                copyText.setSelectionRange(0, 99999); // Para móviles
                
                // Intenta usar el método moderno (navigator.clipboard)
                if (navigator.clipboard && window.isSecureContext) {
                    navigator.clipboard.writeText(copyText.value).then(() => {
                        showMessage("URL copiada al portapapeles.", 'success');
                    }).catch(() => {
                        // Fallback si la API de Clipboard falla (e.g. en algunos iframes)
                        document.execCommand('copy');
                        showMessage("URL copiada al portapapeles (Fallback).", 'success');
                    });
                } else {
                    // Fallback para entornos no seguros o navegadores antiguos
                    document.execCommand('copy');
                    showMessage("URL copiada al portapapeles (Fallback).", 'success');
                }
            } catch (err) {
                console.error('Error al intentar copiar:', err);
                showMessage("Error: No se pudo copiar la URL.", 'error');
            }
        }


        // Event Listeners
        document.addEventListener('DOMContentLoaded', () => {
            // Evento para el formulario de agregar producto
            const form = document.getElementById('add-product-form');
            if (form) {
                form.addEventListener('submit', addProduct);
            }

            // Eventos para el gestor de archivos
            const fileInput = document.getElementById('file-input');
            const uploadBtn = document.getElementById('upload-btn');

            if (fileInput) {
                fileInput.addEventListener('change', (e) => {
                    const fileNameDisplay = document.getElementById('file-name-display');
                    if (e.target.files.length > 0) {
                        fileNameDisplay.textContent = `Archivo: ${e.target.files[0].name}`;
                        uploadBtn.disabled = false;
                    } else {
                        fileNameDisplay.textContent = 'Ningún archivo seleccionado.';
                        uploadBtn.disabled = true;
                    }
                });
            }

            if (uploadBtn) {
                uploadBtn.addEventListener('click', uploadFile);
            }
        });

        // Inicializar Firebase y la vista al cargar
        window.onload = () => {
             initFirebase();
             window.switchView('principal');
        };
    </script>
</body>
</html>
