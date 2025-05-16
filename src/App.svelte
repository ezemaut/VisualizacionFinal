<script>
  import SpiralIcon from './SpiralIcon.svelte';
  import DoubleDiamondIcon from './DoubleDiamondIcon.svelte';
  import ZigzagIcon from './ZigzagIcon.svelte';
  import C from './C.svelte';
  import BrushZIcon from './BrushZIcon.svelte';
  import Python from './Py.svelte';
  import SemiArcsIcon from './SemiArcsIcon.svelte';
  import WavyLineIcon from './WavyLineIcon.svelte';
  import StarIcon from './StarIcon.svelte';
  import LoopyStrokeIcon from './LoopyStrokeIcon.svelte';
  import AbstractBlobIcon from './AbstractBlobIcon.svelte';

  const iconComponents = {
    SpiralIcon,
    DoubleDiamondIcon,
    ZigzagIcon,
    C,
    BrushZIcon,
    Python,
    SemiArcsIcon,
    WavyLineIcon,
    StarIcon,
    LoopyStrokeIcon,
    AbstractBlobIcon
  };

/*  
Combinaciones:
javascript, css, svelte   -> 'ZigzagIcon', 'SpiralIcon', 'BrushZIcon'
html  -> 'AbstractBlobIcon'
python, css, html  -> 'Python', 'SpiralIcon', 'AbstractBlobIcon'
python, html  -> 'Python', 'AbstractBlobIcon'
python  -> 'Python',
python, c++  -> 'Python', 'LoopyStrokeIcon'
python, c  -> 'Python', 'C'
c  -> 'C'

'SpiralIcon',   javascript    
'DoubleDiamondIcon', 
'ZigzagIcon',         css 
'C',              
'BrushZIcon',        svelete
'Python',          
'SemiArcsIcon',        
'LoopyStrokeIcon',   html
'AbstractBlobIcon'   c++

'WavyLineIcon',   peso   
'StarIcon',       commit   
*/

const iconLayout = {
  SpiralIcon:        { x: '80%', y: '0%',    zIndex: 2, scale: 4},
  DoubleDiamondIcon: { x: '15%',  y: '50%',  zIndex: 1, scale: 1.5 },
  ZigzagIcon:        { x: '15%',  y: '75%',  zIndex: 3, scale: 5 },
  C:                 { x: '53%',  y: '50%',  zIndex: 2, scale: 6},
  BrushZIcon:        { x: '80%',  y: '95%',   zIndex: 0, scale: 8.2 },
  Python:            { x: '67%',  y: '50%',  zIndex: 0, scale: 7 },
  SemiArcsIcon:      { x: '90%',  y: '85%',  zIndex: 2, scale: 1.5 },  // big one!
  WavyLineIcon:      { x: '50%',  y: '80%',  zIndex: 0, scale: 1.5 },
  StarIcon:          { x: '15%',  y: '15%',  zIndex: 3, scale: 1.5 },
  LoopyStrokeIcon:   { x: '45%',   y: '45%',  zIndex: 2, scale: 8 },
  AbstractBlobIcon:  { x: '35%',   y: '60%',   zIndex: 1, scale: 5 }
};


let todos = [
   {  nombre: 'Spotify Skip',
      gusto: true,
      iconos: ['StarIcon','SpiralIcon', 'ZigzagIcon', 'BrushZIcon']
    },

   {  nombre: '',
      gusto: false,
      iconos: ['StarIcon','LoopyStrokeIcon',]
    },
   {  nombre: '',
      gusto: true,
      iconos: ['StarIcon','Python', 'ZigzagIcon', 'LoopyStrokeIcon',]
    },

   {  nombre: '',
      gusto: false,
      iconos: ['StarIcon','Python', 'LoopyStrokeIcon',]
    },
   {  nombre: '',
      gusto: true,
      iconos: ['StarIcon','Python',]
    },

   {  nombre: '',
      gusto: false,
      iconos: ['StarIcon','Python', 'AbstractBlobIcon']
    },
   {  nombre: '',
      gusto: true,
      iconos: ['StarIcon','Python', 'C']
    },

   {  nombre: '',
      gusto: false,
      iconos: ['StarIcon','C']
    },

]


    
 const baseIconSize = 50;  // for example, 50px base size
   
</script>

<main class="page">

  <h1 class="title">Todos Repos Posibles</h1>
  <div class="cajas">
    {#each todos as t}
        <div class="colab-box-BIG" style="border-color: {t.gusto ? 'limegreen' : 'deeppink'}">
          <div class="icon-layer-BIG">

           {#each t.iconos as nombre}
            {#if iconComponents[nombre] && iconLayout[nombre]}
              <svelte:component
                this={iconComponents[nombre]}
                size={baseIconSize * iconLayout[nombre].scale}
                class="icon-item-BIG"
                style={`position: absolute;
                        left: ${iconLayout[nombre].x};
                        top: ${iconLayout[nombre].y};
                        transform: translate(-50%, -50%);
                        z-index: ${iconLayout[nombre].zIndex ?? 0};
                        pointer-events: none;`}
              />
            {/if}
          {/each}

          </div>
        </div>
      {/each}
  </div>

  <h2 class="subtitulo">Leyenda de íconos</h2>
  <div class="leyenda">
    <div><WavyLineIcon height={60} color="#e76f51" /> <span>Cantidad de líneas segun intervalo de peso </span></div>
    <div><StarIcon size={40} color="#d673ec" /> <span>Commits, tamaño según cantidad </span></div>
    <div><LoopyStrokeIcon size={40} color1="#8bc34a"  /> <span>HTML</span></div>
    <div><Python size={40} color="#00897b" /> <span>Python</span></div>
    <div><SpiralIcon size={40} color="#ffd97d" /> <span>JavaScript</span></div>
    <div><AbstractBlobIcon size={40} color1="#cceeff"  /> <span>C++</span></div>
    <div><C size={40} color="#ff9900" /> <span>C</span></div>
    <div><BrushZIcon size={40} color="#a142e0" /> <span>Svelte</span></div>
    <div><ZigzagIcon size={40} color="#bfaeff" /> <span>CSS</span></div>
  </div>

  <footer class="footer">
    <div class="footer-content">
      <a href="https://github.com/Sofiik1/Visual" target="_blank">Repositorio en GitHub</a>
      <span>|</span>
      <a href="https://www.linkedin.com/in/sofia-kutter" target="_blank">Sofía Kutter</a>
      <span>|</span>
      <a href="https://www.linkedin.com/in/ezequiel-mautner" target="_blank">Ezequiel Mautner</a>
    </div>
  </footer>
</main>

<style>
  .page {
    background-color: #111;
    color: white;
    min-height: 100vh;
    padding: 2rem;
    text-align: center;
  }
  .cajas {
    display: flex;
    justify-content: center;
    gap: 2rem;
    flex-wrap: wrap;
    margin-bottom: 3rem;
  }
  .colab-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .colab-box {
    background-color: black;
    border: 5px solid;
    border-radius: 16px;
    width: 200px;
    height: 200px;
    position: relative;
    overflow: hidden;
  }
  .icon-layer {
    position: relative;
    inset: 0;
    width: 180px;
    height: 240px;
  }


.icon-item {
  position: absolute;
  animation: float 6s ease-in-out infinite;
}

  .icon-0 { top: 10%; left: 5%; }
  .icon-1 { top: 50%; left: 15%; }
  .icon-2 { top: 30%; right: 5%; }
  .icon-3 { bottom: 10%; left: 30%; }
  .icon-4 { top: 5%; right: 20%; }

  @keyframes float {
    0%, 100% { transform: translateY(0px); }
    50% { transform: translateY(-10px); }
  }

  .nombre {
    margin-top: 0.5rem;
    font-weight: bold;
  }
  .subtitulo {
    font-size: 1.4rem;
    font-weight: bold;
    margin-bottom: 1rem;
  }
  .leyenda {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 1rem;
    align-items: center;
    text-align: left;
    margin-bottom: 2rem;
  }
  .leyenda div {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .footer-content {
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
    font-size: 0.9rem;
  }
</style>
