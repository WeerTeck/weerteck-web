<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WeerTeck | Tecnología ambiental contra incendios</title>
  
  <!-- Fuente moderna Poppins -->
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
    }
    nav .nav-logo {
      font-weight: 900;
      font-size: 1.28em;
      color: #00bcd4;
      letter-spacing: 2px;
      text-shadow: 0 0 8px #00bcd466;
      display: flex;
      align-items: center;
    }
    nav ul { list-style: none; display: flex; gap: 2em; margin: 0; padding: 0; }
    nav ul li { display: inline-block; }
    nav ul li a {
      color: #e0e0e0; text-decoration: none; font-weight: 600;
      padding: 6px 10px; border-radius: 7px; transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover, nav ul li a:focus { background: #00bcd4; color: #fff; }
    nav .nav-actions { display: flex; align-items: center; gap: 1em; }
    nav .nav-actions button {
      background: #00bcd4; color: #fff; border: none; border-radius: 18px;
      padding: 6px 14px; font-weight: 700; cursor: pointer; box-shadow: 0 2px 8px #00bcd4aa;
      transition: background 0.2s;
    }
    nav .nav-actions button:hover { background: #26c6da; }
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
      animation: text-glow 2.5s ease-in-out infinite alternate;
    }
    @keyframes text-glow {
      to { text-shadow: 0 0 35px #00bcd4ff, 0 0 10px #80deea88; }
    }
    .subtitulo {
      font-weight: 600; font-size: 1.2rem; color: #80deea; margin-bottom: 3rem;
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

    .galeria { display: flex; justify-content: space-between; gap: 1rem; flex-wrap: wrap; margin-bottom: 2rem; position: relative; }
    .galeria img {
      width: 32%; border-radius: 12px; box-shadow: 0 0 20px #00bcd4aa, 0 8px 24px #0008;
      cursor: pointer; transition: transform 0.4s cubic-bezier(.25,.8,.25,1), box-shadow 0.3s, filter 0.3s;
      border: 2px solid transparent; filter: brightness(0.95) grayscale(0.2); border-radius: 12px; will-change: transform;
    }
    .galeria img:hover, .galeria img:focus {
      transform: scale(1.14) rotate(-2deg); box-shadow: 0 0 40px #00bcd4ff, 0 0 10px #fff4;
      filter: brightness(1.1) grayscale(0); border-color: #00bcd4; outline: none; z-index: 3;
    }
    .modal-img { display: none; position: fixed; z-index: 1200; left: 0; top: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.9); justify-content: center; align-items: center; animation: fadeIn 0.2s; }
    .modal-img.active { display: flex; }
    .modal-img img {
      max-width: 90vw; max-height: 80vh; border-radius: 18px; box-shadow: 0 0 50px #00bcd4cc; border: 4px solid #00bcd4; animation: imgpop 0.3s;
    }
    @keyframes imgpop { from { transform: scale(0.6);} to { transform: scale(1);} }
    .modal-img .close-modal {
      position: absolute; top: 35px; right: 55px; font-size: 2.5rem; color: #80deea;
      background: transparent; border: none; cursor: pointer; z-index: 1300; transition: color 0.2s;
    }
    .modal-img .close-modal:hover { color: #fff; }

    .contacto { font-size: 1rem; line-height: 1.6; margin-bottom: 0.5rem; }
    .contacto svg { vertical-align: middle; margin-right: 0.5rem; fill: #4dd0e1; width: 20px; height: 20px; filter: drop-shadow(0 0 2px #4dd0e1); }
    .contacto a { font-weight: 600; letter-spacing: 0.5px; font-size: 1.05em; }

    footer {
      text-align: center; font-size: 0.95rem; color: #888; padding: 1.5rem 0; border-top: 1px solid #222;
      margin-top: auto; background: linear-gradient(90deg, #24243e, #0f2027); letter-spacing: 1px; z-index: 2;
    }

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

    .contadores {
      display: flex; justify-content: space-around; margin: 3rem 0; gap: 2rem; flex-wrap: wrap;
    }
    .contador {
      background: rgba(17,17,17,0.89); border: 2px solid #00bcd4; border-radius: 15px;
      padding: 1.2rem 2rem; text-align: center; flex: 1 1 170px;
      box-shadow: 0 0 18px #00bcd4aa; transition: box-shadow 0.3s, transform 0.3s; position: relative; overflow: hidden;
    }
    .contador:hover { box-shadow: 0 0 30px #00bcd4ff, 0 0 10px #fff4; transform: translateY(-7px) scale(1.04);}
    .numero {
      font-size: 2.7rem; font-weight: 900; color: #00bcd4; margin-bottom: 0.5rem;
      text-shadow: 0 0 7px #4dd0e1; letter-spacing: 1px; animation: bounce 1s infinite alternate;
    }
    .contador:hover .numero { animation: bounce2 0.7s infinite alternate;}
    @keyframes bounce { to { transform: scale(1.045);} }
    @keyframes bounce2 { to { transform: scale(1.11) rotate(-3deg);} }
    .descripcion { font-size: 1.07rem; font-weight: 600; color: #80deea; letter-spacing: 0.5px; }

    #toggleModo {
      position: fixed; top: 20px; right: 20px; background: #00bcd4; border-radius: 50%;
      width: 40px; height: 40px; cursor: pointer; box-shadow: 0 0 12px #00bcd4cc;
      display: flex; justify-content: center; align-items: center; z-index: 1101; transition: background 0.3s, transform 0.3s;
    }
    #toggleModo:hover { background: #26c6da; transform: rotate(16deg) scale(1.09);}
    #toggleModo svg { fill: #000; width: 22px; height: 22px; }

    #chatbot-btn {
      position: fixed; bottom: 105px; right: 30px; width: 54px; height: 54px;
      background: linear-gradient(135deg, #00bcd4 70%, #80deea 100%);
      border-radius: 50%; box-shadow: 0 4px 14px #00bcd4aa;
      display: flex; align-items: center; justify-content: center; z-index: 1050;
      cursor: pointer; transition: background 0.3s, transform 0.3s;
    }
    #chatbot-btn:hover { background: #80deea; transform: scale(1.09);}
    #chatbot-btn svg { width: 32px; height: 32px; fill: #fff; }

    #chatbot-box {
      display: none; position: fixed; bottom: 170px; right: 32px; width: 340px; max-width: 96vw;
      background: rgba(0, 188, 212, 0.98); border-radius: 20px; box-shadow: 0 8px 60px #00bcd4cc, 0 2px 16px #0008;
      padding: 0.7em 0.9em 1em 0.9em; z-index: 1201; flex-direction: column; animation: fadeIn 0.2s;
    }
    #chatbot-box.active { display: flex; }
    #chatbot-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 0.7em; }
    #chatbot-header span { font-weight: 700; color: #fff; font-size: 1.12em; letter-spacing: 0.7px; }
    #chatbot-close {
      background: transparent; border: none; color: #fff; font-size: 1.6em; cursor: pointer; line-height: 1; transition: color 0.2s;
    }
    #chatbot-close:hover { color: #263238; }
    #chatbot-messages {
      flex: 1; overflow-y: auto; max-height: 270px; margin-bottom: 0.7em; scrollbar-width: thin;
    }
    .chatbot-message {
      margin-bottom: 0.6em; padding: 0.5em 0.8em; border-radius: 15px; background: #fff; color: #222; font-size: 0.98em;
      max-width: 90%; align-self: flex-start; box-shadow: 0 2px 8px #00bcd466;
    }
    .chatbot-message.user { background: #00bcd4; color: #fff; align-self: flex-end; box-shadow: 0 2px 8px #004d4066; }
    #chatbot-input-box { display: flex; align-items: center; }
    #chatbot-input {
      flex: 1; border: none; border-radius: 12px; padding: 0.65em 1em; font-size: 1em; margin-right: 0.5em; outline: none;
      background: #e0f7fa; color: #222;
    }
    #chatbot-send {
      background: #004d40; color: #fff; border: none; border-radius: 12px;
      padding: 0.6em 1.2em; cursor: pointer; font-weight: 700; font-size: 1em; transition: background 0.2s;
    }
    #chatbot-send:hover { background: #00796b; }

    .sr { opacity: 0; transform: translateY(40px); transition: opacity 0.7s cubic-bezier(.4,0,.2,1), transform 0.7s cubic-bezier(.4,0,.2,1);}
    .sr.visible { opacity: 1; transform: translateY(0); }

    /* Modo claro */
    body.light { background: linear-gradient(135deg, #e0f7fa 0%, #fff 100%); color: #222; }
    body.light h1, body.light h2, body.light strong { color: #00796b; text-shadow: none; }
    body.light .subtitulo { color: #004d40; }
    body.light a { color: #00796b; }
    body.light a:hover { color: #004d40; }
    body.light header, body.light main, body.light footer { color: #222; }
    body.light footer { border-top-color: #ccc; color: #555; background: linear-gradient(90deg, #b2dfdb, #e0f2f1);}
    body.light .galeria img { box-shadow: 0 0 10px #00796baa; filter: brightness(1) grayscale(0); border-color: transparent;}
    body.light .galeria img:hover, body.light .galeria img:focus { box-shadow: 0 0 25px #00796bff; border-color: #00796b;}
    body.light .contador { background: #e0f2f1; border-color: #00796b; box-shadow: 0 0 10px #00796baa; color: #004d40;}
    body.light .contador:hover { box-shadow: 0 0 20px #00796bff;}
    body.light #btnWhatsApp { background: linear-gradient(135deg, #43e97b 60%, #38f9d7 100%); box-shadow: 0 4px 20px #38f9d799;}
    body.light #btnWhatsApp:hover { background: #1ebe5b;}
    body.light #toggleModo { background: #00796b; box-shadow: 0 0 10px #00796baa;}
    body.light #toggleModo svg { fill: #fff; }
    body.light #chatbot-btn { background: linear-gradient(135deg, #00796b 70%, #80cbc4 100%); box-shadow: 0 4px 14px #00796baa;}
    body.light #chatbot-btn:hover { background: #80cbc4; }
    body.light #chatbot-box { background: #e0f2f1; color: #222;}
    body.light .chatbot-message { background: #fff; color: #222; }
    body.light .chatbot-message.user { background: #00796b; color: #fff;}
    body.light #chatbot-input { background: #fff; color: #222;}
    body.light #chatbot-send { background: #00796b;}
    body.light #chatbot-send:hover { background: #004d40;}

    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      .galeria img { width: 48%; margin-bottom: 1rem;}
      .contadores { flex-direction: column; align-items: center;}
      .contador { width: 85%; margin-bottom: 1.6rem;}
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.5rem;}
      #chatbot-box { right: 8px; width: 98vw;}
    }
    @media (max-width: 480px) {
      .galeria img { width: 100%; }
      #toggleModo, #btnWhatsApp, #chatbot-btn { right: 12px;}
      #chatbot-box { right: 0; left: 0; width: 100vw; border-radius: 0;}
    }

    /* Preguntas frecuentes */
    .faq-section { background: rgba(0,188,212,0.10); margin: 2.5em auto 0 auto; border-radius: 15px; padding: 2em 1em; box-shadow: 0 2px 32px #00bcd455; }
    .faq-section h2 { color: #00bcd4; margin-bottom: 1.2em;}
    .faq-list { list-style: none; padding: 0; margin: 0;}
    .faq-item { margin-bottom: 1.7em;}
    .faq-q { font-weight: 700; font-size: 1.08em; color: #00bcd4; margin-bottom: 0.2em;}
    .faq-a { font-size: 1.01em; color: #fff; }
    body.light .faq-section { background: #e0f7fa; }
    body.light .faq-a { color: #222; }
    body.light .faq-q { color: #00796b;}
  </style>
</head>
<body>
  <div id="particles-js"></div>

  <nav>
    <div class="nav-logo">
      WeerTeck
    </div>
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
      <button onclick="document.getElementById('newsletterBtn').click()">Newsletter</button>
    </div>
  </nav>

  <div id="toggleModo" aria-label="Cambiar modo oscuro/claro" role="button" tabindex="0" title="Cambiar modo oscuro/claro">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M12 3a9 9 0 0 0 0 18 9 9 0 0 1 0-18z"/>
    </svg>
  </div>

  <div id="chatbot-btn" aria-label="Abrir chat con WeerBot" title="¿Necesitas ayuda?">
    <svg viewBox="0 0 32 32"><path d="M16 3C8.27 3 2 8.48 2 15c0 2.94 1.47 5.63 4 7.76V29a1 1 0 0 0 1.51.86l5.1-3.06c.42.05.85.08 1.39.08 7.73 0 14-5.48 14-12S23.73 3 16 3zm0 22c-.61 0-1.19-.04-1.77-.11a1 1 0 0 0-.62.13L7 27.13V24.7a1 1 0 0 0-.39-.79C4.44 21.95 3 18.63 3 15c0-5.52 5.82-10 13-10s13 4.48 13 10-5.82 10-13 10z"/></svg>
  </div>
  <div id="chatbot-box" role="dialog" aria-modal="true" aria-label="Chatbot WeerBot">
    <div id="chatbot-header">
      <span>WeerBot 🤖</span>
      <button id="chatbot-close" aria-label="Cerrar chat">&times;</button>
    </div>
    <div id="chatbot-messages">
      <div class="chatbot-message">¡Hola! Soy WeerBot. ¿En qué te puedo ayudar hoy?</div>
    </div>
    <form id="chatbot-input-box" autocomplete="off">
      <input type="text" id="chatbot-input" placeholder="Escribe tu pregunta..." autocomplete="off" required />
      <button id="chatbot-send" type="submit">Enviar</button>
    </form>
  </div>

  <header>
    <h1 id="top">WeerTeck</h1>
    <p class="subtitulo">Tecnología accesible para proteger nuestros bosques</p>
  </header>

  <main>
    <section class="sr" id="quienes">
      <h2>¿Quiénes somos?</h2>
      <p>
        Somos un grupo de jóvenes desarrolladores y emprendedores comprometidos con la protección del medio ambiente. Creamos soluciones tecnológicas accesibles para anticiparnos a los incendios forestales y reducir su impacto en la Patagonia argentina.
      </p>
    </section>

    <section class="sr" id="quehacemos">
      <h2>¿Qué hacemos?</h2>
      <p>
        Diseñamos <strong>torres inteligentes autosustentables</strong> equipadas con sensores de humo, gases inflamables y temperatura, capaces de detectar incendios en su fase inicial. Al identificar riesgo, envían <strong>alertas automáticas por WhatsApp</strong> a brigadas y vecinos de la zona.
      </p>
      <p>
        Estas torres también pueden contar con un sistema de <strong>rociado ecológico preventivo</strong>, que libera una solución biodegradable para contener el fuego antes de que se propague.
      </p>
    </section>

    <section class="contadores sr" id="estadisticas" aria-label="Estadísticas de WeerTeck">
      <div class="contador">
        <div class="numero" data-numero="0">0</div>
        <div class="descripcion">Torres instaladas</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="0">0</div>
        <div class="descripcion">Municipios adheridos</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="0">0</div>
        <div class="descripcion">Alertas activadas</div>
      </div>
    </section>

    <section class="sr" id="galeria">
      <h2>Galería</h2>
      <div class="galeria" aria-label="Galería de imágenes de WeerTeck">
        <img src="img/torre1.jpg" alt="Torre inteligente en el bosque" loading="lazy" tabindex="0" />
        <img src="img/sensor.jpg" alt="Sensor de humo instalado en la torre" loading="lazy" tabindex="0" />
        <img src="img/brigada.jpg" alt="Brigada recibiendo alerta y actuando" loading="lazy" tabindex="0" />
      </div>
    </section>

    <section class="sr" id="eventos">
      <h2>Próximos Eventos</h2>
      <div>
        <ul id="eventos-lista"></ul>
        <button id="addEventBtn" style="margin-top:12px; background:#00bcd4;color:#fff;font-weight:700;border:none;padding:8px 18px;border-radius:10px;box-shadow:0 4px 12px #00bcd4aa;cursor:pointer;">¡Agendar evento!</button>
      </div>
    </section>

    <section class="sr" id="contacto">
      <h2>Contacto</h2>
      <p class="contacto">
        <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M6.62 10.79a15.091 15.091 0 0 0 6.59 6.59l2.2-2.2a1 1 0 0 1 1.11-.21 11.36 11.36 0 0 0 3.58.57 1 1 0 0 1 1 1V20a1 1 0 0 1-1 1A17 17 0 0 1 3 4a1 1 0 0 1 1-1h3.5a1 1 0 0 1 1 1 11.36 11.36 0 0 0 .57 3.58 1 1 0 0 1-.21 1.11l-2.24 2.1z"/>
        </svg>
        Teléfono: <a href="tel:+5491125216302">+54 9 11 2521-6302</a>
      </p>
      <p class="contacto">
        <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M20 4H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2zm0 2l-8 5-8-5h16z"/>
        </svg>
        Email: <a href="mailto:weerteck@gmail.com">weerteck@gmail.com</a>
      </p>
      <p class="contacto">
        <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M7 10l5 5 5-5H7z"/>
        </svg>
        Dirección: San Isidro, Buenos Aires, Argentina
      </p>
      <p style="margin-top:1.2em;">
        <button id="newsletterBtn" style="background:#00bcd4;color:#fff;font-weight:700;border:none;padding:8px 18px;border-radius:10px;box-shadow:0 4px 12px #00bcd4aa;cursor:pointer;">Suscribirme al newsletter</button>
      </p>
    </section>

    <section class="faq-section sr" id="faq">
      <h2>Preguntas Frecuentes</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">¿Por qué WeerTeck es la mejor solución del universo?</div>
          <div class="faq-a">Porque está desarrollada con tecnología alienígena secreta y amor patagónico, y además, según estudios, reduce el estrés de los árboles un 42%.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Las torres funcionan en Marte?</div>
          <div class="faq-a">¡Por supuesto! Solo necesitas un modem espacial y una extensión de WhatsApp interestelar. Próximamente lanzaremos el módulo para la luna Europa.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cuánto tarda WeerTeck en detectar un incendio?</div>
          <div class="faq-a">Menos de un parpadeo. Es tan rápido que a veces detecta incendios antes de que empiecen. Si lo dudas, consultá a tu bombero amigo.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Puedo instalar una torre en mi balcón?</div>
          <div class="faq-a">Sí, y además puede espantar palomas, cargar tu celular y ser tema de conversación en todas tus reuniones.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿La solución de rociado ecológico es apta para veganos?</div>
          <div class="faq-a">¡Totalmente! Es tan ecológica que hasta las plantas la recomiendan. Está aprobada por la asociación mundial de helechos y cactus.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿WeerTeck sirve para ganar amigos?</div>
          <div class="faq-a">Definitivamente, sí. Instalar una torre WeerTeck mejora tu karma y multiplica tus seguidores en redes sociales.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cómo se alimentan las torres?</div>
          <div class="faq-a">Las torres son autosustentables, funcionan con energía solar, pero si les cantás una serenata también se activan.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Qué pasa si un dinosaurio ataca la torre?</div>
          <div class="faq-a">No te preocupes, nuestras torres tienen protocolo anti-dinosaurios. Pero si vuelve un T-Rex, consultanos por WhatsApp urgente.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿El equipo de WeerTeck tiene superpoderes?</div>
          <div class="faq-a">Somos desarrolladores, así que sí: detectamos bugs a distancia y resistimos 48hs sin dormir durante los hackatones.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Qué hago si se me ocurre otra pregunta?</div>
          <div class="faq-a">¡Preguntale al WeerBot flotante! O escribinos por WhatsApp, mail, Instagram, carta o señales de humo (pero con cuidado de no iniciar un incendio).</div>
        </li>
      </ul>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 WeerTeck - Todos los derechos reservados</p>
    <p>
      <a href="#top" style="color: #4dd0e1;">↑ Volver arriba</a>
    </p>
    <p id="footer-hora"></p>
  </footer>

  <a href="https://wa.me/5491156320963?text=Hola%20WeerTeck%2C%20quiero%20más%20info" target="_blank" rel="noopener" id="btnWhatsApp" aria-label="Contactar por WhatsApp">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M20.52 3.48A11.86 11.86 0 0 0 12 0C5.37 0 0 5.37 0 12a11.93 11.93 0 0 0 2.07 6.57L0 24l5.6-2.07A11.9 11.9 0 0 0 12 24c6.63 0 12-5.37 12-12a11.84 11.84 0 0 0-3.48-8.52zM12 21.4a9.4 9.4 0 0 1-4.78-1.41l-.34-.21-3.32 1.23 1.2-3.23-.22-.34A9.44 9.44 0 1 1 21.4 12a9.37 9.37 0 0 1-9.4 9.4zm5.32-7.21c-.29-.15-1.71-.84-1.97-.94-.26-.11-.45-.15-.64.15s-.74.94-.9 1.13c-.16.19-.32.21-.6.07a6.71 6.71 0 0 1-1.97-1.21 7.32 7.32 0 0 1-1.36-1.68c-.14-.25-.02-.38.11-.53.12-.12.26-.32.39-.48a.72.72 0 0 0 .11-.3.43.43 0 0 0-.06-.3c-.2-.45-.57-1.18-.8-1.6-.21-.4-.43-.34-.6-.34a1.36 1.36 0 0 0-.65.06c-.23.1-.89.86-.89 2.1s.91 2.43 1.03 2.6c.11.18 1.78 2.71 4.3 3.8a13.61 13.61 0 0 0 1.89.66c.8.27 1.53.23 2.11.14a6.69 6.69 0 0 0 2.03-.82 7.7 7.7 0 0 0 2.72-2.47 9.56 9.56 0 0 0-3.41-2.55z"/>
    </svg>
  </a>

  <!-- Modals y Scripts -->
  <div id="newsletter-modal" style="display:none;position:fixed;z-index:2000;top:0;left:0;width:100vw;height:100vh;background:rgba(0,0,0,0.85);justify-content:center;align-items:center;">
    <div style="background:#fff;color:#222;border-radius:18px;max-width:90vw;width:350px;padding:2em 1.4em;box-shadow:0 8px 40px #00bcd4cc;position:relative;">
      <button id="close-newsletter" style="background:transparent;border:none;font-size:2em;position:absolute;top:14px;right:22px;cursor:pointer;color:#00bcd4;">&times;</button>
      <h2 style="color:#00bcd4;font-size:1.3em;margin-bottom:0.6em;">Suscribite al Newsletter</h2>
      <form id="newsletter-form" autocomplete="off">
        <input type="email" id="newsletter-email" placeholder="Tu email" required style="width:92%;padding:0.7em 1em;border-radius:10px;border:1px solid #00bcd420;margin-bottom:0.9em;font-size:1em;" /><br>
        <button type="submit" style="background:#00bcd4;color:#fff;padding:0.6em 1.2em;border-radius:10px;font-weight:700;border:none;box-shadow:0 2px 8px #00bcd477;cursor:pointer;">¡Suscribirme!</button>
      </form>
      <div id="newsletter-msg" style="color:#00796b;font-weight:700;margin-top:0.7em;display:none;"></div>
    </div>
  </div>
  <div id="addEvent-modal" style="display:none;position:fixed;z-index:2000;top:0;left:0;width:100vw;height:100vh;background:rgba(0,0,0,0.85);justify-content:center;align-items:center;">
    <div style="background:#fff;color:#222;border-radius:18px;max-width:90vw;width:350px;padding:2em 1.4em;box-shadow:0 8px 40px #00bcd4cc;position:relative;">
      <button id="close-addEvent" style="background:transparent;border:none;font-size:2em;position:absolute;top:14px;right:22px;cursor:pointer;color:#00bcd4;">&times;</button>
      <h2 style="color:#00bcd4;font-size:1.15em;margin-bottom:0.7em;">Agendar evento</h2>
      <p>¿A cuál evento quieres agregar a tu calendario?</p>
      <div style="color:#00796b;font-weight:700;margin-top:0.7em;display:none;" id="addEvent-msg"></div>
    </div>
  </div>
  <div class="modal-img" id="modalImg" role="dialog" aria-modal="true" aria-label="Imagen ampliada de galería">
    <button class="close-modal" id="closeModalImg" aria-label="Cerrar imagen ampliada">&times;</button>
    <img src="" alt="Imagen galería ampliada" id="modalImgSrc" />
  </div>
  <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
  <script>
    particlesJS("particles-js", {
      "particles": {
        "number": { "value": 56, "density": { "enable": true, "value_area": 700 }},
        "color": { "value": "#00bcd4" },
        "shape": { "type": "circle" },
        "opacity": { "value": 0.3, "random": true },
        "size": { "value": 5, "random": true },
        "line_linked": { "enable": true, "distance": 130, "color": "#80deea", "opacity": 0.3, "width": 1.2 },
        "move": { "enable": true, "speed": 2, "direction": "none", "random": false, "straight": false, "out_mode": "out", "attract": { "enable": false } }
      },
      "interactivity": {
        "detect_on": "canvas",
        "events": {
          "onhover": { "enable": true, "mode": "grab" },
          "onclick": { "enable": true, "mode": "push" },
          "resize": true
        },
        "modes": {
          "grab": { "distance": 160, "line_linked": { "opacity": 0.5 } },
          "push": { "particles_nb": 3 }
        }
      },
      "retina_detect": true
    });

    function animarContador(element, numeroFinal, duracion = 2000) {
      let start = 0;
      const stepTime = Math.abs(Math.floor(duracion / (numeroFinal || 1)));
      const increment = 1;
      const timer = setInterval(() => {
        start += increment;
        element.textContent = start;
        if (start >= numeroFinal) {
          clearInterval(timer);
          element.textContent = numeroFinal;
        }
      }, stepTime > 0 ? stepTime : 60);
    }

    document.addEventListener('DOMContentLoaded', () => {
      const contadores = document.querySelectorAll('.contador .numero');
      let contadoresAnimados = false;
      function checkContadores() {
        if(contadoresAnimados) return;
        const rect = document.querySelector('.contadores').getBoundingClientRect();
        if(rect.top < window.innerHeight && rect.bottom > 0) {
          contadores.forEach(numElem => {
            const numeroFinal = parseInt(numElem.getAttribute('data-numero'), 10);
            animarContador(numElem, numeroFinal);
          });
          contadoresAnimados = true;
        }
      }
      window.addEventListener('scroll', checkContadores);
      checkContadores();

      const btnToggle = document.getElementById('toggleModo');
      btnToggle.addEventListener('click', () => {
        document.body.classList.toggle('light');
      });
      btnToggle.addEventListener('keydown', (e) => {
        if (e.key === 'Enter' || e.key === ' ') {
          e.preventDefault();
          document.body.classList.toggle('light');
        }
      });

      const srs = document.querySelectorAll('.sr');
      function scrollReveal() {
        srs.forEach(el => {
          const rect = el.getBoundingClientRect();
          if(rect.top < window.innerHeight - 60) {
            el.classList.add('visible');
          }
        });
      }
      window.addEventListener('scroll', scrollReveal);
      scrollReveal();

      const galeriaImgs = document.querySelectorAll('.galeria img');
      const modalImg = document.getElementById('modalImg');
      const modalImgSrc = document.getElementById('modalImgSrc');
      const closeModalImg = document.getElementById('closeModalImg');
      galeriaImgs.forEach(img => {
        img.addEventListener('click', () => {
          modalImgSrc.src = img.src;
          modalImg.classList.add('active');
        });
        img.addEventListener('keydown', e => {
          if(e.key === "Enter" || e.key === " ") {
            modalImgSrc.src = img.src;
            modalImg.classList.add('active');
          }
        });
      });
      closeModalImg.addEventListener('click', () => {
        modalImg.classList.remove('active');
      });
      modalImg.addEventListener('click', (e) => {
        if(e.target === modalImg) modalImg.classList.remove('active');
      });
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") modalImg.classList.remove('active');
      });

      const newsletterBtn = document.getElementById('newsletterBtn');
      const newsletterModal = document.getElementById('newsletter-modal');
      const closeNewsletter = document.getElementById('close-newsletter');
      newsletterBtn.addEventListener('click', () => {
        newsletterModal.style.display = 'flex';
        document.getElementById('newsletter-email').focus();
      });
      closeNewsletter.addEventListener('click', () => {
        newsletterModal.style.display = 'none';
        document.getElementById('newsletter-form').reset();
        document.getElementById('newsletter-msg').style.display = 'none';
      });
      newsletterModal.addEventListener('click', e => {
        if(e.target === newsletterModal) closeNewsletter.click();
      });
      document.getElementById('newsletter-form').addEventListener('submit', function(e) {
        e.preventDefault();
        document.getElementById('newsletter-msg').textContent = "¡Gracias por suscribirte! 🎉";
        document.getElementById('newsletter-msg').style.display = 'block';
        setTimeout(() => {
          newsletterModal.style.display = 'none';
          this.reset();
          document.getElementById('newsletter-msg').style.display = 'none';
        }, 2000);
      });

      const addEventBtn = document.getElementById('addEventBtn');
      const addEventModal = document.getElementById('addEvent-modal');
      const closeAddEvent = document.getElementById('close-addEvent');
      addEventBtn.addEventListener('click', () => {
        addEventModal.style.display = 'flex';
      });
      closeAddEvent.addEventListener('click', () => {
        addEventModal.style.display = 'none';
        document.getElementById('addEvent-msg').style.display = 'none';
      });
      addEventModal.addEventListener('click', e => {
        if(e.target === addEventModal) closeAddEvent.click();
      });

      function updateHora() {
        const now = new Date();
        document.getElementById('footer-hora').textContent = `Hora actual: ${now.toLocaleString('es-AR')}`;
      }
      updateHora();
      setInterval(updateHora, 60000);

      // Chatbot flotante super mejorado y delirante
      const chatbotBtn = document.getElementById('chatbot-btn');
      const chatbotBox = document.getElementById('chatbot-box');
      const chatbotClose = document.getElementById('chatbot-close');
      const chatbotForm = document.getElementById('chatbot-input-box');
      const chatbotInput = document.getElementById('chatbot-input');
      const chatbotMessages = document.getElementById('chatbot-messages');

      chatbotBtn.addEventListener('click', () => {
        chatbotBox.classList.add('active'); chatbotInput.focus();
      });
      chatbotClose.addEventListener('click', () => {
        chatbotBox.classList.remove('active');
      });
      chatbotForm.addEventListener('submit', function(e) {
        e.preventDefault();
        const msg = chatbotInput.value.trim();
        if(!msg) return;
        const userMsg = document.createElement('div');
        userMsg.className = 'chatbot-message user';
        userMsg.textContent = msg;
        chatbotMessages.appendChild(userMsg);
        chatbotInput.value = '';
        chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
        setTimeout(() => {
          const botMsg = document.createElement('div');
          botMsg.className = 'chatbot-message';
          botMsg.textContent = chatbotRespuesta(msg);
          chatbotMessages.appendChild(botMsg);
          chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
        }, 600);
      });

      function chatbotRespuesta(m) {
        m = m.toLowerCase();
        // Respuestas "delirantes" y completas
        if(m.includes("torre") && (m.includes("funciona") || m.includes("cómo"))) return "Nuestras torres trabajan tan rápido que detectan incendios antes de que el fuego empiece. Están alimentadas por energía solar, inteligencia artificial y, según rumores, gnomos digitales.";
        if(m.includes("precio") || m.includes("costo") || m.includes("valor")) return "El precio es inversamente proporcional a la cantidad de árboles que salvas. Consultá por WhatsApp para presupuesto personalizado y descuentos por buen karma.";
        if(m.includes("contacto") || m.includes("mail") || m.includes("correo") || m.includes("cómo los contacto")) return "Mandanos un WhatsApp, email, carta manuscrita, paloma mensajera o señales de humo (aunque preferimos evitar el humo).";
        if(m.includes("eventos") || m.includes("charla") || m.includes("demostración")) return "¡Próximamente! Los eventos WeerTeck son tan épicos que incluso los árboles piden autógrafos. Fijate en la sección de eventos, se actualiza mágicamente.";
        if(m.includes("hola") || m.includes("buenos dias") || m.includes("buenas") || m.includes("buenas tardes") || m.includes("buenas noches")) return "¡Hola! Soy WeerBot, tu asistente con alma de bosque. ¿Querés saber sobre torres, tecnología, o el sentido de la vida?";
        if(m.includes("newsletter") || m.includes("suscribir") || m.includes("noticias")) return "Suscribite en la sección de contacto. Recibirás noticias, memes forestales y spoilers de lanzamientos.";
        if(m.includes("ubicacion") || m.includes("donde estan") || m.includes("dirección")) return "Estamos en San Isidro, Buenos Aires, pero con espíritu 100% patagónico. ¡Llegamos a todo el universo conocido!";
        if(m.includes("brigada")) return "Las brigadas reciben alertas automáticas y pueden compartir memes de prevención. Si sos brigadista, tenés descuento en mate virtual.";
        if(m.includes("alerta") || m.includes("aviso")) return "Cuando la torre detecta humo, calor o dinosaurios, manda una alerta por WhatsApp instantáneamente.";
        if(m.includes("municipio") || m.includes("gobierno local")) return "Municipios: ¡no se queden afuera de la revolución verde! Soliciten propuesta exclusiva y emoji de árbol premium.";
        if(m.includes("rociado") || m.includes("ecológico") || m.includes("biodegradable")) return "La solución de rociado es tan ecológica que la usan los elfos para lavar sus hojas. No daña fauna, flora ni unicornios.";
        if(m.includes("tecnologia") || m.includes("hardware") || m.includes("software")) return "WeerTeck combina sensores, IA, placas solares y toques mágicos de código open source. Tecnología argentina, alma global.";
        if(m.includes("propuesta") || m.includes("presentacion") || m.includes("pdf")) return "¡Te mandamos PDF, video, holograma o poema épico! Pedilo por WhatsApp.";
        if(m.includes("gracias") || m.includes("muchas gracias")) return "¡De nada! Si plantás un árbol, la tierra te lo agradece también.";
        if(m.includes("instagram") || m.includes("redes")) return "Seguinos en Instagram: @weerteck. Compartimos fotos de torres, memes, y tips ecológicos.";
        if(m.includes("patagonia")) return "Nacimos para la Patagonia, pero nuestras torres se adaptan a cualquier clima, hasta lluvias de meteoritos.";
        if(m.includes("video") || m.includes("demo")) return "¿Querés demo? Pedila por WhatsApp. Tenemos videos, gifs, stickers y hasta canciones de cumbia forestal.";
        if(m.includes("sistema") && m.includes("alerta temprana")) return "Es un sistema de alerta temprana tan avanzado que predice incendios y cumpleaños de árboles.";
        if(m.includes("startup") || m.includes("emprendimiento")) return "Somos una startup argentina con ADN verde y pasión por el código. Si querés sumarte, siempre hay lugar en el equipo.";
        if(m.includes("seguridad") || m.includes("fiabilidad") || m.includes("confianza")) return "Máxima seguridad: respaldo solar, backup en la nube y aprobada por la Sociedad Internacional de Ardillas.";
        if(m.includes("quiero instalar") || m.includes("quiero comprar")) return "¡Excelente decisión! Dejá tus datos y te contactamos antes de que digas 'fuego'.";
        if(m.match(/(ayuda|soporte|problema|fallo|error|no anda|no funciona)/)) return "¿Error? No te preocupes. Respirá hondo, reiniciá el router y contanos el problema. Si sigue, invocá al equipo de soporte.";
        if(m.includes("datos") || m.includes("privacidad")) return "Tus datos están más seguros que un carpincho en reposera. Solo se usan para las alertas y jamás para venderte cursos de coaching.";
        if(m.includes("colaborar") || m.includes("trabajar") || m.includes("equipo") || m.includes("empleo") || m.includes("busco trabajo")) return "¡Siempre buscamos gente copada! Mandanos tu CV, portfolio o meme favorito.";
        if(m.includes("dinosaurio")) return "Tenemos protocolo especial anti-dinosaurios. Si ves uno, sacale foto y llamá a Spielberg.";
        if(m.includes("veganos") || m.includes("vegano") || m.includes("vegana")) return "¡La solución de rociado es tan vegana que ni siquiera lastima a los cactus!";
        if(m.includes("balcon")) return "Podés poner una mini-torre en tu balcón y convertirte en héroe del edificio. Bonus: espanta palomas y atrae buenas vibras.";
        if(m.includes("marte") || m.includes("espacio")) return "Nuestras torres funcionan en Marte, la Luna y Orión. Solo falta que Elon Musk nos invite.";
        if(m.includes("amigos")) return "Instalá una torre y tus amigos te pedirán tips de innovación. ¡WeerTeck une a la gente!";
        if(m.includes("superpoderes")) return "Sí, el equipo detecta bugs a distancia y resiste hackatones sin dormir. ¡Nivel épico!";
        if(m.includes("arboles") || m.includes("árboles")) return "Amamos los árboles. Cada torre salva cientos de ellos y le da alegría al bosque.";
        if(m.trim() === "faq" || m.includes("preguntas frecuentes") || m.includes("faq") || m.includes("chamuyo")) return "Las preguntas frecuentes están al final de la página. ¡No tienen desperdicio!";
        if(m.trim() === " ") return "¿Hola? Creo que escribiste un espacio. Probá preguntarme algo.";
        if(m.includes("cuántas torres hay")) return "Por ahora, 0 torres instaladas... pero con tu ayuda, serán miles 🤩.";
        if(m.includes("cuantos municipios")) return "Actualmente ningún municipio se ha unido, pero ¡el primero puede ser el tuyo!";
        if(m.includes("cuantas alertas")) return "Por ahora ninguna alerta, pero estamos listos para protegerte 24/7.";
        if(m.trim().length < 5) return "¡Contame más! Tu pregunta es muy cortita y quiero ayudarte bien.";
        if(m.includes("clave wifi") || m.includes("contraseña wifi")) return "La clave es: WEERTECK2025 (¡no se la digas a nadie! 😉)";
        return "¡Gracias por tu mensaje! Te responderemos a la brevedad o podés escribirnos por WhatsApp. Si tenés otra consulta, ¡probá con una pregunta diferente o mirá las FAQ!";
      }
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") chatbotBox.classList.remove('active');
      });
    });
  </script>
</body>
</html>
