<!-- LoopyStrokeIcon.svelte -->
<script>
  export let size = 64;
  export let color = "#f03800"; // rojo intenso
</script>

<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 100 100"
  width={size}
  height={size}
  fill="none"
>
  <path
    d="M60 10
       C80 30, 30 30, 50 50
       C70 70, 20 70, 40 90"
    stroke={color}
    stroke-width="14"
    stroke-linecap="round"
    stroke-linejoin="round"
    fill="none"
  />
</svg>