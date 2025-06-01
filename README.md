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
      --shadow: 0 4px 32px 0 #00bcd433;
      --radius: 18px;
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
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      height: 58px;
      z-index: 2002;
      background: rgba(18, 26, 35, 0.95);
      border-bottom: 2px solid var(--primary);
      box-shadow: 0 2px 16px #00bcd433;
      border-radius: 0 0 18px 18px;
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
      filter: drop-shadow(0 0 8px #00bcd477);
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
      padding: 7px 15px;
      border-radius: 8px;
      transition: background 0.18s, color 0.18s, box-shadow 0.13s;
    }
    nav ul li a:hover, nav ul li a:focus {
      background: linear-gradient(90deg,var(--accent) 30%,var(--primary));
      color: #fff;
      box-shadow: 0 0 8px var(--primary);
    }
    nav ul li a:focus {
      box-shadow: 0 0 0 3px #00bcd499;
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
      background: linear-gradient(120deg, #232b38 90%, #00bcd410);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      margin: 1.6em auto 1.3em auto;
      max-width: 750px;
      padding: 2.3em 1.5em 2em 1.5em;
      position: relative;
      z-index: 2;
      border: 2px solid var(--primary);
      transition: box-shadow 0.22s, background 0.3s;
    }
    .hero:hover {
      box-shadow: 0 8px 36px 0 #00bcd455;
      background: linear-gradient(120deg, #263445 80%, #00bcd420);
    }
    .hero h1 {
      font-weight: 900;
      font-size: 2.7rem;
      color: var(--primary);
      text-shadow: 0 0 18px var(--primary), 0 0 6px #00bcd466;
      letter-spacing: 2px;
      background: linear-gradient(90deg,var(--primary), var(--accent) 80%,#fff0);
      background-clip: text; -webkit-background-clip: text;
      color: transparent; -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 30px var(--primary));
      margin-bottom: 0.5rem;
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
      border-radius: 99px;
      font-size: 1.04em;
      box-shadow: 0 2px 16px #00bcd422;
      transition: background 0.2s, scale 0.2s, box-shadow 0.22s;
      cursor: pointer;
      letter-spacing: 1px;
      outline: none;
    }
    .hero .cta:hover { background: linear-gradient(90deg,var(--accent),var(--primary) 70%); scale:1.06;}
    .hero .cta:focus-visible { box-shadow: 0 0 0 4px #00bcd4aa; }
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
    section {
      margin-bottom: 2.8em;
      padding: 1.2em 0.7em;
    }
    h1, h2, h3 {
      letter-spacing: 1.2px;
      font-weight: 800;
      margin-bottom: 0.2em;
    }
    h1 {
      font-size: 2.7rem;
      margin-bottom: 0.5em;
    }
    h2 {
      color: var(--primary);
      font-size: 1.55em;
      margin-bottom: 0.6em;
      text-shadow: 0 0 6px var(--primary);
    }
    h3 {
      color: var(--accent);
      margin-bottom: 0.3em;
      font-size: 1.08em;
    }
    p { font-size: 1.06rem; margin-bottom: 1.1em;}
    .team-list, .aliados-list, .news-list { list-style: none; padding: 0; }
    .team-list li {
      background: linear-gradient(90deg, #202a33 95%, #80deea22);
      border-radius: var(--radius);
      margin-bottom: 1.2em;
      padding: 1em 2em;
      color: var(--text);
      box-shadow: var(--shadow);
      display: flex; align-items: center; gap: 1.5em;
      border-left: 6px solid var(--primary);
      flex-direction: row;
      transition: box-shadow 0.22s, background 0.3s;
    }
    .team-list li:hover {
      box-shadow: 0 8px 36px #00bcd455;
      background: linear-gradient(90deg, #17343e 90%, #80deea22);
    }
    .team-list .team-creator {
      color: var(--primary);
      font-weight: 700;
      font-size: 1.13em;
      margin-bottom: 0.2em;
    }
    .aliados-list { display:grid; grid-template-columns: repeat(auto-fit,minmax(210px,1fr)); gap:1em;}
    .aliados-list li {
      background: linear-gradient(90deg, #1a2332 60%, #00bcd410 100%);
      border-radius: var(--radius);
      margin-bottom:0;
      border-left: 5px solid var(--accent);
      box-shadow: var(--shadow);
      transition: box-shadow 0.22s;
    }
    .aliados-list li:hover { box-shadow: 0 8px 36px #00bcd455; }
    .aliados-nuevo {
      background: #4caf5044;
      border-left: 5px solid var(--success);
    }
    .news-list li {
      background: linear-gradient(90deg, #222a36cc 80%, #00bcd410 100%);
      border-radius: var(--radius);
      margin-bottom: 0.8em;
      padding: 0.7em 1em;
      color: var(--accent);
      border-left: 4px solid var(--accent);
      font-size: 1.02em;
      box-shadow: var(--shadow);
      transition: box-shadow 0.22s;
    }
    .news-list li:hover { box-shadow: 0 8px 36px #00bcd455; }
    .mapa-patagonia {
      width: 100%; max-width: 410px; margin: 1.2em auto 1.1em auto; display: block;
      border-radius: 12px; box-shadow: 0 2px 18px var(--primary);
      border: 2px solid var(--primary);
      filter: grayscale(0.15) brightness(0.93);
    }
    .acciones-box {
      background: linear-gradient(100deg,#263238bb 70%,var(--primary) 100%);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 1.2em 1.5em;
      margin-bottom: 1.7em;
      border-left: 6px solid var(--primary);
      transition: box-shadow 0.22s, background 0.3s;
    }
    .acciones-box:hover {
      box-shadow: 0 8px 36px #00bcd455;
      background: linear-gradient(120deg, #263445 80%, #00bcd420);
    }
    .acciones-box ul { margin-top: 0.4em; margin-bottom: 0;}
    .acciones-box li { margin-bottom: 0.7em; color: var(--accent);}
    .sumate-section {
      background: linear-gradient(120deg, #232b38 90%, #00bcd410);
      border-radius: var(--radius);
      padding: 1.7em 1em 1.6em 1em;
      box-shadow: var(--shadow);
      border: 2px solid var(--primary);
      margin-bottom: 2.3em;
      transition: box-shadow 0.22s, background 0.3s;
    }
    .sumate-section:hover {
      box-shadow: 0 8px 36px #00bcd455;
      background: linear-gradient(120deg, #263445 80%, #00bcd420);
    }
    .sumate-section label { display: block; margin-bottom: 0.4em; color: var(--accent); font-weight: 600;}
    .sumate-section input, .sumate-section textarea, .sumate-section select {
      width: 100%; max-width: 420px;
      padding: 0.65em 1.1em;
      border-radius: 10px;
      border: 1.5px solid var(--accent);
      font-size: 1em;
      background: #e0f7fa;
      color: #232b38;
      margin-bottom: 1em;
      transition: border-color 0.18s, box-shadow 0.18s;
    }
    .sumate-section input:focus, .sumate-section textarea:focus, .sumate-section select:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 2px #00bcd466;
      outline: none;
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
      transition: background 0.2s, scale 0.2s, box-shadow 0.22s;
      margin-top: 0.2em;
      outline: none;
    }
    .sumate-section button:hover { background: var(--primary); scale:1.04;}
    .sumate-section button:focus-visible { box-shadow: 0 0 0 4px #00bcd4aa; }
    .msg-exito, .msg-error {
      text-align:center; font-weight:600; margin-bottom:1em; margin-top:0.1em;
      border-radius:8px; padding:0.6em 0;
    }
    .msg-exito { background: #4caf50cc; color: #fff;}
    .msg-error { background: #e57373cc; color: #fff;}
    .public-comments-section {
      background: linear-gradient(120deg, var(--primary) 60%, var(--accent) 40%, #2226);
      border-radius: var(--radius);
      padding: 2em 1em;
      box-shadow: var(--shadow);
      border: 2px solid var(--primary);
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
      margin-bottom:2em;
      transition: box-shadow 0.22s, background 0.3s;
    }
    .public-comments-section:hover {
      box-shadow: 0 8px 36px #00bcd455;
      background: linear-gradient(120deg, var(--primary) 40%, var(--accent) 60%, #2226);
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
      padding: 0.65em 1.1em;
      border-radius: 10px;
      border: 1.5px solid var(--accent);
      font-size: 1em;
      background: #e0f7fa;
      color: #232b38;
      transition: border-color 0.18s, box-shadow 0.18s;
    }
    #comment-form input:focus, #comment-form textarea:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 2px #00bcd466;
      outline: none;
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
      transition: background 0.2s, box-shadow 0.22s;
      outline: none;
    }
    #comment-form button:hover { background: var(--primary);}
    #comment-form button:focus-visible { box-shadow: 0 0 0 4px #00bcd4aa; }
    .comments-list {
      margin-top: 0.7em;
      list-style: none;
      padding: 0;
      max-width: 650px;
      margin-left: auto;
      margin-right: auto;
    }
    .comments-list li {
      background: #21303f88;
      border-radius: 11px;
      margin-bottom: 1.7em;
      padding: 1em 1.2em;
      color: var(--text);
      box-shadow: var(--shadow);
      border-left: 4px solid var(--primary);
      transition: box-shadow 0.15s;
    }
    .comments-list li:hover {
      box-shadow: 0 4px 20px #00bcd455;
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
      border-radius:99px;
      border:none;
      font-size:1.06em;
      box-shadow:0 2px 16px #00bcd422;
      cursor:pointer;
      transition:background .2s,scale .2s, box-shadow 0.22s;
      letter-spacing:1px;
      outline:none;
    }
    .ir-comentarios:hover {background:var(--primary); scale:1.03;}
    .ir-comentarios:focus-visible { box-shadow: 0 0 0 4px #00bcd4aa; }
    /* Botones flotantes: uno arriba del otro */
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
      box-shadow: 0 6px 32px #00bcd455;
      background: linear-gradient(135deg, var(--primary), var(--accent) 70%);
      outline: none;
    }
    .btn-instagram-flotante:hover { background: #00bcd4; transform: scale(1.11) rotate(-8deg);}
    .btn-whatsapp-flotante:hover { background: #00bcd4; transform: scale(1.11) rotate(8deg);}
    .btn-weerbot-flotante:hover { background: #00bcd4; transform: scale(1.11);}
    .btn-instagram-flotante:focus,
    .btn-whatsapp-flotante:focus,
    .btn-weerbot-flotante:focus {
      outline: 2.5px solid var(--accent);
      box-shadow: 0 0 0 4px #80deea88;
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
    /* Footer y links */
    footer {
      text-align: center;
      font-size: 1.09rem;
      color: var(--muted);
      padding: 1.5rem 0 2.5rem 0;
      border-top: 2px solid var(--primary);
      background: linear-gradient(90deg, #23243e, #0f2027);
      letter-spacing: 1px;
      margin-top: auto;
      box-shadow: 0 -4px 18px var(--primary);
      border-radius: 20px 20px 0 0;
    }
    .footer-links { margin: 0.5em auto 1em auto;}
    .footer-links a {
      color: var(--primary);
      font-weight: 600;
      border-radius: 6px;
      padding: 3px 10px;
      transition: background 0.13s, color 0.13s;
      margin: 0 1.5em;
      text-decoration: none;
    }
    .footer-links a:hover, .footer-links a:focus {
      background: var(--primary);
      color: #fff;
      text-decoration: none;
    }
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
