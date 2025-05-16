<!-- CurvedRibbonIcon.svelte -->
<script>
  export let size = 64;
  export let color = "#f8d471"; // amarillo pastel
  export let style = "";
</script>

<svg
xmlns="http://www.w3.org/2000/svg"
viewBox="0 0 200 200"
width={size}
height={size}
fill="none"
style={style}
>
  <path
    d="M-20 30
       C40 140, 80 120, 100 100
       C120 80, 90 20, 80 10"
    stroke={color}
    stroke-width="20"
    stroke-linecap="round"
    stroke-linejoin="round"
    fill="none"
  />
</svg>

  