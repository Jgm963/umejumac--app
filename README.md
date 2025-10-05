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
            --color-secundario: #0056b3; /* Azul medio */
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
            /* RUTA DEL LOGO: ASUMIDA EN LA RAÍZ */
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
            background-color: var(--color-secundario);
            padding: 10px 0;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .main-nav ul {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-wrap: wrap; /* Permite que los elementos se envuelvan en móvil */
            justify-content: center;
            gap: 20px;
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

        /* --- CONTENEDOR DE SECCIONES PRINCIPALES --- */
        .seccion-pilares {
            margin-top: 40px;
            padding: 20px 0;
        }

        /* --- ESTILOS PARA SECCIONES DESPLEGABLES (ACORDEÓN) --- */
        .acordeon-item {
            background-color: white;
            margin-bottom: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            border-left: 5px solid var(--color-principal);
            overflow: hidden;
            transition: border-left 0.3s;
        }
        .acordeon-item:hover {
            border-left: 5px solid var(--color-acento);
        }

        .acordeon-item summary {
            display: block;
            padding: 25px 30px;
            cursor: pointer;
            font-size: 1.5em;
            font-weight: bold;
            color: var(--color-principal);
            background-color: #ffffff;
            transition: background-color 0.3s;
        }

        .acordeon-item summary:hover {
            background-color: #f8f8ff; /* Fondo ligeramente diferente al pasar el ratón */
        }
        
        /* Estilo y rotación del indicador (Flecha) */
        .acordeon-item summary::marker {
            content: ''; 
            display: none;
        }
        .acordeon-item summary::after {
            content: '▶';
            float: right;
            transition: transform 0.2s;
            font-size: 0.8em;
            color: var(--color-acento);
            margin-top: 5px;
        }
        .acordeon-item[open] summary::after {
            content: '▼';
        }

        .acordeon-content {
            padding: 20px 30px 30px;
            background-color: #fcfcfc;
            border-top: 1px solid #eee;
        }
        
        .acordeon-content h3 {
            color: var(--color-secundario);
            margin-top: 20px;
            border-bottom: 2px dashed #ddd;
            padding-bottom: 5px;
        }
        .acordeon-content .gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
            justify-content: center;
        }
        .acordeon-content .gallery img {
            width: 100%;
            max-width: 280px;
            height: auto;
            border-radius: 4px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            object-fit: cover;
        }
        
        /* --- ESTILOS DE GALERÍA DE PRODUCTOS (VENTA DE BIENES) --- */
        #ventas { 
            padding: 40px 0;
            margin-top: 40px;
            background-color: white;
            border-top: 1px solid #ddd;
            text-align: center;
        }
        #ventas > h2 {
            color: var(--color-principal);
            font-size: 2.2em;
            margin-bottom: 10px;
            border-bottom: 3px solid var(--color-acento);
            display: inline-block;
            padding-bottom: 5px;
        }
        #ventas > p {
             font-size: 1.1em;
             margin-bottom: 40px;
             color: #555;
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
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            background-color: #ffffff;
            text-align: left;
            transition: transform 0.3s;
        }
        .product-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
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
            min-height: 50px;
        }
        .product-price {
            font-weight: bold;
            color: #d9534f;
            font-size: 1.3em;
            display: block;
            margin-top: 10px;
        }


        /* --- ESTILOS ESPECÍFICOS DEL CV (PORTAFOLIO) --- */
        #portafolio-cv { 
            background-color: white;
            padding: 40px;
            margin: 40px auto;
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
        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 5px;
            }
            .main-nav ul {
                gap: 10px;
            }
            .product-grid {
                grid-template-columns: 1fr;
            }
            .acordeon-item summary {
                 font-size: 1.3em;
            }
            .acordeon-content {
                padding: 15px 20px 25px;
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
            <p>Soluciones Integrales y Digitales.</p>
        </div>
    </header>

    <nav class="main-nav">
        <div class="container">
            <ul>
                <li><a href="#consultoria">Consultoría</a></li>
                <li><a href="#servicios">Servicios</a></li>
                <li><a href="#ventas">Venta de Bienes</a></li>
                <li><a href="#portafolio-cv">Portafolio/CV</a></li>
                <li><a href="https://umejumac.blogspot.com/?zx=d20becec4ee219d9" target="_blank">Blog</a></li>
            </ul>
        </div>
    </nav>

    <main class="container">

        <section style="text-align: center; padding: 40px 0;">
            <h2>Nuestros Pilares de Servicio y Negocio</h2>
            <p style="font-size: 1.1em; color: #555;">Acceda a nuestra experiencia en salud, servicios profesionales y catálogo de bienes.</p>
        </section>

        <div class="seccion-pilares">
            
            <details id="consultoria" class="acordeon-item">
                <summary>1. Consultoría en Salud Colectiva</summary>
                <div class="acordeon-content">
                    <p>Ofrecemos consultoría especializada en gestión de riesgos, epidemiología y diseño de políticas de bienestar social y corporativo. Este espacio permite documentar el material de trabajo, capacitación y resultados.</p>
                    
                    <h3>Material de Capacitación y Documentación</h3>
                    <p>Nuestros módulos de capacitación incluyen **Planificación Estratégica y Marco Lógico** aplicados al sector salud. Además, ofrecemos soporte en la **elaboración de diagnósticos situacionales de salud** y **proyectos**.</p>
                    
                    <ul>
                        <li>Análisis Estratégico de Riesgos.</li>
                        <li>Diseño de Planes de Prevención.</li>
                        <li>Documentación de Reuniones de Trabajo.</li>
                    </ul>

                    <h3>Galería de Reuniones y Resultados (Rutas Ficticias)</h3>
                    <div class="gallery">
                        <img src="ruta/a/foto_reunion1.jpg" alt="Resultados de Reunión de Trabajo" title="Capacitación Taller 2024">
                        <img src="ruta/a/capacitacion2.jpg" alt="Foto de Taller de Capacitación" title="Taller de Gestión de Riesgos">
                    </div>
                </div>
            </details>

            <details id="servicios" class="acordeon-item">
                <summary>2. Servicios Profesionales y Soluciones Tecnológicas</summary>
                <div class="acordeon-content">
                    <p>Accede a la experiencia legal, administrativa y de desarrollo de software a medida. Somos tu socio en la transformación digital y la gestión empresarial.</p>
                    
                    <h3>Servicios Ofrecidos</h3>
                    <p>Contamos con profesionales capacitados para la asesoría legal en el área de **Medicina Legal** y **Derecho Penal**, además de experiencia en **Psicocriminología**. Ofrecemos consultoría en **políticas de salud** y sus aspectos jurídicos.</p>
                    
                    <ul>
                        <li>Desarrollo Web Personalizado y E-commerce.</li>
                        <li>Asesoría Legal y Administrativa.</li>
                        <li>Implementación de Software de Gestión y Análisis de Datos.</li>
                    </ul>

                    <h3>Portafolio de Proyectos Recientes (Rutas Ficticias)</h3>
                    <div class="gallery">
                        <img src="ruta/a/proyecto_web_ejemplo.jpg" alt="Ejemplo de Proyecto Web" title="Plataforma de E-commerce B2B">
                        <img src="ruta/a/desarrollo_software.jpg" alt="Desarrollo de Software de Gestión" title="Interfaz de CRM Personalizado">
                    </div>
                </div>
            </details>

        </div>
        
        <section id="ventas">
            <h2>3. Venta de Bienes</h2>
            <p>Instrumental médico, equipos de ejercicio, textos de Derecho y más. ¡Contáctanos para más detalles!</p>

            <div class="product-grid">

                <div class="product-item">
                    <img src="img/instrumental quirurgico Varios.jpg" alt="Instrumental Quirúrgico Vario" class="product-image">
                    <div class="product-details">
                        <h3>Instrumental Quirúrgico Médico (Varios)</h3>
                        <p>Bandeja de instrumental con pinzas, tijeras, escalpelo y accesorios. Ideal para consultorios u hospitales. Acero inoxidable.</p>
                        <span class="product-price">Precio: A consultar</span>
                    </div>
                </div>
                
                <div class="product-item">
                    <img src="img/especulos.jpg" alt="Especulos Vaginales" class="product-image">
                    <div class="product-details">
                        <h3>Set de Especulos Metálicos (Varios Tamaños)</h3>
                        <p>Lote de especulos vaginales de metal en diferentes tamaños y modelos. En excelente estado para esterilización y uso.</p>
                        <span class="product-price">Precio: A consultar</span>
                    </div>
                </div>

                <div class="product-item">
                    <img src="img/forcep.jpg" alt="Fórceps Obstétrico" class="product-image">
                    <div class="product-details">
                        <h3>Fórceps Obstétrico de Acero</h3>
                        <p>Instrumento médico especializado. Fórceps obstétrico en acero de alta calidad. Mantenimiento y esterilización óptimos.</p>
                        <span class="product-price">Precio: A consultar</span>
                    </div>
                </div>

                <div class="product-item">
                    <img src="img/Gaveras.jpg" alt="Cavas Térmicas de Refrigeración" class="product-image">
                    <div class="product-details">
                        <h3>Juego de Cavas Térmicas (Grande y Pequeña)</h3>
                        <p>Dos cavas/gaveras de color rojo. Ideales para transporte de medicinas o alimentos refrigerados. Capacidad media y grande.</p>
                        <span class="product-price">Precio: $XX USD (Juego)</span>
                    </div>
                </div>
                
                <div class="product-item">
                    <img src="img/Levantar pesas.jpg" alt="Máquina de Ejercicios Multipropósito" class="product-image">
                    <div class="product-details">
                        <h3>Máquina de Ejercicios y Levantamiento de Pesas</h3>
                        <p>Equipo de gimnasio multifuncional para entrenamiento de pecho y espalda. Estructura robusta y funcional.</p>
                        <span class="product-price">Precio: $XXX USD</span>
                    </div>
                </div>
                
                <div class="product-item">
                    <img src="img/Guadana.jpg" alt="Guadaña Desmalezadora" class="product-image">
                    <div class="product-details">
                        <h3>Guadaña / Desmalezadora a Motor</h3>
                        <p>Equipo de jardinería y mantenimiento de áreas verdes. Funcionamiento a gasolina, con manillar ajustable.</p>
                        <span class="product-price">Precio: $XXX USD</span>
                    </div>
                </div>
                
                <div class="product-item">
                    <img src="img/LibrosDerecho1.jpg" alt="Colección de Libros de Derecho" class="product-image">
                    <div class="product-details">
                        <h3>Lote de Textos y Cursos de Derecho</h3>
                        <p>Colección variada de libros: Derecho Mercantil (4 tomos), Curso de Obligaciones (2 tomos), Derecho Civil I, II y IV, y Derecho Romano. Ideal para estudiantes o profesionales del Derecho.</p>
                        <span class="product-price">Precio: A consultar (Lote o Individual)</span>
                    </div>
                </div>

            </div>
        </section>
        
        <section id="portafolio-cv">
            <h1 style="text-align: center;">Portafolio / Curriculum Vitae</h1>
            <h1 style="text-align: center;">Dr. José Gregorio Morales</h1>
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
                <li>**Profesor Contratado en Medicina Preventiva y Social** en la Facultad de Medicina de la Universidad de los Andes desde 1993.</li>
                <li>**Profesor invitado** en la Facultad de Ciencias Jurídicas y Políticas (Derecho Penal y Medicina Legal) y en la Escuela de Criminalística (Psicocriminología).</li>
                <li>**Coordinador General** del núcleo de pregrado en Medicina de la UNIVERSIDAD NACIONAL EXPERIMENTAL “RÓMULO GALLEGO” en Mérida.</li>
                <li>**Apoyo Docente** en clases magistrales en políticas de salud y sus aspectos jurídicos, en postgrados de Gestión en salud pública y Epidemiologia del Instituto de Altos Estudios Arnaldo Gabaldón.</li>
                <li>**Logro Destacado:** Aporte a la formación profesional en pregrado y postgrado, conjugando conocimientos adquiridos en la medicina y el derecho.</li>
            </ul>

            <h3>Cargos Directivos y Asesoría en Salud Pública</h3>
            <ul class="cv-list">
                <li>**Asesor en materia de salud** del Despacho de Gobernación del Estado Bolivariano de Mérida (Ene - Nov 2021).</li>
                <li>**Director General** de la Corporación de Salud del Estado Bolivariano de Mérida (2019 - Oct 2020).</li>
                <li>**Director de Gestión Médica Administrativa** de la Corporación de Salud del Estado Mérida (2017 - 2018).</li>
                <li>**Coordinador Estadal de Fortalecimiento Institucional** en el PROYECTO SALUD (Convenio BID), con la obligación de ser la contraparte en el Estado para recuperar infraestructura y capacitar al equipo de salud y comunidades (Abr 1997 - Ene 1999).</li>
                <li>**Director de Hospitales y Coordinador de Programas Prioritarios** (1988 - 2016), incluyendo Director del Hospital II El Vigía y Coordinador Regional de Atención Materna, Planificación Familiar y Oncología.</li>
                <li>**Logro Destacado:** Los logros alcanzados como director y coordinador se expresan en atención en salud y mayor calidad de vida en las poblaciones objetivos.</li>
            </ul>

            <h2>Sociedades a las que Pertenece</h2>
            <ul class="cv-list">
                <li>Miembro Activo del Colegio Médico del Estado Mérida (Matrícula N° 1776).</li>
                <li>Miembro Activo de la Federación Médica Venezolana.</li>
                <li>Miembro Activo del Colegio de Abogados del Estado Mérida (Matrícula N° 6690).</li>
                <li>Miembro Activo de la Sociedad Venezolana de Obstetricia y Ginecología, designado como integrante de la Sección de Medicina Legal.</li>
                <li>Miembro Activo del Instituto de Previsión Social del Médico (INPRES).</li>
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
