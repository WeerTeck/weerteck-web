<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WeerTeck | Tecnología ambiental contra incendios</title>
  <meta name="description" content="Soluciones tecnológicas para anticipar y combatir incendios forestales. Torres inteligentes, alertas automáticas y más.">
  <meta property="og:title" content="WeerTeck | Tecnología ambiental contra incendios">
  <meta property="og:description" content="Soluciones tecnológicas para anticipar y combatir incendios forestales. Torres inteligentes, alertas automáticas y más.">
  <meta property="og:image" content="img/logo.png">
  <meta property="og:type" content="website">

  <!-- Fuente moderna Poppins -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet" />
  <!-- Leaflet CSS para el mapa -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
  <!-- AOS Animations -->
  <link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />

  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: 'Poppins', sans-serif;
      background-color: #000;
      color: #e0e0e0;
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      padding-top: 70px;
    }

    .navbar {
      position: fixed;
      top: 0; left: 0; width: 100%;
      background: rgba(13,36,66,0.97); /* Azul oscuro */
      z-index: 2000;
      box-shadow: 0 2px 10px #0d244288;
    }
    .navbar ul { display: flex; justify-content: center; gap: 2rem; list-style: none; padding: 1rem 0;}
    .navbar a {
      color: #fff;
      font-weight: 600;
      letter-spacing: 0.5px;
      transition: color 0.2s;
      font-size: 1rem;
    }
    .navbar a:hover,
    .navbar a:focus { color: #4dd0e1; }

    header, main, footer {
      max-width: 950px;
      width: 94%;
      margin: auto;
      padding: 1.5rem 0;
    }
    header { text-align: center; }

    .logo {
      max-width: 120px;
      margin-bottom: 1rem;
      filter: drop-shadow(0 0 5px #00bcd4);
    }
    h1 {
      font-weight: 800; font-size: 2.8rem;
      color: #00bcd4;
      margin-bottom: 0.3rem;
      text-shadow: 0 0 8px #00bcd4aa;
    }
    .subtitulo {
      font-weight: 600; font-size: 1.2rem; color: #80deea;
      margin-bottom: 3rem;
      text-shadow: 0 0 6px #80deea88;
    }
    h2 {
      color: #00bcd4;
      margin-bottom: 1rem;
      font-weight: 700;
      font-size: 1.8rem;
      text-shadow: 0 0 6px #00bcd4bb;
    }
    p {
      font-weight: 400; font-size: 1rem;
      margin-bottom: 1.25rem;
      max-width: 800px;
    }
    strong { color: #4dd0e1; }

    .galeria {
      display: flex;
      justify-content: space-between;
      gap: 1rem;
      flex-wrap: wrap;
      margin-bottom: 2rem;
    }
    .galeria img {
      width: 32%;
      border-radius: 10px;
      box-shadow: 0 0 10px #00bcd4aa;
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.3s;
      border: 2px solid transparent;
      filter: brightness(0.95);
    }
    .galeria img:hover,
    .galeria img:focus {
      transform: scale(1.05);
      box-shadow: 0 0 15px #00bcd4ff;
      filter: brightness(1);
      border-color: #00bcd4;
      outline: none;
    }

    #testimonios { margin: 3rem 0; }
    .testimonios-grid {
      display: flex;
      gap: 2rem;
      flex-wrap: wrap;
      justify-content: center;
    }
    blockquote {
      background: #111;
      border-left: 5px solid #00bcd4;
      padding: 1rem 1.5rem;
      border-radius: 8px;
      color: #eee;
      margin: 0 0 1rem 0;
      max-width: 370px;
      font-size: 1.1rem;
      box-shadow: 0 0 10px #00bcd433;
    }
    blockquote footer { color: #80deea; font-size: 0.95rem; margin-top: 0.5rem; }

    #faq details {
      background: #111;
      color: #fff;
      border-radius: 8px;
      margin-bottom: 1rem;
      padding: 1rem;
      cursor: pointer;
      border-left: 4px solid #00bcd4;
    }
    #faq summary { font-weight: 600; font-size: 1.1rem; margin-bottom: 0.5rem;}
    #faq details[open] { background: #222; }

    .cta-btn {
      background: linear-gradient(90deg,#00bcd4,#26c6da);
      color: #fff;
      padding: 1rem 2.1rem;
      border-radius: 30px;
      font-weight: 700;
      font-size: 1.1rem;
      box-shadow: 0 2px 10px #00bcd455;
      transition: background 0.2s, transform 0.2s;
      display: inline-block;
      margin: 2rem 0;
      text-align:center;
    }
    .cta-btn:hover { background: #00796b; transform: scale(1.05); }

    .contadores {
      display: flex;
      justify-content: space-around;
      margin: 3rem 0;
      gap: 2rem;
      flex-wrap: wrap;
    }
    .contador {
      background: #111;
      border: 2px solid #00bcd4;
      border-radius: 15px;
      padding: 1rem 2rem;
      text-align: center;
      flex: 1 1 150px;
      box-shadow: 0 0 10px #00bcd4aa;
      transition: box-shadow 0.3s;
    }
    .contador:hover { box-shadow: 0 0 20px #00bcd4ff; }
    .numero {
      font-size: 2.5rem;
      font-weight: 800;
      color: #00bcd4;
      margin-bottom: 0.5rem;
    }
    .descripcion {
      font-size: 1rem;
      font-weight: 600;
      color: #80deea;
    }

    #mapa { margin: 3rem 0; }
    #map { height: 350px; border-radius: 15px; box-shadow: 0 0 10px #00bcd4aa; margin-bottom: 1rem; }

    .contacto { font-size: 1rem; line-height: 1.6; }
    .contacto svg {
      vertical-align: middle;
      margin-right: 0.5rem;
      fill: #4dd0e1;
      width: 20px;
      height: 20px;
      filter: drop-shadow(0 0 2px #4dd0e1);
    }

    footer {
      text-align: center;
      font-size: 0.9rem;
      color: #555;
      padding: 2rem 0 1.5rem 0;
      border-top: 1px solid #222;
      margin-top: auto;
      background: #0a0a0a;
    }
    .footer-links, .footer-social {
      margin-bottom: 0.7rem;
    }
    .footer-links a, .footer-social a {
      color: #00bcd4;
      margin: 0 0.3rem;
      font-size: 1rem;
      text-decoration: none;
    }
    .footer-links a:hover, .footer-social a:hover { color: #80deea; text-decoration: underline; }

    #btnWhatsApp {
      position: fixed;
      bottom: 25px;
      right: 25px;
      background-color: #25d366;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      box-shadow: 0 4px 10px rgba(37, 211, 102, 0.6);
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.3s;
      z-index: 1000;
    }
    #btnWhatsApp:hover { background-color: #1ebe5b; transform: scale(1.1);}
    #btnWhatsApp svg { width: 30px; height: 30px; fill: white; }

    #toggleModo {
      position: fixed;
      top: 20px;
      right: 20px;
      background: #00bcd4;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      cursor: pointer;
      box-shadow: 0 0 10px #00bcd4aa;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1001;
      transition: background-color 0.3s;
    }
    #toggleModo:hover { background: #26c6da; }
    #toggleModo svg { fill: #000; width: 22px; height: 22px; }

    body.light { background-color: #f5f5f5; color: #222;}
    body.light h1, body.light h2, body.light strong { color: #00796b; text-shadow: none; }
    body.light .subtitulo { color: #004d40; }
    body.light a { color: #00796b; }
    body.light a:hover { color: #004d40; }
    body.light header, body.light main, body.light footer { color: #222; }
    body.light footer { border-top-color: #ccc; color: #555; background: #e0f2f1;}
    body.light .galeria img { box-shadow: 0 0 10px #00796baa; filter: brightness(1); border-color: transparent;}
    body.light .galeria img:hover, body.light .galeria img:focus { box-shadow: 0 0 15px #00796bff; border-color: #00796b;}
    body.light .contador { background: #e0f2f1; border-color: #00796b; box-shadow: 0 0 10px #00796baa; color: #004d40; }
    body.light .contador:hover { box-shadow: 0 0 20px #00796bff;}
    body.light #faq details { background: #e0f2f1; color: #222;}
    body.light #faq details[open] { background: #b2dfdb; }

    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      .navbar ul { gap: 1rem; }
      .galeria img { width: 48%; margin-bottom: 1rem; }
      .contadores { flex-direction: column; align-items: center; }
      .contador { width: 80%; margin-bottom: 1.5rem;}
      h1 { font-size: 2.2rem; }
      h2 { font-size: 1.5rem;}
      .testimonios-grid { flex-direction: column; align-items: center;}
    }
    @media (max-width: 480px) {
      .galeria img { width: 100%; }
      .navbar ul { flex-direction: column; gap: 0.5rem; }
    }
  </style>
</head>
<body>
  <nav class="navbar">
    <ul>
      <li><a href="#quienes-somos">¿Quiénes somos?</a></li>
      <li><a href="#que-hacemos">¿Qué hacemos?</a></li>
      <li><a href="#galeria">Galería</a></li>
      <li><a href="#testimonios">Testimonios</a></li>
      <li><a href="#faq">FAQ</a></li>
      <li><a href="#contacto">Contacto</a></li>
    </ul>
  </nav>

  <div id="toggleModo" aria-label="Cambiar modo oscuro/claro" role="button" tabindex="0" title="Cambiar modo oscuro/claro">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M12 3a9 9 0 0 0 0 18 9 9 0 0 1 0-18z"/>
    </svg>
  </div>

  <header>
    <img src="img/logo.png" alt="Logo WeerTeck" class="logo" />
    <h1>WeerTeck</h1>
    <p class="subtitulo">Tecnología accesible para proteger nuestros bosques</p>
  </header>

  <main>
    <a href="#contacto" class="cta-btn" data-aos="zoom-in">Solicitar Información</a>

    <section id="quienes-somos" data-aos="fade-up">
      <h2>¿Quiénes somos?</h2>
      <p>
        Somos un grupo de jóvenes desarrolladores y emprendedores comprometidos con la protección del medio ambiente. Creamos soluciones tecnológicas accesibles para anticiparnos a los incendios forestales y reducir su impacto en la Patagonia argentina.
      </p>
    </section>

    <section id="que-hacemos" data-aos="fade-up">
      <h2>¿Qué hacemos?</h2>
      <p>
        Diseñamos <strong>torres inteligentes autosustentables</strong> equipadas con sensores de humo, gases inflamables y temperatura, capaces de detectar incendios en su fase inicial. Al identificar riesgo, envían <strong>alertas automáticas por WhatsApp</strong> a brigadas y vecinos de la zona.
      </p>
      <p>
        Estas torres también pueden contar con un sistema de <strong>rociado ecológico preventivo</strong>, que libera una solución biodegradable para contener el fuego antes de que se propague.
      </p>
    </section>

    <section class="contadores" aria-label="Estadísticas de WeerTeck" data-aos="fade-up">
      <div class="contador">
        <div class="numero" data-numero="0">0</div>
        <div class="descripcion">Torres instaladas</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="0">0</div>
        <div class="descripcion">Municipios adheridos</div>
      </div>
      <div class="contador">
        <div class="numero" data-numero="0">0</div>
        <div class="descripcion">Alertas activadas</div>
      </div>
    </section>

    <section id="galeria" data-aos="fade-up">
      <h2>Galería</h2>
      <div class="galeria" aria-label="Galería de imágenes de WeerTeck">
        <img src="img/torre1.jpg" alt="Torre inteligente en el bosque" loading="lazy" tabindex="0" />
        <img src="img/sensor.jpg" alt="Sensor de humo instalado en la torre" loading="lazy" tabindex="0" />
        <img src="img/brigada.jpg" alt="Brigada recibiendo alerta y actuando" loading="lazy" tabindex="0" />
      </div>
    </section>

    <section id="testimonios" data-aos="fade-up">
      <h2>Testimonios (futuros)</h2>
      <div class="testimonios-grid">
        <blockquote>
          <p>“Esperamos que WeerTeck marque un antes y un después en la prevención de incendios en la Patagonia. Con tecnología accesible, el futuro de los bosques puede ser mucho más seguro.”</p>
          <footer>- Proyección de brigadistas de la región</footer>
        </blockquote>
        <blockquote>
          <p>“Si logramos instalar estas torres en zonas críticas, podríamos anticiparnos a los focos y evitar tragedias ambientales a gran escala.”</p>
          <footer>- Opinión de referentes ambientales</footer>
        </blockquote>
      </div>
    </section>

    <section id="mapa" data-aos="fade-up">
      <h2>Mapa de Cobertura (proyectado)</h2>
      <div id="map"></div>
      <p>Estamos proyectando nuestra primera instalación en la Patagonia argentina, una región muy afectada por incendios forestales. Nuestro objetivo es expandir la cobertura a nivel nacional en el futuro.</p>
    </section>

    <section id="faq" data-aos="fade-up">
      <h2>Preguntas Frecuentes</h2>
      <details>
        <summary>¿Las torres funcionan todo el año?</summary>
        <p>Sí, nuestras torres están diseñadas para operar los 365 días del año, sin importar las condiciones meteorológicas. Son autosustentables y cuentan con sistemas de energía renovable para garantizar su funcionamiento continuo.</p>
      </details>
      <details>
        <summary>¿El sistema de rociado ecológico es seguro para el ambiente?</summary>
        <p>Absolutamente. Utilizamos soluciones biodegradables y no tóxicas, desarrolladas para no afectar la flora, la fauna ni los cuerpos de agua cercanos. Nuestro objetivo es prevenir el avance del fuego sin dañar el ecosistema.</p>
      </details>
      <details>
        <summary>¿Quién puede solicitar una torre?</summary>
        <p>Las torres pueden ser solicitadas tanto por municipios, organismos públicos, ONGs como por vecinos organizados. Cuantos más actores se sumen, mayor será la protección para toda la comunidad.</p>
      </details>
      <details>
        <summary>¿Qué sucede cuando se detecta un posible incendio?</summary>
        <p>Al detectar condiciones anormales (humo, gases, temperatura), la torre enviará automáticamente alertas por WhatsApp a los contactos definidos: brigadas, autoridades y vecinos. Esto permitirá una reacción rápida y coordinada, muchas veces antes de que el fuego se propague.</p>
      </details>
      <details>
        <summary>¿Requiere mantenimiento frecuente?</summary>
        <p>No. Las torres están pensadas para requerir un mantenimiento mínimo, y la mayoría de las verificaciones podrán realizarse de forma remota. Se recomendará una inspección anual para asegurar el óptimo funcionamiento de sensores y sistemas de energía.</p>
      </details>
      <details>
        <summary>¿Qué tan rápido se emitirán las alertas?</summary>
        <p>La transmisión de la alerta será prácticamente instantánea una vez que los sensores detecten una amenaza. El sistema está optimizado para enviar las notificaciones en cuestión de segundos, minimizando el tiempo de respuesta.</p>
      </details>
      <details>
        <summary>¿Cómo puedo sumarme o colaborar con el proyecto?</summary>
        <p>Puedes acompañar el desarrollo de WeerTeck desde el inicio y ser parte de la comunidad que protegerá los bosques. Es posible colaborar con una mínima transacción utilizando nuestra cripto WeerCoin (WEER), ayudar en la difusión o sumarte como voluntario/a. ¡Contactanos para ser parte de la prevención de incendios en Argentina!</p>
      </details>
    </section>

    <section id="contacto" data-aos="fade-up">
      <h2>Contacto</h2>
      <p class="contacto">
        <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M6.62 10.79a15.091 15.091 0 0 0 6.59 6.59l2.2-2.2a1 1 0 0 1 1.11-.21 11.36 11.36 0 0 0 3.58.57 1 1 0 0 1 1 1V20a1 1 0 0 1-1 1A17 17 0 0 1 3 4a1 1 0 0 1 1-1h3.5a1 1 0 0 1 1 1 11.36 11.36 0 0 0 .57 3.58 1 1 0 0 1-.21 1.11l-2.24 2.1z"/>
        </svg>
        Teléfono: <a href="tel:+5491125216302">+54 9 11 2521-6302</a>
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
    </section>
  </main>

  <footer>
    <div class="footer-links">
      <a href="#">Política de Privacidad</a> |
      <a href="#">Términos y Condiciones</a>
    </div>
    <div class="footer-social">
      <a href="https://instagram.com/weer.teck" target="_blank" aria-label="Instagram">Instagram</a>
      <a href="https://wa.me/5491125216302" target="_blank" aria-label="WhatsApp">WhatsApp</a>
    </div>
    <p>&copy; 2025 WeerTeck - Todos los derechos reservados</p>
  </footer>

  <a href="https://wa.me/5491125216302?text=Hola%20WeerTeck%2C%20quiero%20m%C3%A1s%20info" target="_blank" rel="noopener" id="btnWhatsApp" aria-label="Contactar por WhatsApp">
    <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
      <path d="M20.52 3.48A11.86 11.86 0 0 0 12 0C5.37 0 0 5.37 0 12a11.93 11.93 0 0 0 2.07 6.57L0 24l5.6-2.07A11.9 11.9 0 0 0 12 24c6.63 0 12-5.37 12-12a11.84 11.84 0 0 0-3.48-8.52zM12 21.4a9.4 9.4 0 0 1-4.78-1.41l-.34-.21-3.32 1.23 1.2-3.23-.22-.34A9.44 9.44 0 1 1 21.4 12a9.37 9.37 0 0 1-9.4 9.4zm5.32-7.21c-.29-.15-1.71-.84-1.97-.94-.26-.11-.45-.15-.64.15s-.74.94-.9 1.13c-.16.19-.32.21-.6.07a6.71 6.71 0 0 1-1.97-1.21 7.32 7.32 0 0 1-1.36-1.68c-.14-.25-.02-.38.11-.53.12-.12.26-.32.39-.48a.72.72 0 0 0 .11-.3.43.43 0 0 0-.06-.3c-.2-.45-.57-1.18-.8-1.6-.21-.4-.43-.34-.6-.34a1.36 1.36 0 0 0-.65.06c-.23.1-.89.86-.89 2.1s.91 2.43 1.03 2.6c.11.18 1.78 2.71 4.3 3.8a13.61 13.61 0 0 0 1.89.66c.8.27 1.53.23 2.11.14a6.69 6.69 0 0 0 2.03-.82 7.7 7.7 0 0 0 2.72-2.47 9.56 9.56 0 0 0-3.41-2.55z"/>
    </svg>
  </a>

  <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
  <script src="https://unpkg.com/aos@next/dist/aos.js"></script>
  <script>
    function animarContador(element, numeroFinal, duracion = 2000) {
      let start = 0;
      const stepTime = Math.max(30, Math.abs(Math.floor(duracion / Math.max(1, numeroFinal))));
      const increment = 1;
      const timer = setInterval(() => {
        start += increment;
        element.textContent = start;
        if (start >= numeroFinal) {
          clearInterval(timer);
        }
      }, stepTime);
    }
    document.addEventListener('DOMContentLoaded', () => {
      const numeros = document.querySelectorAll('.numero');
      numeros.forEach((numElem) => {
        const numeroFinal = parseInt(numElem.getAttribute('data-numero'), 10);
        animarContador(numElem, numeroFinal);
      });

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

      AOS.init({ duration: 800, once: true });

      if (document.getElementById('map')) {
        var map = L.map('map').setView([-42.0, -71.5], 7); // Patagonia
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);
        L.marker([-42, -71.5]).addTo(map)
          .bindPopup('Proyección de primera torre en la Patagonia');
      }
    });
  </script>
</body>
</html>
