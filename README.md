<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC | Unidad Médico-Jurídica Morales A.C.</title>
    
    <style>
        /* --- COLORES CORPORATIVOS --- */
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
        .logo-placeholder {
            width: 50px;
            height: 50px;
            background-color: var(--color-acento);
            border-radius: 50%;
            display: inline-block;
            line-height: 50px;
            text-align: center;
            font-weight: bold;
            color: #333;
            transition: transform 0.3s;
        }
        .logo-placeholder:hover {
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

        /* --- MENÚ PRINCIPAL Y SECCIONES --- */
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

        /* Truco para el desplegable (CSS-Only Accordion) */
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
            max-height: 1000px; /* Suficiente altura para el contenido */
            padding: 20px;
        }

        /* --- CONTENIDO INTERNO --- */
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

        /* --- PIE DE PÁGINA Y CONTACTO (LA "RED") --- */
        .footer-contact {
            background-color: #333;
            color: white;
            padding: 30px 0;
            text-align: center;
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
    </style>
</head>
<body>

    <header class="header-umejumac">
        <h1>UMEJUMAC</h1>
        <a href="#home" class="logo-button">
            <span class="logo-placeholder">LOGO</span>
        </a>
    </header>

    <div class="container" id="home">

        <section class="welcome-section">
            <h2>UNIDAD MÉDICO-JURÍDICA MORALES A.C.</h2>
            <p>La convergencia única de experiencia en **Salud Pública, Derecho y Gestión de Crisis**. Somos su aliado experto en la compleja intersección de la medicina y la ley, liderados por el Dr. José Gregorio Morales.</p>
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
                            <div class="gallery-item">
                                <div class="placeholder-box">Mesa de Trabajo/Reunión de Crisis</div>
                                <p>Planificación Estratégica</p>
                            </div>
                            <div class="gallery-item">
                                <div class="placeholder-box">Foto: Informe / Documento de Logros</div>
                                <p>Resultados y Logros</p>
                            </div>
                        </div>
                        <p><em>(Anexe aquí más fotografías de mesas de trabajo o enlaces a proyectos.)</em></p>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <input type="checkbox" id="toggle-servicios" class="toggle-checkbox">
                <label for="toggle-servicios" class="menu-toggle">2. Servicios Profesionales (Medicina y Derecho) ⚖️</label>
                <div class="dropdown-content">
                    <div class="content-section">
                        <h3>Medicina Legal, Bioética y Asesoría Jurídica</h3>
                        <p>Consultoría experta en la intersección médico-legal. Ofrecemos análisis de casos de responsabilidad médica, asesoría en bioética (autonomía y consentimiento) y docencia en Medicina Legal y Psicocriminología.</p>
                        <div class="gallery">
                            <div class="gallery-item">
                                <div class="placeholder-box">Foto: Simulación de Juicio / Junta Médica</div>
                                <p>Asesoría en Casos Legales</p>
                            </div>
                            <div class="gallery-item">
                                <div class="placeholder-box">Foto: Dr. Morales en Conferencia</div>
                                <p>Formación y Docencia</p>
                            </div>
                        </div>
                        <p><em>(Aquí puede añadir enlaces a publicaciones o el CV detallado.)</em></p>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <input type="checkbox" id="toggle-venta" class="toggle-checkbox">
                <label for="toggle-venta" class="menu-toggle">3. Venta de Bienes UMEJUMAC 🛍️</label>
                <div class="dropdown-content">
                    <div class="content-section">
                        <h3>Galería de Productos Exclusivos</h3>
                        <p>Adquiera recursos y publicaciones del Dr. Morales, instrumental médico-quirúrgico y material de apoyo para la docencia.</p>
                        <div class="gallery">
                            <div class="gallery-item">
                                <div class="placeholder-box">Imagen: Libro "Gestión Estratégica en Crisis"</div>
                                <div class="product-info"><strong>Publicación:</strong> Gestión Estratégica</div>
                            </div>
                            <div class="gallery-item">
                                <div class="placeholder-box">Imagen: Instrumental Médico-Quirúrgico</div>
                                <div class="product-info"><strong>Material:</strong> Instrumental Certificado</div>
                            </div>
                            <div class="gallery-item">
                                <div class="placeholder-box">Imagen: Software o Plataforma Moodle</div>
                                <div class="product-info"><strong>Digital:</strong> Módulos de Capacitación</div>
                            </div>
                        </div>
                        <p style="text-align: center; margin-top: 20px;">*Contáctenos para verificar disponibilidad y precios.</p>
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
            <p style="margin-top: 15px; font-size: 0.9em;">© 2024 UMEJUMAC - Unidad Médico-Jurídica Morales A.C. | Mérida, Venezuela.</p>
        </div>
    </footer>

</body>
</html>
