<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!--
  First you you need to give the div a height to see the effects of
  your styling. Width is one quarter of the parent container.

  Since +page.svelte is rendered in the `body` html element,
  that means the width of this div will be a 1/4 of the width of the body.
-->
<div class="bg-blue-500 h-screen w-1/4">

</div>
