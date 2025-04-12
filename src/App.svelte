<script>
  import * as d3 from "d3";
  
  const grid_size = 6;
  const grid_offset = 0;
  
  let players = ["Messi", "Maradona"];
  let PlayerAndGoals = {}
  
  PlayerAndGoals = {  'Messi': [24, 33, 42, 54, 63, 71, 77, 87, 92, 98]
                    , 'Maradona': [23, 35, 45, 56, 50, 43, 38, 32, 28, 25]}



  'SOLO SI no esta asignado PlayerAndGoals y hay numebers'                  
  function assignNumbersToPlayers(numbers, players) {
  let assignments = {};

  
  let shuffledNumbers = [...numbers];
  shuffledNumbers.sort(() => Math.random() - 0.1);  
  
  // Asignacion
  players.forEach(player => assignments[player] = []);

  // Cantidad de numeros que cada jugador obtiene
  let batchSize = Math.floor(numbers.length / players.length);
  let extraNumbers = numbers.length % players.length;  // numeros extras para distribuir

  // Distribucion de los numeros
  for (let i = 0; i < players.length; i++) {
    // Calculate the start and end index for the batch
    let start = i * batchSize;
    let end = start + batchSize;
    let batch = shuffledNumbers.slice(start, end);
    
    // If there are extra numbers, randomly assign them to players
    if (i < extraNumbers) {
      batch.push(shuffledNumbers[batchSize * players.length + i]);  // Add one extra number
    }
    
    // Assign the batch to the player
    assignments[players[i]] = batch;
  }
  
  return assignments;
}

let size_var = [];
if (Object.keys(PlayerAndGoals).length === 0) {
  PlayerAndGoals = assignNumbersToPlayers(numbers, players);
  size_var = numbers;
} else {
  for (let jugador of players) {
    size_var = size_var.concat(PlayerAndGoals[jugador]);  // Concatenate arrays
  }
}

let messi = [];
let ney = [];
let marado = [];

for (let col = 1+grid_offset; col <= grid_size - grid_offset; col++) {
  for (let row = 1+grid_offset; row <= grid_size - grid_offset; row++) {
    if ((col === grid_offset + 1 || col === grid_size) || 
    (row === grid_offset + 1 || row === grid_size)) {
        messi.push({ col, row });
    }
    else{
      marado.push({ col, row });
    }
  }
}

let posJugadores = [messi,marado]
let positions = [];
let i = 0
for (let jugador of players) {
  let nums = PlayerAndGoals[jugador]
  for (let n of nums){
    let pos;
    if (posJugadores[i].length > 0) {
      pos = posJugadores[i].splice(Math.floor(Math.random() * posJugadores[i].length), 1)[0];
    } else {
      pos = { col: Math.floor(Math.random() * (grid_size - grid_offset)) + 1, row: Math.floor(Math.random() * (grid_size - grid_offset)) + 1 };
    }
    positions.push({ value: n, col: pos.col, row: pos.row, juga: jugador});
  }
  i = i+1
}

//Escala de D3 para el tamaño de los círculos
const sizeScale = d3.scaleLinear()
.domain([d3.min(size_var), d3.max(size_var)])
.range([40, 70]); // Tamaño mínimo y máximo del círculo

</script>


<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap" rel="stylesheet">
<main id="container">
  <div class='title-box'>
    <h1 class="title">Titanes del gol: Messi y Maradona en la cancha</h1>
  </div>

  <h2 class='Subtitulo'>¿Dónde hacen magia? Mapa de goles en sus mejores años</h2>

  <div class="chart">
    <img src="./images/Arco.svg" alt="arco" class="goal-image" />
    <div class="cardinal-container">
      {#each positions as { value, col, row, juga}}
      <div class="circle {juga}"
        style="
              width: {sizeScale(value)}px; 
              height: {sizeScale(value)}px;
              font-size: {sizeScale(value)/2}px;
              grid-column: {col}; 
              grid-row: {row};
              position: relative;
              left: {Math.random() * 50}px; 
              top: {Math.random() * 10}px;
            ">
        {value}
      </div>
      {/each}
    </div>
  </div>

  <div class='ref-box'>
    <h3 class='referencias'>
      <span class="item"><span class="circle Messi"></span> Messi</span>  
      <span class="item"><span class="circle Maradona"></span> Maradona</span>  
    </h3>
  </div>
  

  <div class="descripcion-box"> 
    <p> Entre los 18 y los 24 años, Lionel Messi y Diego Maradona vivieron sus etapas más explosivas frente al arco. A partir de datos oficiales de
    ligas, copas nacionales e internacionales, se trazó un mapa detallado de los goles que convirtieron durante sus respectivos primes.</p> 
    <p>El gráfico revela un contraste marcado en sus estilos de definición. <strong>Messi</strong> concentra sus goles en las esquinas del arco,
    evitando sistemáticamente el centro. Su tendencia a buscar los ángulos no solo habla de precisión, sino también de una lectura quirúrgica del 
    juego. Además, se destaca por anotar desde una mayor variedad de posiciones y alcanzar un volumen goleador superior.</p> 
    <p><strong>Maradona</strong>, en cambio, muestra una preferencia por definir en zonas más centrales del arco. Esta preferencia puede explicarse
    por su explosividad, potencia de remate y su capacidad de decidir en fracciones de segundo dentro del área. Este patrón refleja un estilo más 
    directo, más visceral, y profundamente efectivo en el contexto del fútbol de su época.</p> 
  </div>

   <section class="charts-section">

    <!-- PRIMERA FILA: Gráfico a la izquierda, texto a la derecha -->
    <div class="chart-row-double">
      <div class="chart-box-half">
        <div class="flourish-embed flourish-chart" data-src="visualisation/22585199">
          <script src="https://public.flourish.studio/resources/embed.js"></script>
        </div>
      </div>
      <div class="text-container">
        <h3 class="chart-title" style="margin-left: 10px;">Carreras Contrastantes: La Evolución de Messi y Maradona entre los 18 y 24 años</h3>
        <p class="chart-description" style="margin-left: 10px;">
          <strong>Messi</strong> muestra una progresión constante, sin señales de freno. Su evolución es reflejo de una carrera sólida, marcada por
          su adaptación temprana al fútbol de élite. <br>
          
          En cambio, <strong>Maradona</strong> alcanza su punto más alto a los 18, seguido de un descenso marcado, reflejo de una carrera más irregular en sus 
          inicios, aunque brillante en momentos puntuales. <br>

          Esta comparación no busca determinar quién es mejor, sino evidenciar los distintos ritmos de desarrollo que pueden tener incluso los más
          grandes talentos.
        </p>
      </div>  
    </div>
  
    <!-- SEGUNDA FILA: Gráfico a la derecha, texto a la izquierda -->
    <div class="chart-row-double row-reverse">
      <div class="chart-box-half">
        <div class="flourish-embed flourish-chart" data-src="visualisation/22585254">
          <script src="https://public.flourish.studio/resources/embed.js"></script>
        </div>
      </div>
      <div class="text-container">
        <h3 class="chart-title">Consistencia vs Variabilidad: <br> Goles por Club</h3>
        <p class="chart-description" style="margin-right: 10px;">
          <strong>Messi</strong> demuestra una notable consistencia, manteniendo un nivel goleador alto y regular sin importar 
          el equipo en el que juegue. Su capacidad de adaptación le permite destacar tanto en clubes históricos como en nuevas ligas. <br>
          En contraste, <strong>Maradona</strong> presenta una trayectoria más irregular. Esta variabilidad es causada por distintos 
          contextos, roles y circunstancias personales a lo largo de su paso por diferentes clubes.<br>
        </p>
      </div>
    </div>

   
      <h3 class="final-title">Evolución de los Trofeos a lo Largo de los Años</h3>
      <div class="chart-box">
        <div class="flourish-embed flourish-chart" data-src="visualisation/22585302" style="height: 600px;">
          <script src="https://public.flourish.studio/resources/embed.js"></script>
        </div>
      </div>
      <p class="chart-description">
        <strong>Messi</strong> no solo mantiene un ritmo constante de títulos, sino que incluso logra incrementarlo con el paso del tiempo, consolidando una carrera
        marcada por la regularidad, la excelencia y el éxito sostenido en distintos equipos y competiciones. En cambio, <strong>Maradona</strong> alcanza su mayor 
        cosecha de títulos en una etapa temprana de su carrera, seguida por una disminución progresiva en la cantidad de trofeos obtenidos, 
        reflejo de una carrera más intermitente y afectada por factores externos como lesiones, cambios de equipo y contextos futbolísticos 
        variables.
      </p>

  </section>


  <footer class="footer">
    <div class="footer-content">
      <a href="https://github.com/Sofiik1/Visual" target="_blank"> <i class="fab fa-github"></i> Repositorio en GitHub </a>
      |
      <a href="https://www.linkedin.com/in/sofia-kutter" target="_blank">  <i class="fab fa-linkedin"></i> Sofía Kutter </a>
      |
      <a href="https://www.linkedin.com/in/sofia-kutter" target="_blank">  <i class="fab fa-linkedin"></i> Ezequiel Mautner</a>
    </div>
  </footer>
  
</main>

<style>
  .cardinal-container {
    position:absolute;
    align-items:center;
    top: 25px;
    left: 25px;
    width: 94%;
    height: 95%;
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: repeat(6, 1fr);
    margin-bottom: 20px;
  }


</style>
