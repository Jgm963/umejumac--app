<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC | Soluciones Integrales</title>
    
    <style>
        /* --- VARIABLES DE DISEÑO --- */
        :root {
            --color-principal: #003366; /* Azul Oscuro UMEJUMAC */
            --color-acento: #ffcc00;  /* Amarillo/Naranja */
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
        
        /* --- ENCABEZADO (MODIFICADO) --- */
        header {
            background-color: var(--color-principal);
            color: white;
            padding: 20px 0;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
        }
        .header-logo {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            overflow: hidden;
            background-color: white;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .header-logo img {
            /* Asegúrate de que este nombre de archivo sea exacto: logo_umejumac_circle.png.png */
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
        header h1 {
            margin: 0;
            font-size: 2.2em;
        }
        header p {
            margin: 5px 0 0;
            font-size: 0.9em;
            opacity: 0.9;
        }

        /* --- NAVEGACIÓN PRINCIPAL --- */
        .main-nav {
            background-color: #0056b3;
            padding: 10px 0;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .main-nav ul {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            justify-content: center;
            gap: 25px;
        }
        .main-nav a {
            color: white;
            text-decoration: none;
            font-weight: bold;
            padding: 5px 10px;
            transition: color 0.3s;
        }
        .main-nav a:hover {
            color: var(--color-acento);
        }

        /* --- NUEVOS ESTILOS PARA BOTONES DE ACCIÓN --- */
        .button-group {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-top: 30px;
        }
        .action-button {
            background-color: var(--color-principal);
            color: white;
            text-decoration: none;
            padding: 15px 30px;
            border-radius: 8px;
            font-weight: bold;
            transition: background-color 0.3s, transform 0.2s;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
        }
        .action-button:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
        }
        .action-button.portfolio-btn {
            background-color: var(--color-acento);
            color: var(--color-principal);
        }
        .action-button.portfolio-btn:hover {
            background-color: #f0b400;
        }

        /* --- SECCIONES DE CONTENIDO (TARJETAS) --- */
        .seccion-principal {
            margin-top: 40px;
            padding: 20px;
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
        }
        .card {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            flex: 1 1 300px;
            transition: transform 0.3s, border-left 0.3s;
            border-left: 5px solid var(--color-principal);
        }
        .card:hover {
            transform: translateY(-5px);
            border-left: 5px solid var(--color-acento);
        }
        .card h2 {
            color: var(--color-principal);
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }
        
        /* NUEVO: Estilo para la sección del experto en el home */
        .expert-intro {
            text-align: center;
            padding: 60px 20px;
            background-color: white;
            border-top: 1px solid #ddd;
            margin-top: 40px;
        }
        .expert-intro h2 {
            color: var(--color-principal);
            margin-bottom: 20px;
        }

        /* --- PIE DE PÁGINA --- */
        footer {
            background-color: #333;
            color: white;
            padding: 30px 0;
            margin-top: 60px;
            text-align: center;
        }

        /* --- MEDIA QUERIES (PARA RESPONSIVE) --- */
        @media (max-width: 600px) {
            header {
                flex-direction: column;
                gap: 5px;
            }
            header h1 {
                font-size: 1.8em;
            }
            .main-nav ul {
                flex-direction: column;
                gap: 10px;
            }
            .main-nav a {
                padding: 10px 0;
                display: block;
            }
            .seccion-principal {
                padding: 10px;
            }
            .card {
                flex-basis: 100%;
            }
            .button-group {
                flex-direction: column;
                align-items: center;
            }
            .action-button {
                width: 80%;
                margin: 5px 0;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="header-logo">
            <img src="logo_umejumac_circle.png.png" alt="Logo UMEJUMAC">
        </div>
        <div>
            <h1>UMEJUMAC</h1>
            <p>Soluciones Integrales para tu Negocio.</p>
        </div>
    </header>

    <nav class="main-nav">
        <div class="container">
            <ul>
                <li><a href="#asesoria">Asesoría</a></li>
                <li><a href="#bienesyservicios">Bienes y Servicios</a></li>
                <li><a href="#ventas">Ventas</a></li>
                <li><a href="portafolio.html">Portafolio/CV</a></li>
                <li><a href="https://umejumac.blogspot.com/?zx=d20becec4ee219d9" target="_blank">Blog</a></li>
            </ul>
        </div>
    </nav>

    <main class="container">
        
        <section class="seccion-intro" style="text-align: center; padding: 40px 0;">
            <h2>BIENVENIDO a UMEJUMAC</h2>
            <p style="font-size: 1.1em; color: #555;">Somos tu aliado en el abordaje a inconvenientes en la salud colectiva y personal</p>
            
            <div class="button-group">
                <a href="#asesoria" class="action-button">Nuestros Servicios</a>
                <a href="portafolio.html" class="action-button portfolio-btn">Ver Portafolio/CV</a>
            </div>
        </section>

        <div class="seccion-principal">

            <section id="asesoria" class="card">
                <h2>1. Asesoría en Salud Colectiva</h2>
                <p>Ofrecemos consultoría especializada para optimizar la gestión de riesgos de salud, desde el análisis epidemiológico hasta el diseño de políticas de prevención y bienestar.</p>
                <ul>
                    <li>Análisis Estratégico.</li>
                    <li>Planes de Prevención.</li>
                </ul>
                <a href="#">Más sobre Asesoría →</a>
            </section>

            <section id="bienesyservicios" class="card">
                <h2>2. Bienes y Servicios</h2>
                <p>Garantizamos calidad y logística de un Equipo de Trabajo de Alta Efectividadimpecable. </p>
                <ul>
                    <li>Suministro de material de capacitacion en planificacion estrategica</li>
                    <li>Logística en abordaje estrategico.</li>
                </ul>
                <a href="#">Ver Catálogo →</a>
            </section>

            <section id="ventas" class="card">
                <h2>3. Ventas de bienes de la firma personal UMEJUMAC</h2>
                <p>Tu socio en consenso para precios justos</p>
                <ul>
                    <li>Desarrollo Personalizado.</li>
                    <li>Gestión Estrategica.</li>
                </ul>
                <a href="#">Ver Soluciones →</a>
            </section>

        </div>
        
        <section class="expert-intro">
            <h2>Liderazgo y Experiencia</h2>
            <p style="font-size: 1.1em; max-width: 800px; margin: 0 auto 20px;">
                UMEJUMAC es dirigida y asesorada por el **Dr. José Gregorio Morales**, Doctor en Gestión, Magister en Salud Pública y Abogado, con más de 30 años de experiencia en gestión de salud pública, docencia universitaria y desarrollo de políticas de bienestar. Conoce su trayectoria completa en el Portafolio.
            </p>
            <a href="portafolio.html" class="action-button portfolio-btn" style="background-color: #003366; color: white;">Ver Trayectoria Completa</a>
        </section>

    </main>

    <footer>
        <div class="container">
            <p>Contáctanos: <a href="mailto:jgm963@gmail.com" style="color: white; text-decoration: underline;">jgm963@gmail.com</a> | Telf: +(58) 426 570 83 69</p>
            <p style="font-size: 0.8em; margin-top: 10px;">&copy; 2025 UMEJUMAC. Todos los derechos reservados.</p>
        </div>
    </footer>

</body>
</html>
