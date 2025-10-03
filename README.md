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

        /* --- ESTILOS PARA BOTONES DE ACCIÓN --- */
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
        
        /* Estilo para la sección de introducción al experto */
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

        /* --- ESTILOS DE GALERÍA DE PRODUCTOS (NUEVO) --- */
        #bienesyservicios { /* Utilizamos este ID para la galería */
            padding: 40px 0;
            margin-top: 40px;
            background-color: white;
            border-top: 1px solid #ddd;
            text-align: center;
        }
        #bienesyservicios > h2 {
            color: var(--color-principal);
            font-size: 2em;
            margin-bottom: 30px;
            border-bottom: 3px solid var(--color-acento);
            display: inline-block;
            padding-bottom: 5px;
        }
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            padding: 0 20px;
        }
        .product-item {
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            background-color: #ffffff;
            text-align: left;
            transition: transform 0.3s;
        }
        .product-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
        }
        .product-image {
            width: 100%;
            height: 250px; 
            object-fit: cover; 
            display: block;
        }
        .product-details {
            padding: 15px;
        }
        .product-details h3 {
            margin-top: 0;
            color: var(--color-principal);
            font-size: 1.3em;
            line-height: 1.3;
        }
        .product-details p {
            font-size: 0.95em;
            color: #555;
            margin-bottom: 15px;
            min-height: 50px; /* Asegura espacio para la descripción */
        }
        .product-price {
            font-weight: bold;
            color: #d9534f; /* Color de precio llamativo */
            font-size: 1.3em;
            display: block;
            margin-top: 10px;
        }


        /* --- ESTILOS ESPECÍFICOS DEL CV (PORTAFOLIO) --- */
        #portafolio-cv { 
            background-color: white;
            padding: 40px;
            margin: 40px 0;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }
        #portafolio-cv h1 {
             color: var(--color-principal);
             font-size: 2.5em;
             margin-bottom: 5px;
        }
        #portafolio-cv hr {
            border: 0;
            height: 2px;
            background-color: var(--color-acento);
            margin-bottom: 20px;
        }
        #portafolio-cv h2 {
            color: var(--color-principal);
            border-bottom: 3px solid var(--color-acento);
            padding-bottom: 10px;
            margin-top: 30px;
            font-size: 1.8em;
        }
        #portafolio-cv h3 {
            color: #555;
            margin-top: 25px;
            font-size: 1.2em;
        }
        .personal-info p {
            margin: 5px 0;
        }
        .cv-list {
            list-style: disc;
            margin-left: 20px;
            padding-left: 0;
        }
        .cv-list li {
            margin-bottom: 10px;
            font-weight: bold;
        }
        .cv-list li strong {
            font-weight: normal;
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
                <li><a href="#portafolio-cv">Portafolio/CV</a></li>
                <li><a href="https://umejumac.blogspot.com/?zx=d20becec4ee219d9" target="_blank">Blog</a></li>
            </ul>
        </div>
    </nav>

    <main class="container">
        
        <section class="seccion-intro" style="text-align: center; padding: 40px 0;">
            <h2>Bienvenido a la Plataforma UMEJUMAC</h2>
            <p style="font-size: 1.1em; color: #555;">Somos tu aliado en la convergencia de la salud, la logística y la transformación digital. Descubre nuestros tres pilares:</p>
            
            <div class="button-group">
                <a href="#asesoria" class="action-button">Nuestros Servicios</a>
                <a href="#portafolio-cv" class="action-button portfolio-btn">Ver Portafolio/CV</a>
            </div>
        </section>

        <div class="seccion-principal">

            <section id="asesoria" class="card">
                <h2>1. Asesoría en Salud Colectiva</h2>
                <p>Ofrecemos consultoría especializada para optimizar la gestión de riesgos de salud. Desde el análisis epidemiológico hasta el diseño de políticas de prevención y bienestar.</p>
                <ul>
                    <li>Análisis Estratégico.</li>
                    <li>Planes de Prevención.</li>
                </ul>
                <a href="#">Más sobre Asesoría →</a>
            </section>

            <section class="card">
                <h2>2. Bienes y Servicios</h2>
                <p>Suministro eficiente y confiable de equipos, insumos y materiales esenciales. Garantizamos calidad y logística impecable para el sector público y privado.</p>
                <ul>
                    <li>Suministro de Materiales Críticos.</li>
                    <li>Logística y Distribución.</li>
                </ul>
                <a href="#bienesyservicios">Ver Catálogo y Ofertas →</a>
            </section>

            <section id="ventas" class="card">
                <h2>3. Ventas (Soluciones Tecnológicas)</h2>
                <p>Tu socio en transformación digital. Desarrollamos y vendemos soluciones web a medida, software de gestión (ERP/CRM) y plataformas de comercio electrónico.</p>
                <ul>
                    <li>Desarrollo Web Personalizado.</li>
                    <li>Software de Gestión Empresarial.</li>
                </ul>
                <a href="#">Ver Soluciones →</a>
            </section>

        </div>
        
        <section id="bienesyservicios" class="product-gallery-section">
            <div class="container">
                <h2>Catálogo de Bienes y Productos</h2>
                <p style="text-align: center; margin-bottom: 40px; font-size: 1.1em; color: #555;">Vehículos, Inmuebles, Libros y Material Médico/Quirúrgico a su disposición.</p>

                <div class="product-grid">

                    <div class="product-item">
                        <img src="ruta/a/tu/imagen1.jpg" alt="Vehículo en Venta" class="product-image">
                        <div class="product-details">
                            <h3>Vehículo Sedán Familiar - Excelente Estado</h3>
                            <p>Motor 2.0L, automático, 120.000 km. Mantenimiento al día. Ideal para viajes familiares. Negociable.</p>
                            <span class="product-price">Precio: $8,500 USD</span>
                        </div>
                    </div>

                    <div class="product-item">
                        <img src="ruta/a/tu/imagen2.jpg" alt="Kit Médico Quirúrgico" class="product-image">
                        <div class="product-details">
                            <h3>Kit Básico de Sutura y Cirugía Menor</h3>
                            <p>Material de acero inoxidable de alta calidad. Incluye pinzas, tijeras y porta-agujas. Nuevo, sellado.</p>
                            <span class="product-price">Precio: $120 USD</span>
                        </div>
                    </div>

                    <div class="product-item">
                        <img src="ruta/a/tu/imagen3.jpg" alt="Libro de Derecho Penal" class="product-image">
                        <div class="product-details">
                            <h3>Libro: Fundamentos de Derecho Penal (Última Edición)</h3>
                            <p>Texto clave para estudiantes y profesionales. Tapa dura, excelente condición. Envío a nivel nacional.</p>
                            <span class="product-price">Precio: $45 USD</span>
                        </div>
                    </div>
                    
                    </div>
            </div>
        </section>


        <section class="expert-intro">
            <h2>Liderazgo y Experiencia</h2>
            <p style="font-size: 1.1em; max-width: 800px; margin: 0 auto 20px;">
                UMEJUMAC es dirigida y asesorada por el **Dr. José Gregorio Morales**, Doctor en Gestión, Magister en Salud Pública y Abogado, con más de 30 años de experiencia en gestión de salud pública, docencia universitaria y desarrollo de políticas de bienestar. Conoce su trayectoria completa en el Portafolio.
            </p>
            <a href="#portafolio-cv" class="action-button portfolio-btn" style="background-color: #003366; color: white;">Ver Trayectoria Completa</a>
        </section>

        <section id="portafolio-cv">
            <h1>Dr. José Gregorio Morales</h1>
            <hr>

            <h2>Información de Contacto</h2>
            <div class="personal-info">
                <p><strong>Nacionalidad:</strong> Venezolano</p>
                <p><strong>Organización:</strong> Universidad de los Andes, Mérida, Venezuela.</p>
                <p><strong>Correo electrónico:</strong> <a href="mailto:jgm963@gmail.com">jgm963@gmail.com</a> | <a href="mailto:jgm963@Outlook.com">jgm963@Outlook.com</a></p>
                <p><strong>Teléfonos Celulares:</strong> +(58) 426 570 83 69 y + (58) 412 693 83 69</p>
            </div>

            <h2>Educación</h2>
            <ul class="cv-list">
                <li>**Doctor en Gestión para la Creación Intelectual** (Universidad Politécnica Territorial del Estado Mérida, 2022).</li>
                <li>**Magister Scientiae en Salud Pública** (Universidad de los Andes, 2011).</li>
                <li>**Abogado *Magna Cum Laude*** (Universidad de los Andes, 2006).</li>
                <li>**Especialista en Administración en Salud Pública** (Universidad de los Andes, 1993).</li>
                <li>**Especialista en Obstetricia y Ginecología** (Hospital Universitario de los Andes, 1987).</li>
                <li>**Médico Cirujano** (Universidad Central de Venezuela, 1983).</li>
                <li>**Diplomado en Docencia en Seguridad Ciudadana y Seguridad Penitenciaria** (Universidad Nacional Experimental de la Seguridad, 2016).</li>
            </ul>

            <h2>Resumen de Experiencia</h2>
            
            <h3>Docencia Universitaria (1993 - Presente)</h3>
            <ul class="cv-list">
                <li>**Universidad de los Andes:** Profesor Contratado en Medicina Preventiva y Social, Docencia en pregrado (Medicina, Estadística de Salud, Inspectores de Salud Pública) y postgrado. Responsabilidades en Planificación Estratégica y Marco Lógico.</li>
                <li>**Facultad de Ciencias Jurídicas y Políticas (ULA):** Profesor invitado en Derecho Penal (Medicina Legal) y Psicocriminología.</li>
                <li>**Otras Universidades:** Profesor invitado en el INSTITUTO DE ALTOS ESTUDIOS ARNALDO GABALDÓN y UNIVERSIDAD NACIONAL EXPERIMENTAL DE LA SEGURIDAD. Coordinador en la UNIVERSIDAD NACIONAL EXPERIMENTAL “RÓMULO GALLEGO” (Núcleo Mérida).</li>
                <li><strong>Logro Destacado:</strong> Aporte a la formación profesional en pregrado y postgrado, conjugando conocimientos de Medicina y Derecho.</li>
            </ul>

            <h3>Cargos Directivos y Asesoría en Salud Pública</h3>
            <ul class="cv-list">
                <li>**Asesor en materia de salud** del Despacho de Gobernación del Estado Bolivariano de Mérida (Ene - Nov 2021).</li>
                <li>**Director General** de la Corporación de Salud del Estado Bolivariano de Mérida (2019 - Oct 2020).</li>
                <li>**Director de Gestión Médica Administrativa** de la Corporación de Salud del Estado Mérida (2017 - 2018).</li>
                <li>**Director de Hospitales y Coordinador de Programas Prioritarios** (1988 - 2016), incluyendo Director del Hospital II El Vigía y Jefe del Distrito Sanitario. Coordinador Regional de Atención Materna, Planificación Familiar y Oncología.</li>
                <li><strong>Logro Destacado:</strong> Implementación y coordinación de programas prioritarios de salud (materno infantil, cardiovascular, VIH/sida) y recuperación de infraestructura a través del Proyecto Salud (Convenio BID/OPS).</li>
            </ul>

            <h2>Sociedades a las que Pertenece</h2>
            <ul class="cv-list">
                <li>Miembro Activo del Colegio Médico del Estado Mérida (Matrícula N° 1776).</li>
                <li>Miembro Activo del Instituto de Previsión Social del Médico (INPRES).</li>
                <li>Miembro Activo del Colegio de Abogados del Estado Mérida (Matrícula N° 6690).</li>
                <li>Miembro Activo de la Federación Médica Venezolana.</li>
                <li>Miembro Activo de la Sociedad Venezolana de Obstetricia y Ginecología (Integrante de la Sección de Medicina Legal).</li>
            </ul>
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
