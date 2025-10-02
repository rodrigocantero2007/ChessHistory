<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Historial de Partidas de Ajedrez</title>
  <style>
    body {
      font-family: "Segoe UI", Arial, sans-serif;
      margin: 0;
      background: #f9fafc;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
    }

    h1 {
      color: #2b3a55;
      text-align: center;
      margin-bottom: 20px;
    }

    form {
      background: #ffffff;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      max-width: 600px;
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: space-between;
    }

    label {
      flex: 1 1 100%;
      color: #333;
      font-weight: 600;
    }

    select {
      flex: 1 1 48%;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }

    button {
      flex: 1 1 100%;
      background-color: #2b3a55;
      color: white;
      border: none;
      padding: 10px;
      border-radius: 10px;
      cursor: pointer;
      font-size: 16px;
      transition: background 0.3s;
    }

    button:hover {
      background-color: #1f2b3f;
    }

    table {
      width: 100%;
      max-width: 700px;
      border-collapse: collapse;
      margin-top: 25px;
      background: #fff;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 4px 8px rgba(0,0,0,0.08);
    }

    th, td {
      border-bottom: 1px solid #e0e0e0;
      padding: 10px;
      text-align: center;
    }

    th {
      background-color: #2b3a55;
      color: white;
    }

    tr:nth-child(even) {
      background-color: #f2f6ff;
    }

    @media (max-width: 600px) {
      form {
        flex-direction: column;
      }
      select, button {
        flex: 1 1 100%;
      }
    }
  </style>
</head>
<body>
  <h1>Historial de Partidas</h1>

  <form id="partidaForm">
    <label>Jugador 1:</label>
    <select id="jugador1" required>
      <option value="">Seleccionar</option>
      <option value="Nicolás">Nicolás</option>
      <option value="JuanDiego">JuanDiego</option>
      <option value="Rodrigo">Rodrigo</option>
      <option value="Larroque">Larroque</option>
      <option value="Lautaro">Lautaro</option>
    </select>

    <label>Jugador 2:</label>
    <select id="jugador2" required>
      <option value="">Seleccionar</option>
      <option value="Nicolás">Nicolás</option>
      <option value="JuanDiego">JuanDiego</option>
      <option value="Rodrigo">Rodrigo</option>
      <option value="Larroque">Larroque</option>
      <option value="Lautaro">Lautaro</option>
    </select>

    <label>Resultado:</label>
    <select id="resultado" required>
      <option value="">Seleccionar</option>
      <option value="Gana Jugador 1">Gana Jugador 1</option>
      <option value="Gana Jugador 2">Gana Jugador 2</option>
      <option value="Empate">Empate</option>
    </select>

    <label>Tipo de partida:</label>
    <select id="tipo" required>
      <option value="">Seleccionar</option>
      <option value="Blitz">Blitz</option>
      <option value="Rápida">Rápida</option>
      <option value="Bala">Bala</option>
      <option value="Sin reloj">Sin reloj</option>
    </select>

    <button type="submit">Agregar partida</button>
  </form>

  <table id="tablaPartidas">
    <thead>
      <tr>
        <th>Jugador 1</th>
        <th>Jugador 2</th>
        <th>Resultado</th>
        <th>Tipo</th>
      </tr>
    </thead>
    <tbody></tbody>
  </table>

  <script>
    const form = document.getElementById('partidaForm');
    const tabla = document.querySelector('#tablaPartidas tbody');

    form.addEventListener('submit', e => {
      e.preventDefault();
      const j1 = document.getElementById('jugador1').value;
      const j2 = document.getElementById('jugador2').value;
      const resultado = document.getElementById('resultado').value;
      const tipo = document.getElementById('tipo').value;

      if (j1 === j2) {
        alert("Los jugadores deben ser distintos.");
        return;
      }

      const fila = document.createElement('tr');
      fila.innerHTML = `<td>${j1}</td><td>${j2}</td><td>${resultado}</td><td>${tipo}</td>`;
      tabla.appendChild(fila);

      form.reset();
    });
  </script>
</body>
</html>
