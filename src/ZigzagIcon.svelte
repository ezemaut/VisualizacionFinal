<!-- ZigzagIcon.svelte -->
<script>
  export let size = 64;
  export let color = "#f8b400"; // naranja vibrante
</script>

<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 100 100"
  width={size}
  height={size}
  fill="none"
>
  <path
    d="M30 20 L50 40 L40 60 L60 80"
    stroke={color}
    stroke-width="12"
    stroke-linecap="round"
    stroke-linejoin="round"
  />
</svg>