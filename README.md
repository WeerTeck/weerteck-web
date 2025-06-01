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
      --primary: #00fff7;
      --accent: #00d1ff;
      --secondary: #232e3a;
      --dark: #0a1018;
      --text: #e0e0e0;
      --light: #fff;
      --danger: #e57373;
      --success: #4caf50;
      --muted: #b0bec5;
      --shadow: 0 6px 32px 0 #00fff755;
      --radius: 22px;
      --glow: 0 0 12px #00fff7cc, 0 0 32px #00fff733;
    }
    * { box-sizing: border-box; margin: 0; padding: 0;}
    html { scroll-behavior: smooth;}
    body {
      font-family: 'Poppins', sans-serif;
      background: radial-gradient(circle at 50% 15%, #11202a 0%, #0a1018 80%);
      color: var(--text);
      min-height: 100vh;
      line-height: 1.6;
      position: relative;
      overflow-x: hidden;
      display: flex; flex-direction: column;
    }
    .bg-futuristic {
      position: fixed;
      inset: 0;
      width: 100vw;
      height: 100vh;
      z-index: 0;
      pointer-events: none;
      background: none;
    }
    #bg-futuristic-canvas {
      width: 100vw;
      height: 100vh;
      display: block;
    }
    header, main, nav, footer, .hero, .acciones-box, .sumate-section, .public-comments-section {
      position: relative;
      z-index: 1;
    }
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      height: 60px;
      z-index: 2002;
      background: rgba(8, 14, 22, 0.98);
      border-bottom: 2px solid var(--primary);
      box-shadow: 0 2px 16px #00fff722;
      border-radius: 0 0 22px 22px;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw;
      font-size: 1.1em;
      backdrop-filter: blur(7px);
    }
    nav .nav-logo {
      font-weight: 900;
      font-size: 1.5em;
      letter-spacing: 2px;
      background: linear-gradient(90deg, var(--primary), var(--accent) 70%, transparent);
      background-clip: text; -webkit-background-clip: text;
      color: transparent; -webkit-text-fill-color: transparent;
      animation: logoHue 4s linear infinite alternate;
      display: flex; align-items: center;
      filter: drop-shadow(0 0 16px #00fff777);
      text-shadow: var(--glow);
    }
    @keyframes logoHue {
      0% { filter: hue-rotate(0deg);}
      100%{ filter: hue-rotate(60deg);}
    }
    nav ul { list-style: none; display: flex; gap: 1.7em;}
    nav ul li a {
      color: var(--text);
      text-decoration: none;
      font-weight: 600;
      padding: 8px 17px;
      border-radius: 10px;
      transition: background 0.18s, color 0.18s, box-shadow 0.13s;
      position: relative;
    }
    nav ul li a:hover, nav ul li a:focus {
      background: linear-gradient(90deg,var(--accent) 30%,var(--primary));
      color: #fff;
      box-shadow: 0 0 12px var(--primary);
      text-shadow: var(--glow);
    }
    nav .nav-actions {
      display: flex; gap: 1em;
    }
    nav .nav-actions .btn-ig {
      background: linear-gradient(90deg,#00fff7,#00d1ff 80%);
      color: #232e3a; border: none; border-radius: 22px;
      padding: 7px 16px; font-weight: 700; font-size: 1em;
      cursor: pointer; box-shadow: 0 2px 12px #00fff744;
      display: flex; align-items: center; gap: 7px;
      transition: background 0.2s, scale 0.2s;
    }
    nav .nav-actions .btn-ig:hover {
      background: linear-gradient(90deg,#00d1ff,#00fff7 90%);
      scale:1.08;
      box-shadow: 0 0 18px #00fff7cc;
    }
    @media (max-width: 780px) {
      nav ul { gap: 0.7em; font-size: 0.92em;}
      nav .nav-logo { font-size: 1.1em; }
    }
    @media (max-width: 500px){
      nav { font-size: 0.91em; padding: 0 1vw;}
      nav ul { gap: 0.4em;}
      nav .nav-logo { font-size: 1em;}
    }
    header { margin-top: 60px; text-align: center; padding: 2.7em 0 1.2em 0;}
    .hero {
      background: linear-gradient(120deg, #101b29 80%, #00fff71a 100%);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      margin: 1.6em auto 1.3em auto;
      max-width: 750px;
      padding: 2.5em 1.7em 2.2em 1.7em;
      position: relative;
      z-index: 1;
      border: 2.5px solid var(--primary);
      overflow: hidden;
    }
    .hero h1 {
      font-weight: 900;
      font-size: 2.9rem;
      color: var(--primary);
      text-shadow: 0 0 18px var(--primary), 0 0 30px #00fff733;
      letter-spacing: 2.2px;
      background: linear-gradient(90deg,var(--primary), var(--accent) 80%,#fff0);
      background-clip: text; -webkit-background-clip: text;
      color: transparent; -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 32px var(--primary));
      margin-bottom: 0.5rem;
    }
    .hero .subtitulo {
      font-weight: 600;
      font-size: 1.25rem;
      color: var(--accent);
      margin-bottom: 1.9em;
      text-shadow: 0 0 10px var(--accent);
      letter-spacing: 1.2px;
    }
    .hero .cta {
      display: inline-block;
      margin-top: 1em;
      font-weight: 700;
      padding: 0.85em 2.2em;
      background: linear-gradient(90deg,var(--primary),var(--accent));
      color: #fff;
      border: none;
      border-radius: 99px;
      font-size: 1.08em;
      box-shadow: 0 2px 18px #00fff755;
      transition: background 0.2s, scale 0.2s, box-shadow 0.22s;
      cursor: pointer;
      letter-spacing: 1.2px;
      outline: none;
      text-shadow: var(--glow);
    }
    .hero .cta:hover { background: linear-gradient(90deg,var(--accent),var(--primary) 70%); scale:1.09;}
    .banner-revision {
      background: linear-gradient(90deg,var(--primary) 20%,var(--accent) 80%,#fff0);
      color: #01343a;
      font-weight: bold;
      text-align: center;
      padding: 0.7em 0.2em;
      margin: 0.5em 0 1.3em 0;
      border-radius: 12px;
      font-size: 1.1em;
      box-shadow: 0 2px 18px var(--primary);
      letter-spacing: 1.1px;
      backdrop-filter: blur(1.2px);
    }
    main { max-width: 820px; width: 97%; margin: auto; padding-bottom: 2em;}
    /* ... El resto de tu CSS de contenido ... */
    /* ... Mantén los estilos visuales que ya tienes ... */
    /* Botones flotantes y WeerBot */
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
      transition: background 0.13s, transform 0.18s, box-shadow 0.18s;
      box-shadow: 0 6px 32px #00fff755;
      background: linear-gradient(135deg, var(--primary), var(--accent) 70%);
      outline: none;
    }
    .btn-instagram-flotante:hover { background: #00fff7; transform: scale(1.11) rotate(-8deg);}
    .btn-whatsapp-flotante:hover { background: #00fff7; transform: scale(1.11) rotate(8deg);}
    .btn-weerbot-flotante:hover { background: #00fff7; transform: scale(1.11);}
    .btn-instagram-flotante:focus,
    .btn-whatsapp-flotante:focus,
    .btn-weerbot-flotante:focus {
      outline: 2.5px solid var(--accent);
      box-shadow: 0 0 0 4px #00fff777;
    }
    .btn-instagram-flotante svg,
    .btn-whatsapp-flotante svg,
    .btn-weerbot-flotante svg { width: 37px; height: 37px; fill: #fff;}
    @media (max-width:700px) {
      .floating-btns { right: 10px; bottom: 12px;}
      .btn-instagram-flotante, .btn-whatsapp-flotante, .btn-weerbot-flotante { width:52px; height:52px;}
      .btn-instagram-flotante svg, .btn-whatsapp-flotante svg, .btn-weerbot-flotante svg { width:30px; height:30px;}
    }
    #weerbot-window {
      display:none;
      position:fixed;
      bottom: 235px;
      right: 24px;
      width: 340px; max-width:90vw;
      z-index: 12000;
      background: #0e1825f3;
      border-radius: 22px;
      border: 2.5px solid var(--primary);
      box-shadow: 0 8px 36px #00fff799;
      padding: 0.7em 0 0 0;
      font-family:Poppins,sans-serif;
      color: #e0e0e0;
    }
    #weerbot-window .weerbot-header {
      display:flex;
      align-items:center;
      justify-content:space-between;
      padding:0.9em 1.3em 0.3em 1.3em;
    }
    #weerbot-window .weerbot-header span {
      font-weight:800;
      color:var(--primary);
      font-size:1.18em;
      text-shadow: var(--glow);
    }
    #weerbot-close {
      background:none;
      border:none;
      color:var(--primary);
      font-size:1.4em;
      cursor:pointer;
      font-weight:900;
      padding:0 8px;
      line-height:1;
    }
    #weerbot-messages {
      min-height: 120px; max-height: 260px; overflow-y: auto; padding: 0.7em 1.1em 0.7em 1.1em;
      font-size: 1em; color: #e0e0e0;
    }
    #weerbot-options {padding:0.7em 1.1em 1.3em 1.1em;}
    #weerbot-options button {
      display: block;
      margin: 0.4em 0;
      width: 100%;
      background: linear-gradient(90deg,var(--primary),var(--accent));
      color: #fff;
      border: none;
      border-radius: 10px;
      font-weight: 700;
      padding: 0.75em 1em;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 8px var(--primary);
      transition: background 0.2s, scale 0.15s;
      outline: none;
      text-shadow: var(--glow);
    }
    #weerbot-options button:hover {background: var(--primary); scale:1.03;}
    #weerbot-options button:focus {outline: 2.5px solid var(--accent);}
    @media (max-width:550px) {
      #weerbot-window { width:98vw !important; right:1vw; }
    }
    /* Footer y links ... tu CSS de footer ... */
  </style>
</head>
<body>
  <!-- FONDO TECNOLÓGICO -->
  <div class="bg-futuristic">
    <canvas id="bg-futuristic-canvas"></canvas>
  </div>
  <nav>
    <!-- ... nav igual que tu código ... -->
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
        <svg viewBox="0 0 24 24" style="width:1.25em;height:1.25em;"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 1.17.055 1.796.24 2.216.403a4.292 4.292 0 0 1 1.593.924c.443.444.73.973.924 1.593.163.42.348 1.046.403 2.216.058 1.263.07 1.646.07 4.847 0 3.2-.012 3.584-.07 4.847-.055 1.17-.24 1.796-.403 2.216a4.292 4.292 0 0 1-.924 1.593 4.292 4.292 0 0 1-1.593.924c-.42.163-1.046.348-2.216.403-1.263.058-1.646.07-4.847.07-3.2 0-3.584-.012-4.847-.07-1.17-.055-1.796-.24-2.216-.403a4.292 4.292 0 0 1-1.593-.924 4.292 4.292 0 0 1-.924-1.593c-.163-.42-.348-1.046-.403-2.216C2.212 15.631 2.2 15.247 2.2 12.047c0-3.2.012-3.584.07-4.847.055-1.17.24-1.796.403-2.216A4.292 4.292 0 0 1 3.597 3.39 4.292 4.292 0 0 1 5.19 2.466c.42-.163 1.046-.348 2.216-.403C8.416 2.212 8.8 2.2 12 2.2zm0-2.2C8.74 0 8.332.014 7.052.072 5.73.13 4.684.325 3.81.637a6.492 6.492 0 0 0-2.36 1.547A6.492 6.492 0 0 0 .637 4.19c-.312.874-.507 1.92-.565 3.242C.014 8.332 0 8.74 0 12c0 3.26.014 3.668.072 4.948.058 1.322.253 2.368.565 3.242a6.492 6.492 0 0 0 1.547 2.36 6.492 6.492 0 0 0 2.36 1.547c.874.312 1.92.507 3.242.565C8.332 23.986 8.74 24 12 24c3.26 0 3.668-.014 4.948-.072 1.322-.058 2.368-.253 3.242-.565a6.492 6.492 0 0 0 2.36-1.547 6.492 6.492 0 0 0 1.547-2.36c.312-.874.507-1.92.565-3.242.058-1.28.072-1.688.072-4.948s-.014-3.668-.072-4.948c-.058-1.322-.253-2.368-.565-3.242a6.492 6.492 0 0 0-1.547-2.36A6.492 6.492 0 0 0 20.19.637c-.874-.312-1.92-.507-3.242-.565C15.668.014 15.26 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zm0 10.162a3.999 3.999 0 1 1 0-7.998 3.999 3.999 0 0 1 0 7.998zm7.844-10.406a1.44 1.44 0 1 1-2.88 0 1.44 1.44 0 0 1 2.88 0z"/></svg> Instagram
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
    <!-- ... tu contenido de main ... -->
    <!-- Pega aquí todas tus secciones, formulario, comentarios, etc. -->
  </main>
  <!-- Botones flotantes juntos (Instagram, WeerBot, WhatsApp) -->
  <div class="floating-btns">
    <a href="https://instagram.com/weerteck" class="btn-instagram-flotante" target="_blank" rel="noopener" title="Ir al Instagram de WeerTeck" aria-label="Ir al Instagram de WeerTeck">
      <!-- ... icono Instagram ... -->
    </a>
    <button id="weerbot-button" class="btn-weerbot-flotante" title="Abrir WeerBot" aria-label="Abrir WeerBot">
      <svg viewBox="0 0 32 32" fill="none"><circle cx="16" cy="16" r="15" fill="#fff" stroke="#00fff7" stroke-width="2"/><ellipse cx="11.5" cy="14" rx="2" ry="2.2" fill="#00fff7"/><ellipse cx="20.5" cy="14" rx="2" ry="2.2" fill="#00fff7"/><rect x="11" y="19.2" width="10" height="2.2" rx="1.1" fill="#00d1ff"/><rect x="13" y="22.2" width="6" height="1.4" rx="0.7" fill="#00d1ff"/></svg>
    </button>
    <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta%20o%20recomendaci%C3%B3n" class="btn-whatsapp-flotante" target="_blank" rel="noopener" title="Escribinos por WhatsApp" aria-label="Escribinos por WhatsApp">
      <!-- ... icono WhatsApp ... -->
    </a>
  </div>
  <!-- Ventana flotante del WeerBot (nuevo) -->
  <div id="weerbot-window">
    <div class="weerbot-header">
      <span>🤖 WeerBot</span>
      <button id="weerbot-close">×</button>
    </div>
    <div id="weerbot-messages">
      <div style="color:#00d1ff;margin-bottom:1em;">¡Hola! Soy WeerBot.<br>Elegí una opción para informarte sobre el proyecto, prevención o sumarte.<br>
      <span style="font-size:.97em;color:#b0bec5;">(¡Tocá una pregunta para empezar!)</span></div>
    </div>
    <div id="weerbot-options"></div>
  </div>
  <footer>
    <!-- ... tu footer aquí ... -->
  </footer>
  <script>
    // FONDO FUTURISTA: Partículas tecnológicas en red
    (() => {
      const canvas = document.getElementById('bg-futuristic-canvas');
      let ctx, w, h, nodes = [], lines = [];
      const NODE_COUNT = 32, SPEED = 0.24, LINK_DIST = 140, NODE_RADIUS = 2.6;
      function resize() {
        w = window.innerWidth;
        h = window.innerHeight;
        canvas.width = w;
        canvas.height = h;
      }
      function randomColor() {
        const palette = ['#00fff7', '#00d1ff', '#232e3a', '#fff'];
        return palette[Math.floor(Math.random() * palette.length)];
      }
      function createNodes() {
        nodes = [];
        for(let i=0; i<NODE_COUNT; i++) {
          nodes.push({
            x: Math.random()*w,
            y: Math.random()*h,
            dx: SPEED*(-1 + Math.random()*2),
            dy: SPEED*(-1 + Math.random()*2),
            color: randomColor(),
            radius: NODE_RADIUS + Math.random()*1.2
          });
        }
      }
      function draw() {
        ctx.clearRect(0,0,w,h);
        // DIBUJAR LÍNEAS
        for (let i=0; i<nodes.length; i++) {
          for (let j=i+1; j<nodes.length; j++) {
            let dx = nodes[i].x - nodes[j].x, dy = nodes[i].y - nodes[j].y;
            let dist = Math.sqrt(dx*dx + dy*dy);
            if (dist < LINK_DIST) {
              ctx.save();
              ctx.globalAlpha = 0.09 + 0.23*(1 - dist/LINK_DIST);
              ctx.beginPath();
              ctx.strokeStyle = nodes[i].color;
              ctx.moveTo(nodes[i].x, nodes[i].y);
              ctx.lineTo(nodes[j].x, nodes[j].y);
              ctx.shadowColor = nodes[i].color;
              ctx.shadowBlur = 12;
              ctx.lineWidth = 1.15;
              ctx.stroke();
              ctx.restore();
            }
          }
        }
        // DIBUJAR NODOS
        for(let n of nodes) {
          ctx.save();
          ctx.beginPath();
          ctx.arc(n.x, n.y, n.radius, 0, 2*Math.PI);
          ctx.fillStyle = n.color;
          ctx.shadowColor = n.color;
          ctx.shadowBlur = 16;
          ctx.globalAlpha = 0.85;
          ctx.fill();
          ctx.restore();
        }
        // MOVER
        for(let n of nodes) {
          n.x += n.dx;
          n.y += n.dy;
          if (n.x < 0 || n.x > w) n.dx *= -1;
          if (n.y < 0 || n.y > h) n.dy *= -1;
        }
        requestAnimationFrame(draw);
      }
      function start() {
        ctx = canvas.getContext('2d');
        resize();
        createNodes();
        draw();
      }
      window.addEventListener('resize', () => { resize(); createNodes(); });
      setTimeout(start, 100);
    })();

    // WeerBot: cuestionario interactivo
    (function () {
      const weerbotBtn = document.getElementById('weerbot-button');
      const weerbotWin = document.getElementById('weerbot-window');
      const weerbotClose = document.getElementById('weerbot-close');
      const weerbotMsgs = document.getElementById('weerbot-messages');
      const weerbotOptions = document.getElementById('weerbot-options');
      function scrollDown() {
        setTimeout(() => { weerbotMsgs.scrollTop = weerbotMsgs.scrollHeight; }, 40);
      }
      weerbotBtn.onclick = () => {
        weerbotWin.style.display = 'block';
        showStep('start');
        scrollDown();
      };
      weerbotClose.onclick = () => {
        weerbotWin.style.display = 'none';
      };
      const steps = {
        start: {
          text: "¿Sobre qué tema querés saber?",
          options: [
            { label: "¿Qué es el proyecto WeerTeck?", next: "quees" },
            { label: "¿Cómo puedo sumarme o colaborar?", next: "sumate" },
            { label: "Prevención de incendios", next: "prevencion" },
            { label: "¿Qué es WeerCoin?", next: "weercoin" },
            { label: "Aliados y apoyos", next: "aliados" },
            { label: "Contacto directo", next: "contacto" }
          ]
        },
        quees: {
          text: "WeerTeck desarrolla torres inteligentes y estrategias comunitarias para detectar y prevenir incendios en Patagonia. Usamos tecnología, educación y acción colectiva.<br><br>¿Querés saber más o sumarte?",
          options: [
            { label: "¿Cómo funcionan las torres?", next: "torres" },
            { label: "¿Por qué Patagonia?", next: "patagonia" },
            { label: "Quiero sumarme", next: "sumate" },
            { label: "Volver al inicio", next: "start" }
          ]
        },
        torres: {
          text: "Las torres inteligentes detectan humo y condiciones de incendio usando sensores y tecnología, enviando alertas en tiempo real a brigadas, municipios y vecinos.<br><br>¿Te interesa saber cómo colaborar?",
          options: [
            { label: "Quiero sumarme", next: "sumate" },
            { label: "Volver a preguntas", next: "quees" },
            { label: "Inicio", next: "start" }
          ]
        },
        patagonia: {
          text: "La Patagonia es una de las regiones más afectadas por incendios forestales en Argentina. Protegerla es clave para el ambiente y las comunidades.<br><br>¿Te gustaría ayudar o saber más sobre prevención?",
          options: [
            { label: "Quiero sumarme", next: "sumate" },
            { label: "Prevención de incendios", next: "prevencion" },
            { label: "Inicio", next: "start" }
          ]
        },
        sumate: {
          text: "¡Nos encanta que quieras sumarte! Podés colaborar como voluntario, sumar tu ONG o ayudar con difusión.<br><br>¿Cómo querés contactarnos?",
          options: [
            { label: "WhatsApp", next: "contacto" },
            { label: "Email", next: "contacto" },
            { label: "Volver al inicio", next: "start" }
          ]
        },
        prevencion: {
          text: "Tips básicos: no hagas fuego en zonas no permitidas, no dejes basura ni vidrios, avisá si ves humo. Compartí info y sumate a campañas.<br><br>¿Querés más info o sumarte?",
          options: [
            { label: "Quiero sumarme", next: "sumate" },
            { label: "Volver al inicio", next: "start" }
          ]
        },
        weercoin: {
          text: "WeerCoin es una moneda digital creada para financiar proyectos de prevención y tecnología contra incendios.<br><br>¿Te interesa apoyar o saber cómo usarla?",
          options: [
            { label: "Quiero apoyar con WeerCoin", next: "contacto" },
            { label: "Volver al inicio", next: "start" }
          ]
        },
        aliados: {
          text: "Aún no hay aliados oficiales. Si tu ONG, municipio o grupo quiere sumarse, ¡escribinos!<br><br>¿Querés ser aliado o recibir info?",
          options: [
            { label: "Quiero ser aliado", next: "contacto" },
            { label: "Inicio", next: "start" }
          ]
        },
        contacto: {
          text: `<b>¡Gracias por tu interés!</b><br>Contactanos por WhatsApp <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20sumarme%20al%20proyecto" target="_blank" style="color:var(--accent);">1125216302</a> <br>o por mail: <a href="mailto:weerteck@gmail.com" style="color:var(--accent);">weerteck@gmail.com</a><br><br>¡Te esperamos!`,
          options: [
            { label: "Ir al WhatsApp", url: "https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20sumarme%20al%20proyecto" },
            { label: "Enviar email", url: "mailto:weerteck@gmail.com" },
            { label: "Volver al inicio", next: "start" }
          ]
        }
      };
      function showStep(stepKey) {
        const step = steps[stepKey];
        weerbotMsgs.innerHTML = `<div style="color:#00d1ff;margin-bottom:.8em;">${step.text}</div>`;
        weerbotOptions.innerHTML = '';
        for (const opt of step.options) {
          const btn = document.createElement('button');
          btn.textContent = opt.label;
          if (opt.next) {
            btn.onclick = () => showStep(opt.next);
          } else if (opt.url) {
            btn.onclick = () => window.open(opt.url, '_blank');
          }
          weerbotOptions.appendChild(btn);
        }
        scrollDown();
      }
    })();
  </script>
</body>
</html>

