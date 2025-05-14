<!-- BrushZIcon.svelte -->
<script>
  export let size = 64;
  export let color = "#b24fe1"; // violeta intenso
</script>

<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 100 100"
  width={size}
  height={size}
  fill="none"
>
  <path
    d="M20 30 L40 20 L30 50 L60 30 L50 60 L80 40"
    stroke={color}
    stroke-width="6"
    stroke-linecap="round"
    stroke-linejoin="round"
    fill="none"
  />
</svg>