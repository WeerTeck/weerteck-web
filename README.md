<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WeerTeck | Tecnología ambiental contra incendios</title>

  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet" />

  <style>
    /* RESET Y BASE */
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: 'Poppins', sans-serif;
      background-color: #000;
      color: #e0e0e0;
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    a {
      color: #4dd0e1;
      text-decoration: none;
      transition: color 0.3s ease;
    }
    a:hover, a:focus {
      color: #81d4fa;
      text-decoration: underline;
      outline: none;
    }

    header, main, footer {
      max-width: 900px;
      width: 90%;
      margin: auto;
      padding: 1.5rem 0;
    }

    header { text-align: center; }

    .logo {
      max-width: 120px;
      margin-bottom: 1rem;
      filter: drop-shadow(0 0 5px #00bcd4);
    }

    h1 {
      font-weight: 800;
      font-size: 2.8rem;
      color: #00bcd4;
      margin-bottom: 0.3rem;
      text-shadow: 0 0 8px #00bcd4aa;
    }

    .subtitulo {
      font-weight: 600;
      font-size: 1.2rem;
      color: #80deea;
      margin-bottom: 3rem;
      text-shadow: 0 0 6px #80deea88;
    }

    h2 {
      color: #00bcd4;
      margin-bottom: 1rem;
      font-weight: 700;
      font-size: 1.8rem;
      text-shadow: 0 0 6px #00bcd4bb;
    }

    p {
      font-weight: 400;
      font-size: 1rem;
      margin-bottom: 1.25rem;
      max-width: 800px;
    }

    strong {
      color: #4dd0e1;
    }

    /* GALERÍA */
    .galeria {
      display: flex;
      justify-content: space-between;
      gap: 1rem;
      flex-wrap: wrap;
      margin-bottom: 2rem;
    }

    .galeria img {
      width: 32%;
      border-radius: 8px;
      box-shadow: 0 0 10px #00bcd4aa;
      cursor: pointer;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      border: 2px solid transparent;
      filter: brightness(0.95);
      border-radius: 10px;
    }

    .galeria img:hover, .galeria img:focus {
      transform: scale(1.05);
      box-shadow: 0 0 15px #00bcd4ff;
      filter: brightness(1);
      border-color: #00bcd4;
      outline: none;
    }

    /* CONTACTO */
    .contacto svg {
      vertical-align: middle;
      margin-right: 0.5rem;
      fill: #4dd0e1;
      width: 20px;
      height: 20px;
      filter: drop-shadow(0 0 2px #4dd0e1);
    }

    /* FOOTER */
    footer {
      text-align: center;
      font-size: 0.9rem;
      color: #555;
      padding: 1.5rem 0;
      border-top: 1px solid #222;
      margin-top: auto;
    }

    /* WHATSAPP FLOTANTE */
    #btnWhatsApp {
      position: fixed;
      bottom: 25px;
      right: 25px;
      background-color: #25d366;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      box-shadow: 0 4px 10px rgba(37, 211, 102, 0.6);
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
      z-index: 1000;
    }

    #btnWhatsApp:hover {
      background-color: #1ebe5b;
      transform: scale(1.1);
    }

    #btnWhatsApp svg {
      width: 30px;
      height: 30px;
      fill: white;
    }

    /* CONTADORES */
    .contadores {
      display: flex;
      justify-content: space-around;
      margin: 3rem 0;
      gap: 2rem;
      flex-wrap: wrap;
    }

    .contador {
      background: #111;
      border: 2px solid #00bcd4;
      border-radius: 15px;
      padding: 1rem 2rem;
      text-align: center;
      flex: 1 1 150px;
      box-shadow: 0 0 10px #00bcd4aa;
      transition: box-shadow 0.3s ease;
    }

    .contador:hover {
      box-shadow: 0 0 20px #00bcd4ff;
    }

    .numero {
      font-size: 2.5rem;
      font-weight: 800;
      color: #00bcd4;
      margin-bottom: 0.5rem;
    }

    .descripcion {
      font-size: 1rem;
      font-weight: 600;
      color: #80deea;
    }

    /* MODO CLARO */
    body.light {
      background-color: #f5f5f5;
      color: #222;
    }

    body.light h1,
    body.light h2,
    body.light strong {
      color: #00796b;
      text-shadow: none;
    }

    body.light .subtitulo {
      color: #004d40;
    }

    body.light a {
      color: #00796b;
    }

    body.light a:hover {
      color: #004d40;
    }

    body.light footer {
      border-top-color: #ccc;
      color: #555;
    }

    body.light .galeria img {
      box-shadow: 0 0 10px #00796baa;
      filter: brightness(1);
    }

    body.light .galeria img:hover {
      box-shadow: 0 0 15px #00796bff;
      border-color: #00796b;
    }

    body.light .contador {
      background: #e0f2f1;
      border-color: #00796b;
      box-shadow: 0 0 10px #00796baa;
      color: #004d40;
    }

    body.light .contador:hover {
      box-shadow: 0 0 20px #00796bff;
    }

    /* TOGGLE MODO CLARO/OSCURO */
    #toggleModo {
      position: fixed;
      top: 20px;
      right: 20px;
      background: #00bcd4;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      cursor: pointer;
      box-shadow: 0 0 10px #00bcd4aa;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1001;
      transition: background-color 0.3s ease;
    }

    #toggleModo:hover {
      background: #26c6da;
    }

    #toggleModo svg {
      fill: #000;
      width: 22px;
      height: 22px;
    }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      .galeria img {
        width: 48%;
        margin-bottom: 1rem;
      }
      .contadores {
        flex-direction: column;
        align-items: center;
      }
      .contador {
        width: 80%;
        margin-bottom: 1.5rem;
      }
      h1 {
        font-size: 2.2rem;
      }
      h2 {
        font-size: 1.5rem;
      }
    }

    @media (max-width: 480px) {
      .galeria img {
        width: 100%;
      }
    }
  </style>
</head>

<body>
  <div id="toggleModo" aria-label="Cambiar modo oscuro/claro" role="button" tabindex="0" title="Cambiar modo oscuro/claro">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M12 3a9 9 0 0 0 0 18 9 9 0 0 1 0-18z"/>
    </svg>
  </div>

  <header>
    <img src="img/logo.png" alt="Logo WeerTeck" class="logo" />
    <h1>WeerTeck</h1>
    <p class="subtitulo">Tecnología accesible para proteger nuestros bosques</p>
  </header>

  <!-- SECCIÓN GALERÍA (Agregá las imágenes reales más adelante) -->
  <main>
    <section class="galeria">
      <img src="img/foto1.jpg" alt="Sensor WeerTeck en acción">
      <img src="img/foto2.jpg" alt="Equipo técnico en el bosque">
      <img src="img/foto3.jpg" alt="Instalación del sistema">
    </section>
  </main>

  <!-- FOOTER -->
  <footer>
    &copy; 2025 WeerTeck. Todos los derechos reservados.
  </footer>

  <!-- BOTÓN WHATSAPP -->
  <div id="btnWhatsApp" title="Contactar por WhatsApp">
    <svg viewBox="0 0 24 24">
      <path d="M20.5 3.5A11.74 11.74 0 0012 0 12 12 0 000 12a11.85 11.85 0 001.7 6L0 24l6.5-1.7A12 12 0 1020.5 3.5z"/>
    </svg>
  </div>

  <script>
    document.getElementById('toggleModo').addEventListener('click', () => {
      document.body.classList.toggle('light');
    });
  </script>
</body>
</html>

