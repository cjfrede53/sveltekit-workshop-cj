<script>
  export let label = "Button";
  export let bgColor = "bg-blue-500";
  export let onClick = () => {};
</script>

<button
  class={`px-4 py-2 rounded text-white font-semibold
          ${bgColor}
          hover:opacity-80
          focus:outline-none focus:ring-2 focus:ring-offset-2
          active:scale-95 transition`}
  on:click={onClick}
>
  {label}
</button>