<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC: Unidad Medico Jurídica Morales AC</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            color: #333;
            background-color: #f0f4f8;
            scroll-behavior: smooth;
        }
        .text-venezuelan-primary { color: #FFC107; } /* Amarillo */
        .bg-venezuelan-primary { background-color: #003366; } /* Azul */
        .bg-venezuelan-secondary { background-color: #FFC107; } /* Amarillo */
        .border-venezuelan-primary { border-color: #003366; } /* Azul */
        .border-venezuelan-secondary { border-color: #FFC107; } /* Amarillo */
        
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
    </style>
</head>
<body class="bg-gray-100">

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
            <!-- Mobile Menu -->
            <div class="md:hidden">
                <button id="nav-button" class="text-venezuelan-secondary focus:outline-none">
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
                    </svg>
                </button>
            </div>
        </div>
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
                    Soluciones profesionales en la intersección de la medicina, el derecho y la gestión de bienes y servicios.
                </p>
            </section>

            <!-- TRES GRANDES SECCIONES DE CONTENIDO -->

            <!-- SECCIÓN 1: ASESORÍA EN SALUD COLECTIVA (Bloque grande) -->
            <section id="salud-colectiva" class="py-6 mb-8">
                <h2 class="text-3xl font-bold text-center mb-6">1. Asesoría en Salud Colectiva</h2>
                <div class="bg-white rounded-xl shadow-lg p-8 transform transition-transform duration-300 hover:scale-[1.01]">
                    <h3 class="text-2xl font-bold text-venezuelan-primary mb-3">Planificación y Gestión Sanitaria</h3>
                    <p class="text-gray-700 text-lg">
                        Ofrecemos consultoría especializada en salud pública, planificación estratégica de proyectos sanitarios, optimización de recursos, y capacitación en políticas de salud. Nuestra experiencia incluye la dirección de sistemas de salud complejos y la respuesta a crisis sanitarias.
                    </p>
                </div>
            </section>

            <!-- SECCIÓN 2: ASESORÍA EN BIENES Y SERVICIOS (Bloque grande) -->
            <section id="bienes-servicios" class="py-6 mb-8">
                <h2 class="text-3xl font-bold text-center mb-6">2. Asesoría en Transacciones de Bienes y Servicios</h2>
                <div class="bg-white rounded-xl shadow-lg p-8 transform transition-transform duration-300 hover:scale-[1.01]">
                    <h3 class="text-2xl font-bold text-venezuelan-primary mb-3">Marco Legal y Comercial para Transacciones</h3>
                    <p class="text-gray-700 text-lg">
                        Brindamos soporte legal y comercial para la compra, venta y transferencia de activos. Aseguramos que cada transacción de equipos, inmuebles o servicios se realice con la máxima seguridad y cumplimiento normativo, protegiendo sus intereses en todo momento.
                    </p>
                </div>
            </section>
            
            <!-- SECCIÓN 3: BIENES Y PROPIEDADES EN VENTA (Galería con Título Genérico) -->
            <section id="galeria" class="space-y-8 py-6">
                <!-- TÍTULO CAMBIADO A GENÉRICO -->
                <h3 class="text-center text-4xl font-extrabold text-blue-900">3. Bienes, Equipos y Propiedades de UMEJUMAC en Venta</h3>
                <p class="text-center text-lg text-gray-600">Aquí encontrará **publicaciones, instrumental quirúrgico, vehículos y otros activos** disponibles. Estos 11 espacios están listos para ser editados.</p>
                
                <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-6">
                    
                    <!-- LIBRO 1: Usando la imagen existente fff.png -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <img src="fff.png" alt="Libro: Gestión Sanitaria Moderna" class="w-full h-64 object-cover">
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 1: Gestión Sanitaria Moderna</h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Autor: J. Morales | Formato: Digital
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: $19.99 USD</p>
                        </div>
                    </div>
                    
                    <!-- LIBRO 2: Placeholder con imagen visible -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 2</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 2: Jurisprudencia Médica</h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Análisis legal de la práctica clínica.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: $35.00 USD</p>
                        </div>
                    </div>
                    
                    <!-- LIBRO 3: Placeholder con imagen visible -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 3</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 3: Salud Pública y Crisis</h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Manejo de pandemias y salud colectiva.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: $29.50 USD</p>
                        </div>
                    </div>

                    <!-- LIBRO 4: Placeholder con imagen visible -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 4</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 4: Derecho Sanitario Venezolano</h4> 
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Leyes, normativas y reglamentos vigentes.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: $42.00 USD</p>
                        </div>
                    </div>
                    
                    <!-- LIBRO 5: Placeholder con imagen visible -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 5</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 5: Metodología de Tesis Doctorales</h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Guía completa para doctorados y maestrías.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: $15.99 USD</p>
                        </div>
                    </div>
                    
                    <!-- LIBRO 6: Placeholder con imagen visible -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 6</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 6: Ética Profesional en Medicina</h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Dilemas éticos y el marco legal.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: $22.00 USD</p>
                        </div>
                    </div>

                    <!-- LIBRO 7: Placeholder genérico -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 7</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 7: <span class="text-red-500">Espacio para Nuevo Artículo</span></h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Reemplace este con Instrumental, Vehículo, o Libro.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: USD 0.00</p>
                        </div>
                    </div>
                    
                    <!-- LIBRO 8: Placeholder genérico -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 8</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 8: <span class="text-red-500">Espacio para Nuevo Artículo</span></h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Reemplace este con Instrumental, Vehículo, o Libro.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: USD 0.00</p>
                        </div>
                    </div>

                    <!-- LIBRO 9: Placeholder genérico -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 9</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 9: <span class="text-red-500">Espacio para Nuevo Artículo</span></h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Reemplace este con Instrumental, Vehículo, o Libro.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: USD 0.00</p>
                        </div>
                    </div>

                    <!-- LIBRO 10: Placeholder genérico -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 10</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 10: <span class="text-red-500">Espacio para Nuevo Artículo</span></h4> 
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Reemplace este con Instrumental, Vehículo, o Libro.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: USD 0.00</p>
                        </div>
                    </div>
                    
                    <!-- LIBRO 11: Placeholder genérico -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                        <div class="w-full h-64 placeholder-img">Libro 11</div>
                        <div class="p-3 text-center">
                            <h4 class="font-bold text-md text-blue-800 truncate">Libro 11: <span class="text-red-500">Espacio para Nuevo Artículo</span></h4>
                            <p class="text-xs text-gray-600 mt-1">
                                Descripción: Reemplace este con Instrumental, Vehículo, o Libro.
                            </p>
                            <p class="text-sm font-semibold text-green-600 mt-2">Precio: USD 0.00</p>
                        </div>
                    </div>
                </div>
            </section>
            <!-- FIN DE LA GALERÍA DE BIENES -->

            <!-- Portafolio Section (Oculto por defecto) -->
            <section id="portafolio" class="py-12 hidden-section">
                <div class="bg-white rounded-xl shadow-lg p-8">
                    <h2 class="text-3xl font-bold text-center mb-8">Mi Portafolio Profesional</h2>
                    <div class="max-w-4xl mx-auto">
                        <div class="text-center mb-8 border-b-2 border-gray-200 pb-4">
                            <h3 class="text-2xl font-bold text-gray-800">José Gregorio Morales</h3>
                            <p class="text-lg text-gray-600">Médico, Abogado y Doctor en Gestión para la Creación Intelectual</p>
                            <div class="flex flex-wrap justify-center items-center space-x-4 mt-2 text-gray-500 text-sm">
                                <span>Email: jgm963@gmail.com</span>
                                <span>Teléfono: +58 426 570 83 69</span>
                            </div>
                        </div>

                        <!-- Sección de Perfil Profesional -->
                        <div class="mb-6">
                            <h4 class="text-xl font-bold mb-2 text-venezuelan-primary">Perfil Profesional</h4>
                            <p class="text-gray-700 text-justify">
                                Profesional con más de tres décadas de experiencia en la gestión y administración de la salud colectiva. Mi trayectoria como médico, especialista en Salud Pública y doctor en Gestión me ha permitido liderar la planificación estratégica y la dirección de sistemas de salud complejos, incluso en un contexto de crisis socioeconómica y sanitaria, con una notable actuación en la pandemia de COVID-19. Mi formación en derecho es una ventaja competitiva que me facilita la comprensión de marcos normativos y la gestión integral. Mi objetivo es aplicar mi conocimiento como asesor internacional en salud pública y proyectos comunitarios.
                            </p>
                        </div>
                        
                        <!-- Sección de Experiencia Profesional -->
                        <div class="mb-6">
                            <h4 class="text-xl font-bold mb-2 text-venezuelan-primary">Experiencia Profesional</h4>
                            <ul class="list-disc list-inside space-y-3 text-gray-700">
                                <li>
                                    <span class="font-semibold">Director General de la Corporación de Salud del Estado Mérida</span> (2019 - 2021)
                                    <ul class="list-disc list-inside ml-4 mt-1 space-y-1 text-sm">
                                        <li>Máxima autoridad en salud de la entidad, liderando la planificación estratégica en un entorno de crisis.</li>
                                        <li>Coordinación de acciones entre equipos de trabajo y logro de consensos en momentos de alta dificultad.</li>
                                    </ul>
                                </li>
                                <li>
                                    <span class="font-semibold">Director de Gestión Médica Administrativa</span> (2017 - 2018)
                                    <ul class="list-disc list-inside ml-4 mt-1 space-y-1 text-sm">
                                        <li>Responsable de la dirección y coordinación del plan estratégico institucional.</li>
                                    </ul>
                                </li>
                                <li>
                                    <span class="font-semibold">Docente Universitario</span> (1993 - Presente)
                                    <ul class="list-disc list-inside ml-4 mt-1 space-y-1 text-sm">
                                        <li>Más de 20 años como profesor en pregrado y posgrado en las Facultades de Medicina y Ciencias Jurídicas de la Universidad de los Andes.</li>
                                        <li>Tutor y jurado de múltiples tesis de pregrado, postgrado y maestría.</li>
                                    </ul>
                                </li>
                                <li>
                                    <span class="font-semibold">Director de Hospitales y Coordinador de Programas Prioritarios de Salud</span> (1988 - 2016)
                                    <ul class="list-disc list-inside ml-4 mt-1 space-y-1 text-sm">
                                        <li>Amplia experiencia en la administración hospitalaria y la coordinación de programas de salud pública como el materno infantil y VIH/SIDA.</li>
                                        <li>Participación en la promoción de la salud y la participación comunitaria con la OPS y la OMS en el programa de Municipios Saludables.</li>
                                    </ul>
                                </li>
                            </ul>
                        </div>

                        <!-- Sección de Educación -->
                        <div class="mb-6">
                            <h4 class="text-xl font-bold mb-2 text-venezuelan-primary">Educación</h4>
                            <ul class="list-disc list-inside space-y-2 text-gray-700">
                                <li><span class="font-semibold">Doctorado en Gestión para la Creación Intelectual</span> - Universidad Politécnica Territorial Kleber Ramírez, 2022.</li>
                                <li><span class="font-semibold">Magister Scientiae en Salud Pública</span> - Universidad de los Andes, 2011.</li>
                                <li><span class="font-semibold">Abogado Magna Cum Laude</span> - Universidad de los Andes, 2006.</li>
                                <li><span class="font-semibold">Especialista en Administración en Salud Pública</span> - Universidad de los Andes, 1993.</li>
                                <li><span class="font-semibold">Especialista en Obstetricia y Ginecología</span> - Hospital Universitario de los Andes, 1987.</li>
                                <li><span class="font-semibold">Médico Cirujano</span> - Universidad Central de Venezuela, 1983.</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </section>
            <!-- FIN DEL PORTAFOLIO -->

            <!-- Contact Section -->
            <section id="contacto" class="text-center py-12 bg-venezuelan-primary text-white rounded-xl shadow-lg mt-12 fade-in">
                <h2 class="text-3xl font-bold mb-4">Contáctenos</h2>
                <p class="text-lg">Si desea más información o agendar una cita, contáctenos.</p>
                <div class="mt-4 space-y-2">
                    <p class="text-xl font-bold">Email: jgm963@gmail.com</p>
                    <p class="text-xl font-bold">Teléfono: +58 426 570 83 69</p>
                </div>
            </section>
        </div>
    </main>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const miPortafolioLink = document.getElementById('miPortafolioLink');
            const mobilePortafolioLink = document.getElementById('mobilePortafolioLink');
            const portafolioSection = document.getElementById('portafolio');
            const navButton = document.getElementById('nav-button');
            const mobileMenu = document.getElementById('mobile-menu');

            function togglePortafolio(event) {
                event.preventDefault();
                portafolioSection.classList.toggle('hidden-section');
                
                // If mobile menu is open, close it
                if (!mobileMenu.classList.contains('hidden')) {
                    mobileMenu.classList.add('hidden');
                }

                // Scroll to the section if it is visible
                if (!portafolioSection.classList.contains('hidden-section')) {
                    portafolioSection.scrollIntoView({ behavior: 'smooth' });
                }
            }

            miPortafolioLink.addEventListener('click', togglePortafolio);
            mobilePortafolioLink.addEventListener('click', togglePortafolio);
            
            navButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            // Smooth scrolling for other links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    
                    // Check if the clicked link is not the portafolio link
                    if (this.id !== 'miPortafolioLink' && this.id !== 'mobilePortafolioLink') {
                        // Hide portafolio section if it is visible
                        if (!portafolioSection.classList.contains('hidden-section')) {
                            portafolioSection.classList.add('hidden-section');
                        }
                    }

                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                });
            });
        });
    </script>
</body>
</html>
