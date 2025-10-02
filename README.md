<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC | Unidad Médico-Jurídica Morales A.C.</title>
    
    <style>
        /* --- COLORES CORPORATIVOS Y VARIABLES --- */
        :root {
            --color-principal: #0056b3; 
            --color-secundario: #2a6496; 
            --color-acento: #fca311; 
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
            /* Aunque el JS toma el control, se mantiene por si acaso */
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
        /* Logo en el encabezado: usando la imagen zzz.png */
        .header-logo-display {
            width: 50px;
            height: 50px;
            background-color: white; 
            border-radius: 50%;
            display: inline-flex; 
            justify-content: center;
            align-items: center;
            transition: transform 0.3s;
            overflow: hidden; 
            padding: 5px; 
            box-sizing: border-box;
        }
        .header-logo-display img {
            width: 100%;
            height: 100%;
            object-fit: contain; 
        }
        .header-logo-display:hover {
            transform: scale(1.1);
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
        .fabricated-logo-display {
            width: 200px;
            height: 200px;
            background-color: #ffffff;
            border: 3px solid var(--color-principal);
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
        .fabricated-logo-display .logo-text-top {
            font-size: 0.9em;
            font-weight: bold;
            color: var(--color-principal);
            position: absolute;
            top: 25px;
            width: 100%;
            text-align: center;
        }
        .fabricated-logo-display .logo-initials {
            font-size: 0.7em;
            color: #555;
            position: absolute;
            top: 45px;
            width: 100%;
            text-align: center;
        }
        .fabricated-logo-display .logo-m {
            font-size: 6em; 
            font-weight: bold;
            color: black;
            line-height: 1; 
        }
        .fabricated-logo-display .logo-text-bottom {
            font-size: 0.9em;
            font-weight: bold;
            color: var(--color-principal);
            position: absolute;
            bottom: 25px;
            width: 100%;
            text-align: center;
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
        <h1>UMEJUMAC</h1>
        <a href="#about-logo" onclick="event.preventDefault(); scrollToLogo('about-logo');" class="logo-button" aria-label="Ver detalles del logo UMEJUMAC">
            <div class="header-logo-display">
                <img src="zzz.png" alt="Logo UMEJUMAC">
            </div>
        </a>
    </header>

    <div class="container" id="home">

        <section class="welcome-section">
            <h2>UNIDAD MÉDICO-JURÍDICA MORALES A.C.</h2>
            <p>La convergencia única de experiencia en **Salud Pública, Derecho y Gestión de Crisis**. Somos su aliado experto en la compleja intersección de la medicina y la ley, liderados por el Dr. José Gregorio Morales.</p>
        </section>

        <section id="about-logo">
            <h2 style="color: var(--color-principal);">Nuestro Sello Distintivo</h2>
            <div class="fabricated-logo-display">
                <span class="logo-text-top">UMEJUMAC</span>
                <span class="logo-initials">E.J.M.R. (Edgar José Morales Rojas)</span>
                <span class="logo-m">M</span>
                <span class="logo-text-bottom">ETA (Equipo de Trabajo de Alta Efectividad)</span>
            </div>
            <p>Este logo representa la **convergencia** de la gestión profesional de la Unidad Médico-Jurídica, bajo el liderazgo del Dr. Morales, y el compromiso con la **Alta Efectividad (ETA)** en cada consulta y proyecto.</p>
        </section>


        <div class="main-menu">

            <div class="menu-item">
                <input type="checkbox" id="toggle-salud" class="toggle-checkbox">
                <label for="toggle-salud" class="menu-toggle">1. Consultoría en Salud Colectiva 📈</label>
                <div class="dropdown-content">
                    <div class="content-section">
                        <h3>Gestión y Planificación Estratégica</h3>
                        <p>Asesoramiento especializado en la gestión de sistemas de salud, diagnóstico situacional y elaboración de planes estratégicos en contextos de crisis.</p>
                        <div class="gallery">
                            <div class="gallery-item"><div class="placeholder-box">Fotografía: Mesas de Trabajo/Reunión de Crisis</div><p>Planificación Estratégica</p></div>
                            <div class="gallery-item"><div class="placeholder-box">Fotografía: Informe / Documento de Logros</div><p>Resultados y Logros</p></div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <input type="checkbox" id="toggle-servicios" class="toggle-checkbox">
                <label for="toggle-servicios" class="menu-toggle">2. Servicios Profesionales (Medicina y Derecho) ⚖️</label>
                <div class="dropdown-content">
                    <div class="content-section">
                        <h3>Medicina Legal, Bioética y Asesoría Jurídica</h3>
                        <p>Consultoría experta en la intersección médico-legal. Ofrecemos análisis de casos de responsabilidad médica, asesoría en bioética y docencia.</p>
                        <div class="gallery">
                            <div class="gallery-item"><div class="placeholder-box">Fotografía: Simulación de Juicio / Junta Médica</div><p>Asesoría en Casos Legales</p></div>
                            <div class="gallery-item"><div class="placeholder-box">Fotografía: Dr. Morales en Conferencia</div><p>Formación y Docencia</p></div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <input type="checkbox" id="toggle-venta" class="toggle-checkbox">
                <label for="toggle-venta" class="menu-toggle">3. Venta de Bienes UMEJUMAC 🛍️</label>
                <div class="dropdown-content">
                    <div class="content-section">
                        <h3>Galería de Productos Exclusivos</h3>
                        <p>Adquiera recursos y publicaciones del Dr. Morales, instrumental médico-quirúrgico y material de apoyo.</p>
                        <div class="gallery">
                            <div class="gallery-item"><div class="placeholder-box">Imagen: Libro "Gestión Estratégica en Crisis"</div><div class="product-info"><strong>Publicación:</strong> Gestión Estratégica</div></div>
                            <div class="gallery-item"><div class="placeholder-box">Imagen: Instrumental Médico-Quirúrgico</div><div class="product-info"><strong>Material:</strong> Instrumental Certificado</div></div>
                            <div class="gallery-item"><div class="placeholder-box">Imagen: Plataforma Moodle</div><div class="product-info"><strong>Digital:</strong> Módulos de Capacitación</div></div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
        </div>

    <footer class="footer-contact">
        <div class="container">
            <h2>📞 Contáctenos Hoy para Asesoría Experta</h2>
            <div class="contact-details">
                <p>
                    <a href="mailto:jgm963@gmail.com">📧 jgm963@gmail.com</a>
                    <a href="mailto:jgm963@outlook.com">📧 jgm963@outlook.com</a>
                    <a href="tel:+584265708369">📞 0426 570 83 69</a>
                    <a href="tel:+584126938369">📞 0412 693 83 69</a>
                </p>
            </div>
            <p style="margin-top: 15px; font-size: 0.9em;">© 2024 UMEJUMAC - Unidad Médico-Jurídica Morales A.C.</p>
        </div>
    </footer>

    <script>
        function scrollToLogo(targetId) {
            // Obtiene el elemento de destino usando el ID
            const targetElement = document.getElementById(targetId);
