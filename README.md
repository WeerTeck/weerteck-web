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
      background: linear-gradient(90deg,#00bcd4,#80deea,#fff0,#ff6f91 80%);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
      animation: navLogoHue 3s linear infinite alternate;
      display: flex;
      align-items: center;
    }
    nav .nav-logo::after {
      content: " 🌈✨";
      font-size: 1.1em;
      margin-left: 6px;
      filter: drop-shadow(0 0 5px #fff7);
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
      background: linear-gradient(90deg,#00bcd4,#ff6f91);
      color: #fff; border: none; border-radius: 18px;
      padding: 6px 14px; font-weight: 700; cursor: pointer; box-shadow: 0 2px 8px #00bcd4aa;
      transition: background 0.2s, box-shadow 0.2s, scale 0.2s;
      letter-spacing: 0.5px;
    }
    nav .nav-actions button:hover {
      background: linear-gradient(90deg,#ff6f91,#00bcd4 60%);
      box-shadow: 0 0 16px #ff6f91cc;
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
      background: linear-gradient(90deg,#00bcd4,#ff6f91 80%,#fff0);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 30px #00bcd4cc);
    }
    .subtitulo {
      font-weight: 600; font-size: 1.3rem; color: #ff6f91;
      margin-bottom: 3rem;
      text-shadow: 0 0 6px #ff90d588; letter-spacing: 1px; animation: fadeIn 2s 0.5s both;
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
      background: linear-gradient(90deg, #00bcd4 20%, #80deea 70%, #ff6f91 100%, transparent);
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
    .contacto svg { vertical-align: middle; margin-right: 0.5rem; fill: #4dd0e1; width: 20px; height: 20px; filter: drop-shadow(0 0 2px #4dd0e1); }
    .contacto a { font-weight: 600; letter-spacing: 0.5px; font-size: 1.05em; }
    .ig-section {
      background: linear-gradient(105deg, #00bcd4 40%, #263238 100%);
      color: #fff;
      border-radius: 22px;
      box-shadow: 0 0 28px #00bcd4ab, 0 8px 12px #0007;
      padding: 1.5em 1.3em;
      margin: 3em auto 0 auto;
      display: flex;
      align-items: center;
      gap: 1.4em;
      max-width: 490px;
      justify-content: center;
      flex-wrap: wrap;
      animation: igGlow 4s infinite alternate;
    }
    @keyframes igGlow {
      to { box-shadow: 0 0 45px #00bcd4ee;}
    }
    .ig-section .ig-logo {
      width: 55px; height: 55px; background: #fff; border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      box-shadow: 0 0 18px #80deea88;
    }
    .ig-section .ig-link {
      font-size: 1.26em;
      font-weight: 700;
      letter-spacing: 0.6px;
      color: #fff;
      text-shadow: 0 0 4px #222;
      transition: color 0.15s;
    }
    .ig-section .ig-link:hover { color: #ffe082;}
    .ig-section .ig-follow {
      background: #fff;
      color: #00bcd4;
      font-weight: 700;
      border: none;
      border-radius: 14px;
      padding: 7px 18px;
      margin-left: 12px;
      cursor: pointer;
      box-shadow: 0 4px 12px #00bcd477;
      transition: background 0.18s, color 0.18s;
    }
    .ig-section .ig-follow:hover { background: #00bcd4; color: #fff;}
    footer {
      text-align: center; font-size: 1.05rem; color: #888; padding: 1.5rem 0; border-top: 1px solid #222;
      margin-top: auto; background: linear-gradient(90deg, #24243e, #0f2027); letter-spacing: 1px; z-index: 2;
      box-shadow: 0 -3px 18px #ff6f91aa;
      border-top: 1.5px solid #00bcd4cc;
    }
    footer .frase-chique {
      color: #ff6f91; font-weight: bold; margin: 1em 0 0.5em 0; font-size: 1.08em; letter-spacing: 0.5px;
      display:inline-block; text-shadow: 0 0 6px #ff90d588;
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
    #btnWhatsApp:hover { background: #ff6f91; transform: scale(1.13) rotate(-10deg);}
    #btnWhatsApp svg { width: 30px; height: 30px; fill: white; }
    .contadores {
      display: flex; justify-content: space-around; margin: 3rem 0; gap: 2rem; flex-wrap: wrap;
    }
    .contador {
      background: rgba(17,17,17,0.89); border: 2px solid #00bcd4; border-radius: 15px;
      padding: 1.2rem 2rem; text-align: center; flex: 1 1 170px;
      box-shadow: 0 0 18px #00bcd4aa; transition: box-shadow 0.3s, transform 0.3s; position: relative; overflow: hidden;
      filter: drop-shadow(0 0 18px #00bcd4aa);
    }
    .contador:hover { box-shadow: 0 0 30px #ff6f91ff, 0 0 10px #fff4; transform: translateY(-7px) scale(1.04);}
    .numero {
      font-size: 2.7rem; font-weight: 900; color: #00bcd4; margin-bottom: 0.5rem;
      text-shadow: 0 0 7px #4dd0e1; letter-spacing: 1px;
      background: linear-gradient(90deg,#00bcd4,#ff6f91,#fff0);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
    }
    .contador:hover .numero { animation: bounce2 0.7s infinite alternate;}
    @keyframes bounce2 { to { transform: scale(1.11) rotate(-3deg);} }
    .descripcion { font-size: 1.07rem; font-weight: 600; color: #80deea; letter-spacing: 0.5px; }
    #toggleModo {
      position: fixed; top: 20px; right: 20px; background: #00bcd4; border-radius: 50%;
      width: 40px; height: 40px; cursor: pointer; box-shadow: 0 0 12px #00bcd4cc;
      display: flex; justify-content: center; align-items: center; z-index: 1101; transition: background 0.3s, transform 0.3s;
    }
    #toggleModo:hover { background: #ff6f91; transform: rotate(16deg) scale(1.09);}
    #toggleModo svg { fill: #000; width: 22px; height: 22px; }
    #chatbot-btn {
      position: fixed; bottom: 105px; right: 30px; width: 54px; height: 54px;
      background: linear-gradient(135deg, #00bcd4 70%, #ff6f91 100%);
      border-radius: 50%; box-shadow: 0 4px 14px #00bcd4aa;
      display: flex; align-items: center; justify-content: center; z-index: 1050;
      cursor: pointer; transition: background 0.3s, transform 0.3s;
      border: 2px solid #fff;
      animation: floatWA 2.2s infinite alternate cubic-bezier(.6,0,.4,1);
    }
    #chatbot-btn:hover { background: #ff6f91; transform: scale(1.09);}
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
    #chatbot-input {
      flex: 1; border: none; border-radius: 12px; padding: 0.65em 1em; font-size: 1em; margin-right: 0.5em; outline: none;
      background: #e0f7fa; color: #222;
    }
    #chatbot-send {
      background: #ff6f91; color: #fff; border: none; border-radius: 12px;
      padding: 0.6em 1.2em; cursor: pointer; font-weight: 700; font-size: 1em; transition: background 0.2s;
    }
    #chatbot-send:hover { background: #00796b; }
    .sr { opacity: 0; transform: translateY(40px); transition: opacity 0.7s cubic-bezier(.4,0,.2,1), transform 0.7s cubic-bezier(.4,0,.2,1);}
    .sr.visible { opacity: 1; transform: translateY(0); }
    .faq-section { background: rgba(0,188,212,0.10); margin: 2.5em auto 0 auto; border-radius: 15px; padding: 2em 1em; box-shadow: 0 2px 32px #00bcd455; border: 2px solid #00bcd4cc;}
    .faq-section h2 { color: #00bcd4; margin-bottom: 1.2em;}
    .faq-list { list-style: none; padding: 0; margin: 0;}
    .faq-item { margin-bottom: 1.7em;}
    .faq-q { font-weight: 700; font-size: 1.08em; color: #00bcd4; margin-bottom: 0.2em;}
    .faq-a { font-size: 1.01em; color: #fff; }
    body.light .faq-section { background: #e0f7fa; }
    body.light .faq-a { color: #222; }
    body.light .faq-q { color: #00796b;}
    @media (max-width: 520px) {
      #chatbot-box {
        right: 0; left: 0; width: 100vw; border-radius: 0; min-height: 60vh; max-height: 94vh;
      }
      .modal-img .close-modal { right: 12px; top: 74px;}
    }
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
    }
  </style>
</head>
<body>
  <div id="particles-js"></div>
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
      <button onclick="document.getElementById('newsletterBtn').click()">Newsletter 🌈</button>
    </div>
  </nav>
  <div id="toggleModo" aria-label="Cambiar modo oscuro/claro" role="button" tabindex="0" title="Cambiar modo oscuro/claro">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M12 3a9 9 0 0 0 0 18 9 9 0 0 1 0-18z"/>
    </svg>
  </div>
  <div id="chatbot-btn" aria-label="Abrir chat con WeerBot" title="¿Necesitás ayuda?">
    <svg viewBox="0 0 32 32"><path d="M16 3C8.27 3 2 8.48 2 15c0 2.94 1.47 5.63 4 7.76V29a1 1 0 0 0 1.51.86l5.1-3.06c.42.05.85.08 1.39.08 7.73 0 14-5.48 14-12S23.73 3 16 3zm0 22c-.61 0-1.19-.04-1.77-.11a1 1 0 0 0-.62.13L7 27.13V24.7a1 1 0 0 0-.39-.79C4.44 21.95 3 18.63 3 15c0-5.52 5.82-10 13-10s13 4.48 13 10-5.82 10-13 10z"/></svg>
  </div>
  <div id="chatbot-box" role="dialog" aria-modal="true" aria-label="Chatbot WeerBot">
    <div id="chatbot-header">
      <span>WeerBot 🤖🌱</span>
      <button id="chatbot-close" aria-label="Cerrar chat">&times;</button>
    </div>
    <div id="chatbot-messages">
      <div class="chatbot-message">¡Hola! Soy WeerBot, tu compa virtual para consultas de tecnología, ambiente, datos random, chistes verdes y más. ¿En qué te ayudo hoy? 🌈🌎</div>
    </div>
    <form id="chatbot-input-box" autocomplete="off">
      <input type="text" id="chatbot-input" placeholder="Escribí tu pregunta o pedí un chiste..." autocomplete="off" required />
      <button id="chatbot-send" type="submit">Enviar</button>
    </form>
  </div>
  <header>
    <h1 id="top">WeerTeck</h1>
    <p class="subtitulo">Tecnología joven, inclusiva y ecológica para cambiar el mundo 🌱✨</p>
  </header>
  <main>
    <section class="sr" id="quienes">
      <h2>¿Quiénes somos?</h2>
      <p>
        Somos un grupo de jóvenes de UDESA soñando con innovar y cuidar el ambiente 💚. WeerTeck nació como proyecto para Ingenia 2025 y acá estamos: sin títulos de ingenierxs pero con muchísima curiosidad, ganas de aprender y dejar una huella positiva. Si sos chique, tenés ideas locas y te interesa la tecnología para el bien común, ¡sumate a la movida!
      </p>
    </section>
    <section class="sr" id="quehacemos">
      <h2>¿Qué hacemos?</h2>
      <p>
        Estamos desarrollando <strong>torres inteligentes autosustentables</strong> para detectar incendios temprano usando sensores y tecnología abierta. Buscamos alertar a lxs vecinxs, brigadas y municipios por WhatsApp o la app que elijan, para que nadie llegue tarde a cuidar el bosque. 
      </p>
      <p>
        Si pinta, agregamos rociado ecológico y otras ideas que vayan surgiendo. Todo lo que ayude a frenar el fuego y cuidar el planeta entra en la lista 💡🔥.
      </p>
    </section>
    <section class="contadores sr" id="estadisticas" aria-label="Estadísticas de WeerTeck">
      <div class="contador">
        <div class="numero" data-numero="3">0</div>
        <div class="descripcion">Torres prototipo</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="2">0</div>
        <div class="descripcion">Municipios curiosxs</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="7">0</div>
        <div class="descripcion">Alertas de prueba</div>
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
    <section class="ig-section" id="instagram">
      <div class="ig-logo">
        <svg width="36" height="36" viewBox="0 0 448 448"><defs><radialGradient id="iggrad" cx="50%" cy="50%" r="80%"><stop offset="0%" stop-color="#fff"/><stop offset="100%" stop-color="#00bcd4"/></radialGradient></defs>
          <rect width="100%" height="100%" rx="20%" fill="url(#iggrad)"/>
          <path d="M224 126a98 98 0 1 0 0 196 98 98 0 0 0 0-196zm0 162a64 64 0 1 1 0-128 64 64 0 0 1 0 128zm112-166a22 22 0 1 1 0-44 22 22 0 0 1 0 44zm76 22c-1-27-7-51-25-70s-43-24-70-25C295 16 251 16 224 16s-71 0-93 1c-27 1-51 7-70 25S37 87 36 114C35 137 35 181 35 208s0 71 1 93c1 27 7 51 25 70s43 24 70 25c22 1 66 1 93 1s71 0 93-1c27-1 51-7 70-25s24-43 25-70c1-22 1-66 1-93s0-71-1-93zm-48 206c-7 17-19 29-36 36-25 10-85 8-113 8s-88 2-113-8c-17-7-29-19-36-36-10-25-8-85-8-113s-2-88 8-113c7-17 19-29 36-36 25-10 85-8 113-8s88-2 113 8c17 7 29 19 36 36 10 25 8 85 8 113s2 88-8 113z" fill="#222"/>
        </svg>
      </div>
      <div>
        <a class="ig-link" href="https://instagram.com/weerteck" target="_blank" rel="noopener">@weerteck</a>
        <button class="ig-follow" onclick="window.open('https://instagram.com/weerteck','_blank')">Seguir</button>
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
        Teléfono: <a href="tel:+541125216302">+54 11 2521-6302</a>
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
          <div class="faq-q">¿Qué es una torre WeerTeck?</div>
          <div class="faq-a">Es una torre autosustentable equipada con sensores ambientales, cámaras y conectividad IoT para detectar incendios forestales en etapas tempranas y enviar alertas automáticas a lxs responsables.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cómo detectan los incendios?</div>
          <div class="faq-a">Utilizamos sensores de humo, temperatura y gases inflamables junto con inteligencia artificial para identificar señales de riesgo y activar alertas inmediatas.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿A quiénes llegan las alertas?</div>
          <div class="faq-a">A brigadas de emergencia, municipios, bomberos y vecinxs registradxs, a través de WhatsApp y otros canales configurables.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿En qué zonas se pueden instalar?</div>
          <div class="faq-a">Las torres pueden instalarse en bosques, áreas rurales, reservas naturales, parques industriales y zonas periurbanas. El alcance es flexible.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Qué mantenimiento requieren?</div>
          <div class="faq-a">Mínimo. El sistema es autosustentable con panel solar y batería, y se monitorea en remoto. Sólo se recomienda una revisión anual presencial.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cuánto cuesta una torre?</div>
          <div class="faq-a">Depende de la configuración y cantidad de sensores. Contactanos por WhatsApp o email y te enviamos una cotización personalizada.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Ofrecen integración con sistemas municipales?</div>
          <div class="faq-a">Sí, contamos con integración para sistemas de monitoreo municipal, protección civil y apps de gestión de emergencias.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Qué sucede si se corta la luz?</div>
          <div class="faq-a">Las torres funcionan con energía solar y baterías, por lo que son autónomas y no dependen de la red eléctrica.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Puedo recibir reportes?</div>
          <div class="faq-a">Sí, generamos reportes periódicos sobre estado, alertas y estadísticas, adaptados para municipios u organizaciones.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cómo me sumo o pido información?</div>
          <div class="faq-a">Completá el formulario de contacto, escribinos por WhatsApp al +54 11 2521-6302 o enviá un mail a weerteck@gmail.com.</div>
        </li>
      </ul>
    </section>
  </main>
  <footer>
    <span class="frase-chique">🌈 Cuidar el planeta es el futuro más top. ¡Sumate y hacé historia con nosotrxs! 🚀</span>
    <p>&copy; 2025 WeerTeck - Todxs los derechos reservados</p>
    <p><a href="#top" style="color: #ff6f91;">↑ Volver arriba</a></p>
    <p id="footer-hora"></p>
  </footer>
  <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20más%20info" target="_blank" rel="noopener" id="btnWhatsApp" aria-label="Contactar por WhatsApp">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M20.52 3.48A11.86 11.86 0 0 0 12 0C5.37 0 0 5.37 0 12a11.93 11.93 0 0 0 2.07 6.57L0 24l5.6-2.07A11.9 11.9 0 0 0 12 24c6.63 0 12-5.37 12-12a11.84 11.84 0 0 0-3.48-8.52zM12 21.4a9.4 9.4 0 0 1-4.78-1.41l-.34-.21-3.32 1.23 1.2-3.23-.22-.34A9.44 9.44 0 1 1 21.4 12a9.37 9.37 0 0 1-9.4 9.4zm5.32-7.21c-.29-.15-1.71-.84-1.97-.94-.26-.11-.45-.15-.64.15s-.74.94-.9 1.13c-.16.19-.32.21-.6.07a6.71 6.71 0 0 1-1.97-1.21 7.32 7.32 0 0 1-1.36-1.68c-.14-.25-.02-.38.11-.53.12-.12.26-.32.39-.48a.72.72 0 0 0 .11-.3.43.43 0 0 0-.06-.3c-.2-.45-.57-1.18-.8-1.6-.21-.4-.43-.34-.6-.34a1.36 1.36 0 0 0-.65.06c-.23.1-.89.86-.89 2.1s.91 2.43 1.03 2.6c.11.18 1.78 2.71 4.3 3.8a13.61 13.61 0 0 0 1.89.66c.8.27 1.53.23 2.11.14a6.69 6.69 0 0 0 2.03-.82 7.7 7.7 0 0 0 2.72-2.47 9.56 9.56 0 0 0-3.41-2.55z"/>
    </svg>
  </a>
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

      // --- Chatbot chique e inclusivo ---
      const chatbotBtn = document.getElementById('chatbot-btn');
      const chatbotBox = document.getElementById('chatbot-box');
      const chatbotClose = document.getElementById('chatbot-close');
      const chatbotForm = document.getElementById('chatbot-input-box');
      const chatbotInput = document.getElementById('chatbot-input');
      const chatbotMessages = document.getElementById('chatbot-messages');

      chatbotBtn.addEventListener('click', () => {
        chatbotBox.classList.add('active'); chatbotInput.focus();
        setTimeout(()=>{chatbotBox.scrollIntoView({behavior:"smooth",block:"center"});},20);
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
          botMsg.innerHTML = chatbotRespuesta(msg);
          chatbotMessages.appendChild(botMsg);
          chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
        }, 600);
      });

      function chatbotRespuesta(m) {
        m = m.toLowerCase();
        const datos = [
          "¿Sabías que un solo árbol puede absorber hasta 150 kg de CO₂ por año? 🌳",
          "La Patagonia tiene más de 3 millones de hectáreas de bosque nativo. ¡A cuidar! 🏞️",
          "El reciclaje de una lata ahorra la energía suficiente para escuchar música todo un día. 🎶"
        ];
        const chistes = [
          "¿Por qué el pasto nunca pierde? Porque siempre tiene la raíz del asunto 😄",
          "¿Qué hace un volcán en el gimnasio? ¡Erup-ciones! 💪🌋",
          "¿Por qué el planeta fue al médico? Porque tenía fiebre global 🌡️🌎"
        ];
        const tips = [
          "Tip eco: Apagá la compu si no la usás, ¡el planeta lo agradece! 🌱",
          "Separá la basura y dale una segunda vida a tus residuos ♻️",
          "Andá en bici o caminá cuando puedas, tu salud y el ambiente te lo van a agradecer 🚲"
        ];

        if(m.includes("cambio climático")) return "¡El cambio climático es real y urgente! Si querés saber cómo ayudar, preguntame por tips ecológicos 🌱✨";
        if(m.includes("dato") && m.includes("curioso")) return datos[Math.floor(Math.random()*datos.length)];
        if(m.includes("chiste")) return chistes[Math.floor(Math.random()*chistes.length)];
        if(m.includes("hola") || m.includes("buenos")) return "¡Hola chique! ¿En qué te puedo ayudar hoy? Preguntame sobre tecnología, ambiente, memes verdes o lo que quieras 🌈🦾";
        if(m.includes("tecnología") || m.includes("sensor") || m.includes("torre")) return "¡Nuestra torre es 100% experimental y hecha con amor estudiantil! Usa sensores, código abierto y energía solar para ayudar a prevenir incendios.";
        if(m.includes("equipo") || m.includes("quiénes son")) return "Somos un grupo de estudiantes de UDESA, con muchas ganas de innovar y aprender. ¡Sumate si querés!";
        if(m.includes("tips") || m.includes("eco")) return tips[Math.floor(Math.random()*tips.length)];
        if(m.includes("proyecto") || m.includes("ingenia")) return "Este proyecto nació en el marco de Ingenia 2025 en UDESA. Si querés sumarte o proponer ideas, ¡mandanos un mensaje!";
        if(m.includes("sumar") || m.includes("colaborar")) return "¡Siempre hay lugar para más chiques con ganas de transformar el ambiente! Escribinos por WhatsApp, mail o Instagram.";
        if(m.includes("contacto") || m.includes("mail")) return "Podés contactarnos por WhatsApp (+54 11 2521-6302), mail (weerteck@gmail.com) o Instagram (@weerteck).";
        if(m.includes("instagram") || m.includes("redes")) return "Seguinos en Instagram: <a href='https://instagram.com/weerteck' target='_blank'>@weerteck</a>";
        if(m.includes("municipio")) return "¡Sí! Los municipios pueden sumarse, proponer ideas o pedir una demo. Escribinos y charlamos 🏛️";
        if(m.includes("rociado")) return "El sistema de rociado utiliza líquidos biodegradables y ecológicos que ayudan a contener el fuego en la etapa inicial.";
        if(m.includes("integrar") || m.includes("dashboard") || m.includes("panel")) return "Ofrecemos integración con dashboards web y sistemas de monitoreo municipales.";
        if(m.includes("energía") || m.includes("solar")) return "Las torres son autosustentables y operan con energía solar y baterías de respaldo.";
        if(m.includes("reporte") || m.includes("estadisticas")) return "Se generan reportes periódicos de alertas, estado y funcionamiento, adaptados a municipios o privados.";
        if(m.includes("faq") || m.includes("preguntas frecuentes")) return "Consultá las preguntas frecuentes en la sección FAQ al pie de página.";
        if(m.includes("random")) {
          const all = [...datos, ...chistes, ...tips];
          return all[Math.floor(Math.random()*all.length)];
        }
        if(m.trim().length < 5) return "Porfa, detallá mejor tu consulta para poder ayudarte 😊";
        return "¡Gracias por escribir! Soy WeerBot, tu compa para preguntas de ambiente, tecnología, memes verdes y más. ¿Querés que te cuente un dato random, un tip o un chiste? 🌱😄";
      }
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") chatbotBox.classList.remove('active');
      });
    });
  </script>
</body>
</html>
