<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora del Índice de Complejidad Farmacoterapéutica (MRCI)</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      line-height: 1.6;
    }
    .section {
      margin-bottom: 20px;
    }
    .section h2 {
      margin-bottom: 10px;
    }
    .results {
      font-weight: bold;
    }
    button {
      padding: 10px 15px;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>
  <h1>Calculadora del Índice de Complejidad Farmacoterapéutica (MRCI)</h1>
  
  <!-- Sección A -->
  <div class="section" id="section-a">
    <h2>Sección A: Formas farmacéuticas</h2>
    <p>Marque cada forma farmacéutica presente en el tratamiento:</p>
    <!-- Formas farmacéuticas -->
    <label><input type="checkbox" class="form-a" value="1"> Cápsula / Comprimido / Gragea</label><br>
    <label><input type="checkbox" class="form-a" value="2"> Gargarismo / Enjuague</label><br>
    <label><input type="checkbox" class="form-a" value="2"> Chicle / Comprimido para chupar / Bucodispersable / Masticable</label><br>
    <label><input type="checkbox" class="form-a" value="2"> Líquido</label><br>
    <label><input type="checkbox" class="form-a" value="2"> Polvo / Granulado / Comprimido efervescente</label><br>
    <label><input type="checkbox" class="form-a" value="2"> Comprimido sublingual / Spray sublingual</label><br>
    <label><input type="checkbox" class="form-a" value="2"> Crema / Gel / Pomada / Ungüento</label><br>
    <label><input type="checkbox" class="form-a" value="3"> Apósito</label><br>
    <label><input type="checkbox" class="form-a" value="3"> Pasta</label><br>
    <label><input type="checkbox" class="form-a" value="3"> Solución de diálisis</label><br>
    <label><input type="checkbox" class="form-a" value="4"> Ampolla inyectable / Vial inyectable</label><br>
    <label><input type="checkbox" class="form-a" value="3"> Dispositivos inyectables precargados</label><br>
    <!-- Continuar con todas las opciones... -->
  </div>

  <!-- Sección B -->
  <div class="section" id="section-b">
    <h2>Sección B: Frecuencia de administración</h2>
    <p>Ingrese el número de medicamentos para cada frecuencia:</p>
    <!-- Frecuencias de administración -->
    <label>Una vez al día: <input type="number" class="freq-b" data-weight="1" min="0"></label><br>
    <label>Dos veces al día: <input type="number" class="freq-b" data-weight="2" min="0"></label><br>
    <label>Tres veces al día: <input type="number" class="freq-b" data-weight="3" min="0"></label><br>
    <label>Cada 12 horas: <input type="number" class="freq-b" data-weight="2.5" min="0"></label><br>
    <label>Cada 8 horas: <input type="number" class="freq-b" data-weight="3.5" min="0"></label><br>
    <label>Cada 6 horas: <input type="number" class="freq-b" data-weight="4.5" min="0"></label><br>
    <label>Cada 4 horas: <input type="number" class="freq-b" data-weight="6.5" min="0"></label><br>
    <label>A demanda o si precisa: <input type="number" class="freq-b" data-weight="0.5" min="0"></label><br>
    <!-- Continuar con todas las opciones... -->
  </div>

  <!-- Sección C -->
  <div class="section" id="section-c">
    <h2>Sección C: Instrucciones adicionales</h2>
    <p>Ingrese el número de medicamentos para cada instrucción adicional:</p>
    <!-- Instrucciones adicionales -->
    <label>Partir los comprimidos: <input type="number" class="instr-c" data-weight="1" min="0"></label><br>
    <label>Disolver el comprimido (excluyendo efervescentes): <input type="number" class="instr-c" data-weight="1" min="0"></label><br>
    <label>Varias dosis en la misma administración: <input type="number" class="instr-c" data-weight="1" min="0"></label><br>
    <label>Dosis variable: <input type="number" class="instr-c" data-weight="1" min="0"></label><br>
    <label>Escala móvil de insulina: <input type="number" class="instr-c" data-weight="2" min="0"></label><br>
    <!-- Continuar con todas las opciones... -->
  </div>

  <!-- Botón de cálculo -->
  <button id="calculate">Calcular Índice</button>

  <!-- Resultados -->
  <p class="results">Resultado total: <span id="total-score">0</span></p>

  <script>
    document.getElementById('calculate').addEventListener('click', function () {
      let totalA = 0, totalB = 0, totalC = 0;

      // Calcular total sección A
      document.querySelectorAll('.form-a:checked').forEach(item => {
        totalA += parseFloat(item.value);
      });

      // Calcular total sección B
      document.querySelectorAll('.freq-b').forEach(item => {
        const weight = parseFloat(item.getAttribute('data-weight'));
        const count = parseInt(item.value) || 0;
        totalB += weight * count;
      });

      // Calcular total sección C
      document.querySelectorAll('.instr-c').forEach(item => {
        const weight = parseFloat(item.getAttribute('data-weight'));
        const count = parseInt(item.value) || 0;
        totalC += weight * count;
      });

      // Calcular total
      const totalScore = totalA + totalB + totalC;
      document.getElementById('total-score').innerText = totalScore.toFixed(2);
    });
  </script>
</body>
</html>
