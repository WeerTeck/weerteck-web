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
    section { margin-bottom: 2.8em; padding: 1.2em 0.7em;}
    h2 { color: var(--primary); font-size: 1.55em; margin-bottom: 0.6em; text-shadow: var(--glow);}
    h3 { color: var(--accent); margin-bottom: 0.3em; font-size: 1.1em; }
    p { font-size: 1.07rem; margin-bottom: 1.1em;}
    .team-list, .aliados-list, .news-list { list-style: none; padding: 0; }
    .team-list li {
      background: linear-gradient(90deg, #17293a 95%, #00fff722);
      border-radius: var(--radius);
      margin-bottom: 1.2em;
      padding: 1.1em 2em;
      color: var(--text);
      box-shadow: var(--shadow);
      display: flex; align-items: center; gap: 2em;
      border-left: 7px solid var(--primary);
      flex-direction: row;
      transition: box-shadow 0.22s, background 0.3s;
    }
    .team-list .team-creator {
      color: var(--primary);
      font-weight: 700;
      font-size: 1.13em;
      margin-bottom: 0.2em;
      text-shadow: var(--glow);
    }
    .aliados-list { display:grid; grid-template-columns: repeat(auto-fit,minmax(210px,1fr)); gap:1em;}
    .aliados-list li {
      background: linear-gradient(90deg, #15202e 60%, #00d1ff11 100%);
      border-radius: var(--radius);
      border-left: 5px solid var(--accent);
      box-shadow: var(--shadow);
      padding: 1.1em 1.2em;
      transition: box-shadow 0.22s;
    }
    .aliados-nuevo {
      background: #4caf5044;
      border-left: 5px solid var(--success);
    }
    .news-list li {
      background: linear-gradient(90deg, #232e3aee 80%, #00d1ff11 100%);
      border-radius: var(--radius);
      margin-bottom: 0.8em;
      padding: 0.7em 1.2em;
      color: var(--accent);
      border-left: 4px solid var(--accent);
      font-size: 1.05em;
      box-shadow: var(--shadow);
      transition: box-shadow 0.22s;
    }
    .mapa-patagonia {
      width: 100%; max-width: 410px; margin: 1.2em auto 1.1em auto; display: block;
      border-radius: 13px; box-shadow: 0 2px 18px var(--primary);
      border: 2px solid var(--primary);
      filter: grayscale(0.15) brightness(0.93);
    }
    .acciones-box {
      background: linear-gradient(100deg,#232e3add 70%,var(--primary) 100%);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 1.2em 1.5em;
      margin-bottom: 1.7em;
      border-left: 7px solid var(--primary);
      transition: box-shadow 0.22s, background 0.3s;
    }
    .acciones-box ul { margin-top: 0.4em; margin-bottom: 0;}
    .acciones-box li { margin-bottom: 0.7em; color: var(--accent);}
    .sumate-section {
      background: linear-gradient(120deg, #18283b 90%, #00fff71a);
      border-radius: var(--radius);
      padding: 2em 1em 2em 1em;
      box-shadow: var(--shadow);
      border: 2.5px solid var(--primary);
      margin-bottom: 2.3em;
      transition: box-shadow 0.22s, background 0.3s;
    }
    .sumate-section label { display: block; margin-bottom: 0.4em; color: var(--accent); font-weight: 600;}
    .sumate-section input, .sumate-section textarea, .sumate-section select {
      width: 100%; max-width: 420px;
      padding: 0.7em 1.2em;
      border-radius: 11px;
      border: 1.7px solid var(--accent);
      font-size: 1em;
      background: #e0f7fa;
      color: #18283b;
      margin-bottom: 1em;
      transition: border-color 0.18s, box-shadow 0.18s;
    }
    .sumate-section input:focus, .sumate-section textarea:focus, .sumate-section select:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 2.5px #00fff75a;
      outline: none;
    }
    .sumate-section button {
      background: linear-gradient(90deg, var(--primary), var(--accent));
      color: #fff;
      padding: 0.8em 2.1em;
      border: none;
      border-radius: 11px;
      font-weight: 700;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 12px var(--primary);
      transition: background 0.2s, scale 0.2s, box-shadow 0.22s;
      margin-top: 0.2em;
      outline: none;
    }
    .sumate-section button:hover { background: var(--primary); scale:1.04;}
    .msg-exito, .msg-error {
      text-align:center; font-weight:600; margin-bottom:1em; margin-top:0.1em;
      border-radius:10px; padding:0.6em 0;
    }
    .msg-exito { background: #4caf50cc; color: #fff;}
    .msg-error { background: #e57373cc; color: #fff;}
    .public-comments-section {
      background: linear-gradient(120deg, var(--primary) 60%, var(--accent) 40%, #232e3a88);
      border-radius: var(--radius);
      padding: 2.3em 1em;
      box-shadow: var(--shadow);
      border: 2.5px solid var(--primary);
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
      margin-bottom:2em;
      transition: box-shadow 0.22s, background 0.3s;
    }
    .public-comments-section h2 {
      text-align: center;
      margin-bottom: 1.1em;
      color: var(--primary);
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
      padding: 0.7em 1.2em;
      border-radius: 11px;
      border: 1.7px solid var(--accent);
      font-size: 1em;
      background: #e0f7fa;
      color: #18283b;
      transition: border-color 0.18s, box-shadow 0.18s;
    }
    #comment-form input:focus, #comment-form textarea:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 2.5px #00fff75a;
      outline: none;
    }
    #comment-form button {
      background: linear-gradient(90deg, var(--primary), var(--accent));
      color: #fff;
      padding: 0.7em 1.8em;
      border: none;
      border-radius: 10px;
      font-weight: 700;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 10px var(--primary);
      transition: background 0.2s, box-shadow 0.22s;
      outline: none;
    }
    #comment-form button:hover { background: var(--primary);}
    .comments-list {
      margin-top: 0.7em;
      list-style: none;
      padding: 0;
      max-width: 650px;
      margin-left: auto;
      margin-right: auto;
    }
    .comments-list li {
      background: #13202eaa;
      border-radius: 12px;
      margin-bottom: 1.7em;
      padding: 1em 1.2em;
      color: var(--text);
      box-shadow: var(--shadow);
      border-left: 4px solid var(--primary);
      transition: box-shadow 0.15s;
    }
    .comments-list li:hover {
      box-shadow: 0 4px 20px #00fff744;
    }
    .comments-list .comment-author {
      font-weight: bold;
      color: var(--primary);
      margin-bottom: 0.2em;
    }
    .comments-list .comment-date {
      font-size: 0.93em;
      color: var(--accent);
      float: right;
    }
    .ir-comentarios {
      display:inline-block;
      margin:.7em auto 1.1em auto;
      padding:.7em 1.7em;
      background:linear-gradient(90deg,var(--primary),var(--accent));
      color:#fff;
      font-weight:700;
      border-radius:99px;
      border:none;
      font-size:1.06em;
      box-shadow:0 2px 18px #00fff744;
      cursor:pointer;
      transition:background .2s,scale .2s, box-shadow 0.22s;
      letter-spacing:1.1px;
      outline:none;
      text-shadow: var(--glow);
    }
    .ir-comentarios:hover {background:var(--primary); scale:1.03;}
    @media (max-width: 700px) {
      .hero, .acciones-box, .sumate-section, .public-comments-section {
        padding: 1.2em 0.6em;
      }
      .team-list li {
        flex-direction: column;
        padding: 1em 1em;
        gap: 0.7em;
      }
    }
    /* Floating buttons & WeerBot ... ya incluido arriba ... */
    /* ... Footer ... */
  </style>
</head>
<body>
  <!-- FONDO TECNOLÓGICO -->
  <div class="bg-futuristic">
    <canvas id="bg-futuristic-canvas"></canvas>
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
        <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 ..."/></svg>
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
    <section id="quienes">
      <h2>¿Quiénes somos?</h2>
      <ul class="team-list">
        <li>
          <div class="team-creator">Santiago Martinez</div>
          <span>Creador del proyecto</span>
        </li>
        <li>
          <div class="team-creator">Lucas De Cesare</div>
          <span>Creador del proyecto, desarrollador de la página y de la cripto WeerCoin para financiar el proyecto</span>
        </li>
      </ul>
      <p>
        Somos un equipo comprometido en crear soluciones tecnológicas y comunitarias para enfrentar los incendios forestales, especialmente en la Patagonia, una de las zonas más afectadas de Argentina.
      </p>
    </section>
    <section id="patagonia">
      <h2>¿Por qué Patagonia?</h2>
      <img src="https://upload.wikimedia.org/wikipedia/commons/8/85/Mapa_de_la_Patagonia.svg" class="mapa-patagonia" alt="Mapa de la Patagonia Argentina" loading="lazy"/>
      <p>
        La Patagonia es uno de los territorios más golpeados por incendios forestales en el país. Cada año, miles de hectáreas de bosque y vida silvestre se pierden, afectando a comunidades, turismo y biodiversidad. 
      </p>
      <p>
        Concientizar y actuar en esta región es clave para prevenir tragedias, proteger la naturaleza y asegurar un futuro sustentable.
      </p>
    </section>
    <section id="quehacemos">
      <h2>¿Qué hacemos?</h2>
      <p>
        Desarrollamos <strong>torres inteligentes</strong> y estrategias comunitarias para detectar incendios en etapas tempranas, enviar alertas a brigadas, municipios y vecinos, y facilitar la respuesta rápida.
      </p>
      <p>
        Además, promovemos la educación y la acción colectiva para prevenir incendios y minimizar impactos.
      </p>
    </section>
    <section class="acciones-box">
      <h3>¿Qué podés hacer vos para prevenir incendios?</h3>
      <ul>
        <li>Informate y compartí recomendaciones sobre el uso responsable del fuego.</li>
        <li>Participá en campañas y jornadas de concientización.</li>
        <li>Alertá a las autoridades ante cualquier columna de humo o situación sospechosa.</li>
        <li>No dejes basura ni vidrios en zonas naturales.</li>
        <li>Sumate a proyectos y movimientos ambientales.</li>
      </ul>
    </section>
    <section id="aliados">
      <h2>Ranking de aliados y apoyos</h2>
      <ul class="aliados-list">
        <li class="aliados-nuevo"><strong>¿Tu ONG, municipio o grupo?</strong> <br><span style="color:#fff;">Sumate desde la sección <a href="#sumate" style="color:var(--accent);">Sumate</a></span></li>
      </ul>
    </section>
    <section id="novedades">
      <h2>Novedades y próximos eventos</h2>
      <ul class="news-list">
        <li>Próximamente — Demo para presentar el proyecto en la UDESA</li>
      </ul>
    </section>
    <section id="sumate" class="sumate-section">
      <h2>Sumate a la campaña</h2>
      <p>
        Si querés colaborar, hacer una campaña publicitaria, sumar tu ONG o tu municipio, o simplemente recibir novedades, completá este formulario. ¡Te contactamos!
      </p>
      <form id="form-sumate" autocomplete="off">
        <label for="sumate-nombre">Nombre y apellido</label>
        <input type="text" id="sumate-nombre" maxlength="60" placeholder="Tu nombre completo" />
        <label for="sumate-email">Email de contacto <span style="color:var(--danger);">*</span></label>
        <input type="email" id="sumate-email" required maxlength="60" placeholder="tunombre@email.com" />
        <label for="sumate-tipo">¿Cómo querés sumarte?</label>
        <select id="sumate-tipo">
          <option value="Campaña publicitaria">Campaña publicitaria</option>
          <option value="ONG / Municipio">ONG / Municipio</option>
          <option value="Voluntario/a">Voluntario/a</option>
          <option value="Otro">Otro</option>
        </select>
        <label for="sumate-msg">Mensaje</label>
        <textarea id="sumate-msg" rows="3" maxlength="300" placeholder="Contanos tu idea o consulta"></textarea>
        <button type="submit">Enviar</button>
        <div id="sumate-estado"></div>
      </form>
      <div style="margin-top:1em;font-size:.98em;color:var(--muted);text-align:center;">
        Creadores: <span style="color:var(--primary)">Santiago Martinez</span> y <span style="color:var(--primary)">Lucas De Cesare</span> — <span style="color:var(--accent);">weerteck@gmail.com</span>
      </div>
    </section>
    <button class="ir-comentarios" onclick="document.getElementById('comentarios').scrollIntoView({behavior:'smooth'})">
      Ir a opiniones de la comunidad
    </button>
    <section class="public-comments-section" id="comentarios">
      <h2>Opiniones y recomendaciones</h2>
      <form id="comment-form">
        <input type="text" id="comment-author" placeholder="Tu nombre (opcional)" maxlength="40" autocomplete="off"/>
        <textarea id="comment-text" placeholder="Escribí tu comentario, opinión o recomendación..." rows="3" required maxlength="400"></textarea>
        <button type="submit">Publicar comentario</button>
      </form>
      <ul class="comments-list" id="comments-list"></ul>
      <div style="text-align:center;margin-top:1em;color:var(--accent);">
        También podés escribirnos por <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta%20o%20opinión" target="_blank" rel="noopener">WhatsApp</a> o <a href="https://instagram.com/weerteck" target="_blank" rel="noopener">Instagram</a>.
      </div>
    </section>
  </main>
  <div class="floating-btns">
    <a href="https://instagram.com/weerteck" class="btn-instagram-flotante" target="_blank" rel="noopener" title="Ir al Instagram de WeerTeck" aria-label="Ir al Instagram de WeerTeck">
      <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 ..."/></svg>
    </a>
    <button id="weerbot-button" class="btn-weerbot-flotante" title="Abrir WeerBot" aria-label="Abrir WeerBot">
      <svg viewBox="0 0 32 32" fill="none"><circle cx="16" cy="16" r="15" fill="#fff" stroke="#00fff7" stroke-width="2"/><ellipse cx="11.5" cy="14" rx="2" ry="2.2" fill="#00fff7"/><ellipse cx="20.5" cy="14" rx="2" ry="2.2" fill="#00fff7"/><rect x="11" y="19.2" width="10" height="2.2" rx="1.1" fill="#00d1ff"/><rect x="13" y="22.2" width="6" height="1.4" rx="0.7" fill="#00d1ff"/></svg>
    </button>
    <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta%20o%20recomendaci%C3%B3n" class="btn-whatsapp-flotante" target="_blank" rel="noopener" title="Escribinos por WhatsApp" aria-label="Escribinos por WhatsApp">
      <!-- ... icono WhatsApp ... -->
    </a>
  </div>
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

    // Comentarios públicos (localStorage)
    document.addEventListener('DOMContentLoaded', () => {
      const commentsList = document.getElementById('comments-list');
      function loadComments() {
        commentsList.innerHTML = '';
        let comments = [];
        try {
          comments = JSON.parse(localStorage.getItem('weer-comments') || '[]');
        } catch {}
        if (comments.length === 0) {
          commentsList.innerHTML = "<li style='text-align:center;color:var(--accent);'>Sé el primero en dejar tu comentario.</li>";
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

      // Formulario sumate
      const formSumate = document.getElementById('form-sumate');
      const estadoSumate = document.getElementById('sumate-estado');
      formSumate.addEventListener('submit', function(e){
        e.preventDefault();
        const nombre = document.getElementById('sumate-nombre').value.trim();
        const email = document.getElementById('sumate-email').value.trim();
        const tipo = document.getElementById('sumate-tipo').value;
        const msg = document.getElementById('sumate-msg').value.trim();
        if (!email || !/\S+@\S+\.\S+/.test(email)) {
          estadoSumate.innerHTML = "<div class='msg-error'>Poné un email válido.</div>";
          return;
        }
        estadoSumate.innerHTML = "<div class='msg-exito'>¡Gracias por sumarte! Nos contactaremos a la brevedad.</div>";
        formSumate.reset();
      });
    });

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

