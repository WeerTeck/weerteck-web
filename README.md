<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>WeerTeck | Tecnología ambiental contra incendios</title>
  <link rel="stylesheet" href="style.css" />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
</head>
<body>
  <header>
    <div class="container">
      <img src="img/logo.png" alt="Logo WeerTeck" class="logo" />
      <h1>WeerTeck</h1>
      <p class="subtitulo">Tecnología accesible para proteger nuestros bosques</p>
    </div>
  </header>

  <main class="container">
    <section>
      <h2>¿Quiénes somos?</h2>
      <p>
        Somos un grupo de jóvenes desarrolladores y emprendedores comprometidos con la protección del medio ambiente. Creamos soluciones tecnológicas accesibles para anticiparnos a los incendios forestales y reducir su impacto en la Patagonia argentina.
      </p>
    </section>

    <section>
      <h2>¿Qué hacemos?</h2>
      <p>
        Diseñamos <strong>torres inteligentes autosustentables</strong> equipadas con sensores de humo, gases inflamables y temperatura, capaces de detectar incendios en su fase inicial. Al identificar riesgo, envían <strong>alertas automáticas por WhatsApp</strong> a brigadas y vecinos de la zona.
      </p>
      <p>
        Estas torres también pueden contar con un sistema de <strong>rociado ecológico preventivo</strong>, que libera una solución biodegradable para contener el fuego antes de que se propague.
      </p>
    </section>

    <section>
      <h2>¿Cómo lo financiamos?</h2>
      <p>
        Desarrollamos <strong>WeerTeck Token</strong>, una criptomoneda solidaria que permite financiar la producción e instalación de las torres y recompensar a quienes colaboran con la red de monitoreo ambiental.
      </p>
    </section>

    <section>
      <h2>Impacto visual</h2>
      <div class="galeria">
        <img src="img/incendio1.jpg" alt="Incendio forestal" />
        <img src="img/deforestacion2.jpg" alt="Zona deforestada" />
        <img src="img/bosque.jpg" alt="Bosque protegido" />
      </div>
    </section>

    <section>
      <h2>Contacto</h2>
      <p class="contacto">
        📷 <a href="https://instagram.com/WeerTeck" target="_blank">@WeerTeck</a><br />
        ✉️ <a href="mailto:weerteck@gmail.com">weerteck@gmail.com</a><br />
        📞 <a href="tel:+541125216302">(+54) 11 2521 6302</a>
      </p>
    </section>
  </main>

body {
  margin: 0;
  font-family: 'Inter', sans-serif;
  background-color: #f9fbfc;
  color: #222;
}

.container {
  max-width: 900px;
  margin: auto;
  padding: 40px 20px;
}

header {
  background: linear-gradient(to right, #0077cc, #004d99);
  color: white;
  text-align: center;
  padding: 60px 20px;
}

.logo {
  max-width: 100px;
  margin-bottom: 20px;
}

h1 {
  margin: 0;
  font-size: 36px;
  font-weight: 800;
}

.subtitulo {
  font-size: 18px;
  font-weight: 400;
  margin-top: 10px;
}

h2 {
  color: #0077cc;
  font-size: 28px;
  margin-top: 50px;
}

p {
  font-size: 17px;
  line-height: 1.7;
}

.galeria {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
  margin-top: 20px;
}

.galeria img {
  width: 280px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  object-fit: cover;
}

.contacto a {
  color: #004d99;
  font-weight: 600;
  text-decoration: none;
}

.contacto a:hover {
  text-decoration: underline;
}

footer {
  text-align: center;
  background-color: #eee;
  padding: 25px;
  font-size: 14px;
  margin-top: 60px;
}




      
