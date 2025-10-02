<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMEJUMAC | Unidad Médico-Jurídica Morales A.C.</title>
    
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
