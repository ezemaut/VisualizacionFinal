<script>
  import SpiralIcon from './SpiralIcon.svelte';
  import DoubleDiamondIcon from './DoubleDiamondIcon.svelte';
  import ZigzagIcon from './ZigzagIcon.svelte';
  import CurvedRibbonIcon from './CurvedRibbonIcon.svelte';
  import BrushZIcon from './BrushZIcon.svelte';
  import SwooshIcon from './SwooshIcon.svelte';
  import SemiArcsIcon from './SemiArcsIcon.svelte';
  import WavyLineIcon from './WavyLineIcon.svelte';
  import StarIcon from './StarIcon.svelte';
  import LoopyStrokeIcon from './LoopyStrokeIcon.svelte';
  import AbstractBlobIcon from './AbstractBlobIcon.svelte';

  let colaboradores = [
    {
      nombre: 'Lobo',
      gusto: true,
      iconos: [
        'WavyLineIcon',
        'SwooshIcon',
        'CurvedRibbonIcon',
        'StarIcon',
        'SpiralIcon',
        'AbstractBlobIcon'
      ]
    },
    {
      nombre: 'Kutter',
      gusto: false,
      iconos: [
        'WavyLineIcon',
        'SwooshIcon',
        'CurvedRibbonIcon',
        'StarIcon',
        'SpiralIcon'
      ]
    },
    {
      nombre: 'Mautner',
      gusto: true,
      iconos: [
        'WavyLineIcon',
        'SwooshIcon',
        'CurvedRibbonIcon',
        'StarIcon',
        'SpiralIcon',
        'LoopyStrokeIcon'
      ]
    }
  ];

  const iconComponents = {
    SpiralIcon,
    DoubleDiamondIcon,
    ZigzagIcon,
    CurvedRibbonIcon,
    BrushZIcon,
    SwooshIcon,
    SemiArcsIcon,
    WavyLineIcon,
    StarIcon,
    LoopyStrokeIcon,
    AbstractBlobIcon
  };
</script>

<main class="page">
  <h1 class="title">Spotify Skip – 2025</h1>
  <div class="cajas">
    {#each colaboradores as c}
      <div class="colab-container">
        <div class="colab-box" style="border-color: {c.gusto ? 'limegreen' : 'deeppink'}">
          <div class="icon-layer">
            {#each c.iconos as nombre, i}
              {#if iconComponents[nombre]}
                <svelte:component this={iconComponents[nombre]} size={60} class="icon-item icon-{i}" />
              {/if}
            {/each}
          </div>
        </div>
        <p class="nombre">{c.nombre}</p>
      </div>
    {/each}
  </div>

  <h2 class="subtitulo">Leyenda de íconos</h2>
  <div class="leyenda">
    <div><WavyLineIcon height={60} color="#e76f51" /> <span>Cantidad de líneas segun intervalo de peso </span></div>
    <div><StarIcon size={40} color="#d673ec" /> <span>Commits, tamaño según cantidad </span></div>
    <div><SemiArcsIcon size={40} color1="#8bc34a" color2="#212529" /> <span>HTML</span></div>
    <div><SwooshIcon size={40} color="#00897b" /> <span>Python</span></div>
    <div><CurvedRibbonIcon size={40} color="#ffd97d" /> <span>JavaScript</span></div>
    <div><DoubleDiamondIcon size={40} color1="#cceeff" color2="#1a5dab" /> <span>C++</span></div>
    <div><ZigzagIcon size={40} color="#ff9900" /> <span>C</span></div>
    <div><BrushZIcon size={40} color="#a142e0" /> <span>Svelte</span></div>
    <div><SpiralIcon size={40} color="#bfaeff" /> <span>CSS</span></div>
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
    position: absolute;
    inset: 0;
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
