<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!--
  Unlike the `body` html element, 
  the div element (and other container elements) 
  do not have a default height. 

  Its height depends on the total height used by the html elements inside it.
  So if a div is empty, you won't be able to see 
  the effects of `bg-purple-950` unless you explicitly set the height 
  of the div.

  `h-screen` sets the height of the div to the height of the viewport.
-->
<div class="bg-purple-950 h-screen">

</div>
