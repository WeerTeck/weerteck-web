<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>weerTeck</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background-color: #000;
      color: #fff;
      transition: background 0.3s, color 0.3s;
    }

    header {
      text-align: center;
      padding: 40px 20px;
    }

    header h1 {
      font-size: 2.5em;
      color: #00eaff;
      text-shadow: 0 0 10px #00eaff;
      margin: 0;
    }

    .counter-section {
      display: flex;
      justify-content: center;
      gap: 40px;
      margin: 40px 0;
      flex-wrap: wrap;
    }

    .counter {
      text-align: center;
      font-size: 1.2em;
    }

    .counter span {
      font-size: 2em;
      display: block;
      color: #00eaff;
    }

    .section-title {
      text-align: center;
      font-size: 2em;
      margin: 60px 0 20px;
    }

    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      padding: 0 20px;
    }

    .gallery img {
      width: 300px;
      height: 200px;
      object-fit: cover;
      border-radius: 12px;
    }

    .whatsapp-float {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #25d366;
      color: white;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      text-align: center;
      font-size: 30px;
      line-height: 60px;
      box-shadow: 0 0 10px #25d366;
      z-index: 1000;
      text-decoration: none;
    }

    .toggle-dark {
      position: fixed;
      top: 20px;
      right: 20px;
      cursor: pointer;
      font-size: 1em;
      background: #333;
      color: #fff;
      padding: 8px 16px;
      border-radius: 6px;
    }

    .light-mode {
      background-color: #f4f4f4;
      color: #000;
    }

    .light-mode header h1 {
      color: #0077cc;
      text-shadow: none;
    }

    .light-mode .counter span {
      color: #0077cc;
    }
  </style>
</head>
<body>
  <button class="toggle-dark" onclick="toggleMode()">🌙 / ☀️</button>

  <header>
    <h1>weerteck-web</h1>
    <hr style="width: 60px; margin: 10px auto; border: 1px solid #fff;">
  </header>

  <section class="counter-section">
    <div class="counter">
      <span id="torres">0</span>
      Torres
    </div>
    <div class="counter">
      <span id="municipios">0</span>
      Municipios
    </div>
    <div class="counter">
      <span id="alertas">0</span>
      Alertas
    </div>
  </section>

  <section>
    <h2 class="section-title">Prototipos</h2>
    <div class="gallery">
      <!-- Acá podés subir tus imágenes de prototipos -->
      <img src="https://via.placeholder.com/300x200?text=Prototipo+1" alt="Prototipo 1" />
      <img src="https://via.placeholder.com/300x200?text=Prototipo+2" alt="Prototipo 2" />
      <img src="https://via.placeholder.com/300x200?text=Prototipo+3" alt="Prototipo 3" />
    </div>
  </section>

  <a class="whatsapp-float" href="https://wa.me/549XXXXXXXXXX" target="_blank" title="Contactanos por WhatsApp">💬</a>

  <script>
    function toggleMode() {
      document.body.classList.toggle("light-mode");
    }

    // Si más adelante querés animar los contadores, podés reemplazar los valores de abajo
    document.getElementById("torres").textContent = 0;
    document.getElementById("municipios").textContent = 0;
    document.getElementById("alertas").textContent = 0;
  </script>
</body>
</html>

