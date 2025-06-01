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
      --success: #4caf50;
      --muted: #b0bec5;
    }
    * { box-sizing: border-box; margin: 0; padding: 0;}
    html { scroll-behavior: smooth;}
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, var(--dark) 60%, var(--secondary) 100%);
      color: var(--text);
      min-height: 100vh;
      line-height: 1.6;
      position: relative;
      overflow-x: hidden;
      display: flex; flex-direction: column;
    }
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
      background: linear-gradient(90deg,#ed4264,#ffedbc 80%);
      color: #262626; border: none; border-radius: 22px;
      padding: 7px 16px; font-weight: 700; font-size: 1em;
      cursor: pointer; box-shadow: 0 2px 8px #ed426455;
      display: flex; align-items: center; gap: 7px;
      transition: background 0.2s, scale 0.2s;
    }
    nav .nav-actions .btn-ig:hover {
      background: linear-gradient(90deg,#ffedbc,#ed4264 90%);
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
    .team-list, .aliados-list, .news-list { list-style: none; padding: 0; }
    .team-list li, .aliados-list li {
      background: #1a2733cc;
      border-radius: 9px;
      margin-bottom: 0.7em;
      padding: 0.5em 1em;
      color: var(--text);
      box-shadow: 0 2px 10px #00bcd433;
      display: flex; align-items: center; gap: 0.7em;
      border-left: 5px solid var(--primary);
    }
    .aliados-list { display:grid; grid-template-columns: repeat(auto-fit,minmax(210px,1fr)); gap:1em;}
    .aliados-list li { margin-bottom:0; }
    .aliados-nuevo {
      background: #4caf5044;
      border-left: 5px solid var(--success);
    }
    .news-list li {
      background: #222a36cc;
      border-radius: 7px;
      margin-bottom: 0.8em;
      padding: 0.7em 1em;
      color: var(--accent);
      border-left: 4px solid var(--accent);
      font-size: 1.02em;
    }
    .mapa-patagonia {
      width: 100%; max-width: 410px; margin: 1.2em auto 1.1em auto; display: block;
      border-radius: 12px; box-shadow: 0 2px 18px var(--primary);
      border: 2px solid var(--primary);
      filter: grayscale(0.15) brightness(0.93);
    }
    .acciones-box {
      background: linear-gradient(100deg,#263238bb 70%,var(--primary) 100%);
      border-radius: 14px;
      box-shadow: 0 2px 18px var(--primary);
      padding: 1.2em 1.5em;
      margin-bottom: 1.7em;
      border-left: 6px solid var(--primary);
    }
    .acciones-box ul { margin-top: 0.4em; margin-bottom: 0;}
    .acciones-box li { margin-bottom: 0.7em; color: var(--accent);}
    .sumate-section {
      background: #1a2733cc;
      border-radius: 15px;
      padding: 1.7em 1em 1.6em 1em;
      box-shadow: 0 2px 20px #00bcd444;
      border: 2px solid var(--primary);
      margin-bottom: 2.3em;
    }
    .sumate-section label { display: block; margin-bottom: 0.4em; color: var(--accent); font-weight: 600;}
    .sumate-section input, .sumate-section textarea, .sumate-section select {
      width: 100%; max-width: 420px;
      padding: 0.6em 1em;
      border-radius: 8px;
      border: 1px solid var(--accent);
      font-size: 1em;
      background: #e0f7fa;
      color: #222;
      margin-bottom: 1em;
    }
    .sumate-section button {
      background: linear-gradient(90deg, var(--primary), var(--accent));
      color: #fff;
      padding: 0.7em 2em;
      border: none;
      border-radius: 9px;
      font-weight: 700;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 8px var(--primary);
      transition: background 0.2s, scale 0.2s;
      margin-top: 0.2em;
    }
    .sumate-section button:hover { background: var(--primary); scale:1.04;}
    .msg-exito, .msg-error {
      text-align:center; font-weight:600; margin-bottom:1em; margin-top:0.1em;
      border-radius:8px; padding:0.6em 0;
    }
    .msg-exito { background: #4caf50cc; color: #fff;}
    .msg-error { background: #e57373cc; color: #fff;}
    .public-comments-section {
      background: linear-gradient(120deg, var(--primary) 60%, var(--accent) 40%, #2226);
      border-radius: 15px;
      padding: 2em 1em;
      box-shadow: 0 2px 32px var(--primary);
      border: 2px solid var(--primary);
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
      margin-bottom:2em;
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
      padding: 0.6em 1em;
      border-radius: 8px;
      border: 1px solid var(--accent);
      font-size: 1em;
      background: #e0f7fa;
      color: #222;
    }
    #comment-form button {
      background: linear-gradient(90deg, var(--primary), var(--accent));
      color: #fff;
      padding: 0.6em 1.5em;
      border: none;
      border-radius: 8px;
      font-weight: 700;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 8px var(--primary);
      transition: background 0.2s;
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
      background: #fff3;
      border-radius: 8px;
      margin-bottom: 1.2em;
      padding: 1em 1.2em;
      color: var(--text);
      box-shadow: 0 2px 10px #00bcd433;
      border-left: 4px solid var(--primary);
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
      padding:.6em 1.6em;
      background:linear-gradient(90deg,var(--primary),var(--accent));
      color:#fff;
      font-weight:700;
      border-radius:9px;
      border:none;
      font-size:1.06em;
      box-shadow:0 2px 8px var(--primary);
      cursor:pointer;
      transition:background .2s,scale .2s;
      letter-spacing:1px;
    }
    .ir-comentarios:hover {background:var(--primary); scale:1.03;}
    .btn-instagram-flotante {
      position: fixed; bottom: 32px; right: 28px;
      background: linear-gradient(135deg, #ed4264 60%, #ffedbc 100%);
      border-radius: 50%; width: 62px; height: 62px; box-shadow: 0 4px 24px #ed426466;
      display: flex; justify-content: center; align-items: center; cursor: pointer;
      z-index: 1050; border: 2.5px solid #fff;
      transition: background 0.3s, transform 0.3s;
      animation: flotar 2.2s infinite alternate cubic-bezier(.6,0,.4,1);
    }
    @keyframes flotar { to { transform: translateY(-10px) scale(1.07);} }
    .btn-instagram-flotante:hover { background: #ed4264; transform: scale(1.11) rotate(-8deg);}
    .btn-instagram-flotante svg { width: 37px; height: 37px; fill: #fff;}
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
    @media (max-width: 930px) { main { width: 99%;} }
    @media (max-width: 700px) {
      nav ul { gap: 0.3em; }
      .hero h1 { font-size:1.5em;}
      .aliados-list { grid-template-columns:1fr;}
    }
    @media (max-width: 520px) {
      nav, header, main, footer { font-size:0.97em;}
      .banner-revision { font-size:0.93em;}
      .hero { padding:1.2em 0.5em 1.1em 0.5em;}
      .btn-instagram-flotante { right:10px; bottom:12px;}
    }
  </style>
</head>
<body>
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
    <section id="quienes">
      <h2>¿Quiénes somos?</h2>
      <ul class="team-list">
        <li><strong>Lucas De Cesare</strong> — CEO y cofundador</li>
        <li><strong>Santiago Martinez</strong> — Cofundador</li>
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
        <li><strong>Municipio de San Isidro</strong> <span style="color:var(--success);font-weight:600;">(Próximo a sumarse)</span></li>
        <li><strong>EcoJóvenes ONG</strong></li>
        <li class="aliados-nuevo"><strong>¿Tu ONG, municipio o grupo?</strong> <br><span style="color:#fff;">Sumate desde la sección <a href="#sumate" style="color:var(--accent);">Sumate</a></span></li>
      </ul>
    </section>
    <section id="novedades">
      <h2>Novedades y próximos eventos</h2>
      <ul class="news-list">
        <li>01/06/2025 — Lanzamiento de la campaña "Patagonia sin fuego" 🚒</li>
        <li>18/05/2025 — Charla en UDESA sobre tecnología y prevención de incendios.</li>
        <li>10/05/2025 — Alianza con EcoJóvenes ONG para difusión digital.</li>
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
        CEO: Lucas De Cesare — <span style="color:var(--accent);">weerteck@gmail.com</span>
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
  <a href="https://instagram.com/weerteck" class="btn-instagram-flotante" target="_blank" rel="noopener" title="Ir al Instagram de WeerTeck" aria-label="Ir al Instagram de WeerTeck">
    <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 1.17.055 1.796.24 2.216.403a4.292 4.292 0 0 1 1.593.924c.443.444.73.973.924 1.593.163.42.348 1.046.403 2.216.058 1.263.07 1.646.07 4.847 0 3.2-.012 3.584-.07 4.847-.055 1.17-.24 1.796-.403 2.216a4.292 4.292 0 0 1-.924 1.593 4.292 4.292 0 0 1-1.593.924c-.42.163-1.046.348-2.216.403-1.263.058-1.646.07-4.847.07-3.2 0-3.584-.012-4.847-.07-1.17-.055-1.796-.24-2.216-.403a4.292 4.292 0 0 1-1.593-.924 4.292 4.292 0 0 1-.924-1.593c-.163-.42-.348-1.046-.403-2.216C2.212 15.631 2.2 15.247 2.2 12.047c0-3.2.012-3.584.07-4.847.055-1.17.24-1.796.403-2.216A4.292 4.292 0 0 1 3.597 3.39 4.292 4.292 0 0 1 5.19 2.466c.42-.163 1.046-.348 2.216-.403C8.416 2.212 8.8 2.2 12 2.2zm0-2.2C8.74 0 8.332.014 7.052.072 5.73.13 4.684.325 3.81.637a6.492 6.492 0 0 0-2.36 1.547A6.492 6.492 0 0 0 .637 4.19c-.312.874-.507 1.92-.565 3.242C.014 8.332 0 8.74 0 12c0 3.26.014 3.668.072 4.948.058 1.322.253 2.368.565 3.242a6.492 6.492 0 0 0 1.547 2.36 6.492 6.492 0 0 0 2.36 1.547c.874.312 1.92.507 3.242.565C8.332 23.986 8.74 24 12 24c3.26 0 3.668-.014 4.948-.072 1.322-.058 2.368-.253 3.242-.565a6.492 6.492 0 0 0 2.36-1.547 6.492 6.492 0 0 0 1.547-2.36c.312-.874.507-1.92.565-3.242.058-1.28.072-1.688.072-4.948s-.014-3.668-.072-4.948c-.058-1.322-.253-2.368-.565-3.242a6.492 6.492 0 0 0-1.547-2.36A6.492 6.492 0 0 0 20.19.637c-.874-.312-1.92-.507-3.242-.565C15.668.014 15.26 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zm0 10.162a3.999 3.999 0 1 1 0-7.998 3.999 3.999 0 0 1 0 7.998zm7.844-10.406a1.44 1.44 0 1 1-2.88 0 1.44 1.44 0 0 1 2.88 0z"/></svg>
  </a>
  <footer>
    <div class="footer-links">
      <a href="#top">↑ Volver arriba</a>
      <a href="mailto:weerteck@gmail.com">Contacto</a>
      <a href="https://instagram.com/weerteck" target="_blank" rel="noopener">Instagram</a>
    </div>
    <div>
      &copy; 2025 WeerTeck — Todos los derechos reservados<br>
      <span style="font-size:.93em;color:var(--accent);">Página en revisión y mejora continua.</span>
    </div>
  </footer>
  <script>
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
  </script>
</body>
</html>
