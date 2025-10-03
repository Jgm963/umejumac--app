<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC | Soluciones Integrales y Digitales</title>
    
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
            display: flex; /* Para alinear el logo y el texto */
            justify-content: center; /* Centrar el contenido horizontalmente */
            align-items: center; /* Centrar el contenido verticalmente */
            gap: 15px; /* Espacio entre el logo y el texto */
        }
        /* Estilos para el contenedor del logo en el encabezado */
        .header-logo {
            width: 60px; /* Tamaño de tu logo */
            height: 60px;
            border-radius: 50%; /* Si quieres que el contenedor del logo sea circular */
            overflow: hidden; /* Asegura que la imagen se ajuste al círculo */
            background-color: white; /* Fondo blanco si la imagen no llena todo el círculo */
            display: flex; /* Para centrar la imagen dentro del contenedor */
            justify-content: center;
            align-items: center;
        }
        .header-logo img {
            width: 100%; /* La imagen ocupa todo el contenedor */
            height: 100%;
            object-fit: contain; /* Para que la imagen se vea completa sin recortarse */
        }
        header h1 {
            margin: 0;
            font-size: 2.2em;
        }
        header p { /* Estilo para el eslogan debajo del título */
            margin: 5px 0 0;
            font-size: 0.9em;
            opacity: 0.9;
        }

        /* --- NAVEGACIÓN PRINCIPAL --- */
        .main-nav {
            background-color: #0056b3; /* Azul Medio */
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
            background-color: var(--color-principal); /* Azul Oscuro */
            color: white;
            text-decoration: none;
            padding: 15px 30px;
            border-radius: 8px;
            font-weight: bold;
            transition: background-color 0.3s, transform 0.2s;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
        }
        .action-button:hover {
            background-color: #0056b3; /* Azul Medio en hover */
            transform: translateY(-2px);
        }
        /* Estilo diferente para el Portafolio para destacarlo */
        .action-button.portfolio-btn {
            background-color: var(--color-acento); /* Amarillo/Naranja */
            color: var(--color-principal);
        }
        .action-button.portfolio-btn:hover {
            background-color: #f0b400; /* Tono más oscuro de acento */
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
            flex: 1 1 300px; /* Hace que las tarjetas sean responsivas */
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
                flex-direction: column; /* Apila el logo y el texto en pantallas pequeñas */
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
                flex-basis: 100%; /* Una tarjeta por fila en móviles */
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
            <p>Soluciones Integrales.</p>
        </div>
    </header>

    <nav class="main-nav">
        <div class="container">
            <ul>
                <li><a href="#asesoria">Asesoría</a></li>
                <li><a href="#bienesyservicios">Bienes y Servicios</a></li>
                <li><a href="#ventas">Ventas</a></li>
                <li><a href="portafolio.html">Portafolio</a></li>
                <li><a href="https://umejumac.blogspot.com/?zx=d20becec4ee219d9" target="_blank">Blog</a></li>
            </ul>
        </div>
    </nav>

    <main class="container">
        
        <section class="seccion-intro" style="text-align: center; padding: 40px 0;">
            <h2>Bienvenido a la Plataforma UMEJUMAC</h2>
            <p style="font-size: 1.1em; color: #555;">Somos tu aliado en abordar crisis en salud bajo el pensamiento estrategico</p>
            
            <div class="button-group">
                <a href="#asesoria" class="action-button">Nuestros Servicios</a>
                <a href="portafolio.html" class="action-button portfolio-btn">Ver Portafolio</a>
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
                <p>Conformamos equipos de trabajo de alta efectividad, Garantizando calidad y logística impecable para el sector público y privado.</p>
                <ul>
                    <li>Suministro de material sobre abordajes estrategicos.</li>
                    <li>Logística en marco logico.</li>
                </ul>
                <a href="#">Conformacion de ETAE: equipos de trabajo de alta efectividad →</a>
            </section>

            <section id="ventas" class="card">
                <h2>3. Ventas de productos varios propiedad de la firma personal UMEJUMAC</h2>
                <p>Tu socio en adquirir bienes a precios justos.</p>
                <ul>
                    <li> Atencion Personalizada.</li>
                    <li>Precios consensuados.</li>
                </ul>
                <a href="#">Ver Soluciones →</a>
            </section>

        </div>

    </main>

    <footer>
        <div class="container">
            <p>Contáctanos: jgm963@gmail.com | Tel: +58 4265708369>
            <p style="font-size: 0.8em; margin-top: 10px;">&copy; 2025 UMEJUMAC. Todos los derechos reservados.</p>
        </div>
    </footer>

</body>
</html>
