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
      background: linear-gradient(90deg,#00bcd4,#80deea,#fff0);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
      animation: navLogoHue 3s linear infinite alternate;
      display: flex;
      align-items: center;
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
      background: linear-gradient(90deg,#00bcd4,#80deea);
      color: #fff; border: none; border-radius: 18px;
      padding: 6px 14px; font-weight: 700; cursor: pointer; box-shadow: 0 2px 8px #00bcd4aa;
      transition: background 0.2s, box-shadow 0.2s, scale 0.2s;
      letter-spacing: 0.5px;
    }
    nav .nav-actions button:hover {
      background: linear-gradient(90deg,#80deea,#00bcd4 60%);
      box-shadow: 0 0 16px #00bcd4cc;
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
      background: linear-gradient(90deg,#00bcd4,#80deea 80%,#fff0);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 30px #00bcd4cc);
    }
    .subtitulo {
      font-weight: 600; font-size: 1.3rem; color: #80deea;
      margin-bottom: 3rem;
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
    main:after {
      content: "";
      display:block;
      width: 100%;
      height: 4px;
      background: linear-gradient(90deg, #00bcd4 20%, #80deea 70%, transparent);
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
      box-shadow: 0 -3px 18px #00bcd4aa;
      border-top: 1.5px solid #00bcd4cc;
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
      filter: drop-shadow(0 0 18px #00bcd4aa);
    }
    .contador:hover { box-shadow: 0 0 30px #00bcd4ff, 0 0 10px #fff4; transform: translateY(-7px) scale(1.04);}
    .numero {
      font-size: 2.7rem; font-weight: 900; color: #00bcd4; margin-bottom: 0.5rem;
      text-shadow: 0 0 7px #4dd0e1; letter-spacing: 1px;
      background: linear-gradient(90deg,#00bcd4,#80deea,#fff0);
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
    #toggleModo:hover { background: #26c6da; transform: rotate(16deg) scale(1.09);}
    #toggleModo svg { fill: #000; width: 22px; height: 22px; }
    #chatbot-btn {
      position: fixed; bottom: 105px; right: 30px; width: 54px; height: 54px;
      background: linear-gradient(135deg, #00bcd4 70%, #80deea 100%);
      border-radius: 50%; box-shadow: 0 4px 14px #00bcd4aa;
      display: flex; align-items: center; justify-content: center; z-index: 1050;
      cursor: pointer; transition: background 0.3s, transform 0.3s;
      border: 2px solid #fff;
      animation: floatWA 2.2s infinite alternate cubic-bezier(.6,0,.4,1);
    }
    #chatbot-btn:hover { background: #80deea; transform: scale(1.09);}
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
      background: #004d40; color: #fff; border: none; border-radius: 12px;
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
    .public-comments-section {
      margin-top: 3em;
      margin-bottom: 2em;
      background: linear-gradient(120deg,#00bcd4aa,#80deea44,#2226);
      border-radius: 15px;
      padding: 2em 1em;
      box-shadow: 0 2px 32px #00bcd455;
      border: 2px solid #00bcd4cc;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }
    .public-comments-section h2 {
      text-align: center;
      margin-bottom: 1.2em;
      color: #00bcd4;
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
      border: 1px solid #00bcd4aa;
      font-size: 1em;
      background: #e0f7fa;
      color: #222;
    }
    #comment-form button {
      background: linear-gradient(90deg, #00bcd4, #80deea);
      color: #fff;
      padding: 0.6em 1.5em;
      border: none;
      border-radius: 8px;
      font-weight: 700;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 8px #00bcd4aa;
      transition: background 0.2s;
    }
    #comment-form button:hover { background: #00bcd4; }
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
      color: #e0e0e0;
      box-shadow: 0 2px 10px #00bcd433;
      border-left: 4px solid #00bcd4;
    }
    .comments-list .comment-author {
      font-weight: bold;
      color: #00bcd4;
      margin-bottom: 0.2em;
    }
    .comments-list .comment-date {
      font-size: 0.93em;
      color: #80deea;
      float: right;
    }
    @media (max-width: 520px) {
      #chatbot-box {
        right: 0; left: 0; width: 100vw; border-radius: 0; min-height: 60vh; max-height: 94vh;
      }
      .modal-img .close-modal { right: 12px; top: 74px;}
      .public-comments-section { padding: 1.3em 0.2em;}
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
  <!-- El resto del HTML (header, main, galería, comentarios, contacto, etc.) debe ir aquí igual que en tus versiones anteriores -->
  <!-- Por espacio y claridad, aquí se muestra la integración del chatbot con IA y comentarios públicos -->
  <div id="chatbot-btn" aria-label="Abrir chat con WeerBot" title="¿Necesitás ayuda?">
    <svg viewBox="0 0 32 32"><path d="M16 3C8.27 3 2 8.48 2 15c0 2.94 1.47 5.63 4 7.76V29a1 1 0 0 0 1.51.86l5.1-3.06c.42.05.85.08 1.39.08 7.73 0 14-5.48 14-12S23.73 3 16 3zm0 22c-.61 0-1.19-.04-1.77-.11a1 1 0 0 0-.62.13L7 27.13V24.7a1 1 0 0 0-.39-.79C4.44 21.95 3 18.63 3 15c0-5.52 5.82-10 13-10s13 4.48 13 10-5.82 10-13 10z"/></svg>
  </div>
  <div id="chatbot-box" role="dialog" aria-modal="true" aria-label="Chatbot WeerBot">
    <div id="chatbot-header">
      <span>WeerBot 🤖</span>
      <button id="chatbot-close" aria-label="Cerrar chat">&times;</button>
    </div>
    <div id="chatbot-messages">
      <div class="chatbot-message">¡Hola! Soy WeerBot con inteligencia artificial. Preguntame lo que quieras sobre el proyecto, ambiente, tecnología o cualquier otra cosa.</div>
    </div>
    <form id="chatbot-input-box" autocomplete="off">
      <input type="text" id="chatbot-input" placeholder="Escribí tu pregunta..." autocomplete="off" required />
      <button id="chatbot-send" type="submit">Enviar</button>
    </form>
  </div>
  <section class="public-comments-section sr" id="comentarios">
    <h2>Dejanos tu opinión o recomendación</h2>
    <form id="comment-form">
      <input type="text" id="comment-author" placeholder="Tu nombre (opcional)" maxlength="40" autocomplete="off"/>
      <textarea id="comment-text" placeholder="Escribí tu comentario, opinión o recomendación..." rows="3" required maxlength="400"></textarea>
      <button type="submit">Publicar comentario</button>
    </form>
    <ul class="comments-list" id="comments-list"></ul>
    <div style="text-align:center;margin-top:1em;color:#80deea;">
      También podés escribirnos directo por <a href="https://wa.me/541125216302?text=Hola%20WeerTeck%2C%20tengo%20una%20consulta%20o%20opinión" target="_blank" rel="noopener">WhatsApp</a>.
    </div>
  </section>
  <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
  <script>
    // Chatbot con OpenAI GPT
    async function obtenerRespuestaIA(pregunta) {
      const apiKey = "TU_API_KEY_AQUI"; // ← PONÉ TU API KEY AQUÍ
      const endpoint = "https://api.openai.com/v1/chat/completions";
      try {
        const response = await fetch(endpoint, {
          method: "POST",
          headers: {
            "Authorization": "Bearer " + apiKey,
            "Content-Type": "application/json"
          },
          body: JSON.stringify({
            model: "gpt-3.5-turbo",
            messages: [
              {role: "system", content: "Sos WeerBot, un asistente de la web WeerTeck. Respondé sobre tecnología ambiental, prevención de incendios, sensores, impacto ambiental, el proyecto WeerTeck y dudas generales de ciencia y tecnología. Si no tenés la respuesta, respondé de manera clara, positiva y educativa."},
              {role: "user", content: pregunta}
            ],
            max_tokens: 250,
            temperature: 0.7
          })
        });
        const data = await response.json();
        if (data && data.choices && data.choices.length > 0) {
          return data.choices[0].message.content.trim();
        }
        return "Perdón, no pude procesar tu pregunta. ¿Podés intentarlo de nuevo?";
      } catch (e) {
        return "Ocurrió un error al contactar a la IA. Por favor, intentá más tarde.";
      }
    }
    document.addEventListener('DOMContentLoaded', () => {
      // Chatbot
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
      chatbotForm.addEventListener('submit', async function(e) {
        e.preventDefault();
        const msg = chatbotInput.value.trim();
        if(!msg) return;
        const userMsg = document.createElement('div');
        userMsg.className = 'chatbot-message user';
        userMsg.textContent = msg;
        chatbotMessages.appendChild(userMsg);
        chatbotInput.value = '';
        chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
        const botMsg = document.createElement('div');
        botMsg.className = 'chatbot-message';
        botMsg.textContent = "Pensando...";
        chatbotMessages.appendChild(botMsg);
        chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
        const respuesta = await obtenerRespuestaIA(msg);
        botMsg.textContent = respuesta;
        chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
      });
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") chatbotBox.classList.remove('active');
      });
      // Caja de comentarios públicos
      const commentsList = document.getElementById('comments-list');
      function loadComments() {
        commentsList.innerHTML = '';
        let comments = [];
        try {
          comments = JSON.parse(localStorage.getItem('weer-comments') || '[]');
        } catch {}
        if (comments.length === 0) {
          commentsList.innerHTML = "<li style='text-align:center;color:#80deea;'>Sé el primero en dejar tu comentario.</li>";
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
    });
  </script>
</body>
</html>
