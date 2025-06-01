<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WeerTeck | Concientización contra incendios en Patagonia</title>
  <meta name="description" content="Concientización y acción contra incendios forestales en Patagonia. Tecnología, comunidad y prevención. Sumate a la campaña.">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet" />
  <link rel="icon" type="image/png" href="img/logo.png">
  <style>
    :root {
      --primary: #00bcd4;
      --accent: #80deea;
      --secondary: #263238;
      --dark: #121a23;
      --text: #e0e0e0;
      --light: #fff;
      --danger: #e57373;
      --muted: #b0bec5;
    }
    * { box-sizing: border-box; margin: 0; padding: 0;}
    html { scroll-behavior: smooth;}
    body {
      font-family: 'Poppins', sans-serif;
      background: #121a23;
      color: var(--text);
      min-height: 100vh;
      line-height: 1.6;
      position: relative;
      overflow-x: hidden;
      display: flex; flex-direction: column;
    }
    .bg-animated {
      position: fixed;
      top: 0; left: 0; width: 100vw; height: 100vh;
      z-index: 0;
      pointer-events: none;
      overflow: hidden;
    }
    .bg-animated-canvas {
      position: absolute;
      top: 0; left: 0; width: 100vw; height: 100vh;
      display: block;
      z-index: 0;
    }
    /* Contenedor flotante de los 3 botones */
    .floating-btns {
      position: fixed;
      bottom: 32px;
      right: 28px;
      z-index: 1050;
      display: flex;
      flex-direction: column;
      gap: 15px;
      align-items: flex-end;
    }
    .btn-instagram-flotante,
    .btn-whatsapp-flotante,
    .btn-weerbot-flotante {
      width: 62px; height: 62px; border-radius: 50%;
      border: 2.5px solid #fff;
      display: flex; justify-content: center; align-items: center;
      cursor: pointer;
      transition: background 0.2s, transform 0.3s;
      box-shadow: 0 4px 24px #00bcd455;
      background: linear-gradient(135deg, var(--primary) 60%, var(--accent) 100%);
    }
    .btn-instagram-flotante:hover { background: #00bcd4; transform: scale(1.11) rotate(-8deg);}
    .btn-whatsapp-flotante:hover { background: #00bcd4; transform: scale(1.11) rotate(8deg);}
    .btn-weerbot-flotante:hover { background: #00bcd4; transform: scale(1.11);}
    .btn-instagram-flotante svg,
    .btn-whatsapp-flotante svg,
    .btn-weerbot-flotante svg { width: 37px; height: 37px; fill: #fff;}
    @media (max-width:700px) {
      .floating-btns { right: 10px; bottom: 12px;}
      .btn-instagram-flotante, .btn-whatsapp-flotante, .btn-weerbot-flotante { width:52px; height:52px;}
      .btn-instagram-flotante svg, .btn-whatsapp-flotante svg, .btn-weerbot-flotante svg { width:30px; height:30px;}
    }
    /* WeerBot ventana flotante */
    #weerbot-window {
      display:none;
      position:fixed;
      bottom: 235px;
      right: 24px;
      width: 330px; max-width:90vw;
      z-index: 12000;
      background: #141e25ee;
      border-radius: 18px;
      border: 2px solid var(--primary);
      box-shadow: 0 8px 36px #00bcd488;
      padding: 0.7em 0 0 0;
      font-family:Poppins,sans-serif;
      color: #e0e0e0;
    }
    #weerbot-window .weerbot-header {
      display:flex;
      align-items:center;
      justify-content:space-between;
      padding:0.7em 1.1em 0.1em 1.1em;
    }
    #weerbot-window .weerbot-header span {
      font-weight:700;
      color:var(--primary);
      font-size:1.15em;
    }
    #weerbot-close {
      background:none;
      border:none;
      color:var(--primary);
      font-size:1.4em;
      cursor:pointer;
      font-weight:800;
      padding:0 6px;
      line-height:1;
    }
    #weerbot-messages {
      min-height: 140px; max-height: 275px; overflow-y: auto; padding: 0.5em 1.1em 0.5em 1.1em;
      font-size: 1em; color: #e0e0e0;
    }
    #weerbot-form {
      display:flex;align-items:center;padding:0.3em 1.1em 0.9em 1.1em;
    }
    #weerbot-input {
      flex:1;padding:0.6em 1em;border-radius:9px;
      border:1px solid var(--primary);font-size:1em;margin-right:0.6em;
      background:#e0f7fa;color:#222;
    }
    #weerbot-form button {
      background:linear-gradient(90deg,var(--primary),var(--accent));
      color:#fff;font-weight:700;
      border:none;border-radius:8px;padding:0.6em 1.1em;cursor:pointer;font-size:1em;box-shadow:0 2px 8px var(--primary);
    }
    @media (max-width:550px) {
      #weerbot-window { width:98vw !important; right:1vw; }
    }
    /* Resto de tu CSS (nav, header, main, footer, etc.) */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      height: 58px;
      z-index: 2002;
      background: rgba(18, 26, 35, 0.95);
      border-bottom: 2px solid var(--primary);
      box-shadow: 0 3px 18px var(--primary);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw;
      font-size: 1.1em;
      backdrop-filter: blur(5px);
    }
    nav .nav-logo {
      font-weight: 900;
      font-size: 1.38em;
      letter-spacing: 2px;
      background: linear-gradient(90deg, var(--primary), var(--accent) 70%, transparent);
      background-clip: text; -webkit-background-clip: text;
      color: transparent; -webkit-text-fill-color: transparent;
      animation: logoHue 4s linear infinite alternate;
      display: flex; align-items: center;
    }
    @keyframes logoHue {
      0% { filter: hue-rotate(0deg);}
      100%{ filter: hue-rotate(40deg);}
    }
    nav ul { list-style: none; display: flex; gap: 1.7em;}
    nav ul li a {
      color: var(--text);
      text-decoration: none;
      font-weight: 600;
      padding: 6px 13px;
      border-radius: 8px;
      transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover, nav ul li a:focus {
      background: linear-gradient(90deg,var(--accent) 30%,var(--primary));
      color: #fff;
      box-shadow: 0 0 8px var(--primary);
    }
    nav .nav-actions {
      display: flex; gap: 1em;
    }
    nav .nav-actions .btn-ig {
      background: linear-gradient(90deg,#00bcd4,#80deea 80%);
      color: #262626; border: none; border-radius: 22px;
      padding: 7px 16px; font-weight: 700; font-size: 1em;
      cursor: pointer; box-shadow: 0 2px 8px #00bcd455;
      display: flex; align-items: center; gap: 7px;
      transition: background 0.2s, scale 0.2s;
    }
    nav .nav-actions .btn-ig:hover {
      background: linear-gradient(90deg,#80deea,#00bcd4 90%);
      scale:1.08;
    }
    @media (max-width: 780px) {
      nav ul { gap: 0.7em; font-size: 0.92em;}
      nav .nav-logo { font-size: 1em; }
    }
    @media (max-width: 500px){
      nav { font-size: 0.91em; padding: 0 1vw;}
      nav ul { gap: 0.4em;}
    }
    header { margin-top: 58px; text-align: center; padding: 2.2em 0 1.2em 0;}
    .hero {
      background: linear-gradient(100deg, #222a36 80%, #004d4044 100%);
      border-radius: 16px;
      box-shadow: 0 2px 28px #00bcd444;
      margin: 1.6em auto 1.3em auto;
      max-width: 750px;
      padding: 2.3em 1.5em 2em 1.5em;
      position: relative;
      z-index: 2;
      border: 2px solid var(--primary);
    }
    .hero h1 {
      font-weight: 900;
      font-size: 2.6rem;
      color: var(--primary);
      text-shadow: 0 0 18px var(--primary), 0 0 6px #00bcd466;
      letter-spacing: 2px;
      background: linear-gradient(90deg,var(--primary), var(--accent) 80%,#fff0);
      background-clip: text; -webkit-background-clip: text;
      color: transparent; -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 30px var(--primary));
      margin-bottom: 0.4rem;
    }
    .hero .subtitulo {
      font-weight: 600;
      font-size: 1.25rem;
      color: var(--accent);
      margin-bottom: 1.5em;
      text-shadow: 0 0 6px var(--accent);
      letter-spacing: 1px;
    }
    .hero .cta {
      display: inline-block;
      margin-top: 1em;
      font-weight: 700;
      padding: 0.8em 2em;
      background: linear-gradient(90deg,var(--primary),var(--accent));
      color: #fff;
      border: none;
      border-radius: 20px;
      font-size: 1.04em;
      box-shadow: 0 2px 12px var(--primary);
      transition: background 0.2s, scale 0.2s;
      cursor: pointer;
      letter-spacing: 1px;
    }
    .hero .cta:hover { background: linear-gradient(90deg,var(--accent),var(--primary) 70%); scale:1.06;}
    .banner-revision {
      background: linear-gradient(90deg,var(--primary) 20%,var(--accent) 80%,#fff0);
      color: #01343a;
      font-weight: bold;
      text-align: center;
      padding: 0.7em 0.2em;
      margin: 0.5em 0 1.3em 0;
      border-radius: 7px;
      font-size: 1em;
      box-shadow: 0 2px 18px var(--primary);
      letter-spacing: 1px;
    }
    main { max-width: 820px; width: 97%; margin: auto; padding-bottom: 2em;}
    section { margin-bottom: 2em;}
    h2 {
      color: var(--primary);
      font-size: 1.5em;
      margin-bottom: 0.7em;
      font-weight: 700;
      letter-spacing: 1px;
      text-shadow: 0 0 6px var(--primary);
    }
    h3 {
      color: var(--accent); margin-bottom: 0.3em; font-size: 1.08em;
    }
    p { font-size: 1.06rem; margin-bottom: 1.1em;}
    /* ... resto de tu CSS ... */
    /* Footer y links */
    footer {
      text-align: center;
      font-size: 1.09rem;
      color: var(--muted);
      padding: 1.5rem 0 0.7rem 0;
      border-top: 2px solid var(--primary);
      background: linear-gradient(90deg, #24243e, #0f2027);
      letter-spacing: 1px;
      margin-top: auto;
      box-shadow: 0 -3px 18px var(--primary);
    }
    .footer-links { margin: 0.5em auto 1em auto;}
    .footer-links a { color: var(--primary); margin: 0 1.5em; text-decoration: none; font-weight: 600;}
    .footer-links a:hover { text-decoration: underline; color: var(--accent);}
  </style>
</head>
<body>
  <div class="bg-animated">
    <canvas class="bg-animated-canvas" id="bg-animated-canvas"></canvas>
  </div>
  <nav>
    <div class="nav-logo">WeerTeck</div>
    <ul>
      <li><a href="#top">Inicio</a></li>
      <li><a href="#quienes">Quiénes somos</a></li>
      <li><a href="#patagonia">¿Por qué Patagonia?</a></li>
      <li><a href="#quehacemos">¿Qué hacemos?</a></li>
      <li><a href="#aliados">Aliados</a></li>
      <li><a href="#novedades">Novedades</a></li>
      <li><a href="#sumate">Sumate</a></li>
      <li><a href="#comentarios">Opiniones</a></li>
    </ul>
    <div class="nav-actions">
      <button class="btn-ig" onclick="window.open('https://instagram.com/weerteck','_blank')" title="Seguinos en Instagram">
        <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 1.17.055 1.796.24 2.216.403a4.292 4.292 0 0 1 1.593.924c.443.444.73.973.924 1.593.163.42.348 1.046.403 2.216.058 1.263.07 1.646.07 4.847 0 3.2-.012 3.584-.07 4.847-.055 1.17-.24 1.796-.403 2.216a4.292 4.292 0 0 1-.924 1.593 4.292 4.292 0 0 1-1.593.924c-.42.163-1.046.348-2.216.403-1.263.058-1.646.07-4.847.07-3.2 0-3.584-.012-4.847-.07-1.17-.055-1.796-.24-2.216-.403a4.292 4.292 0 0 1-1.593-.924 4.292 4.292 0 0 1-.924-1.593c-.163-.42-.348-1.046-.403-2.216C2.212 15.631 2.2 15.247 2.2 12.047c0-3.2.012-3.584.07-4.847.055-1.17.24-1.796.403-2.216A4.292 4.292 0 0 1 3.597 3.39 4.292 4.292 0 0 1 5.19 2.466c.42-.163 1.046-.348 2.216-.403C8.416 2.212 8.8 2.2 12 2.2zm0-2.2C8.74 0 8.332.014 7.052.072 5.73.13 4.684.325 3.81.637a6.492 6.492 0 0 0-2.36 1.547A6.492 6.492 0 0 0 .637 4.19c-.312.874-.507 1.92-.565 3.242C.014 8.332 0 8.74 0 12c0 3.26.014 3.668.072 4.948.058 1.322.253 2.368.565 3.242a6.492 6.492 0 0 0 1.547 2.36 6.492 6.492 0 0 0 2.36 1.547c.874.312 1.92.507 3.242.565C8.332 23.986 8.74 24 12 24c3.26 0 3.668-.014 4.948-.072 1.322-.058 2.368-.253 3.242-.565a6.492 6.492 0 0 0 2.36-1.547 6.492 6.492 0 0 0 1.547-2.36c.312-.874.507-1.92.565-3.242.058-1.28.072-1.688.072-4.948s-.014-3.668-.072-4.948c-.058-1.322-.253-2.368-.565-3.242a6.492 6.492 0 0 0-1.547-2.36A6.492 6.492 0 0 0 20.19.637c-.874-.312-1.92-.507-3.242-.565C15.668.014 15.26 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zm0 10.162a3.999 3.999 0 1 1 0-7.998 3.999 3.999 0 0 1 0 7.998zm7.844-10.406a1.44 1.44 0 1 1-2.88 0 1.44 1.44 0 0 1 2.88 0z"/></svg>
        Instagram
      </button>
    </div>
  </nav>
  <header>
    <a id="top"></a>
    <div class="hero">
      <h1>Concientización contra incendios en Patagonia</h1>
      <div class="subtitulo">
        Prevenir y actuar juntos por nuestros bosques y comunidades.<br>
        Tecnología, compromiso y acción desde la Patagonia para el país.
      </div>
      <button class="cta" onclick="document.getElementById('sumate').scrollIntoView({behavior:'smooth'})">
        ¡Sumate a la campaña!
      </button>
    </div>
    <div class="banner-revision">
      🚀 Esta página está en constante revisión y mejora para ofrecerte la mejor experiencia y recursos actualizados. ¡Gracias por tu visita!
    </div>
  </header>
  <main>
    <!-- ... tu contenido principal ... -->
    <!-- igual que antes -->
  </main>
  <!-- Botones flotantes juntos (Instagram, WeerBot, WhatsApp) -->
  <div class="floating-btns">
    <a href="https://instagram.com/weerteck" class="btn-instagram-flotante" target="_blank" rel="noopener" title="Ir al Instagram de WeerTeck" aria-label="Ir al Instagram de WeerTeck">
      <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 1.17.055 1.796.24 2.216.403a4.292 4.292 0 0 1 1.593.924c.443.444.73.973.924 1.593.163.42.348 1.046.403 2.216.058 1.263.07 1.646.07 4.847 0 3.2-.012 3.584-.07 4.847-.055 1.17-.24 1.796-.403 2.216a4.292 4.292 0 0 1-.924 1.593 4.292 4.292 0 0 1-1.593.924c-.42.163-1.046.348-2.216.403-1.263.058-1.646.07-4.847.07-3.2 0-3.584-.012-4.847-.07-1.17-.055-1.796-.24-2.216-.403a4.292 4.292 0 0 1-1.593-.924 4.292 4.292 0 0 1-.924-1.593c-.163-.42-.348-1.046-.403-2.216C2.212 15.631 2.2 15.247 2.2 12.047c0-3.2.012-3.584.07-4.847.055-1.17.24-1.796.403-2.216A4.292 4.292 0 0 1 3.597 3.39 4.292 4.292 0 0 1 5.19 2.466c.42-.163 1.046-.348 2.216-.403C8.416 2.212 8.8 2.2 12 2.2zm0-2.2C8.74 0 8.332.014 7.052.072 5.73.13 4.684.325 3.81.637a6.492 6.492 0 0 0-2.36 1.547A6.492 6.492 0 0 0 .637 4.19c-.312.874-.507 1.92-.565 3.242C.014 8.332 0 8.74 0 12c0 3.26.014 3.668.072 4.948.058 1.322.253 2.368.565 3.242a6.492 6.492 0 0 0 1.547 2.36 6.492 6.492 0 0 0 2.36 1.547c.874.312 1.92.507 3.242.565C8.332 23.986 8.74 24 12 24c3.26 0 3.668-.014 4.948-.072 1.322-.058 2.368-.253 3.242-.565a6.492 6.492 0 0 0 2.36-1.547 6.492 6.492 0 0 0 1.547-2.36c.312-.874.507-1.92.565-3.242.058-1.28.072-1.688.072-4.948s-.014-3.668-.072-4.948c-.058-1.322-.253-2.368-.565-3.242a6.492 6.492 0 0 0-1.547-2.36A6.492 6.492 0 0 0 20.19.637c-.874-.312-1.92-.507-3.242-.565C15.668.014 15.26 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zm0 10.162a3.999 3.999 0 1 1 0-7.998 3.999 3.999 0 0 1 0 7.998zm7.844-10.406a1.44 1.44 0 1 1-2.88 0 1.44 1.44 0 0 1 2.88 0z"/></svg>
    </a>
    <button id="weerbot-button" class="btn-weerbot-flotante" title="Abrir WeerBot" aria-label="Abrir WeerBot">
      <svg viewBox="0 0 32 32" fill="none"><circle cx="16" cy="16" r="15" fill="#fff" stroke="#00bcd4" stroke-width="2"/><ellipse cx="11.5" cy="14" rx="2" ry="2.2" fill="#00bcd4"/><ellipse cx="20.5" cy="14" rx="2" ry="2.2" fill="#00bcd4"/><rect x="11" y="19.2" width="10" height="2.2" rx="1.1" fill="#80deea"/><rect x="13" y="22.2" width="6" height="1.4" rx="0.7" fill="#80deea"/></svg>
    </button>
    <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta%20o%20recomendaci%C3%B3n" class="btn-whatsapp-flotante" target="_blank" rel="noopener" title="Escribinos por WhatsApp" aria-label="Escribinos por WhatsApp">
      <svg viewBox="0 0 32 32" fill="none"><circle cx="16" cy="16" r="15" fill="#fff" stroke="#00bcd4" stroke-width="2"/><path d="M22.5 21.2c-.11-.06-2.63-1.31-3.05-1.46-.41-.15-.71-.22-1 .11-.3.34-1.15 1.46-1.41 1.77-.26.3-.52.34-.96.11-.44-.22-1.85-.68-3.52-2.17-1.3-1.16-2.18-2.6-2.43-3.04-.26-.44-.03-.64.2-.84.2-.19.44-.49.66-.73.22-.24.29-.43.44-.7.15-.27.07-.51-.04-.73-.11-.22-1-2.42-1.37-3.31-.36-.88-.73-.76-1-.77a1.02 1.02 0 0 0-.87.03c-.27.13-1.02 1-1.02 2.43 0 1.43 1.04 2.82 1.19 3.02.14.2 2.04 3.14 5.4 4.32 3.36 1.19 3.36.79 3.96.74.6-.05 1.96-.8 2.24-1.57.28-.77.28-1.43.19-1.57-.09-.14-.27-.22-.56-.37z" fill="#00bcd4"/></svg>
    </a>
  </div>
  <!-- Ventana flotante del WeerBot -->
  <div id="weerbot-window">
    <div class="weerbot-header">
      <span>🤖 WeerBot</span>
      <button id="weerbot-close">×</button>
    </div>
    <div id="weerbot-messages">
      <div style="color:#80deea;margin-bottom:.7em;">¡Hola! Soy WeerBot.<br>Puedo responder dudas sobre la campaña, prevención de incendios, cómo sumarte o WeerCoin.<br>
      <span style="font-size:.97em;color:#b0bec5;">(¡Probá preguntarme algo!)</span></div>
    </div>
    <form id="weerbot-form">
      <input id="weerbot-input" type="text" placeholder="Escribí tu pregunta..." maxlength="180">
      <button type="submit">Enviar</button>
    </form>
  </div>
  <footer>
    <div class="footer-links">
      <a href="#top">↑ Volver arriba</a>
      <a href="mailto:weerteck@gmail.com">Contacto</a>
      <a href="https://instagram.com/weerteck" target="_blank" rel="noopener">Instagram</a>
      <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta" target="_blank" rel="noopener">WhatsApp</a>
    </div>
    <div>
      &copy; 2025 WeerTeck — Todos los derechos reservados<br>
      <span style="font-size:.93em;color:var(--accent);">Página en revisión y mejora continua.</span>
    </div>
  </footer>
  <script>
    // Fondo animado de líneas tecnológicas
    (() => {
      const canvas = document.getElementById('bg-animated-canvas');
      let ctx, w, h, lines = [];
      const lineCount = 22;
      function resize() {
        w = window.innerWidth;
        h = window.innerHeight;
        canvas.width = w;
        canvas.height = h;
      }
      function randomColor() {
        const palette = ['#00bcd4', '#80deea', '#263238', '#fff'];
        return palette[Math.floor(Math.random() * palette.length)];
      }
      function createLines() {
        lines = [];
        for(let i=0; i<lineCount; i++) {
          let y = Math.random()*h;
          let speed = 0.6 + Math.random()*1.3;
          let len = 160 + Math.random()*220;
          lines.push({
            x: Math.random()*w,
            y,
            len,
            width: 1.2 + Math.random()*1.7,
            dx: -0.8 + Math.random()*1.6,
            dy: -0.2 + Math.random()*0.4,
            color: randomColor(),
            alpha: 0.32 + Math.random()*0.46
          });
        }
      }
      function draw() {
        ctx.clearRect(0,0,w,h);
        for(let l of lines) {
          ctx.save();
          ctx.globalAlpha = l.alpha;
          ctx.strokeStyle = l.color;
          ctx.shadowColor = l.color;
          ctx.shadowBlur = 8;
          ctx.lineWidth = l.width;
          ctx.beginPath();
          ctx.moveTo(l.x, l.y);
          ctx.lineTo(l.x + l.dx * l.len, l.y + l.dy * l.len);
          ctx.stroke();
          ctx.restore();

          l.x += l.dx * 0.8;
          l.y += l.dy * 0.8;

          if(l.x > w+40 || l.x < -40 || l.y < -40 || l.y > h+40) {
            l.x = Math.random()*w;
            l.y = Math.random()*h;
            l.color = randomColor();
            l.alpha = 0.32 + Math.random()*0.46;
          }
        }
        requestAnimationFrame(draw);
      }
      function start() {
        ctx = canvas.getContext('2d');
        resize();
        createLines();
        draw();
      }
      window.addEventListener('resize', () => { resize(); createLines(); });
      setTimeout(start, 70);
    })();

    // WeerBot: chat simulado
    (function () {
      const weerbotBtn = document.getElementById('weerbot-button');
      const weerbotWin = document.getElementById('weerbot-window');
      const weerbotClose = document.getElementById('weerbot-close');
      const weerbotForm = document.getElementById('weerbot-form');
      const weerbotInput = document.getElementById('weerbot-input');
      const weerbotMsgs = document.getElementById('weerbot-messages');

      function scrollDown() {
        setTimeout(() => { weerbotMsgs.scrollTop = weerbotMsgs.scrollHeight; }, 40);
      }

      weerbotBtn.onclick = () => {
        weerbotWin.style.display = 'block';
        weerbotInput.focus();
        scrollDown();
      };
      weerbotClose.onclick = () => {
        weerbotWin.style.display = 'none';
      };

      function botReply(msg, delay = 600) {
        setTimeout(() => {
          const div = document.createElement('div');
          div.style.margin = "0.5em 0 0.7em 0";
          div.style.color = "#80deea";
          div.innerHTML = msg;
          weerbotMsgs.appendChild(div);
          scrollDown();
        }, delay);
      }

      function replyToUser(text) {
        const t = text.trim().toLowerCase();
        if (!t) return botReply('¿Podés escribir tu consulta? 🤔', 300);
        if (t.includes('sumar') || t.includes('colaborar') || t.includes('participar')) {
          botReply('¡Genial que quieras sumarte! Completá el formulario en la sección <b>Sumate</b> o contanos por WhatsApp o Instagram.', 550);
        }
        else if (t.includes('incendio') || t.includes('prevenció') || t.includes('fuego')) {
          botReply('La prevención es clave: no hagas fuego en zonas no permitidas, no dejes basura ni vidrios, avisá si ves humo y sumate a campañas de concientización. Si querés más info específica, preguntame.', 600);
        }
        else if (t.includes('weercoin')) {
          botReply('WeerCoin es la moneda digital pensada para financiar proyectos de prevención y tecnología en incendios. ¿Querés saber cómo funciona o cómo podés ayudar?', 650);
        }
        else if (t.includes('contacto') || t.includes('mail') || t.includes('whatsapp')) {
          botReply('Podés escribirnos por WhatsApp al <b>1125216302</b>, Instagram o email: <b>weerteck@gmail.com</b>', 500);
        }
        else if (t.includes('udesa')) {
          botReply('Estamos preparando una demo para presentar el proyecto en la UDESA. Si te interesa apoyar o participar, avisá!', 650);
        }
        else if (t.includes('quiénes') || t.includes('creador') || t.includes('lucas') || t.includes('santiago')) {
          botReply('Los creadores del proyecto son <b>Santiago Martinez</b> y <b>Lucas De Cesare</b> (también desarrollador de la página y WeerCoin).', 650);
        }
        else if (t.includes('aliado') || t.includes('aliados')) {
          botReply('Todavía no tenemos aliados oficiales. Si tu ONG, municipio o grupo quiere sumarse, completá el formulario o escribinos.', 600);
        }
        else if (t.includes('qué hac') || t.includes('proyecto')) {
          botReply('Desarrollamos torres inteligentes y estrategias para alertar incendios temprano, usando tecnología y comunidad. También promovemos educación y acción colectiva.', 700);
        }
        else if (t.includes('hola') || t.includes('buenas') || t.includes('saludo')) {
          botReply('¡Hola! ¿En qué puedo ayudarte sobre prevención de incendios, la campaña o WeerCoin?', 400);
        }
        else if (t.length < 8) {
          botReply('¿Podés darme más detalles para ayudarte mejor?', 400);
        }
        else {
          botReply('¡Gracias por tu mensaje! Si no tengo la respuesta, te recomiendo contactarnos directo por WhatsApp o Instagram. 😊', 800);
        }
      }

      weerbotForm.onsubmit = function (e) {
        e.preventDefault();
        const txt = weerbotInput.value.trim();
        if (!txt) return;
        const userMsg = document.createElement('div');
        userMsg.style.margin = "0.2em 0 0.2em 0";
        userMsg.style.textAlign = "right";
        userMsg.style.color = "#00bcd4";
        userMsg.innerHTML = txt;
        weerbotMsgs.appendChild(userMsg);
        weerbotInput.value = "";
        scrollDown();
        replyToUser(txt);
      };

      weerbotInput.addEventListener('keydown', function(e){
        if (e.key === 'Enter' && !e.shiftKey) {
          e.preventDefault();
          weerbotForm.dispatchEvent(new Event('submit'));
        }
      });
    })();
  </script>
</body>
</html>
