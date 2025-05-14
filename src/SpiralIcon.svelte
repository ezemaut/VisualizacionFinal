<!-- SpiralIcon.svelte -->
<script>
  export let color = "#c9b8f8"; // Color violeta pastel
  export let size = 64;         // Tamaño en px
</script>


<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 100 100"
  width={size}
  height={size}
  fill="none"
>
  <path
    d="M50,50
       c0,-15 -20,-15 -20,0
       c0,10 10,20 20,20
       c20,0 30,-20 30,-40
       c0,-25 -25,-40 -50,-40"
    stroke={color}
    stroke-width="6"
    stroke-linecap="round"
    fill="none"
  />
</svg>
