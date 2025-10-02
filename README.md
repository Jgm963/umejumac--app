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
        /* Ajuste para el contenedor interno del header para alinear H1 y Logo */
        .header-content-wrapper { 
            display: flex;
            align-items: center; /* Centra verticalmente el h1 y el logo */
            padding-left: 30px; /* Mantiene el padding izquierdo del texto */
        }
        .header-umejumac h1 {
            margin: 0;
            /* padding-left: 30px; */ /* Movido a .header-content-wrapper */
            font-size: 2.2em;
            letter-spacing: 1px;
            color: white; /* Asegura el color blanco del texto */
            line-height: 1; /* Para alinear mejor con el logo */
        }
        /* ELIMINADO: .logo-button */ 

        /* Logo en el encabezado: Ajustes para el contenedor de la imagen */
        .header-logo-display {
            width: 50px;
            height: 50px;
            background-color: white; /* Fondo blanco para el logo circular */
            border-radius: 50%; /* Hace el contenedor circular */
            display: flex; /* Cambiado a flex para centrar contenido */
            justify-content: center;
            align-items: center;
            /* transition: transform 0.3s; */ /* Eliminado: ya no es interactivo */
            overflow: hidden; /* Recorta cualquier parte de la imagen que sobresalga */
            /* padding: 5px; */ /* Eliminado para que el logo tenga más espacio */
            box-sizing: border-box;
            border: 2px solid var(--color-acento); /* Borde para que destaque */
            margin-left: 15px; /* Espacio entre el texto y el logo */
        }
        .header-logo-display img {
            width: 100%;
            height: 100%;
            object-fit: contain; /* Ajusta la imagen dentro del contenedor sin recortar */
        }
        /* ELIMINADO: .header-logo-display:hover */

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
            /* Ajuste para el encabezado en móvil */
            .header-umejumac .container {
                flex-direction: column; /* Apila elementos */
                align-items: flex-start; /* Alinea a la izquierda */
                padding-left: 15px;
            }
            .header-content-wrapper {
                padding-left: 0; /* Elimina el padding extra en móvil si se apilan */
                justify-content: center; /* Centra el logo y h1 si están apilados */
                width: 100%; /* Ocupa todo el ancho disponible */
            }
            .header-umejumac h1 {
                font-size: 1.8em;
                padding-left: 0; /* Ya no es necesario con el wrapper */
                text-align: center; /* Centra el título en móvil */
                width: 100%;
            }
            .header-logo-display {
                margin-left: 0; /* Elimina margen si se apilan */
                margin-top: 10px; /* Espacio entre título y logo en móvil */
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
            <div class="header-content-wrapper">
                <h1>Umejumac</h1>
                <div class="header-logo-display">
                    <img src="ruta/al/logo-pequeno.png" alt="Logo Umejumac">
                </div>
            </div>
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
                        <div class="gallery-item
