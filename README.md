index.html<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC: Unidad Medico Juridica Morales AC</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            color: #333;
        }
        .text-venezuelan-primary {
            color: #FFC107; /* Amarillo */
        }
        .bg-venezuelan-primary {
            background-color: #003666; /* Azul */
        }
        .bg-venezuelan-secondary {
            background-color: #FFC107; /* Amarillo */
        }
        .border-venezuelan-primary {
            border-color: #003666; /* Azul */
        }
        .border-venezuelan-secondary {
            border-color: #FFC107; /* Amarillo */
        }
    </style>
</head>
<body class="bg-[#F7F7F7]">

    <!-- Header -->
    <header class="bg-venezuelan-primary text-white p-4 shadow-md sticky top-0 z-50">
        <div class="container mx-auto flex justify-between items-center">
            <h1 class="text-2xl font-bold">UMEJUMAC</h1>
            <nav class="hidden md:flex space-x-6 text-lg">
                <a href="#servicios" class="hover:text-venezuelan-secondary transition-colors duration-300">Servicios</a>
                <a href="#contacto" class="hover:text-venezuelan-secondary transition-colors duration-300">Contacto</a>
                <a href="https://umejumac.blogspot.com/" target="_blank" class="hover:text-venezuelan-secondary transition-colors duration-300">Nuestro Blog</a>
                <a href="#portafolio" class="hover:text-venezuelan-secondary transition-colors duration-300">Mi Portafolio</a>
            </nav>
            <div class="md:hidden">
                <button id="menu-button" class="bg-transparent text-white text-2xl relative p-2 rounded-full hover:bg-venezuelan-secondary focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-venezuelan-primary focus:ring-venezuelan-secondary">
                    <span class="sr-only">Open main menu</span>
                    <!-- Icono SVG de menú -->
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"/>
                    </svg>
                </button>
                <div id="mobile-menu" class="hidden absolute top-16 right-4 bg-venezuelan-primary rounded-lg shadow-xl py-2 w-48 text-right">
                    <a href="#servicios" class="block px-4 py-2 hover:bg-venezuelan-secondary">Servicios</a>
                    <a href="#contacto" class="block px-4 py-2 hover:bg-venezuelan-secondary">Contacto</a>
                    <a href="https://umejumac.blogspot.com/" target="_blank" class="block px-4 py-2 hover:bg-venezuelan-secondary">Nuestro Blog</a>
                    <a href="#portafolio" class="block px-4 py-2 hover:bg-venezuelan-secondary">Mi Portafolio</a>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-4 py-8 space-y-12">

        <!-- Sección Principal -->
        <section class="text-center py-16 bg-gradient-to-r from-blue-900 to-blue-700 text-white rounded-xl shadow-lg transform transition-transform duration-500 hover:scale-105">
            <h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold">UMEJUMAC: Unidad Medico Juridica Morales AC</h2>
            <p class="mt-4 text-lg sm:text-xl">Asesoría integral en salud y derecho para tu bienestar.</p>
            <a href="#servicios" class="mt-8 inline-block px-8 py-3 bg-blue-900 text-white font-bold rounded-full shadow-lg transform transition-transform duration-300 hover:scale-110 hover:bg-blue-800">
                Explorar Servicios
            </a>
        </section>

        <!-- Sección de Servicios -->
        <section id="servicios" class="space-y-8">
            <h3 class="text-center text-4xl font-extrabold text-blue-900">Nuestros Servicios</h3>
            <div class="grid md:grid-cols-2 gap-8">
                <!-- Tarjeta de Salud Colectiva -->
                <div class="bg-blue-900 text-white p-6 rounded-xl shadow-lg hover:shadow-2xl transition-shadow duration-300 transform hover:-translate-y-2">
                    <h4 class="text-2xl font-bold">Salud Colectiva</h4>
                    <p class="mt-2">Asesorías en salud</p>
                    <div class="space-y-4 mt-6">
                        <div id="galeria-eventos" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-4 mt-4">
                            <!-- Las fotos de eventos se insertarán aquí por JavaScript -->
                        </div>
                    </div>
                </div>
                <!-- Tarjeta de Bienes y Servicios -->
                <div class="bg-yellow-400 text-blue-900 p-6 rounded-xl shadow-lg hover:shadow-2xl transition-shadow duration-300 transform hover:-translate-y-2">
                    <h4 class="text-2xl font-bold">Bienes y Servicios</h4>
                    <p class="mt-2">Transacciones de bienes</p>
                    <div class="space-y-4 mt-6">
                        <div id="galeria-venta" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-4 mt-4">
                             <!-- Las fotos de venta se insertarán aquí por JavaScript -->
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contacto -->
        <section id="contacto" class="text-center py-16 bg-blue-900 text-white rounded-xl shadow-lg">
            <h3 class="text-3xl font-bold">Contáctenos</h3>
            <p class="mt-4 text-lg">Si desea más información o agendar una cita, contáctenos.</p>
            <p class="mt-2 text-xl font-bold">Email: jgm963@gmail.com</p>
            <p class="mt-2 text-xl font-bold">Teléfono: +58 426 570 83 69</p>
        </section>
        
        <!-- Sección de Portafolio Profesional -->
        <section id="portafolio" class="bg-white p-8 rounded-xl shadow-lg">
            <h3 class="text-center text-4xl font-extrabold text-blue-900 mb-6">Mi Portafolio Profesional</h3>
            <div class="space-y-6">
                <p class="text-2xl font-bold text-gray-800">Dr. José Gregorio Morales</p>
                <p class="text-xl font-bold text-gray-600">Médico, Abogado y Doctor en Gestión para la Creación Intelectual</p>
                <p class="text-lg text-gray-500">jgm963@gmail.com | +58 426 570 83 69</p>
                <div class="border-b-2 border-venezuelan-primary my-6"></div>

                <h4 class="text-2xl font-bold text-blue-900">Perfil Profesional</h4>
                <p class="text-gray-700">Profesional con una trayectoria de más de tres décadas en la gestión y administración de la salud colectiva. Mi experiencia como médico, especialista en Salud Pública y Doctor en Gestión me ha permitido liderar la planificación estratégica y la dirección de sistemas de salud complejos, incluso en contextos de crisis. Mi formación en derecho es un activo que me facilita la comprensión y adaptación a marcos normativos, garantizando una gestión integral y efectiva. Mi propósito es aplicar mis conocimientos como asesor internacional en salud pública, con un interés particular en la colaboración con la comunidad hispanohablante de Guinea Ecuatorial.</p>
                
                <h4 class="text-2xl font-bold text-blue-900 mt-8">Áreas de Experiencia y Logros Clave</h4>
                <ul class="list-disc list-inside space-y-2 text-gray-700">
                    <li><span class="font-bold">Gestión Estratégica en Salud Pública:</span> Como Director General de la Corporación de Salud del Estado Mérida, fui responsable de la máxima autoridad en salud de la entidad. Mis logros se centran en la planificación y ejecución de acciones estratégicas para mantener los servicios de salud en un entorno de crisis socioeconómica y sanitaria, coordinando equipos de alta eficiencia y conciliando esfuerzos entre múltiples actores.</li>
                    <li><span class="font-bold">Administración y Dirección:</span> Lideré la gestión administrativa de la Corporación de Salud, supervisando y coordinando las estructuras para asegurar que se cumplieran los objetivos institucionales. Esto incluyó la dirección de hospitales y la coordinación de programas prioritarios de salud como el materno infantil y VIH/SIDA.</li>
                    <li><span class="font-bold">Docencia Universitaria:</span> Con más de 20 años de experiencia como profesor, he formado a múltiples cohortes de estudiantes en pregrado y postgrado en áreas como Medicina Preventiva, Salud Pública y Metodología de la Investigación. He sido tutor y jurado de tesis, combinando mi experiencia práctica con el conocimiento académico para formar a la próxima generación de profesionales.</li>
                    <li><span class="font-bold">Conocimiento Jurídico Aplicado:</span> Aunque mi enfoque principal es la gestión de la salud colectiva, mi título de abogado me proporciona una ventaja única para entender los aspectos legales de la salud pública. Esta habilidad me ha permitido impartir clases de medicina legal y psicocriminología, así como actuar como asesor en comisiones legislativas.</li>
                </ul>

                <h4 class="text-2xl font-bold text-blue-900 mt-8">Formación Académica</h4>
                <ul class="list-disc list-inside space-y-2 text-gray-700">
                    <li><span class="font-bold">Doctorado en Gestión para la Creación Intelectual</span> - Universidad Politécnica Territorial Klever Ramirez, 2022.</li>
                    <li><span class="font-bold">Magister Scientiae en Salud Pública</span> - Universidad de los Andes, 2011.</li>
                    <li><span class="font-bold">Abogado Magna Cum Laude</span> - Universidad de los Andes, 2006.</li>
                    <li><span class="font-bold">Especialista en Administración en Salud Pública</span> - Universidad de los Andes, 1993.</li>
                    <li><span class="font-bold">Especialista en Obstetricia y Ginecología</span> - Hospital Universitario de los Andes, 1987.</li>
                    <li><span class="font-bold">Médico Cirujano</span> - Universidad Central de Venezuela, 1983.</li>
                </ul>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-blue-900 text-white p-4 mt-8">
        <div class="container mx-auto text-center text-sm">
            &copy; 2024 UMEJUMAC. Todos los derechos reservados.
        </div>
    </footer>

    <script>
        document.getElementById('menu-button').addEventListener('click', function() {
            var mobileMenu = document.getElementById('mobile-menu');
            if (mobileMenu.classList.contains('hidden')) {
                mobileMenu.classList.remove('hidden');
            } else {
                mobileMenu.classList.add('hidden');
            }
        });

        document.addEventListener('DOMContentLoaded', function() {
            // Lista de fotos para la sección de ventas (productos/libros)
            const fotosDeVenta = [
                { nombreArchivo: 'cc.png', titulo: 'Evento 2' },
                { nombreArchivo: 'tt.png', titulo: 'Producto 1' },
                { nombreArchivo: 'vv.png', titulo: 'Reunión de Equipo' },
                { nombreArchivo: 'fg.png', titulo: 'Libro 1' },
                { nombreArchivo: 'z.png', titulo: 'Libro 2' },
                { nombreArchivo: 'x.png', titulo: 'Libro 3' },
                { nombreArchivo: 'q.png', titulo: 'Libro 4' },
                { nombreArchivo: 'www.png', titulo: 'Libro 5' },
                { nombreArchivo: 'ooo.jpg', titulo: 'Libro 6' },
                { nombreArchivo: 'lll.png', titulo: 'Libro 7' },
                { nombreArchivo: 'tttt.jpg', titulo: 'Libro 8' }
            ];

            // Lista de fotos para la sección de eventos (reuniones/exposiciones)
            const fotosDeEventos = [
                { nombreArchivo: 'd.png', titulo: 'Reunión de Equipo' }
            ];

            function generarGaleria(fotos, contenedorId, mostrarTitulo) {
                const contenedor = document.getElementById(contenedorId);
                if (!contenedor) return;

                contenedor.innerHTML = ''; // Limpia el contenedor
                
                fotos.forEach(foto => {
                    const tarjeta = document.createElement('div');
                    tarjeta.className = 'bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105';
                    
                    const imagen = document.createElement('img');
                    imagen.src = 'https://raw.githubusercontent.com/jgm963/umejumac--app/main/' + foto.nombreArchivo;
                    imagen.alt = foto.titulo;
                    imagen.className = 'w-full h-auto object-cover rounded-t-xl';
                    tarjeta.appendChild(imagen);

                    if (mostrarTitulo) {
                        const divTexto = document.createElement('div');
                        divTexto.className = 'p-4';
                        const titulo = document.createElement('h4');
                        titulo.className = 'font-bold text-lg';
                        titulo.textContent = foto.titulo;
                        divTexto.appendChild(titulo);
                        tarjeta.appendChild(divTexto);
                    }
                    contenedor.appendChild(tarjeta);
                });
            }

            // Genera las galerías
            generarGaleria(fotosDeVenta, 'galeria-venta', false); // No mostrar título en ventas
            generarGaleria(fotosDeEventos, 'galeria-eventos', true); // Mostrar título en eventos

        });
    </script>
</body>
</html>
