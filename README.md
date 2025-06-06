<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Opiniones Personales - CBTIS64</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f1f5f9;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #1e3a8a;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 800px;
      margin: auto;
      padding: 20px;
    }
    textarea, select {
      width: 100%;
      padding: 10px;
      margin-top: 8px;
      border-radius: 5px;
      border: 1px solid #ccc;
      resize: vertical;
    }
    button {
      margin-top: 12px;
      padding: 10px 20px;
      background-color: #2563eb;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #1d4ed8;
    }
    .opiniones {
      margin-top: 30px;
    }
    .opinion {
      background-color: white;
      padding: 15px;
      margin-bottom: 15px;
      border-left: 5px solid #9ca3af;
    }
    .opinion.sugerencia { border-left-color: #10b981; }
    .opinion.queja { border-left-color: #ef4444; }
    .opinion.reconocimiento { border-left-color: #f59e0b; }
    .opinion h4 {
      margin: 0 0 5px 0;
      font-size: 1rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>Opiniones del Personal sobre la Escuela CBTIS 64</h1>
    <p>Comparte sugerencias, quejas o reconocimientos de forma anónima</p>
  </header>

  <div class="container">
    <form id="formOpiniones">
      <label for="tipo">Tipo de mensaje:</label>
      <select id="tipo" required>
        <option value="">Selecciona una opción</option>
        <option value="sugerencia">Sugerencia</option>
        <option value="queja">Queja</option>
        <option value="reconocimiento">Reconocimiento</option>
      </select>

      <label for="mensaje">Tu mensaje:</label>
      <textarea id="mensaje" placeholder="Escribe aquí tu opinión..." required></textarea>

      <button type="submit">Enviar</button>
    </form>

    <div class="opiniones" id="opiniones">
      <h2>Mensajes publicados</h2>
      <!-- Aquí aparecen los mensajes -->
    </div>
  </div>

  <script>
    const form = document.getElementById('formOpiniones');
    const opinionesDiv = document.getElementById('opiniones');

    form.addEventListener('submit', function(event) {
      event.preventDefault();

      const tipo = document.getElementById('tipo').value;
      const mensaje = document.getElementById('mensaje').value;

      const opinionDiv = document.createElement('div');
      opinionDiv.className = 'opinion ' + tipo;

      const titulo = {
        sugerencia: "💡 Sugerencia",
        queja: "⚠️ Queja",
        reconocimiento: "⭐ Reconocimiento"
      };

      opinionDiv.innerHTML = `
        <h4>${titulo[tipo]}</h4>
        <p>${mensaje}</p>
      `;

      opinionesDiv.appendChild(opinionDiv);
      form.reset();
    });
  </script>
</body>
</html>
