<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Wheel of Fortune</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
    }
    .container { 
      text-align: center;
      margin-top: 50px;
      background-color: #ffffff;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      width: 80%;
      max-width: 500px;
      margin: 0 auto;
      position: relative; /* Permitir posicionamiento absoluto */
    }
    form {
      margin-bottom: 20px;
    }
    input[type="text"] {
      padding: 10px;
      width: 80%;
      border: 1px solid #ccc;
      border-radius: 5px;
      margin: 10px auto;
      display: block;
    }
    .button {
      display: inline-block;
      padding: 15px 30px;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      text-decoration: none;
      font-size: 16px;
      font-weight: bold;
    }

   .button:hover {
      background-color: #45a049;
    }
    /* Estilos de la flecha */
    .arrow {
      position: absolute;
      bottom: 0; /* Alinear con la parte inferior de la imagen */
      right: -30px; /* Ajusta la posición a la derecha */
      transform: translateY(50%) rotate(270deg); /* Rotar la flecha hacia arriba */
      width: 0;
      height: 0;
      border-top: 20px solid transparent;
      border-bottom: 20px solid transparent;
      border-left: 20px solid black;
    }
    .arrow:before {
      content: '';
      position: absolute;
      top: -20px;
      left: 0;
      width: 0;
      height: 0;
      border-top: 20px solid transparent;
      border-bottom: 20px solid transparent;
      border-left: 20px solid red;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Acierta y gana</h1>
    <form id="quizForm">
      <label for="question1"> ¿Cuál es tu personaje favorito de Sanrio?</label>
      <input type="text" id="question1" name="question1" required>
      <label for="question2">Question 2: What is the capital of France?</label>
      <input type="text" id="question2" name="question2" required>
      <label for="question3">Noé sería capaz de sacarse el corazón por tí?</label>
      <input type="text" id="question3" name="question3" required>
      <button type="submit" class="button">Comprobar Resultados</button> <!-- Botón para comprobar resultados -->
    </form>
    <div class="arrow"></div> <!-- Flecha añadida -->
    <img id="wheelImage" src="https://play-lh.googleusercontent.com/ffamZbyiKd8_lHlNCebq1f8GziHWOWR3NUVUDsp1ji-lrbD20VaaK2UMZZvrPqOIGNZD=w600-h300-pc0xffffff-pd" alt="Wheel of Fortune"> <!-- Imagen añadida -->
  </div>

  <script>
    const quizForm = document.getElementById('quizForm');
    const wheelImage = document.getElementById('wheelImage'); // Obtener la imagen

    quizForm.addEventListener('submit', function(event) {
      event.preventDefault();
      const answers = {
        question1: document.getElementById('question1').value.trim().toLowerCase(),
        question2: document.getElementById('question2').value.trim().toLowerCase(),
        question3: document.getElementById('question3').value.trim().toLowerCase()
      };
  // Check answers
      if (answers.question1 === 'kuromi' && answers.question2 === 'paris' && answers.question3 === 'si') {
        // Generar un ángulo de rotación aleatorio entre 360 y 2880 grados
        const randomRotation = Math.floor(Math.random() * (2880 - 360 + 1)) + 360;
        // Aplicar la rotación a la imagen en sentido de las manecillas del reloj
        wheelImage.style.transition = 'transform 4s ease-out'; // Animación de rotación de 4 segundos
        wheelImage.style.transform = `rotate(${randomRotation}deg)`;
      }
    });
  </script>
</body>
</html>
