<!-- CurvedAbstractIcon.svelte -->
<script>
  export let size = 64;
  export let color = "#8bc34a"; // verde lima
</script>

<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 100 100"
  width={size}
  height={size}
  fill="none"
>
  <path
    d="M10 80
       C20 60, 40 60, 50 80
       C60 100, 80 90, 80 70
       C80 50, 60 40, 50 50
       C40 60, 20 40, 10 20"
    fill="none"
    stroke={color}
    stroke-width="10"
    stroke-linecap="round"
    stroke-linejoin="round"
  />
</svg>