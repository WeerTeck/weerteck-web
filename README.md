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
      --wa: #25d366;
      --wa-dark: #128c7e;
      --ig-grad1: #ed4264;
      --ig-grad2: #ffedbc;
      --bot-grad1: #00bcd4;
      --bot-grad2: #80deea;
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
    .flotantes-columna {
      position: fixed;
      bottom: 26px;
      right: 24px;
      display: flex;
      flex-direction: column;
      gap: 17px;
      z-index: 1050;
      align-items: flex-end;
    }
    .flotante-btn {
      border-radius: 50%;
      width: 56px; height: 56px;
      border: 2.5px solid #fff;
      box-shadow: 0 4px 22px #0007, 0 1px 12px #fff3;
      display: flex; justify-content: center; align-items: center;
      cursor: pointer;
      transition: background 0.2s, transform 0.2s, box-shadow 0.2s;
      animation: flotar 2.1s infinite alternate cubic-bezier(.6,0,.4,1);
      will-change: transform;
    }
    .flotante-btn svg { width: 32px; height: 32px; display: block;}
    .flotante-btn.whatsapp {
      background: linear-gradient(135deg, var(--wa) 60%, var(--wa-dark) 100%);
    }
    .flotante-btn.whatsapp:hover { background: var(--wa);}
    .flotante-btn.instagram {
      background: linear-gradient(135deg, var(--ig-grad1) 60%, var(--ig-grad2) 100%);
    }
    .flotante-btn.instagram:hover { background: var(--ig-grad1);}
    .flotante-btn.weerbot {
      background: linear-gradient(135deg, var(--bot-grad1) 70%, var(--bot-grad2) 100%);
    }
    .flotante-btn.weerbot:hover { background: var(--bot-grad2);}
    @keyframes flotar { to { transform: translateY(-8px) scale(1.05);} }
    #chatbot-box {
      display: none; position: fixed; bottom: 95px; right: 30px; width: 340px; max-width: 96vw;
      background: rgba(0, 188, 212, 0.99); border-radius: 20px; box-shadow: 0 8px 60px #00bcd4cc, 0 2px 16px #0008;
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
    @media (max-width: 560px) {
      #chatbot-box {
        right: 0; left: 0; width: 100vw; border-radius: 0; min-height: 60vh; max-height: 94vh;
      }
      .flotantes-columna { right:10px; bottom:10px; }
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
      <li><a href="#weercoin">WeerCoin</a></li>
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
        <li><strong>Lucas De Cesare</strong> — Creador del proyecto, programador y creador de la criptomoneda WeerCoin.</li>
        <li><strong>Santiago Martinez</strong> — Creador del proyecto.</li>
      </ul>
      <p>
        Somos dos jóvenes comprometidos en crear soluciones tecnológicas y comunitarias para enfrentar los incendios forestales, especialmente en la Patagonia, una de las zonas más afectadas de Argentina.
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
    <section id="weercoin">
      <h2>WeerCoin: nuestra criptomoneda para financiar las torres</h2>
      <p>
        Creamos <strong>WeerCoin</strong>, una criptomoneda pensada como herramienta de financiación colectiva para la instalación de torres inteligentes en la Patagonia y otras regiones de riesgo.
      </p>
      <ul>
        <li>Cualquier persona, ONG o municipio puede sumarse y aportar comprando WeerCoin.</li>
        <li>La recaudación se usará íntegramente para fabricar e instalar más torres de prevención de incendios.</li>
        <li>Transparencia total: vas a poder ver el avance del proyecto y el destino de los fondos.</li>
        <li>¡Próximamente más info y cómo participar!</li>
      </ul>
      <p style="font-size:0.98em;color:var(--accent);margin-top:0.7em;">
        ¿Querés ser de los primeros en enterarte? <a href="#sumate" style="color:var(--primary);">Sumate a la campaña</a> y te avisamos.
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
      <p style="color:var(--muted);margin:1.2em 0 0.8em 0;">No hay novedades ni eventos disponibles por el momento.</p>
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
          <option value="WeerCoin">Aportar con WeerCoin</option>
          <option value="Otro">Otro</option>
        </select>
        <label for="sumate-msg">Mensaje</label>
        <textarea id="sumate-msg" rows="3" maxlength="300" placeholder="Contanos tu idea o consulta"></textarea>
        <button type="submit">Enviar</button>
        <div id="sumate-estado"></div>
      </form>
      <div style="margin-top:1em;font-size:.98em;color:var(--muted);text-align:center;">
        Contacto: <span style="color:var(--accent);">weerteck@gmail.com</span>
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
  <div class="flotantes-columna">
    <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20más%20info" class="flotante-btn whatsapp" target="_blank" rel="noopener" aria-label="Contactar por WhatsApp">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M20.52 3.48A11.86 11.86 0 0 0 12 0C5.37 0 0 5.37 0 12a11.93 11.93 0 0 0 2.07 6.57L0 24l5.6-2.07A11.9 11.9 0 0 0 12 24c6.63 0 12-5.37 12-12a11.84 11.84 0 0 0-3.48-8.52zM12 21.4a9.4 9.4 0 0 1-4.78-1.41l-.34-.21-3.32 1.23 1.2-3.23-.22-.34A9.44 9.44 0 1 1 21.4 12a9.37 9.37 0 0 1-9.4 9.4zm5.32-7.21c-.29-.15-1.71-.84-1.97-.94-.26-.11-.45-.15-.64.15s-.74.94-.9 1.13c-.16.19-.32.21-.6.07a6.71 6.71 0 0 1-1.97-1.21 7.32 7.32 0 0 1-1.36-1.68c-.14-.25-.02-.38.11-.53.12-.12.26-.32.39-.48a.72.72 0 0 0 .11-.3.43.43 0 0 0-.06-.3c-.2-.45-.57-1.18-.8-1.6-.21-.4-.43-.34-.6-.34a1.36 1.36 0 0 0-.65.06c-.23.1-.89.86-.89 2.1s.91 2.43 1.03 2.6c.11.18 1.78 2.71 4.3 3.8a13.61 13.61 0 0 0 1.89.66c.8.27 1.53.23 2.11.14a6.69 6.69 0 0 0 2.03-.82 7.7 7.7 0 0 0 2.72-2.47 9.56 9.56 0 0 0-3.41-2.55z"/></svg>
    </a>
    <a href="https://instagram.com/weerteck" class="flotante-btn instagram" target="_blank" rel="noopener" title="Instagram WeerTeck" aria-label="Ir al Instagram de WeerTeck">
      <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.584.012 4.847.07 1.17.055 1.796.24 2.216.403a4.292 4.292 0 0 1 1.593.924c.443.444.73.973.924 1.593.163.42.348 1.046.403 2.216.058 1.263.07 1.646.07 4.847 0 3.2-.012 3.584-.07 4.847-.055 1.17-.24 1.796-.403 2.216a4.292 4.292 0 0 1-.924 1.593 4.292 4.292 0 0 1-1.593.924c-.42.163-1.046.348-2.216.403-1.263.058-1.646.07-4.847.07-3.2 0-3.584-.012-4.847-.07-1.17-.055-1.796-.24-2.216-.403a4.292 4.292 0 0 1-1.593-.924 4.292 4.292 0 0 1-.924-1.593c-.163-.42-.348-1.046-.403-2.216C2.212 15.631 2.2 15.247 2.2 12.047c0-3.2.012-3.584.07-4.847.055-1.17.24-1.796.403-2.216A4.292 4.292 0 0 1 3.597 3.39 4.292 4.292 0 0 1 5.19 2.466c.42-.163 1.046-.348 2.216-.403C8.416 2.212 8.8 2.2 12 2.2zm0-2.2C8.74 0 8.332.014 7.052.072 5.73.13 4.684.325 3.81.637a6.492 6.492 0 0 0-2.36 1.547A6.492 6.492 0 0 0 .637 4.19c-.312.874-.507 1.92-.565 3.242C.014 8.332 0 8.74 0 12c0 3.26.014 3.668.072 4.948.058 1.322.253 2.368.565 3.242a6.492 6.492 0 0 0 1.547 2.36 6.492 6.492 0 0 0 2.36 1.547c.874.312 1.92.507 3.242.565C8.332 23.986 8.74 24 12 24c3.26 0 3.668-.014 4.948-.072 1.322-.058 2.368-.253 3.242-.565a6.492 6.492 0 0 0 2.36-1.547 6.492 6.492 0 0 0 1.547-2.36c.312-.874.507-1.92.565-3.242.058-1.28.072-1.688.072-4.948s-.014-3.668-.072-4.948c-.058-1.322-.253-2.368-.565-3.242a6.492 6.492 0 0 0-1.547-2.36A6.492 6.492 0 0 0 20.19.637c-.874-.312-1.92-.507-3.242-.565C15.668.014 15.26 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zm0 10.162a3.999 3.999 0 1 1 0-7.998 3.999 3.999 0 0 1 0 7.998zm7.844-10.406a1.44 1.44 0 1 1-2.88 0 1.44 1.44 0 0 1 2.88 0z"/></svg>
    </a>
    <button id="chatbot-btn" class="flotante-btn weerbot" aria-label="Abrir chat con WeerBot" title="¿Necesitás ayuda?">
      <svg viewBox="0 0 32 32"><path d="M16 3C8.27 3 2 8.48 2 15c0 2.94 1.47 5.63 4 7.76V29a1 1 0 0 0 1.51.86l5.1-3.06c.42.05.85.08 1.39.08 7.73 0 14-5.48 14-12S23.73 3 16 3zm0 22c-.61 0-1.19-.04-1.77-.11a1 1 0 0 0-.62.13L7 27.13V24.7a1 1 0 0 0-.39-.79C4.44 21.95 3 18.63 3 15c0-5.52 5.82-10 13-10s13 4.48 13 10-5.82 10-13 10z"/></svg>
    </button>
  </div>
  <div id="chatbot-box" role="dialog" aria-modal="true" aria-label="Chatbot WeerBot">
    <div id="chatbot-header">
      <span>WeerBot 🤖</span>
      <button id="chatbot-close" aria-label="Cerrar chat">&times;</button>
    </div>
    <div id="chatbot-messages"></div>
    <form id="chatbot-input-box" autocomplete="off" style="flex-direction:column;gap:0.5em;display:none;">
      <select id="chatbot-select" class="chatbot-select"></select>
      <button id="chatbot-send" type="submit">Siguiente</button>
    </form>
  </div>
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

      // WeerBot (menú ramificado)
      const chatbotGuia = [
        {
          mensaje: "¿Sobre qué tema te gustaría saber más?",
          opciones: [
            { texto: "¿Qué hace WeerTeck?", siguiente: 1 },
            { texto: "¿Cómo ayudan las torres?", siguiente: 2 },
            { texto: "¿Dónde se instalan?", siguiente: 3 },
            { texto: "Quiero contactarlos", siguiente: "fin" }
          ]
        },
        {
          mensaje: "Desarrollamos torres que detectan incendios y avisan rápido a bomberos y vecinos.<br><br>¿Te gustaría saber cómo funcionan o cómo pedir una torre?",
          opciones: [
            { texto: "¿Cómo funciona la torre?", siguiente: 4 },
            { texto: "¿Cómo puedo pedir una torre?", siguiente: 5 },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        },
        {
          mensaje: "Las torres detectan humo y calor. Si hay peligro, envían alerta al instante.<br><br>¿Te gustaría saber quién recibe las alertas o cómo sumarte?",
          opciones: [
            { texto: "¿Quién recibe las alertas?", siguiente: 6 },
            { texto: "¿Cómo puedo sumarme?", siguiente: 5 },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        },
        {
          mensaje: "Las torres pueden instalarse en zonas verdes, campos, barrios y reservas.<br><br>¿Querés saber si tu zona es apta o cómo instalar una?",
          opciones: [
            { texto: "¿Mi zona es apta?", siguiente: 7 },
            { texto: "¿Cómo instalar una torre?", siguiente: 5 },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        },
        {
          mensaje: "La torre tiene sensores, panel solar y batería. Detecta humo y calor y avisa al celular.<br><br>¿Querés recibir asesoramiento personalizado?",
          opciones: [
            { texto: "Contactar a WeerTeck", siguiente: "fin" },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        },
        {
          mensaje: "¡Buenísimo! Te guiamos personalmente.<br><br>¿Preferís WhatsApp o email?",
          opciones: [
            { texto: "WhatsApp (respuesta más rápida)", siguiente: "fin" },
            { texto: "Email", siguiente: "fin-email" },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        },
        {
          mensaje: "Reciben la alerta los bomberos, brigadas municipales y vecinos registrados.<br><br>¿Querés sumarte o que te contactemos?",
          opciones: [
            { texto: "Quiero sumarme / recibir info", siguiente: 5 },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        },
        {
          mensaje: "Contactanos y vemos juntos si tu zona es apta para instalar una torre.<br><br>¿Querés que te asesoremos?",
          opciones: [
            { texto: "Sí, asesorame", siguiente: "fin" },
            { texto: "Volver al inicio", siguiente: 0 }
          ]
        }
      ];
      function mostrarPasoWeerbot(paso) {
        const box = document.getElementById('chatbot-box');
        const form = document.getElementById('chatbot-input-box');
        const select = document.getElementById('chatbot-select');
        const mensajes = document.getElementById('chatbot-messages');
        mensajes.innerHTML = '';
        form.style.display = 'block';
        if (paso === "fin") {
          mensajes.innerHTML = '<div class="chatbot-message">¡Perfecto! Escribinos directo por <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20más%20info" target="_blank" style="color:#00796b;font-weight:bold;">WhatsApp</a> para asesorarte y ayudarte en tu caso.<br><br>¡Te esperamos!</div>';
          form.style.display = 'none';
          return;
        }
        if (paso === "fin-email") {
          mensajes.innerHTML = '<div class="chatbot-message">¡Genial! Escribinos a <a href="mailto:weerteck@gmail.com" style="color:#00796b;font-weight:bold;">weerteck@gmail.com</a> y te asesoramos a la brevedad.</div>';
          form.style.display = 'none';
          return;
        }
        const pasoInfo = chatbotGuia[paso];
        mensajes.innerHTML = `<div class="chatbot-message">${pasoInfo.mensaje}</div>`;
        select.innerHTML = '';
        pasoInfo.opciones.forEach(function(op, i){
          const opt = document.createElement('option');
          opt.value = op.siguiente;
          opt.innerHTML = op.texto;
          if (i === 0) opt.selected = true;
          select.appendChild(opt);
        });
      }
      // WeerBot (menú ramificado)
      const chatbotBtn = document.getElementById('chatbot-btn');
      const chatbotBox = document.getElementById('chatbot-box');
      const chatbotClose = document.getElementById('chatbot-close');
      const chatbotForm = document.getElementById('chatbot-input-box');
      const chatbotSelect = document.getElementById('chatbot-select');
      let pasoActual = 0;
      chatbotBtn.addEventListener('click', () => {
        chatbotBox.classList.add('active');
        mostrarPasoWeerbot(0);
        chatbotSelect.focus();
        setTimeout(()=>{chatbotBox.scrollIntoView({behavior:"smooth",block:"center"});},20);
      });
      chatbotClose.addEventListener('click', () => {
        chatbotBox.classList.remove('active');
      });
      chatbotForm.addEventListener('submit', function(e) {
        e.preventDefault();
        const value = chatbotSelect.value;
        pasoActual = value;
        mostrarPasoWeerbot(value);
      });
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") chatbotBox.classList.remove('active');
      });
    });
  </script>
</body>
</html>
