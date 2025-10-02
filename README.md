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
        
        /* --- ENCABEZADO --- */
        header {
            background-color: var(--color-principal);
            color: white;
            padding: 20px 0;
            text-align: center;
        }
        header h1 {
            margin: 0;
            font-size: 2.2em;
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

        /* --- SECCIONES DE CONTENIDO --- */
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
    </style>
</head>
<body>

    <header>
        <div class="container">
            <img src="ruta/al/logo.png" alt="Logo UMEJUMAC" style="width: 50px; height: 50px; margin-bottom: 10px;">
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
                <li><a href="blog.html">Blog</a></li>
            </ul>
        </div>
    </nav>

    <main class="container">
        
        <section class="seccion-intro" style="text-align: center; padding: 40px 0;">
            <h2>Bienvenido a  UMEJUMAC</h2>
            <p style="font-size: 1.1em; color: #555;">Somos tu aliado en la convergencia de la salud, la logística y la transformación digital. Descubre nuestros tres pilares:</p>
        </section>

        <div class="seccion-principal">

            <section id="asesoria" class="card">
                <h2>1. Asesoría en Salud Colectiva</h2>
                <p>Ofrecemos consultoría especializada para optimizar la gestión de riesgos  desde el análisis epidemiológico hasta el diseño de políticas de prevención y bienestar.</p>
                <ul>
                    <li>Análisis Estratégico.</li>
                    <li>Planes de Prevención.</li>
                </ul>
                <a href="#">Más sobre Asesoría →</a>
            </section>

            <section id="bienesyservicios" class="card">
                <h2>2. Bienes y Servicios</h2>
                <p> Garantizamos calidad y logística impecable por un equipo de trabajo de alta efectividadpara el sector público y privado.</p>
                <ul>
                    <li>Suministro de informacion para logica estrategica.</li>
                    <li>Logística y estrategia.</li>
                </ul>
                <a href="#">Ver Catálogo →</a>
            </section>

            <section id="ventas" class="card">
                <h2>3. Ventas (bienes de la firma personal UMEJUMAC)</h2>
                <p>Tu socio en transformación personal.</p>
                <ul>
                    <li>Desarrollo de estrategias Personalizado.</li>
                    <li> Gestión Estrategica.</li>
                </ul>
                <a href="#">Ver Soluciones →</a>
            </section>

        </div>

    </main>

    <footer>
        <div class="container">
            <p>Contáctanos: jgm963@gmail.com | Tel: +58 426 570 83 69</p>
            <p style="font-size: 0.8em; margin-top: 10px;">&copy; 2025 UMEJUMAC. Todos los derechos reservados.</p>
        </div>
    </footer>

</body>
</html>
