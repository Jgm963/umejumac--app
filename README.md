<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Título de la Aplicación -->
    <title>UMEJUMAC: Unidad Médica Jurídica Morales AC</title> 
    <!-- Carga de Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style> 
        body { 
            font-family: 'Inter', sans-serif; 
            color: #333; 
            background-color: #f0f4f8; 
            scroll-behavior: smooth; 
        } 
        /* Colores inspirados en la bandera de Venezuela */
        .text-venezuelan-primary { color: #FFC107; } /* Amarillo */ 
        .bg-venezuelan-primary { background-color: #003366; } /* Azul */ 
        .bg-venezuelan-secondary { background-color: #FFC107; } /* Amarillo */ 
        .border-venezuelan-primary { border-color: #003366; } /* Azul */ 
        .border-venezuelan-secondary { border-color: #FFC107; } /* Amarillo */    
        
        /* Animaciones para transiciones suaves */
        .fade-in {
            animation: fadeIn 1s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .hidden-section {
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

        /* Ajuste de la cuadrícula para 6 columnas en pantallas muy grandes (2XL) */
        @media (min-width: 1536px) { 
            .grid-2xl-6 {
                grid-template-columns: repeat(6, minmax(0, 1fr));
            }
        }
    </style>
</head>
<body>

<!-- Header and Navigation -->
<header class="bg-venezuelan-primary text-white p-4 shadow-md sticky top-0 z-50">
    <div class="container mx-auto flex justify-between items-center">
        <h1 class="text-3xl font-bold">UMEJUMAC</h1>
        <nav class="hidden md:flex space-x-6 text-lg">
            <a href="#salud-colectiva" class="hover:text-venezuelan-secondary transition-colors duration-300">Asesoría</a>
            <a href="#galeria" class="hover:text-venezuelan-secondary transition-colors duration-300">Bienes en Venta</a>
            <a href="#contacto" class="hover:text-venezuelan-secondary transition-colors duration-300">Contacto</a>
            <a href="#" id="miPortafolioLink" class="hover:text-venezuelan-secondary transition-colors duration-300">Mi Portafolio</a>
            <a href="https://umejumac.blogspot.com/" target="_blank" class="hover:text-venezuelan-secondary transition-colors duration-300">Blog</a>
        </nav>
        <!-- Mobile Menu Toggle -->
        <div class="md:hidden">
            <button id="nav-button" class="text-venezuelan-secondary focus:outline-none">
                <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
                </svg>
            </button>
        </div>
    </div>
    <!-- Mobile Menu Content -->
    <div id="mobile-menu" class="hidden md:hidden absolute top-16 right-4 bg-venezuelan-primary rounded-lg shadow-lg p-2 w-48 text-right">
        <a href="#salud-colectiva" class="block py-2 hover:bg-venezuelan-secondary hover:text-gray-800 rounded">Asesoría</a>
        <a href="#galeria" class="block py-2 hover:bg-venezuelan-secondary hover:text-gray-800 rounded">Bienes en Venta</a>
        <a href="#contacto" class="block py-2 hover:bg-venezuelan-secondary hover:text-gray-800 rounded">Contacto</a>
        <a href="#" id="mobilePortafolioLink" class="block py-2 hover:bg-venezuelan-secondary hover:text-gray-800 rounded">Mi Portafolio</a>
        <a href="https://umejumac.blogspot.com/" target="_blank" class="block py-2 hover:bg-venezuelan-secondary hover:text-gray-800 rounded">Blog</a>
    </div>
</header>

<main class="py-12">
    <div class="container mx-auto px-4">
        
        <!-- Hero Section -->
        <section class="text-center py-20 bg-white rounded-xl shadow-lg mb-12 fade-in">
            <h2 class="text-4xl md:text-5xl font-extrabold text-venezuelan-primary mb-4">
                Unidad Medico Jurídica Morales A.C.
            </h2>
            <p class="text-lg text-gray-700 max-w-2xl mx-auto">
                Soluciones profesionales en la intersección de la **medicina, el derecho y la gestión de bienes y servicios**.
            </p>
        </section>

        <!-- TRES GRANDES SECCIONES DE CONTENIDO -->

        <!-- SECCIÓN 1: ASESORÍA EN SALUD COLECTIVA (Bloque grande) -->
        <section id="salud-colectiva" class="py-6 mb-8">
            <h2 class="text-3xl font-bold text-center mb-6 text-gray-800">1. Asesoría en Salud Colectiva</h2>
            <div class="bg-white rounded-xl shadow-lg p-8 transform transition-transform duration-300 hover:scale-[1.01]">
                <h3 class="text-2xl font-bold text-blue-800 mb-3">Planificación Estratégica y Gestión Sanitaria</h3>
                <p class="text-gray-700 text-lg">
                    Ofrecemos consultoría especializada en **salud pública**, planificación estratégica de proyectos sanitarios, optimización de recursos, y capacitación en políticas de salud. Nuestra experiencia incluye la dirección de sistemas de salud complejos y la respuesta a crisis sanitarias, combinando la visión médica y legal para una gestión integral.
                </p>
            </div>
        </section>

        <!-- SECCIÓN 2: ASESORÍA EN BIENES Y SERVICIOS (Bloque grande) -->
        <section id="bienes-servicios" class="py-6 mb-8">
            <h2 class="text-3xl font-bold text-center mb-6 text-gray-800">2. Asesoría en Transacciones de Bienes y Servicios</h2>
            <div class="bg-white rounded-xl shadow-lg p-8 transform transition-transform duration-300 hover:scale-[1.01]">
                <h3 class="text-2xl font-bold text-blue-800 mb-3">Marco Legal y Comercial para Transacciones</h3>
                <p class="text-gray-700 text-lg">
                    Brindamos soporte legal y comercial para la compra, venta y transferencia de activos. Aseguramos que cada transacción de **equipos, inmuebles o servicios** se realice con la máxima seguridad y cumplimiento normativo, protegiendo sus intereses en el marco legal del comercio internacional y nacional.
                </p>
            </div>
        </section>
        
        <!-- SECCIÓN 3: BIENES Y PROPIEDADES EN VENTA (Galería de 30 espacios) -->
        <section id="galeria" class="space-y-8 py-6">
            <h3 class="text-center text-4xl font-extrabold text-blue-900">3. Bienes, Equipos y Propiedades de UMEJUMAC en Venta</h3>
            <p class="text-center text-lg text-gray-600">Aquí encontrará **publicaciones especializadas, instrumental, vehículos y otros activos** disponibles para su adquisición. Puede editar el código para añadir sus 30 bienes.</p>
            
            <!-- La cuadrícula se ajusta a 2, 3, 4, 5 y 6 columnas en pantallas extra grandes -->
            <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 2xl:grid-cols-6 gap-6">
                
                <!-- ###################################################################### -->
                <!-- ###################### ARTÍCULOS EXISTENTES (1 al 11) ################## -->
                <!-- ###################################################################### -->
                
                <!-- ARTÍCULO 1: LIBRO (fff.png) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="fff.png" alt="Libro: Gestión Sanitaria Moderna" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+1';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 1: Gestión Sanitaria Moderna</h4>
                        <p class="text-xs text-gray-600 mt-1">Autor: J. Morales | Formato: Digital/Impreso</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $19.99 USD</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 2: LIBRO (nnn.jpg) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="nnn.jpg" alt="Libro: Jurisprudencia Médica" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+2';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 2: Jurisprudencia Médica</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Análisis legal de la práctica clínica.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $35.00 USD</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 3: LIBRO (ddd.png) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="ddd.png" alt="Libro: Salud Pública y Crisis" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+3';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 3: Salud Pública y Crisis</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Manejo de pandemias y salud colectiva.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $29.50 USD</p>
                    </div>
                </div>

                <!-- ARTÍCULO 4: LIBRO (li8.png) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="li8.png" alt="Libro: Derecho Sanitario Venezolano" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+4';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 4: Derecho Sanitario Venezolano</h4> 
                        <p class="text-xs text-gray-600 mt-1">Descripción: Leyes, normativas y reglamentos vigentes.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $42.00 USD</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 5: LIBRO (actuuu.png) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="actuuu.png" alt="Libro: Metodología de Tesis Doctorales" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+5';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 5: Metodología de Tesis Doctorales</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Guía completa para doctorados y maestrías.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $15.99 USD</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 6: LIBRO (bb.png) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="bb.png" alt="Libro: Ética Profesional en Medicina" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+6';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 6: Ética Profesional en Medicina</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Dilemas éticos y el marco legal.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $22.00 USD</p>
                    </div>
                </div>

                <!-- ARTÍCULO 7: LIBRO (fff.png - Repetido) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="fff.png" alt="Libro: Liderazgo en Salud" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+7';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 7: Liderazgo en Gestión Sanitaria</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Estrategias para dirigir equipos de alto rendimiento.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $28.00 USD</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 8: LIBRO (nnn.jpg - Repetido) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="nnn.jpg" alt="Publicación: Evaluación de Proyectos Comunitarios" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+8';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Publicación: Proyectos Comunitarios</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Guía de planificación y evaluación de impacto social.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $18.50 USD</p>
                    </div>
                </div>

                <!-- ARTÍCULO 9: LIBRO (ddd.png - Repetido) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="ddd.png" alt="Libro: La Dirección Médica" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Libro+9';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Libro 9: La Dirección Médica y sus Desafíos</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Texto esencial sobre administración hospitalaria moderna.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: $39.99 USD</p>
                    </div>
                </div>

                <!-- ARTÍCULO 10: ACTIVO (li8.png - Repetido) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="li8.png" alt="Activo: Equipo de Laboratorio" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Equipo+Lab';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Activo: Equipo de Laboratorio Clínico</h4> 
                        <p class="text-xs text-gray-600 mt-1">Descripción: Analizador químico semiautomático de segunda mano.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: **Consultar**</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 11: ACTIVO (actuuu.png - Repetido) -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="actuuu.png" alt="Activo: Inmueble Comercial" onerror="this.onerror=null;this.src='https://placehold.co/300x300/003366/FFFFFF?text=Inmueble';" class="w-full h-48 object-cover">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Activo: Inmueble Comercial Tipo Oficina</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: Espacio ideal para consultorio o sede administrativa.</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: **Consultar**</p>
                    </div>
                </div>
                
                <!-- ###################################################################### -->
                <!-- ########## ESPACIOS VACÍOS PARA INGRESO MANUAL (12 al 30) ############ -->
                <!-- ###################################################################### -->
                
                <!-- ARTÍCULO 12: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <!-- REEMPLAZAR 'url-de-tu-imagen.jpg' con la ruta de tu foto -->
                    <img src="url-de-tu-imagen.jpg" alt="Activo 12: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+12';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 12: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 13: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 13: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+13';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 13: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 14: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 14: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+14';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 14: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 15: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 15: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+15';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 15: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 16: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 16: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+16';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 16: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 17: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 17: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+17';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 17: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 18: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 18: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+18';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 18: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 19: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 19: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+19';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 19: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 20: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 20: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+20';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 20: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 21: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 21: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+21';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 21: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 22: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 22: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+22';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 22: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>
                
                <!-- ARTÍCULO 23: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 23: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+23';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 23: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 24: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 24: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+24';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 24: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 25: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 25: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+25';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 25: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 26: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 26: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+26';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 26: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 27: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 27: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+27';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 27: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 28: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 28: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+28';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 28: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 29: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 29: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+29';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 29: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>

                <!-- ARTÍCULO 30: PLANTILLA VACÍA -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="url-de-tu-imagen.jpg" alt="Activo 30: Título del Producto" onerror="this.onerror=null;this.src='https://placehold.co/300x300/FFC107/003366?text=ESPACIO+30';" class="w-full h-48 object-cover placeholder-img">
                    <div class="p-3 text-center">
                        <h4 class="font-bold text-md text-blue-800 truncate">Artículo 30: [INGRESE TÍTULO]</h4>
                        <p class="text-xs text-gray-600 mt-1">Descripción: [Detalles del artículo]</p>
                        <p class="text-sm font-semibold text-green-600 mt-2">Precio: [Bs / USD]</p>
                    </div>
                </div>
            </div>
        </section>
        <!-- FIN DE LA GALERÍA DE BIENES -->

        <!-- Portafolio Section (Oculto por defecto) -->
        <section id="portafolio" class="py-12 hidden-section fade-in">
            <div class="bg-white rounded-xl shadow-lg p-8">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">Mi Portafolio Profesional</h2>
                <div class="max-w-4xl mx-auto">
                    <div class="text-center mb-8 border-b-2 border-gray-200 pb-4">
                        <h3 class="text-2xl font-bold text-gray-800">Dr. José Gregorio Morales</h3>
                        <p class="text-lg text-gray-600">Médico, Abogado y Doctor en Gestión</p>
                        <div class="flex flex-wrap justify-center items-center space-x-4 mt-2 text-gray-500 text-sm">
                            <span>Email: jgm963@gmail.com</span>
                            <span>Teléfono: +58 426 570 83 69</span>
                        </div>
                    </div>

                    <!-- Sección de Perfil Profesional (Tomado de curriculum_vitae.md) -->
                    <div class="mb-6">
                        <h4 class="text-xl font-bold mb-2 text-blue-800 border-b pb-1">Perfil Profesional</h4>
                        <p class="text-gray-700 text-justify">
                            Profesional con más de tres décadas de experiencia en la gestión y administración de la salud colectiva. Mi trayectoria como médico, especialista en Salud Pública y doctor en Gestión me ha permitido liderar la planificación estratégica y la dirección de sistemas de salud complejos, incluso en un contexto de crisis socioeconómica y sanitaria, con una notable actuación en la pandemia de COVID-19. Mi formación en derecho es una ventaja competitiva que me facilita la comprensión de marcos normativos y la gestión integral. Mi objetivo es aplicar mi conocimiento como asesor internacional en salud pública y proyectos comunitarios.
                        </p>
                    </div>
                    
                    <!-- Sección de Experiencia Profesional (Tomado de curriculum_vitae.md) -->
                    <div class="mb-6">
                        <h4 class="text-xl font-bold mb-2 text-blue-800 border-b pb-1">Experiencia Profesional Clave</h4>
                        <ul class="list-disc list-inside space-y-3 text-gray-700">
                            <li>
                                <span class="font-semibold">Director General de la Corporación de Salud del Estado Mérida</span> (2019 - 2021). Máxima autoridad en salud de la entidad, liderando la planificación estratégica en un entorno de crisis.
                            </li>
                            <li>
                                <span class="font-semibold">Docente Universitario</span> (1993 - Presente). Profesor en pregrado y posgrado en las Facultades de Medicina y Ciencias Jurídicas de la Universidad de los Andes.
                            </li>
                            <li>
                                <span class="font-semibold">Director de Hospitales y Coordinador de Programas Prioritarios de Salud</span> (1988 - 2016). Experiencia en la administración hospitalaria y la coordinación de programas de salud pública (materno infantil, VIH/SIDA).
                            </li>
                        </ul>
                    </div>

                    <!-- Sección de Educación (Tomado de curriculum_vitae.md) -->
                    <div class="mb-6">
                        <h4 class="text-xl font-bold mb-2 text-blue-800 border-b pb-1">Educación</h4>
                        <ul class="list-disc list-inside space-y-2 text-gray-700">
                            <li><span class="font-semibold">Doctorado en Gestión para la Creación Intelectual</span> - Universidad Politécnica Territorial Kleber Ramírez, 2022.</li>
                            <li><span class="font-semibold">Abogado Magna Cum Laude</span> - Universidad de los Andes, 2006.</li>
                            <li><span class="font-semibold">Magister Scientiae en Salud Pública</span> - Universidad de los Andes, 2011.</li>
                            <li><span class="font-semibold">Especialista en Obstetricia y Ginecología</span> - Hospital Universitario de los Andes, 1987.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>
        <!-- FIN DEL PORTAFOLIO -->

        <!-- Contact Section -->
        <section id="contacto" class="text-center py-12 bg-venezuelan-primary text-white rounded-xl shadow-lg mt-12 fade-in">
            <h2 class="text-3xl font-bold mb-4">Contáctenos</h2>
            <p class="text-lg">Si desea más información o agendar una consulta, contáctenos directamente.</p>
            <div class="mt-4 space-y-2">
                <p class="text-xl font-bold">Email: jgm963@gmail.com</p>
                <p class="text-xl font-bold">Teléfono: +58 426 570 83 69</p>
            </div>
        </section>
    </div>
</main>

<script>
    document.addEventListener('DOMContentLoaded', () => {
        const portafolioSection = document.getElementById('portafolio');
        const navButton = document.getElementById('nav-button');
        const mobileMenu = document.getElementById('mobile-menu');

        // Función para mostrar/ocultar el Portafolio y manejar la animación
        function togglePortafolio(event) {
            event.preventDefault();
            
            // Ocultar el menú móvil si está abierto
            if (!mobileMenu.classList.contains('hidden')) {
                mobileMenu.classList.add('hidden');
            }

            // Si está oculto, lo mostramos con fade-in y ajustamos el scroll
            if (portafolioSection.classList.contains('hidden-section')) {
                portafolioSection.classList.remove('hidden-section');
                portafolioSection.classList.add('fade-in');
                
                // Asegurar que el scroll se dirija a la sección visible
                setTimeout(() => {
                    portafolioSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }, 10); // Un pequeño retraso para que la sección se haga visible antes de scrollear
            } else {
                // Si está visible, lo ocultamos
                portafolioSection.classList.add('hidden-section');
                portafolioSection.classList.remove('fade-in');
            }
        }

        // Asignar el evento a los enlaces de Portafolio
        document.getElementById('miPortafolioLink').addEventListener('click', togglePortafolio);
        document.getElementById('mobilePortafolioLink').addEventListener('click', togglePortafolio);
        
        // Manejar el botón del menú móvil
        navButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // Smooth scrolling para otros enlaces
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();

                // FIX: Si el href es solo '#', se ignora el intento de querySelector,
                // ya que estos enlaces son manejados por la función togglePortafolio.
                if (this.getAttribute('href') === '#') {
                    return; 
                }
                
                // Ocultar el portafolio si se navega a otra sección principal
                if (this.getAttribute('href') !== '#portafolio' && !this.id.includes('PortafolioLink') && !portafolioSection.classList.contains('hidden-section')) {
                    portafolioSection.classList.add('hidden-section');
                    portafolioSection.classList.remove('fade-in');
                }
                
                // Ocultar menú móvil después de hacer clic en un enlace
                if (!mobileMenu.classList.contains('hidden')) {
                    mobileMenu.classList.add('hidden');
                }

                // Scroll a la sección
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    });
</script>
</body>
</html>
