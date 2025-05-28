<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>WeerTec</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom right, #001f3f, #0074D9);
      color: white;
    }

    header {
      background-color: rgba(0, 0, 0, 0.6);
      padding: 1rem;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 2.5rem;
    }

    .subtitulo {
      font-size: 1.2rem;
      margin-top: 0.5rem;
      color: #7FDBFF;
    }

    main {
      padding: 2rem;
      text-align: center;
    }

    .descripcion {
      font-size: 1.2rem;
      margin-bottom: 2rem;
    }

    .contadores {
      display: flex;
      justify-content: center;
      gap: 2rem;
      flex-wrap: wrap;
    }

    .contador {
      background-color: rgba(255, 255, 255, 0.1);
      padding: 1.5rem;
      border-radius: 1rem;
      width: 150px;
    }

    .contador .numero {
      font-size: 2rem;
      font-weight: bold;
      color: #FFDC00;
    }

    .contador .descripcion {
      margin-top: 0.5rem;
      font-size: 1rem;
    }

    footer {
      margin-top: 3rem;
      font-size: 0.9rem;
      color: #AAAAAA;
      text-align: center;
      padding: 1rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>WeerTec</h1>
    <div class="subtitulo">Soluciones tecnológicas para la sequía</div>
  </header>

  <main>
    <p class="descripcion">
      En el norte argentino, la falta de acceso a información meteorológica precisa limita la capacidad de respuesta de los municipios frente a la sequía. WeerTec propone una solución: una red de torres meteorológicas de bajo costo y código abierto para monitorear y alertar a las comunidades rurales.
    </p>

    <section class="contadores">
      <div class="contador">
        <div class="numero">0</div>
        <div class="descripcion">Torres instaladas</div>
      </div>
      <div class="contador">
        <div class="numero">0</div>
        <div class="descripcion">Municipios</div>
      </div>
      <div class="contador">
        <div class="numero">0</div>
        <div class="descripcion">Alertas</div>
      </div>
      <div class="contador">
        <div class="numero">1</div>
        <div class="descripcion">Prototipo</div>
      </div>
    </section>
  </main>

  <footer>
    Proyecto desarrollado por Lucas De Cesare y equipo para UDESA Ingenia · 2025
  </footer>
</body>
</html>


