/* --- VARIABLES DE COLOR (Optimización) --- */
:root {
    --color-primary: #003366; /* Azul Oscuro */
    --color-accent: #ffcc00;  /* Amarillo/Naranja */
    --color-light: #f7f9fc;   /* Gris Claro para tarjetas */
}

/* ====================================
    ESTILOS GENERALES Y DE NAVEGACIÓN
    ==================================== */

.fade-in { animation: fadeIn 0.5s ease-in-out; }
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

/* CORRECCIÓN: Si usas .view para ocultar contenido dinámicamente,
   este estilo es correcto, pero ten en cuenta que ocultará el elemento
   a menos que JavaScript lo cambie a display: block. */
.view { display: none; } 
 
.placeholder-img {
    background-color: var(--color-primary);
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.25rem;
    font-weight: 700;
}

.cover-placeholder {
    height: 180px; 
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    text-align: center;
}
 
.cover-placeholder span {
    font-size: 1.25rem;
    line-height: 1.4;
    display: block;
    max-height: 100%;
    overflow: hidden;
    word-break: break-word;
}
 
.cover-image {
    height: 180px;
    width: 100%;
    object-fit: cover; 
}

.header-nav {
    background-color: var(--color-primary); 
    color: white;
    position: sticky;
    top: 0;
    z-index: 20;
    box-shadow: 0 2px 4px 0 rgba(0,0,0,0.1);
}
 
.logo-click-area {
    display: flex;
    flex-direction: column;
    align-items: center;
    cursor: pointer;
    transition: all 0.2s;
    padding: 0.25rem; 
    border-radius: 0.5rem;
}
.logo-click-area:hover {
    background-color: rgba(255, 255, 255, 0.1); 
}

#logo-image {
    background-color: var(--color-accent); 
    border: 2px solid var(--color-accent); 
    border-radius: 0.5rem; 
    padding: 4px; 
    transition: all 0.2s ease-in-out;
    box-shadow: 0 0 8px rgba(255, 204, 0, 0.7); 
}
.logo-click-area:hover #logo-image {
    transform: scale(1.05); 
    box-shadow: 0 0 12px rgba(255, 204, 0, 1);
}
 
.book-card {
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.05);
    transition: transform 0.2s, box-shadow 0.2s;
    overflow: hidden; 
}
.book-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
}

.main-section-card {
    background-color: var(--color-light);
    border-left: 5px solid var(--color-primary); 
    transition: all 0.3s;
    cursor: pointer; 
}
.main-section-card:hover {
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    transform: translateY(-5px);
    border-left: 5px solid var(--color-accent); 
}
 
/* ====================================
    ESTILOS DEL LOGO PERSONALIZADO (Modal)
    ==================================== */
.custom-logo-container {
    width: 100%;
    max-width: 250px;
    margin: 0 auto;
    background-color: white; 
    border: 2px solid var(--color-primary); 
    /* Asegura que el contenido interno se centre */
    text-align: center; 
}
.logo-m {
    font-size: 7rem;
    line-height: 1;
    font-weight: 900;
    color: #000000; 
    text-shadow: none; 
}
.logo-acronym {
    font-size: 1rem;
    font-weight: 500;
    color: #444;
    margin-top: -5px; 
}
.acronym-highlight {
    font-weight: 900;
    color: var(--color-primary); 
    font-size: 1.1rem;
    padding: 0 2px;
}
.autonomy-concept {
    font-size: 1.2rem; 
    font-weight: 900;
    color: #000000; 
    margin-top: 10px; 
    border-top: 2px solid var(--color-primary); 
    padding-top: 8px;
    width: 90%; 
    /* Centrado si se usa width: 90% */
    margin-left: auto;
    margin-right: auto;
}
.etae-concept {
    font-size: 0.8rem;
    font-weight: 700;
    color: #dc2626; 
    margin-top: 5px; 
    padding-bottom: 5px;
    width: 90%;
    border-bottom: 1px solid #e5e7eb; 
    /* Centrado si se usa width: 90% */
    margin-left: auto;
    margin-right: auto;
}
