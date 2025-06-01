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
      --primary: #5fd1f9;
      --accent: #4eb9e5;
      --secondary: #222934;
      --dark: #181b22;
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
    html, body { height:100%; }
    body {
      font-family: 'Poppins', sans-serif;
      min-height: 100vh;
      color: var(--text);
      background: #181b22;
      position: relative;
      overflow-x: hidden;
      margin: 0; padding: 0;
    }
    /* Fondo animado profesional */
    .bg-animated {
      position: fixed;
      top: 0; left: 0; width: 100vw; height: 100vh;
      z-index: 0;
      pointer-events: none;
      overflow: hidden;
      background: linear-gradient(120deg, #181b22 0%, #222938 100%);
    }
    .bg-grad {
      position: absolute;
      width: 100vw; height: 100vh;
      top: 0; left: 0;
      background: radial-gradient(ellipse 80% 70% at 60% 30%, #222a33 60%, #181b22 100%);
      opacity: 0.72;
    }
    .lines {
      position: absolute; width: 100vw; height: 100vh; top: 0; left: 0;
      overflow: hidden; pointer-events: none;
      z-index: 1;
    }
    .line {
      position: absolute;
      width: 1.2px;
      height: 120vh;
      background: linear-gradient(180deg, #2c3e50 0%, #5fd1f9 30%, #222 100%);
      opacity: 0.11;
      animation: moveLine 23s linear infinite;
      border-radius: 8px;
      filter: blur(0.2px);
    }
    @keyframes moveLine {
      0% {transform: translateY(-15vh);}
      100% {transform: translateY(12vh);}
    }
    .glow {
      position: absolute;
      width: 160vw; height: 100vh;
      left: -20vw; top: 0;
      background: radial-gradient(ellipse 55% 20% at 50% 30%, #5fd1f9 0%, #181b22 80%);
      opacity: 0.04;
      animation: glowmove 18s ease-in-out infinite alternate;
      z-index: 0;
    }
    @keyframes glowmove {
      0% {transform: translateY(-60px);}
      100% {transform: translateY(60px);}
    }
    main, nav, header, footer, .flotantes-columna, #chatbot-box {
      position: relative;
      z-index: 3;
    }
    /* CONTENIDO PRINCIPAL (todo igual que la última versión) */
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
      background: linear-gradient(100deg, #242d39 80%, #263248 100%);
      border-radius: 16px;
      box-shadow: 0 2px 28px #5fd1f933;
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
      text-shadow: 0 0 18px var(--primary), 0 0 6px #5fd1f988;
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
    main { max-width: 820px; width: 97%; margin: auto; padding-bottom: 2em; position:relative; z-index:2;}
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
      background: #212a35cc;
      border-radius: 9px;
      margin-bottom: 0.7em;
      padding: 0.5em 1em;
      color: var(--text);
      box-shadow: 0 2px 10px #5fd1f933;
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
      background: #242d39cc;
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
      background: #212a35cc;
      border-radius: 15px;
      padding: 1.7em 1em 1.6em 1em;
      box-shadow: 0 2px 20px #5fd1f944;
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
    .comments-counter {
      text-align: center;
      color: var(--accent);
      margin: 0 0 1.3em 0;
      font-size: 1.09em;
      letter-spacing: 1px;
      font-weight: 600;
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
      box-shadow: 0 2px 10px #5fd1f933;
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
  <!-- Fondo animado profesional -->
  <div class="bg-animated" aria-hidden="true">
    <div class="bg-grad"></div>
    <div class="glow"></div>
    <div class="lines"></div>
  </div>
  <!-- CONTENIDO PRINCIPAL: igual que antes... -->
  <!-- ... (tu nav, hero, main, secciones) ... -->
  <!-- ... (pega el contenido de la versión anterior aquí) ... -->
  <!-- ... (ver anterior para no repetir por límite de tokens) ... -->

  <!-- SONIDO DE NOTIFICACIÓN PARA WEERBOT -->
  <audio id="bot-sound" preload="auto">
    <source src="data:audio/wav;base64,UklGRiQAAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YZAAAAAAAgAAgAAAgAAgICAAkAAgACAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAIABgAIAAA==" type="audio/wav">
  </audio>
  <script>
    // Fondo animado líneas lentas y glow
    const linesContainer = document.querySelector('.lines');
    for(let i=0;i<18;i++){
      let line=document.createElement('div');
      line.className='line';
      line.style.left=(8+i*5.3)+'vw';
      line.style.height=(85+Math.random()*15)+'vh';
      line.style.animationDelay = (Math.random()*23)+'s';
      linesContainer.appendChild(line);
    }
    // SONIDO WeerBot: función para reproducir cuando el bot responde
    function playBotSound() {
      const audio = document.getElementById('bot-sound');
      if(audio) {
        audio.currentTime = 0;
        audio.volume = 0.18; // Sutil
        audio.play();
      }
    }
    // ---------
    // En tu función mostrarPasoWeerbot poné playBotSound() después de mostrar el mensaje del bot:
    // mensajes.innerHTML = `<div class="chatbot-message">${pasoInfo.mensaje}</div>`; playBotSound();
    // ---------
    // (El resto del JS es igual a lo que ya usabas para comentarios, formulario, etc)
  </script>
</body>
</html>
