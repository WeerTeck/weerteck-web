<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WeerTeck | Tecnología ambiental para el futuro</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet" />
  <link rel="icon" type="image/png" href="img/logo.png">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #0f2027 0%, #2c5364 100%);
      color: #e0e0e0;
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      overflow-x: hidden;
      position: relative;
    }
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      height: 56px;
      background: rgba(11,40,50,0.98);
      box-shadow: 0 3px 16px #00bcd4cc;
      z-index: 2002;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 2.5vw;
      font-size: 1.08em;
      transition: background 0.3s;
      backdrop-filter: blur(7px);
      border-bottom: 1.5px solid #00bcd4cc;
    }
    nav .nav-logo {
      font-weight: 900;
      font-size: 1.28em;
      letter-spacing: 2px;
      background: linear-gradient(90deg,#00bcd4,#80deea,#fff0);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
      animation: navLogoHue 3s linear infinite alternate;
      display: flex;
      align-items: center;
    }
    @keyframes navLogoHue {
      0% { filter: hue-rotate(0deg);}
      100%{ filter: hue-rotate(40deg);}
    }
    nav ul { list-style: none; display: flex; gap: 2em; margin: 0; padding: 0; }
    nav ul li a {
      color: #e0e0e0; text-decoration: none; font-weight: 600;
      padding: 6px 10px; border-radius: 7px; transition: background 0.2s, color 0.2s;
      position: relative;
      z-index: 1;
    }
    nav ul li a:hover, nav ul li a:focus {
      background: linear-gradient(90deg,#80deea44,#00bcd4,#004d4044);
      color: #fff;
      box-shadow: 0 0 8px #00bcd4bb;
    }
    nav .nav-actions button {
      background: linear-gradient(90deg,#00bcd4,#80deea);
      color: #fff; border: none; border-radius: 18px;
      padding: 6px 14px; font-weight: 700; cursor: pointer; box-shadow: 0 2px 8px #00bcd4aa;
      transition: background 0.2s, box-shadow 0.2s, scale 0.2s;
      letter-spacing: 0.5px;
    }
    nav .nav-actions button:hover {
      background: linear-gradient(90deg,#80deea,#00bcd4 60%);
      box-shadow: 0 0 16px #00bcd4cc;
      scale:1.08;
    }
    @media (max-width: 700px) { nav ul { gap: 1em; } nav .nav-logo { font-size: 1em; } }
    @media (max-width: 520px) {
      nav { font-size: 0.97em; padding: 0 1vw;}
      nav ul { gap: 0.6em;}
    }
    header, main, footer { margin-top: 56px; }
    @media (max-width: 520px) { header, main, footer { margin-top: 65px;} }
    #particles-js {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      z-index: 0; pointer-events: none;
      width: 100vw; height: 100vh;
      opacity: 0.75;
    }
    a { color: #4dd0e1; text-decoration: none; transition: color 0.3s ease; }
    a:hover, a:focus { color: #81d4fa; text-decoration: underline; outline: none; }
    header, main, footer {
      position: relative; z-index: 2; max-width: 900px; width: 90%; margin: auto; padding: 1.5rem 0;
    }
    header { text-align: center; }
    h1 {
      font-weight: 800;
      font-size: 2.8rem;
      color: #00bcd4;
      margin-bottom: 0.3rem;
      text-shadow: 0 0 18px #00bcd4cc, 0 0 6px #00bcd466;
      letter-spacing: 2px;
      background: linear-gradient(90deg,#00bcd4,#80deea 80%,#fff0);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 30px #00bcd4cc);
    }
    .subtitulo {
      font-weight: 600; font-size: 1.3rem; color: #80deea;
      margin-bottom: 3rem;
      text-shadow: 0 0 6px #80deea88; letter-spacing: 1px; animation: fadeIn 2s 0.5s both;
    }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(40px);} to { opacity: 1; transform: translateY(0);} }
    h2 {
      color: #00bcd4; margin-bottom: 1rem; font-weight: 700; font-size: 1.8rem;
      text-shadow: 0 0 6px #00bcd4bb; letter-spacing: 1px;
    }
    p { font-weight: 400; font-size: 1.06rem; margin-bottom: 1.25rem; max-width: 800px; transition: color 0.3s; }
    strong { color: #4dd0e1; font-weight: 700; }
    section:hover p, section:focus-within p { color: #ffecb3; transition: color 0.7s; }
    main:after {
      content: "";
      display:block;
      width: 100%;
      height: 4px;
      background: linear-gradient(90deg, #00bcd4 20%, #80deea 70%, transparent);
      border-radius: 6px;
      margin-top: 35px;
      filter: blur(0.7px);
      animation: barraNeon 4s linear infinite alternate;
    }
    @keyframes barraNeon {
      to { filter: blur(2px) brightness(2);}
    }
    .galeria { display: flex; justify-content: space-between; gap: 1rem; flex-wrap: wrap; margin-bottom: 2rem; position: relative; }
    .galeria img {
      width: 32%; border-radius: 12px; box-shadow: 0 0 20px #00bcd4aa, 0 8px 24px #0008;
      cursor: pointer; transition: transform 0.4s cubic-bezier(.25,.8,.25,1), box-shadow 0.3s, filter 0.3s;
      border: 2px solid transparent; filter: brightness(0.95) grayscale(0.2); border-radius: 12px; will-change: transform;
      background: linear-gradient(120deg,#00bcd422,#0002);
    }
    .galeria img:hover, .galeria img:focus {
      transform: scale(1.14) rotate(-2deg);
      box-shadow: 0 0 40px #00bcd4ff, 0 0 10px #fff4;
      filter: brightness(1.1) grayscale(0);
      border-color: #00bcd4;
      outline: none;
      z-index: 3;
      transition: all 0.22s cubic-bezier(.68,.25,.85,1.4);
    }
    .modal-img { display: none; position: fixed; z-index: 1200; left: 0; top: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.9); justify-content: center; align-items: center; animation: fadeIn 0.2s; }
    .modal-img.active { display: flex; }
    .modal-img img {
      max-width: 90vw; max-height: 80vh; border-radius: 18px; box-shadow: 0 0 50px #00bcd4cc; border: 4px solid #00bcd4; animation: imgpop 0.3s;
      background:#fff;
    }
    @keyframes imgpop { from { transform: scale(0.6);} to { transform: scale(1);} }
    .modal-img .close-modal {
      position: fixed; top: 74px; right: 36px; font-size: 2.5rem; color: #80deea;
      background: transparent; border: none; cursor: pointer; z-index: 1300; transition: color 0.2s;
      outline: none;
    }
    .modal-img .close-modal:hover { color: #fff; }
    .contacto { font-size: 1rem; line-height: 1.6; margin-bottom: 0.5rem; }
    .public-comments-section h2 { color: #00bcd4;}
    #btnWhatsApp {
      position: fixed; bottom: 25px; right: 25px;
      background: linear-gradient(135deg, #25d366 60%, #128c7e 100%);
      border-radius: 50%; width: 60px; height: 60px; box-shadow: 0 4px 20px rgba(37, 211, 102, 0.7);
      display: flex; justify-content: center; align-items: center; cursor: pointer;
      transition: background 0.3s, transform 0.3s; z-index: 1050;
      animation: floatWA 2.2s infinite alternate cubic-bezier(.6,0,.4,1);
    }
    @keyframes floatWA { to { transform: translateY(-10px) scale(1.07);} }
    #btnWhatsApp:hover { background: #1ebe5b; transform: scale(1.13) rotate(-10deg);}
    #btnWhatsApp svg { width: 30px; height: 30px; fill: white; }
    #chatbot-btn {
      position: fixed; bottom: 105px; right: 30px; width: 54px; height: 54px;
      background: linear-gradient(135deg, #00bcd4 70%, #80deea 100%);
      border-radius: 50%; box-shadow: 0 4px 14px #00bcd4aa;
      display: flex; align-items: center; justify-content: center; z-index: 1050;
      cursor: pointer; transition: background 0.3s, transform 0.3s;
      border: 2px solid #fff;
      animation: floatWA 2.2s infinite alternate cubic-bezier(.6,0,.4,1);
    }
    #chatbot-btn:hover { background: #80deea; transform: scale(1.09);}
    #chatbot-btn svg { width: 32px; height: 32px; fill: #fff; }
    #chatbot-box {
      display: none; position: fixed; bottom: 8px; right: 32px; width: 340px; max-width: 96vw;
      background: rgba(0, 188, 212, 0.98); border-radius: 20px; box-shadow: 0 8px 60px #00bcd4cc, 0 2px 16px #0008;
      padding: 0.7em 0.9em 1em 0.9em; z-index: 2103; flex-direction: column; animation: fadeIn 0.2s;
      backdrop-filter: blur(6px);
      border: 1.5px solid #fff;
      min-height: 340px;
      max-height: 88vh;
    }
    #chatbot-box.active { display: flex; }
    #chatbot-header {
      display: flex; align-items: center; justify-content: space-between; margin-bottom: 0.7em;
      position: sticky; top: 0; z-index: 3;
    }
    #chatbot-header span { font-weight: 700; color: #fff; font-size: 1.12em; letter-spacing: 0.7px; }
    #chatbot-close {
      background: transparent; border: none; color: #fff; font-size: 1.6em; cursor: pointer; line-height: 1; transition: color 0.2s;
      margin-left: 1em;
      margin-top: 0.1em;
      z-index: 4;
    }
    #chatbot-close:hover { color: #263238; }
    #chatbot-messages {
      flex: 1; overflow-y: auto; max-height: 270px; margin-bottom: 0.7em; scrollbar-width: thin;
      background: linear-gradient(108deg,#fff4,#00bcd422);
      border-radius: 12px;
      padding: 0.4em 0.2em;
    }
    .chatbot-message {
      margin-bottom: 0.6em; padding: 0.5em 0.8em; border-radius: 15px; background: #fff; color: #222; font-size: 0.98em;
      max-width: 90%; align-self: flex-start; box-shadow: 0 2px 8px #00bcd466;
      animation: fadeIn 0.39s;
    }
    .chatbot-message.user { background: #00bcd4; color: #fff; align-self: flex-end; box-shadow: 0 2px 8px #004d4066; }
    #chatbot-input-box { display: flex; align-items: center; }
    #chatbot-select {
      width: 100%; padding: 0.7em 1em; border-radius: 8px; font-size: 1em;
      margin-bottom: 0.5em; background: #e0f7fa; color: #222; border: 1px solid #00bcd4aa;
    }
    #chatbot-send {
      background: #004d40; color: #fff; border: none; border-radius: 12px;
      padding: 0.6em 1.2em; cursor: pointer; font-weight: 700; font-size: 1em; transition: background 0.2s;
    }
    #chatbot-send:hover { background: #00796b; }
    .public-comments-section {
      margin-top: 3em;
      margin-bottom: 2em;
      background: linear-gradient(120deg,#00bcd4aa,#80deea44,#2226);
      border-radius: 15px;
      padding: 2em 1em;
      box-shadow: 0 2px 32px #00bcd455;
      border: 2px solid #00bcd4cc;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }
    .public-comments-section h2 {
      text-align: center;
      margin-bottom: 1.2em;
      color: #00bcd4;
    }
    #comment-form {
      display: flex;
      flex-direction: column;
      gap: 0.8em;
      margin-bottom: 1.5em;
      align-items: center;
    }
    #comment-form input, #comment-form textarea {
      width: 95%;
      max-width: 480px;
      padding: 0.6em 1em;
      border-radius: 8px;
      border: 1px solid #00bcd4aa;
      font-size: 1em;
      background: #e0f7fa;
      color: #222;
    }
    #comment-form button {
      background: linear-gradient(90deg, #00bcd4, #80deea);
      color: #fff;
      padding: 0.6em 1.5em;
      border: none;
      border-radius: 8px;
      font-weight: 700;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 8px #00bcd4aa;
      transition: background 0.2s;
    }
    #comment-form button:hover { background: #00bcd4; }
    .comments-list {
      margin-top: 0.7em;
      list-style: none;
      padding: 0;
      max-width: 650px;
      margin-left: auto;
      margin-right: auto;
    }
    .comments-list li {
      background: #fff3;
      border-radius: 8px;
      margin-bottom: 1.2em;
      padding: 1em 1.2em;
      color: #e0e0e0;
      box-shadow: 0 2px 10px #00bcd433;
      border-left: 4px solid #00bcd4;
    }
    .comments-list .comment-author {
      font-weight: bold;
      color: #00bcd4;
      margin-bottom: 0.2em;
    }
    .comments-list .comment-date {
      font-size: 0.93em;
      color: #80deea;
      float: right;
    }
    footer {
      text-align: center; font-size: 1.05rem; color: #888; padding: 1.5rem 0; border-top: 1px solid #222;
      margin-top: auto; background: linear-gradient(90deg, #24243e, #0f2027); letter-spacing: 1px; z-index: 2;
      box-shadow: 0 -3px 18px #00bcd4aa;
      border-top: 1.5px solid #00bcd4cc;
    }
    @media (max-width: 520px) {
      #chatbot-box {
        right: 0; left: 0; width: 100vw; border-radius: 0; min-height: 60vh; max-height: 94vh;
      }
      .public-comments-section { padding: 1.3em 0.2em;}
    }
    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      .galeria img { width: 48%; margin-bottom: 1rem;}
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.5rem;}
      #chatbot-box { right: 8px; width: 98vw;}
    }
    @media (max-width: 480px) {
      .galeria img { width: 100%; }
      #btnWhatsApp, #chatbot-btn { right: 12px;}
    }
  </style>
</head>
<body>
  <nav>
    <div class="nav-logo">WeerTeck</div>
    <ul>
      <li><a href="#top">Inicio</a></li>
      <li><a href="#quienes">¿Quiénes somos?</a></li>
      <li><a href="#quehacemos">¿Qué hacemos?</a></li>
      <li><a href="#estadisticas">Estadísticas</a></li>
      <li><a href="#galeria">Galería</a></li>
      <li><a href="#eventos">Eventos</a></li>
      <li><a href="#contacto">Contacto</a></li>
      <li><a href="#faq">FAQ</a></li>
    </ul>
    <div class="nav-actions">
      <button onclick="alert('¡Newsletter pronto disponible!')">Newsletter</button>
    </div>
  </nav>
  <header>
    <h1 id="top">WeerTeck</h1>
    <p class="subtitulo">Tecnología para prevenir incendios y proteger el ambiente</p>
  </header>
  <main>
    <section id="quienes">
      <h2>¿Quiénes somos?</h2>
      <p>
        Somos un grupo de jóvenes con ganas de innovar y aportar soluciones reales para prevenir incendios forestales y cuidar el medio ambiente. Este proyecto lo estamos desarrollando para presentarlo en UDESA y también buscamos que llegue a nivel nacional.
      </p>
    </section>
    <section id="quehacemos">
      <h2>¿Qué hacemos?</h2>
      <p>
        Desarrollamos <strong>torres inteligentes autosustentables</strong> que detectan incendios en etapa temprana mediante sensores de humo, gases inflamables y temperatura. Las alertas ya no serán simples notificaciones de WhatsApp, sino que ahora se enviarán a bomberos, brigadas y vecinos a través de <strong>notificaciones push en el celular</strong> y <strong>alarmas sonoras tradicionales</strong> para una respuesta rápida y efectiva.
      </p>
      <p>
        Además, las torres pueden incluir un sistema de <strong>rociado preventivo</strong> con soluciones ecológicas para contener focos de fuego y minimizar el impacto ambiental.
      </p>
    </section>
    <section class="contadores" id="estadisticas" aria-label="Estadísticas de WeerTeck">
      <div class="contador">
        <div class="numero" data-numero="3">0</div>
        <div class="descripcion">Torres prototipo</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="2">0</div>
        <div class="descripcion">Municipios interesados</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="7">0</div>
        <div class="descripcion">Alertas de prueba</div>
      </div>
    </section>
    <section id="galeria">
      <h2>Galería</h2>
      <div class="galeria" aria-label="Galería de imágenes de WeerTeck">
        <img src="img/torre1.jpg" alt="Torre inteligente en el bosque" loading="lazy" tabindex="0" />
        <img src="img/sensor.jpg" alt="Sensor de humo instalado en la torre" loading="lazy" tabindex="0" />
        <img src="img/brigada.jpg" alt="Brigada recibiendo alerta y actuando" loading="lazy" tabindex="0" />
      </div>
    </section>
    <section id="eventos">
      <h2>Próximos Eventos</h2>
      <ul id="eventos-lista">
        <li>Demo en UDESA: 15/07/2025</li>
        <li>Charla online de prevención: 30/07/2025</li>
      </ul>
    </section>
    <section id="contacto">
      <h2>Contacto</h2>
      <p class="contacto">
        Teléfono: <a href="tel:+541125216302">+54 11 2521-6302</a>
      </p>
      <p class="contacto">
        Email: <a href="mailto:weerteck@gmail.com">weerteck@gmail.com</a>
      </p>
      <p class="contacto">
        Dirección: San Isidro, Buenos Aires, Argentina
      </p>
    </section>
    <section class="faq-section" id="faq">
      <h2>Preguntas Frecuentes</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">¿Qué es una torre WeerTeck?</div>
          <div class="faq-a">Es una torre autosustentable equipada con sensores ambientales y conectividad IoT para detectar incendios forestales en etapas tempranas y enviar alertas automáticas mediante notificaciones push y alarmas sonoras.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cómo detectan los incendios?</div>
          <div class="faq-a">Utilizamos sensores de humo, temperatura y gases inflamables junto con inteligencia artificial para identificar señales de riesgo y activar alertas inmediatas.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿A quiénes llegan las alertas?</div>
          <div class="faq-a">A bomberos, brigadas, municipios, y vecinos registrados, a través de notificaciones push en el celular y alarmas sonoras tradicionales.</div>
        </li>
      </ul>
    </section>
    <div id="chatbot-btn" aria-label="Abrir chat con WeerBot" title="¿Necesitás ayuda?">
      <svg viewBox="0 0 32 32"><path d="M16 3C8.27 3 2 8.48 2 15c0 2.94 1.47 5.63 4 7.76V29a1 1 0 0 0 1.51.86l5.1-3.06c.42.05.85.08 1.39.08 7.73 0 14-5.48 14-12S23.73 3 16 3zm0 22c-.61 0-1.19-.04-1.77-.11a1 1 0 0 0-.62.13L7 27.13V24.7a1 1 0 0 0-.39-.79C4.44 21.95 3 18.63 3 15c0-5.52 5.82-10 13-10s13 4.48 13 10-5.82 10-13 10z"/></svg>
    </div>
    <div id="chatbot-box" role="dialog" aria-modal="true" aria-label="Chatbot WeerBot">
      <div id="chatbot-header">
        <span>WeerBot 🤖</span>
        <button id="chatbot-close" aria-label="Cerrar chat">&times;</button>
      </div>
      <div id="chatbot-messages">
        <div class="chatbot-message">
          ¡Hola! Soy WeerBot. Elegí una pregunta o tema de la lista para saber más:
        </div>
      </div>
      <form id="chatbot-input-box" autocomplete="off" style="flex-direction:column;gap:0.5em;">
        <select id="chatbot-select" class="chatbot-select">
          <option value="" disabled selected>Elegí una pregunta o tema...</option>
          <optgroup label="Sobre el proyecto">
            <option value="quienes">¿Quiénes son ustedes?</option>
            <option value="objetivo">¿Cuál es el objetivo del proyecto?</option>
            <option value="udesa">¿Por qué lo presentan en UDESA?</option>
            <option value="nacional">¿Por qué quieren llegar a nivel nacional?</option>
          </optgroup>
          <optgroup label="Tecnología y funcionamiento">
            <option value="tecnologia">¿Cómo funciona la torre?</option>
            <option value="sensores">¿Qué sensores usan?</option>
            <option value="alertas">¿Cómo avisa la torre si detecta un incendio?</option>
            <option value="rociado">¿El sistema puede apagar el fuego?</option>
            <option value="autosustentable">¿La torre necesita electricidad?</option>
            <option value="panel">¿Hay panel o dashboard web?</option>
            <option value="app">¿Hay una app para celulares?</option>
          </optgroup>
          <optgroup label="Instalación y uso">
            <option value="instalar">¿Dónde se puede instalar una torre?</option>
            <option value="mantenimiento">¿Qué mantenimiento requiere?</option>
            <option value="municipio">¿Pueden integrarse con municipios?</option>
            <option value="vecinos">¿Los vecinos pueden recibir alertas?</option>
            <option value="bomberos">¿Cómo se avisa a bomberos y brigadas?</option>
          </optgroup>
          <optgroup label="Costos y contacto">
            <option value="costo">¿Cuánto cuesta una torre?</option>
            <option value="cotizacion">¿Cómo pido una cotización?</option>
            <option value="contacto">¿Cómo los contacto?</option>
            <option value="instagram">¿Tienen Instagram?</option>
            <option value="whatsapp">¿Tienen WhatsApp?</option>
          </optgroup>
          <optgroup label="Educación y ambiente">
            <option value="dato">Dame un dato curioso sobre incendios</option>
            <option value="tip">Dame un tip ambiental</option>
            <option value="importancia">¿Por qué es importante prevenir incendios?</option>
          </optgroup>
          <optgroup label="Otras preguntas">
            <option value="faq">Ver preguntas frecuentes</option>
            <option value="comentario">¿Cómo puedo dejar un comentario?</option>
            <option value="evento">¿Hay eventos o presentaciones?</option>
          </optgroup>
        </select>
        <button id="chatbot-send" type="submit">Ver respuesta</button>
      </form>
    </div>
    <section class="public-comments-section" id="comentarios">
      <h2>Dejanos tu opinión o recomendación</h2>
      <form id="comment-form">
        <input type="text" id="comment-author" placeholder="Tu nombre (opcional)" maxlength="40" autocomplete="off"/>
        <textarea id="comment-text" placeholder="Escribí tu comentario, opinión o recomendación..." rows="3" required maxlength="400"></textarea>
        <button type="submit">Publicar comentario</button>
      </form>
      <ul class="comments-list" id="comments-list"></ul>
      <div style="text-align:center;margin-top:1em;color:#80deea;">
        También podés escribirnos directo por <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta%20o%20opinión" target="_blank" rel="noopener">WhatsApp</a>.
      </div>
    </section>
  </main>
  <footer>
    <p>&copy; 2025 WeerTeck - Todos los derechos reservados</p>
    <p>
      <a href="#top" style="color: #4dd0e1;">↑ Volver arriba</a>
    </p>
  </footer>
  <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20más%20info" target="_blank" rel="noopener" id="btnWhatsApp" aria-label="Contactar por WhatsApp">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M20.52 3.48A11.86 11.86 0 0 0 12 0C5.37 0 0 5.37 0 12a11.93 11.93 0 0 0 2.07 6.57L0 24l5.6-2.07A11.9 11.9 0 0 0 12 24c6.63 0 12-5.37 12-12a11.84 11.84 0 0 0-3.48-8.52zM12 21.4a9.4 9.4 0 0 1-4.78-1.41l-.34-.21-3.32 1.23 1.2-3.23-.22-.34A9.44 9.44 0 1 1 21.4 12a9.37 9.37 0 0 1-9.4 9.4zm5.32-7.21c-.29-.15-1.71-.84-1.97-.94-.26-.11-.45-.15-.64.15s-.74.94-.9 1.13c-.16.19-.32.21-.6.07a6.71 6.71 0 0 1-1.97-1.21 7.32 7.32 0 0 1-1.36-1.68c-.14-.25-.02-.38.11-.53.12-.12.26-.32.39-.48a.72.72 0 0 0 .11-.3.43.43 0 0 0-.06-.3c-.2-.45-.57-1.18-.8-1.6-.21-.4-.43-.34-.6-.34a1.36 1.36 0 0 0-.65.06c-.23.1-.89.86-.89 2.1s.91 2.43 1.03 2.6c.11.18 1.78 2.71 4.3 3.8a13.61 13.61 0 0 0 1.89.66c.8.27 1.53.23 2.11.14a6.69 6.69 0 0 0 2.03-.82 7.7 7.7 0 0 0 2.72-2.47 9.56 9.56 0 0 0-3.41-2.55z"/>
    </svg>
  </a>
  <script>
    const respuestasWeerBot = {
      quienes: "Somos un grupo de jóvenes con ganas de innovar y aportar soluciones reales para prevenir incendios forestales y cuidar el medio ambiente. Estamos desarrollando el proyecto para presentarlo en UDESA y buscar que llegue a nivel nacional.",
      objetivo: "Buscamos prevenir incendios forestales, proteger el ambiente y ayudar a las brigadas, municipios y vecinos con tecnología accesible.",
      udesa: "Presentamos el proyecto en UDESA porque creemos que allí podemos mostrar el valor de la tecnología aplicada a problemas ambientales importantes y buscar alianzas para expandirlo.",
      nacional: "Queremos que la solución llegue a todo el país porque los incendios afectan a miles de hectáreas y comunidades en muchas provincias.",
      tecnologia: "La torre funciona con sensores de humo, temperatura y gases, alimentada por panel solar. Detecta focos de incendio y activa alertas automáticas.",
      sensores: "Utilizamos sensores de humo, temperatura y gases inflamables, además de módulos de comunicación y alarma.",
      alertas: "Al detectar peligro, la torre envía notificaciones push al celular de bomberos, brigadas y vecinos, y activa alarmas sonoras tradicionales.",
      rociado: "Algunas versiones de la torre pueden activar un rociador con soluciones ecológicas para contener el fuego de inmediato.",
      autosustentable: "La torre es autosustentable con panel solar y batería. No depende de la red eléctrica.",
      panel: "Hay un panel web para monitorear todas las torres, recibir alertas, ver estadísticas y estado de sensores.",
      app: "Se está desarrollando una app móvil para que vecinos, brigadas y municipios reciban alertas y accedan a información en tiempo real.",
      instalar: "Podés instalar una torre en bosques, reservas, zonas rurales, parques industriales y áreas periurbanas.",
      mantenimiento: "El mantenimiento es mínimo: solo se recomienda una revisión anual presencial. El resto se monitorea en remoto.",
      municipio: "Sí, podemos integrarnos con sistemas municipales y de protección civil para alertas y gestión de emergencias.",
      vecinos: "Los vecinos pueden registrarse para recibir alertas y reportes sobre el estado de sus zonas.",
      bomberos: "Bomberos y brigadas reciben notificaciones push y alarmas sonoras inmediatas ante cualquier señal de incendio.",
      costo: "El costo depende de la cantidad de sensores y las opciones elegidas. Consultanos para una cotización personalizada.",
      cotizacion: "Podés pedir cotización escribiéndonos por WhatsApp, mail o dejando tus datos en la web.",
      contacto: "WhatsApp: +54 11 2521-6302 / Mail: weerteck@gmail.com / Instagram: @weerteck",
      instagram: "Nuestro Instagram es <a href='https://instagram.com/weerteck' target='_blank'>@weerteck</a>. Seguinos para novedades y tips ambientales.",
      whatsapp: "Podés escribirnos al WhatsApp: <a href='https://wa.me/541125216302' target='_blank'>+54 11 2521-6302</a>.",
      dato: "¿Sabías que en Argentina se queman más de 100.000 hectáreas de bosques por año debido a incendios? La mayoría podrían evitarse con prevención y alerta temprana.",
      tip: "Nunca hagas fuego en zonas prohibidas. Si hacés un asado, asegurate de apagar bien las brasas. Si ves humo, avisá rápido a las autoridades.",
      importancia: "Prevenir incendios es fundamental para cuidar la biodiversidad, la calidad del aire y el futuro de las comunidades.",
      faq: "Podés leer todas las preguntas frecuentes en la sección FAQ de la web. Si te queda alguna duda, escribinos.",
      comentario: "Para dejar tu comentario, completá la caja de comentarios públicos al final de la página. ¡Leemos y respondemos todas las opiniones!",
      evento: "Publicamos los eventos y presentaciones en la sección eventos. Si querés que presentemos en tu zona, escribinos."
    };
    document.addEventListener('DOMContentLoaded', () => {
      // Chatbot menú
      const chatbotBtn = document.getElementById('chatbot-btn');
      const chatbotBox = document.getElementById('chatbot-box');
      const chatbotClose = document.getElementById('chatbot-close');
      const chatbotForm = document.getElementById('chatbot-input-box');
      const chatbotSelect = document.getElementById('chatbot-select');
      const chatbotMessages = document.getElementById('chatbot-messages');
      chatbotBtn.addEventListener('click', () => {
        chatbotBox.classList.add('active');
        chatbotSelect.focus();
        setTimeout(()=>{chatbotBox.scrollIntoView({behavior:"smooth",block:"center"});},20);
      });
      chatbotClose.addEventListener('click', () => {
        chatbotBox.classList.remove('active');
      });
      chatbotForm.addEventListener('submit', function(e) {
        e.preventDefault();
        const value = chatbotSelect.value;
        if(!value || !respuestasWeerBot[value]) return;
        const userMsg = document.createElement('div');
        userMsg.className = 'chatbot-message user';
        userMsg.textContent = chatbotSelect.options[chatbotSelect.selectedIndex].text;
        chatbotMessages.appendChild(userMsg);
        const botMsg = document.createElement('div');
        botMsg.className = 'chatbot-message';
        botMsg.innerHTML = respuestasWeerBot[value];
        chatbotMessages.appendChild(botMsg);
        chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
      });
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") chatbotBox.classList.remove('active');
      });
      // Comentarios públicos
      const commentsList = document.getElementById('comments-list');
      function loadComments() {
        commentsList.innerHTML = '';
        let comments = [];
        try {
          comments = JSON.parse(localStorage.getItem('weer-comments') || '[]');
        } catch {}
        if (comments.length === 0) {
          commentsList.innerHTML = "<li style='text-align:center;color:#80deea;'>Sé el primero en dejar tu comentario.</li>";
          return;
        }
        comments.slice().reverse().forEach(c => {
          const li = document.createElement('li');
          li.innerHTML = `<span class="comment-author">${c.author ? c.author : "Anónimo"}</span> <span class="comment-date">${c.date}</span><br>${c.text}`;
          commentsList.appendChild(li);
        });
      }
      loadComments();
      document.getElementById('comment-form').addEventListener('submit', function(e) {
        e.preventDefault();
        const author = document.getElementById('comment-author').value.trim();
        const text = document.getElementById('comment-text').value.trim();
        if (!text) return;
        let comments = [];
        try {
          comments = JSON.parse(localStorage.getItem('weer-comments') || '[]');
        } catch {}
        comments.push({
          author,
          text,
          date: new Date().toLocaleString('es-AR')
        });
        localStorage.setItem('weer-comments', JSON.stringify(comments));
        document.getElementById('comment-author').value = '';
        document.getElementById('comment-text').value = '';
        loadComments();
      });
    });
  </script>
</body>
</html>
