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

        /* Estilos del Modal del Logo y Utilidad (Modal) */
        .custom-logo-container {
            width: 100%; max-width: 280px; margin: 0 auto;
            background-color: white; border: 2px solid #003366; 
            border-radius: 0.75rem;
        }
        .logo-ejmr { font-size: 1.8rem; font-weight: 900; line-height: 1; color: #1f2937; }
        .logo-m { font-size: 9rem; line-height: 1; font-weight: 900; color: #000000; margin-top: -20px; }
        .logo-title-acronym-modal {
            font-size: 0.9rem; font-weight: 900; color: #003366;
            padding: 5px 10px; background-color: #ffcc00; 
            border-radius: 0.25rem; display: inline-block; margin-bottom: 5px;
        }
        .autonomy-concept {
            font-size: 1.1rem; font-weight: 900; color: #000000; 
            margin-top: 15px; padding-top: 8px; width: 90%; 
        }
        .etae-concept {
            font-size: 0.85rem; font-weight: 700; color: #dc2626; 
            margin-top: 5px; padding-bottom: 5px; width: 90%;
            border-top: 2px solid #003366; padding-top: 8px;
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
            height: 150px; /* Altura fija para el contenedor de la imagen */
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
            object-fit: cover; /* Asegura que la imagen cubra el área sin deformarse */
        }
    </style>
</head>
<body class="bg-bg-light min-h-screen font-sans">

    <!-- Mensaje de Notificación (Reemplazo de alert()) -->
    <div id="message-container" class="message-modal hidden">
        <div id="message-content" class="text-sm font-semibold"></div>
    </div>
    
    <!-- Modal de Logo Personalizado/Contexto (UMEJUMAC Detalle) -->
    <div id="info-modal" class="hidden fixed inset-0 bg-black bg-opacity-50 z-40 flex items-center justify-center fade-in">
        <div class="bg-white p-6 rounded-xl shadow-2xl max-w-sm w-full">
            <div class="p-4 text-center custom-logo-container border-2 border-primary-dark rounded-xl">
                <!-- Acrónimo Superior: UMEJUMAC (Modal) -->
                <p class="logo-title-acronym-modal mx-auto">
                    UMEJUMAC
                </p>

                <!-- EJMR (Edgar José Morales Rojas) - Más pequeño -->
                <p class="logo-ejmr mx-auto mt-2">EJMR</p>

                <!-- M (Letra principal) - Más grande -->
                <p class="logo-m mx-auto mt-2">M</p>
                
                <!-- Concepto de Autonomía -->
                <p class="autonomy-concept mx-auto">
                    AUTONOMY CONCEPT
                </p>

                <!-- Definición de ETAE (Equipo de Trabajo de Alta Efectividad) -->
                <p class="etae-concept mx-auto">
                    ETAE: Equipo de Trabajo de Alta Efectividad
                </p>
            </div>
            <button onclick="toggleModal('info-modal')" class="mt-4 w-full bg-primary-dark text-white p-2 rounded-lg font-semibold hover:bg-opacity-90 transition">
                Cerrar Información
            </button>
        </div>
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
                
                <!-- Campo 4: URL de Imagen (Nuevo) -->
                <div class="mb-4">
                    <label for="product-image-url" class="block text-sm font-medium text-gray-700">URL de la Imagen (Opcional)</label>
                    <input type="url" id="product-image-url" placeholder="https://ejemplo.com/imagen.jpg" class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-primary-dark focus:border-primary-dark">
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
                
                <!-- Logo M + UMEJUMAC + PULSAR (Vuelve a Vista Principal al hacer clic y abre modal de info) -->
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

                <!-- Botones de Navegación -->
                <nav class="flex space-x-2 sm:space-x-4">
                    <button id="nav-btn-asesoria-detalle" data-view="asesoria-detalle" class="nav-btn text-white" onclick="switchView('asesoria-detalle')">1. Asesoría en Salud Colectiva</button>
                    <button id="nav-btn-bienes-servicios-detalle" data-view="bienes-servicios-detalle" class="nav-btn text-white" onclick="switchView('bienes-servicios-detalle')">2. Bienes y Servicios</button>
                    <button id="nav-btn-ventas-detalle" data-view="ventas-detalle" class="nav-btn text-white" onclick="switchView('ventas-detalle')">3. Ventas de Producto</button>
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

        <!-- 4. VISTA DETALLE: Ventas de Producto (Dinámico con Firebase) -->
        <section id="ventas-detalle-view" class="view fade-in">
            <h1 class="text-3xl font-extrabold text-primary-dark mb-8 border-b-4 border-accent-gold pb-2">
                3. Ventas de Producto
            </h1>
            <button onclick="switchView('principal')" class="text-sm bg-gray-200 text-gray-800 p-2 rounded-lg mb-4 hover:bg-gray-300 transition">
                ← Volver a Vista Principal
            </button>
            <p class="text-lg text-gray-700 mb-6">Catálogo dinámico de publicaciones y otros bienes de UMEJUMAC.</p>
            
            <!-- Botón para abrir el modal de agregar producto -->
            <button onclick="toggleModal('add-product-modal')" class="text-sm bg-accent-gold text-primary-dark font-bold p-3 rounded-lg mb-4 hover:bg-yellow-400 transition flex items-center space-x-2">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path></svg>
                <span>Agregar Nuevo Producto</span>
            </button>

            <!-- Contenedor de la lista de productos (Cargado por JS) -->
            <div id="product-list-container" class="mt-4 grid grid-cols-1 md:grid-cols-2 gap-6">
                <p class="text-center text-gray-500 col-span-full" id="loading-message">Iniciando conexión. Si tarda, revise la consola.</p>
            </div>
        </section>

    </main>

    <!-- Lógica de la Aplicación y Firebase -->
    <script type="module">
        // Importaciones de Firebase
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot, query, setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Variables Globales de Firebase
        let db;
        let auth;
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
         * Agrega un nuevo producto a la colección de ventas.
         */
        async function addProduct(event) {
            event.preventDefault(); // Previene el envío estándar del formulario
            
            const form = document.getElementById('add-product-form');
            const name = form.elements['product-name'].value;
            const category = form.elements['product-category'].value;
            const price = parseFloat(form.elements['product-price'].value);
            const description = form.elements['product-description'].value;
            const imageUrl = form.elements['product-image-url'].value; // Nuevo campo

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
                    imageUrl: imageUrl.trim() || '', // Guarda la URL o una cadena vacía
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
                    // Si el mensaje de carga aún existe, lo eliminamos.
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
            const placeholderImageUrl = `https://placehold.co/400x150/003366/ffcc00?text=${product.category.substring(0, 1) + 'P'}`;
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
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('active');
            });

            // Mostrar la vista seleccionada
            const targetView = document.getElementById(viewId + '-view');
            
            if (targetView) {
                targetView.classList.add('active');
            }
            
            // Activar el botón de navegación correspondiente (solo si es una vista de detalle)
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

        // Asignar la función addProduct al evento submit del formulario
        document.addEventListener('DOMContentLoaded', () => {
            const form = document.getElementById('add-product-form');
            if (form) {
                form.addEventListener('submit', addProduct);
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
