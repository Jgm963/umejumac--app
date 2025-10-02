<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Umejumac - Soluciones Digitales</title>
    <style>
        /* --- COLORES CORPORATIVOS Y VARIABLES --- */
        :root {
            --color-principal: #0056b3; /* Azul Oscuro */
            --color-secundario: #2a6496; /* Azul Medio */
            --color-acento: #fca311; /* Naranja/Ámbar */
            --color-fondo: #f4f4f9;
        }

        /* --- ESTILOS GENERALES --- */
        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: var(--color-fondo);
            color: #333;
            /* Scroll suave activado para el desplazamiento del logo */
            scroll-behavior: smooth; 
        }
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }

        /* --- ENCABEZADO (HEADER) --- */
        .header-umejumac {
            background-color: var(--color-principal);
            color: white;
            padding: 15px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.15);
        }
        .header-umejumac h1 {
            margin: 0;
            padding-left: 30px;
            font-size: 2.2em;
            letter-spacing: 1px;
        }
        .logo-button {
            background: none;
            border: none;
            cursor: pointer;
            padding: 0 30px;
            text-decoration: none;
        }
        /* Logo en el encabezado: Ajustes para el contenedor de la imagen */
        .header-logo-display {
            width: 50px;
            height: 50px;
            background-color: white; /* Fondo blanco para el logo circular */
            border-radius: 50%; /* Hace el contenedor circular */
            display: inline-flex; 
            justify-content: center;
            align-items: center;
            transition: transform 0.3s;
            overflow: hidden; /* Recorta cualquier parte de la imagen que sobresalga */
            padding: 5px; /* Espacio alrededor del logo dentro del círculo */
            box-sizing: border-box;
            border: 2px solid var(--color-acento); /* Borde para que destaque */
        }
        .header-logo-display img {
            width: 100%;
            height: 100%;
            object-fit: contain; /* Ajusta la imagen dentro del contenedor sin recortar */
        }
        .header-logo-display:hover {
            transform: scale(1.1); /* Efecto de zoom al pasar el ratón */
        }

        /* --- BIENVENIDA --- */
        .welcome-section {
            text-align: center; 
            padding: 50px 0 30px; 
            margin-bottom: 30px;
        }
        .welcome-section h2 {
            color: var(--color-principal); 
            font-size: 2.5em; 
            margin-bottom: 10px;
        }
        .welcome-section p {
            font-size: 1.2em; 
            color: #555; 
            max-width: 900px; 
            margin: 0 auto;
        }

        /* --- MENÚ PRINCIPAL Y SECCIONES (ACORDEÓN CSS) --- */
        .main-menu {
            display: flex;
            justify-content: space-around;
            padding: 20px 0;
            background-color: #fff;
            gap: 20px;
            margin-bottom: 40px;
        }
        .menu-item {
            flex: 1;
            text-align: center;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            transition: box-shadow 0.3s;
        }
        .menu-item:hover {
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        .menu-toggle {
            display: block;
            width: 100%;
            padding: 18px 10px;
            background-color: var(--color-secundario);
            color: white;
            border: none;
            cursor: pointer;
            font-size: 1.15em;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        .menu-toggle:hover {
            background-color: var(--color-principal);
        }

        /* Mecánica de Despliegue (CSS Pura) */
        .toggle-checkbox {
            display: none;
        }
        .dropdown-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.7s ease-in-out, padding 0.7s;
            background-color: #ffffff;
            text-align: left;
            padding: 0 20px;
            box-sizing: border-box;
            border-top: 3px solid var(--color-principal);
        }
        .toggle-checkbox:checked + .menu-toggle + .dropdown-content {
            max-height: 1000px;
            padding: 20px;
        }

        /* --- CONTENIDO INTERNO Y GALERÍA --- */
        .content-section h3 {
            color: var(--color-acento);
            border-bottom: 2px solid #ddd;
            padding-bottom: 5px;
            margin-top: 10px;
        }
        .gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 15px;
            justify-content: space-around;
        }
        .gallery-item {
            flex: 1 1 calc(45% - 15px);
            min-width: 180px;
            text-align: center;
            border: 1px solid #eee;
            border-radius: 5px;
            padding-bottom: 10px;
        }
        .placeholder-box {
            width: 100%;
            height: 100px;
            background-color: #eee;
            border-bottom: 1px dashed #ccc;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 0.9em;
            color: #666;
            margin-bottom: 5px;
        }
        .product-info strong {
            color: var(--color-principal);
            display: block;
            margin-bottom: 5px;
        }

        /* --- SECCIÓN DEL LOGO FABRICADO (DESTINO INTERACTIVO) --- */
        #about-logo {
            padding: 60px 0;
            text-align: center;
            background-color: #ffffff;
            border-top: 1px solid #eee;
            margin-top: 40px;
            min-height: 400px; 
        }
        /* Estilos ajustados para el logo en la sección de destino */
        .fabricated-logo-display {
            width: 250px; 
            height: 250px;
            background-color: #ffffff; 
            border: 5px solid var(--color-principal); 
            border-radius: 50%; 
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            margin: 20px auto 30px auto;
            position: relative;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        
        .logo-image-large {
            width: 90%; 
            height: 90%;
            object-fit: contain; 
        }
        
        #about-logo p {
            max-width: 800px;
            margin: 0 auto;
            color: #555;
        }

        /* --- PIE DE PÁGINA Y CONTACTO --- */
        .footer-contact {
            background-color: #333;
            color: white;
            padding: 30px 0;
            text-align: center;
            margin-top: 60px;
        }
        .footer-contact h2 {
            color: var(--color-acento);
            margin-bottom: 15px;
            font-size: 1.8em;
        }
        .contact-details a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
            font-weight: bold;
            display: inline-block;
            margin-bottom: 8px;
        }
        .contact-details a:hover {
            color: var(--color-acento);
            text-decoration: underline;
        }
        
        /* --- MEDIA QUERIES (RESPONSIVE) --- */
        @media (max-width: 768px) {
            .main-menu {
                flex-direction: column;
                gap: 15px;
                padding: 10px;
            }
            .header-umejumac h1 {
                font-size: 1.8em;
                padding-left: 15px;
            }
            .fabricated-logo-display {
                width: 180px;
                height: 180px;
            }
        }
    </style>
</head>
<body>

    <header class="header-umejumac">
        <div class="container" style="display: flex; justify-content: space-between; align-items: center;">
            <h1>Umejumac</h1>
            
            <a href="#about-logo" class="logo-button">
                <div class="header-logo-display">
                    <img src="ruta/al/logo-pequeno.png" alt="Logo Umejumac">
                </div>
            </a>
        </div>
    </header>

    <main>
        <section class="welcome-section container">
            <h2>Bienvenido a Umejumac</h2>
            <p>Especialistas en soluciones digitales y desarrollo web, impulsando tu negocio al siguiente nivel con tecnología y diseño innovadores.</p>
        </section>

        <section class="main-menu container">
            
            <div class="menu-item">
                <input type="checkbox" id="toggle-servicios" class="toggle-checkbox">
                <label for="toggle-servicios" class="menu-toggle">Nuestros Servicios</label>
                
                <div class="dropdown-content content-section">
                    <h3>Desarrollo Web y Apps</h3>
                    <p>Creación de sitios web a medida y aplicaciones móviles eficientes.</p>
                    <div class="gallery">
                        <div class="gallery-item">
                            <div class="placeholder-box">Diseño UI/UX</div>
                            <div class="product-info"><strong>Web Responsive</strong></div>
                        </div>
                        <div class="gallery-item">
                            <div class="placeholder-box">Desarrollo Front-End</div>
                            <div class="product-info"><strong>Optimización SEO</strong></div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <input type="checkbox" id="toggle-proyectos" class="toggle-checkbox">
                <label for="toggle-proyectos" class="menu-toggle">Proyectos Recientes</label>
                
                <div class="dropdown-content content-section">
                    <h3>Portafolio Destacado</h3>
                    <p>Mira nuestros casos de éxito y las soluciones que hemos implementado.</p>
                    <div class="gallery">
                        <div class="gallery-item">
                            <div class="placeholder-box">E-Commerce B2B</div>
                            <div class="product-info"><strong>Cliente Industrial</strong></div>
                        </div>
                        <div class="gallery-item">
                            <div class="placeholder-box">Plataforma Educativa</div>
                            <div class="product-info"><strong>Inicio Rápido</strong></div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <input type="checkbox" id="toggle-nosotros" class="toggle-checkbox">
                <label for="toggle-nosotros" class="menu-toggle">Filosofía de Trabajo</label>
                
                <div class="dropdown-content content-section">
                    <h3>Nuestro Compromiso</h3>
                    <ul>
                        <li>Innovación constante.</li>
                        <li>Transparencia total.</li>
                        <li>Soporte dedicado 24/7.</li>
                    </ul>
                </div>
            </div>

        </section>

        <section id="about-logo" class="container">
            <h2>Identidad de Umejumac</h2>
            
            <div class="fabricated-logo-display">
                <img src="ruta/al/logo-grande.png" alt="Logo Principal Umejumac" class="logo-image-large">
            </div>
            
            <p>El logo de Umejumac representa la **convergencia digital** y la **eficiencia**. Los colores azul y naranja simbolizan la confianza, la seriedad técnica y la creatividad que inyectamos en cada proyecto.</p>
        </section>
    </main>

    <footer class="footer-contact">
        <div class="container">
            <h2>Hablemos de tu Proyecto</h2>
            <div class="contact-details">
                <a href="mailto:contacto@umejumac.com">Email: contacto@umejumac.com</a>
                <a href="tel:+1234567890">Teléfono: +1 (234) 567-890</a>
            </div>
            <p style="margin-top: 20px; font-size: 0.9em; color: #bbb;">&copy; 2024 Umejumac. Todos los derechos reservados.</p>
        </div>
    </footer>

</body>
</html>
