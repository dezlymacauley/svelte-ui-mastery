<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!--
  `size` allows you to set the height and width of an element at the same
  time. E.g. `size-20` is the same as `h-20 w-20`

  This can be quite useful for creating squares
-->
<div class="bg-amber-300 size-20">

</div>

<!--
  This is the long version
-->
<div class="bg-pink-500 h-20 w-20">

</div>
