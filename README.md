<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WeerTeck | Tecnología ambiental contra incendios</title>
  
  <!-- Fuente moderna Poppins -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet" />
  
  <style>
    /* Reset básico */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background-color: #000;
      color: #e0e0e0;
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    a {
      color: #4dd0e1;
      text-decoration: none;
      transition: color 0.3s ease;
    }

    a:hover,
    a:focus {
      color: #81d4fa;
      text-decoration: underline;
      outline: none;
    }

    header, main, footer {
      max-width: 900px;
      width: 90%;
      margin: auto;
      padding: 1.5rem 0;
    }

    header {
      text-align: center;
    }

    .logo {
      max-width: 120px;
      margin-bottom: 1rem;
      filter: drop-shadow(0 0 5px #00bcd4);
    }

    h1 {
      font-weight: 800;
      font-size: 2.8rem;
      color: #00bcd4;
      margin-bottom: 0.3rem;
      text-shadow: 0 0 8px #00bcd4aa;
    }

    .subtitulo {
      font-weight: 600;
      font-size: 1.2rem;
      color: #80deea;
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
      font-weight: 400;
      font-size: 1rem;
      margin-bottom: 1.25rem;
      max-width: 800px;
    }

    strong {
      color: #4dd0e1;
    }

    /* Galería de imágenes */
    .galeria {
      display: flex;
      justify-content: space-between;
      gap: 1rem;
      flex-wrap: wrap;
      margin-bottom: 2rem;
    }

    .galeria img {
      width: 32%;
      border-radius: 8px;
      box-shadow: 0 0 10px #00bcd4aa;
      cursor: pointer;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      border: 2px solid transparent;
      filter: brightness(0.95);
      border-radius: 10px;
    }

    .galeria img:hover,
    .galeria img:focus {
      transform: scale(1.05);
      box-shadow: 0 0 15px #00bcd4ff;
      filter: brightness(1);
      border-color: #00bcd4;
      outline: none;
    }

    /* Contacto con íconos SVG */
    .contacto {
      font-size: 1rem;
      line-height: 1.6;
    }

    .contacto svg {
      vertical-align: middle;
      margin-right: 0.5rem;
      fill: #4dd0e1;
      width: 20px;
      height: 20px;
      filter: drop-shadow(0 0 2px #4dd0e1);
    }

    /* Footer */
    footer {
      text-align: center;
      font-size: 0.9rem;
      color: #555;
      padding: 1.5rem 0;
      border-top: 1px solid #222;
      margin-top: auto;
    }

    /* Botón flotante WhatsApp */
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
      transition: background-color 0.3s ease, transform 0.3s ease;
      z-index: 1000;
    }

    #btnWhatsApp:hover {
      background-color: #1ebe5b;
      transform: scale(1.1);
    }

    #btnWhatsApp svg {
      width: 30px;
      height: 30px;
      fill: white;
    }

    /* Contadores animados */
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
      transition: box-shadow 0.3s ease;
    }

    .contador:hover {
      box-shadow: 0 0 20px #00bcd4ff;
    }

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

    /* Toggle modo oscuro/claro */
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
      transition: background-color 0.3s ease;
    }

    #toggleModo:hover {
      background: #26c6da;
    }

    #toggleModo svg {
      fill: #000;
      width: 22px;
      height: 22px;
    }

    /* Modo claro */
    body.light {
      background-color: #f5f5f5;
      color: #222;
    }

    body.light h1,
    body.light h2,
    body.light strong {
      color: #00796b;
      text-shadow: none;
    }

    body.light .subtitulo {
      color: #004d40;
    }

    body.light a {
      color: #00796b;
    }

    body.light a:hover {
      color: #004d40;
    }

    body.light header,
    body.light main,
    body.light footer {
      color: #222;
    }

    body.light footer {
      border-top-color: #ccc;
      color: #555;
    }

    body.light .galeria img {
      box-shadow: 0 0 10px #00796baa;
      filter: brightness(1);
      border-color: transparent;
    }

    body.light .galeria img:hover,
    body.light .galeria img:focus {
      box-shadow: 0 0 15px #00796bff;
      border-color: #00796b;
    }

    body.light .contador {
      background: #e0f2f1;
      border-color: #


