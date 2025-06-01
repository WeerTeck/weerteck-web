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
    /* ----------- Mini Chat Encuesta ----------- */
    .floating-btns {
      position: fixed;
      bottom: 22px;
      right: 10px;
      z-index: 9999;
      display: flex;
      flex-direction: column;
      gap: 13px;
      align-items: flex-end;
      pointer-events: none;
    }
    .floating-btns > * { pointer-events: auto; }
    .btn-floating {
      background: #fff;
      box-shadow: 0 2px 18px #00fff744;
      border-radius: 50%;
      width: 44px;
      height: 44px;
      display: flex; align-items: center; justify-content: center;
      border: 2px solid #00fff7;
      transition: box-shadow 0.18s, border-color 0.18s, transform 0.14s;
      cursor: pointer; outline: none;
    }
    .btn-floating:hover, .btn-floating:focus {
      box-shadow: 0 0 20px #00fff7cc;
      border-color: #00d1ff;
      transform: scale(1.11);
    }
    .btn-instagram svg { filter: none; }
    .btn-whatsapp svg  { filter: none; }
    .btn-weerbot svg   { filter: drop-shadow(0 0 12px #00fff7cc); }
    .weerbot-chat.mini {
      width: 220px;
      min-width: 170px;
      right: 12px;
      bottom: 78px;
      border-radius: 13px;
      box-shadow: 0 2px 16px #00fff755;
      font-size: 0.98em;
      display: none;
      position: fixed;
      z-index: 12000;
      background: #11202aea;
      overflow: hidden;
      border: 2px solid #00fff7;
      animation: slideInBot 0.18s cubic-bezier(.7,1.4,.8,.94);
      font-family: 'Poppins', sans-serif;
    }
    @keyframes slideInBot {
      0% { transform: translateY(72px) scale(0.93); opacity:0; }
      100%{ transform: translateY(0) scale(1); opacity:1; }
    }
    .weerbot-chat-header {
      background: linear-gradient(90deg,#00fff7 0%,#00d1ff 100%);
      color: #232e3a;
      font-weight: 800;
      font-size: 0.97em;
      padding: 0.4em 0.7em;
      border-radius: 13px 13px 0 0;
      display: flex; justify-content: space-between; align-items: center;
    }
    .weerbot-chat-header button {
      background: none;
      border: none;
      color: #232e3a;
      font-size: 1.22em;
      cursor: pointer;
      font-weight: bold;
      transition: color .16s;
      padding: 0 8px;
    }
    .weerbot-chat-header button:hover { color: #e57373;}
    .weerbot-chat-messages {
      max-height: 75px;
      min-height: 32px;
      padding: .6em .6em .25em .6em;
      font-size: .94em;
      gap: .23em;
      background: #0e1825e6;
      color: #e0e0e0;
      display: flex;
      flex-direction: column;
    }
    .weerbot-chat-bubble {
      padding: .39em .7em;
      font-size: 1em;
      border-radius: 10px 10px 10px 4px;
      margin-bottom: .13em;
      background: #00fff722;
      color: #00fff7;
      font-weight: 600;
      box-shadow: 0 2px 8px #00fff744;
      word-break: break-word;
    }
    .weerbot-chat-options {
      padding: .45em .55em .7em .55em;
      display: flex;
      flex-direction: column;
      gap: 0.29em;
      background: #11202af6;
    }
    .real-btn {
      background: linear-gradient(90deg,#00fff7,#00d1ff 90%);
      color: #232e3a;
      border: none;
      border-radius: 6px;
      font-weight: 600;
      font-size: .98em;
      cursor: pointer;
      display: flex; align-items: center; justify-content: center;
      gap: 7px;
      box-shadow: 0 1.5px 8px #00fff733;
      padding: .45em .7em;
      margin-bottom: 0;
      transition: background 0.13s, box-shadow 0.13s, transform 0.11s;
      outline: none;
    }
    .real-btn:hover, .real-btn:focus {
      background: linear-gradient(90deg,#00d1ff,#00fff7 90%);
      box-shadow: 0 0 12px #00fff7aa;
      transform: scale(1.055);
      color: #18283b;
    }
    .real-btn-close {
      background: #e57373;
      color: #fff;
      margin-top: 0.12em;
    }
    .real-btn-close:hover, .real-btn-close:focus {
      background: #c62828;
      color: #fff;
    }
    @media (max-width:390px) {
      .weerbot-chat.mini { width: 97vw !important; right: 1vw; }
    }
    /* ----------- Footer ----------- */
    footer {
      background: linear-gradient(90deg, #18283b, #0a1018 90%);
      text-align: center;
      font-size: 1.09rem;
      color: var(--muted);
      padding: 1.5rem 0 4.5rem 0;
      border-top: 2px solid var(--primary);
      letter-spacing: 1px;
      margin-top: auto;
      box-shadow: 0 -4px 18px var(--primary);
      border-radius: 20px 20px 0 0;
    }
    .footer-links { margin: 0.5em auto 1em auto;}
    .footer-links a {
      color: var(--primary);
      font-weight: 600;
      border-radius: 8px;
      padding: 4px 12px;
      transition: background 0.13s, color 0.13s;
      margin: 0 1.5em;
      text-decoration: none;
    }
    .footer-links a:hover, .footer-links a:focus {
      background: var(--primary);
      color: #232e3a;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <!-- ...contenido principal igual que antes... -->
  <!-- ...main, header, etc... -->
  <!-- Botones flotantes actualizados -->
  <div class="floating-btns">
    <a href="https://instagram.com/weerteck" class="btn-floating btn-instagram" target="_blank" aria-label="Instagram WeerTeck">
      <svg width="32" height="32" viewBox="0 0 32 32" fill="none"><rect width="32" height="32" rx="8" fill="#fff"/><path d="M22.222 7.889a3.11 3.11 0 0 1 3.111 3.111v9.999a3.11 3.11 0 0 1-3.111 3.111h-9.999a3.11 3.11 0 0 1-3.111-3.111v-9.999a3.11 3.11 0 0 1 3.111-3.111h9.999zm-4.999 3.111a4.889 4.889 0 1 0 0 9.778 4.889 4.889 0 0 0 0-9.778zm0 1.333a3.556 3.556 0 1 1 0 7.111 3.556 3.556 0 0 1 0-7.111zm5.555-1.222a1.111 1.111 0 1 0 0 2.222 1.111 1.111 0 0 0 0-2.222z" fill="#E1306C"/></svg>
    </a>
    <button id="weerbot-button" class="btn-floating btn-weerbot" title="Abrir WeerBot" aria-label="Abrir WeerBot">
      <svg width="32" height="32" viewBox="0 0 32 32" fill="none"><rect width="32" height="32" rx="8" fill="#fff"/><ellipse cx="16" cy="15" rx="5" ry="5.5" fill="#00fff7"/><ellipse cx="13.5" cy="14.5" rx="1.2" ry="1.5" fill="#232e3a"/><ellipse cx="18.5" cy="14.5" rx="1.2" ry="1.5" fill="#232e3a"/><rect x="13" y="18" width="6" height="1.7" rx="0.85" fill="#00d1ff"/></svg>
    </button>
    <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta" class="btn-floating btn-whatsapp" target="_blank" aria-label="WhatsApp WeerTeck">
      <svg width="32" height="32" viewBox="0 0 32 32" fill="none"><rect width="32" height="32" rx="8" fill="#fff"/><path fill="#25D366" d="M16 6.67A9.32 9.32 0 0 0 6.67 16c0 1.54.38 3.02 1.12 4.34L6 26l5.8-1.53A9.29 9.29 0 0 0 16 25.34c5.13 0 9.33-4.2 9.33-9.34S21.13 6.67 16 6.67zm0 16.67c-1.37 0-2.71-.36-3.88-1.06l-.28-.16-3.44.91.92-3.35-.18-.28A7.68 7.68 0 0 1 8.33 16a7.66 7.66 0 1 1 7.67 7.34zm4.2-5.54c-.23-.11-1.37-.67-1.58-.74-.21-.08-.36-.11-.5.11-.15.21-.57.74-.7.89-.13.15-.25.17-.46.06a6.29 6.29 0 0 1-1.85-1.14 6.98 6.98 0 0 1-1.29-1.59c-.13-.22-.01-.34.1-.45.11-.11.24-.29.36-.43.12-.14.16-.25.24-.42.08-.17.04-.32-.02-.44-.06-.11-.5-1.21-.68-1.66-.18-.44-.37-.38-.5-.39-.13 0-.28-.01-.44-.01-.15 0-.4.06-.61.29-.21.24-.8.79-.8 1.93 0 1.13.82 2.23.93 2.38.11.15 1.62 2.49 4.06 3.39.57.2 1 .32 1.34.41.56.14 1.07.12 1.47.07.45-.07 1.37-.56 1.56-1.1.19-.54.19-1 .14-1.1z"/></svg>
    </a>
  </div>
  <div id="weerbot-chat" class="weerbot-chat mini">
    <div class="weerbot-chat-header">
      <span>🤖 WeerBot</span>
      <button id="weerbot-close" title="Cerrar Chat" aria-label="Cerrar Chat">&times;</button>
    </div>
    <div id="weerbot-messages" class="weerbot-chat-messages"></div>
    <div id="weerbot-options" class="weerbot-chat-options"></div>
  </div>
  <!-- ...footer igual que antes... -->
  <script>
    // Mini WeerBot tipo encuesta RAMIFICADA
    (() => {
      const weerbotBtn = document.getElementById('weerbot-button');
      const weerbotChat = document.getElementById('weerbot-chat');
      const weerbotClose = document.getElementById('weerbot-close');
      const weerbotMsgs = document.getElementById('weerbot-messages');
      const weerbotOptions = document.getElementById('weerbot-options');
      let closed = false;

      // Estructura ramificada de encuestas
      const flow = {
        start: {
          msg: "¡Hola! ¿Sobre qué te gustaría contactarnos?",
          options: [
            { label: "Quiero colaborar", next: "colaborar" },
            { label: "Tengo una duda", next: "duda" },
            { label: "Sugerir campaña", next: "campania" },
            { label: "Sumar mi ONG o municipio", next: "ong" },
            { label: "Recibir novedades", next: "novedades" }
          ]
        },
        colaborar: {
          msg: "¿Cómo querés colaborar?",
          options: [
            { label: "Como voluntario/a", next: "voluntario" },
            { label: "Difusión en redes", next: "difusion" },
            { label: "Aportar fondos", next: "fondos" },
            { label: "Otra forma", next: "otra" }
          ]
        },
        voluntario: {
          msg: "¿En qué área te gustaría ayudar?",
          options: [
            { label: "Campo/brigadista", next: "contacto" },
            { label: "Educación/charlas", next: "contacto" },
            { label: "Tecnología", next: "contacto" },
            { label: "Otra tarea", next: "contacto" }
          ]
        },
        difusion: {
          msg: "¿En qué plataforma pensás difundir?",
          options: [
            { label: "Instagram", next: "contacto" },
            { label: "Facebook", next: "contacto" },
            { label: "Otra", next: "contacto" }
          ]
        },
        fondos: {
          msg: "¿Querés información para aportar fondos?",
          options: [
            { label: "Sí, por WhatsApp", next: "contacto" },
            { label: "Sí, por email", next: "contacto" }
          ]
        },
        otra: {
          msg: "¡Contanos tu propuesta! ¿Preferís WhatsApp o Email?",
          options: [
            { label: "WhatsApp", next: "contacto" },
            { label: "Email", next: "contacto" }
          ]
        },
        duda: {
          msg: "¿Sobre qué tema es tu duda?",
          options: [
            { label: "Prevención de incendios", next: "contacto" },
            { label: "El proyecto", next: "contacto" },
            { label: "WeerCoin", next: "contacto" },
            { label: "Otro", next: "contacto" }
          ]
        },
        campania: {
          msg: "¿En qué ámbito querés sugerir la campaña?",
          options: [
            { label: "Escuelas", next: "contacto" },
            { label: "Redes sociales", next: "contacto" },
            { label: "Municipios", next: "contacto" },
            { label: "Otro", next: "contacto" }
          ]
        },
        ong: {
          msg: "¿Qué tipo de organización sos?",
          options: [
            { label: "ONG ambiental", next: "contacto" },
            { label: "Municipio", next: "contacto" },
            { label: "Grupo barrial", next: "contacto" },
            { label: "Otro", next: "contacto" }
          ]
        },
        novedades: {
          msg: "¿Querés recibir novedades por WhatsApp o Email?",
          options: [
            { label: "WhatsApp", next: "contacto" },
            { label: "Email", next: "contacto" }
          ]
        },
        contacto: {
          msg: `<b>¡Gracias por tu interés!</b><br>
            <span style="font-size:1.07em">Contactanos directo:</span><br>
            <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20quiero%20sumarme%20al%20proyecto" target="_blank" style="color:var(--accent);font-weight:600;text-decoration:underline;margin-right:10px;">
            WhatsApp</a> o
            <a href="mailto:weerteck@gmail.com" style="color:var(--accent);font-weight:600;text-decoration:underline;">
            Email</a>
            <br><br><span style="font-size:.95em;color:var(--muted);">¡Te esperamos!</span>`,
          options: [
            { label: "Volver al inicio", next: "start" },
            { label: "Cerrar chat", close: true }
          ]
        }
      };

      function showStep(key) {
        weerbotMsgs.innerHTML = `<div class="weerbot-chat-bubble bot">${flow[key].msg}</div>`;
        weerbotOptions.innerHTML = "";
        flow[key].options.forEach(opt => {
          const btn = document.createElement("button");
          btn.className = opt.close ? "real-btn real-btn-close" : "real-btn";
          btn.innerHTML = `<span>${opt.label}</span>`;
          btn.onclick = () => {
            if (opt.close) {
              weerbotChat.style.display = "none"; closed = true;
            }
            else showStep(opt.next);
          };
          weerbotOptions.appendChild(btn);
        });
      }

      weerbotBtn.addEventListener("click", () => {
        if (closed) closed = false;
        weerbotChat.style.display = "block";
        showStep("start");
        setTimeout(() => { weerbotMsgs.scrollTop = weerbotMsgs.scrollHeight; }, 60);
      });
      weerbotClose.addEventListener("click", () => {
        weerbotChat.style.display = "none";
        closed = true;
      });
    })();
  </script>
</body>
</html>
