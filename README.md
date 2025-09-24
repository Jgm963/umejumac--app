index.html
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
                <a href="#productos" class="hover:text-venezuelan-secondary transition-colors duration-300">Servicios</a>
                <a href="#contacto" class="hover:text-venezuelan-secondary transition-colors duration-300">Contacto</a>
            </nav>
            <div class="md:hidden">
                <button id="cart-button" class="bg-transparent text-white text-2xl relative p-2 rounded-full hover:bg-venezuelan-secondary focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-venezuelan-primary focus:ring-venezuelan-secondary">
                    <span class="sr-only">Open main menu</span>
                    <!-- Icono SVG de menú -->
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"/>
                    </svg>
                </button>
                <div id="mobile-menu" class="hidden absolute top-16 right-4 bg-venezuelan-primary rounded-lg shadow-xl py-2 w-48 text-right">
                    <a href="#productos" class="block px-4 py-2 hover:bg-venezuelan-secondary">Servicios</a>
                    <a href="#contacto" class="block px-4 py-2 hover:bg-venezuelan-secondary">Contacto</a>
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
            <a href="#servicios" class="mt-8 inline-block px-8 py-3 bg-venezuelan-secondary text-venezuelan-primary font-bold rounded-full shadow-lg transform transition-transform duration-300 hover:scale-110 hover:bg-yellow-400">
                Explorar Servicios
            </a>
        </section>

        <!-- Sección de Servicios -->
        <section id="servicios" class="space-y-8">
            <h3 class="text-center text-4xl font-extrabold text-blue-900">Nuestros Servicios</h3>
            <div class="grid md:grid-cols-2 gap-8">
                <div class="bg-blue-900 text-white p-6 rounded-xl shadow-lg hover:shadow-2xl transition-shadow duration-300 transform hover:-translate-y-2">
                    <h4 class="text-2xl font-bold">Salud Colectiva</h4>
                    <p class="mt-2">Asesorías en salud</p>
                </div>
                <div class="bg-yellow-400 text-blue-900 p-6 rounded-xl shadow-lg hover:shadow-2xl transition-shadow duration-300 transform hover:-translate-y-2">
                    <h4 class="text-2xl font-bold">Bienes y Servicios</h4>
                    <p class="mt-2">Transacciones de bienes</p>
                </div>
            </div>
        </section>

        <!-- Sección Galería -->
        <section id="galeria" class="space-y-8">
            <h3 class="text-center text-4xl font-extrabold text-blue-900">Nuestros Momentos</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Tarjeta de foto de ejemplo 1 -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="https://placehold.co/600x400/003666/FFFFFF?text=Equipo+1" alt="Foto de equipo" class="w-full h-auto object-cover rounded-t-xl">
                    <div class="p-4">
                        <h4 class="font-bold text-lg">Equipo 1</h4>
                    </div>
                </div>

                <!-- Tarjeta de foto de ejemplo 2 -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="https://placehold.co/600x400/FFC107/003666?text=Evento+2" alt="Foto de evento" class="w-full h-auto object-cover rounded-t-xl">
                    <div class="p-4">
                        <h4 class="font-bold text-lg">Evento 2</h4>
                    </div>
                </div>

                <!-- Tarjeta de foto de ejemplo 3 -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden transform transition-transform duration-300 hover:scale-105">
                    <img src="https://placehold.co/600x400/003666/FFFFFF?text=Reunión+3" alt="Foto de reunión" class="w-full h-auto object-cover rounded-t-xl">
                    <div class="p-4">
                        <h4 class="font-bold text-lg">Reunión 3</h4>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sección de Contacto -->
        <section id="contacto" class="py-12">
            <h3 class="text-center text-4xl font-extrabold text-blue-900">Contáctanos</h3>
            <div class="mt-8 flex justify-center space-x-6 text-2xl">
                <!-- Íconos de contacto (ejemplos) -->
                <a href="#" class="hover:text-venezuelan-secondary transition-colors duration-300">
                    <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.58.016 4.85.07c1.42.067 2.05.293 2.5.47a2.82 2.82 0 011.63 1.63c.177.45.403 1.08.47 2.5.054 1.27.07 1.646.07 4.85s-.016 3.58-.07 4.85c-.067 1.42-.293 2.05-.47 2.5a2.82 2.82 0 01-1.63 1.63c-.45.177-1.08.403-2.5.47-1.27.054-1.646.07-4.85.07s-3.58-.016-4.85-.07c-1.42-.067-2.05-.293-2.5-.47a2.82 2.82 0 01-1.63-1.63c-.177-.45-.403-1.08-.47-2.5-.054-1.27-.07-1.646-.07-4.85s.016-3.58.07-4.85c.067-1.42.293-2.05.47-2.5a2.82 2.82 0 011.63-1.63c.45-.177 1.08-.403 2.5-.47 1.27-.054 1.646-.07 4.85-.07zM12 0c-3.266 0-3.693.016-4.993.07c-1.4.067-2.316.3-3.11.603a4.576 4.576 0 00-1.87 1.87C.3 5.397.067 6.313.07 7.72c.054 1.3.07 1.727.07 4.993s-.016 3.693-.07 4.993c-.067 1.4-.3 2.316-.603 3.11a4.576 4.576 0 001.87 1.87c.8.303 1.716.536 3.11.603 1.3.054 1.727.07 4.993.07s3.693-.016 4.993-.07c1.4-.067 2.316-.3 3.11-.603a4.576 4.576 0 001.87-1.87c.303-.8.536-1.716.603-3.11.054-1.3.07-1.727.07-4.993s-.016-3.693-.07-4.993c-.067-1.4-.3-2.316-.603-3.11a4.576 4.576 0 00-1.87-1.87c-.8-.303-1.716-.536-3.11-.603C15.693 0 15.266 0 12 0zm0 4.5a7.5 7.5 0 100 15 7.5 7.5 0 000-15zm0 2.5a5 5 0 110 10 5 5 0 010-10z"/></svg>
                </a>
                <a href="#" class="hover:text-venezuelan-secondary transition-colors duration-300">
                    <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.58.016 4.85.07c1.42.067 2.05.293 2.5.47a2.82 2.82 0 011.63 1.63c.177.45.403 1.08.47 2.5.054 1.27.07 1.646.07 4.85s-.016 3.58-.07 4.85c-.067 1.42-.293 2.05-.47 2.5a2.82 2.82 0 01-1.63 1.63c-.45.177-1.08.403-2.5.47-1.27.054-1.646.07-4.85.07s-3.58-.016-4.85-.07c-1.42-.067-2.05-.293-2.5-.47a2.82 2.82 0 01-1.63-1.63c-.177-.45-.403-1.08-.47-2.5-.054-1.27-.07-1.646-.07-4.85s.016-3.58.07-4.85c.067-1.42.293-2.05.47-2.5a2.82 2.82 0 011.63-1.63c.45-.177 1.08-.403 2.5-.47 1.27-.054 1.646-.07 4.85-.07zM12 0c-3.266 0-3.693.016-4.993.07c-1.4.067-2.316.3-3.11.603a4.576 4.576 0 00-1.87 1.87C.3 5.397.067 6.313.07 7.72c.054 1.3.07 1.727.07 4.993s-.016 3.693-.07 4.993c-.067 1.4-.3 2.316-.603 3.11a4.576 4.576 0 001.87 1.87c.8.303 1.716.536 3.11.603 1.3.054 1.727.07 4.993.07s3.693-.016 4.993-.07c1.4-.067 2.316-.3 3.11-.603a4.576 4.576 0 001.87-1.87c.303-.8.536-1.716.603-3.11.054-1.3.07-1.727.07-4.993s-.016-3.693-.07-4.993c-.067-1.4-.3-2.316-.603-3.11a4.576 4.576 0 00-1.87-1.87c-.8-.303-1.716-.536-3.11-.603C15.693 0 15.266 0 12 0zm0 4.5a7.5 7.5 0 100 15 7.5 7.5 0 000-15zm0 2.5a5 5 0 110 10 5 5 0 010-10z"/></svg>
                </a>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="bg-blue-900 text-white text-center p-4 mt-8">
        <p>© 2024 UMEJUMAC. Todos los derechos reservados.</p>
    </footer>

    <!-- Script para el menú móvil -->
    <script>
        const cartButton = document.getElementById('cart-button');
        const mobileMenu = document.getElementById('mobile-menu');

        cartButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });
    </script>

</body>
</html>
