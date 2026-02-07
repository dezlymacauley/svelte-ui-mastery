<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>


<style>
  @reference "./page.css";

  .brand-heading {

    /* 
      Apply a left → right background gradient to the width of the span
    */
    @apply bg-linear-to-r from-purple-500 to-fuchsia-900;

    /* The text must be large and bold enough for you to see the effects */
    @apply text-4xl font-extrabold;

    /* 
      Make the the area that contains the text color (inside the letters), 
      transparent.
    */
    @apply text-transparent;

    /*
      This will ensure that the background gradient color is only visible,
      inside the letters of the text, 
      instead of appearing across the entire `span` element.
    */
    @apply bg-clip-text;

  }

</style>

<div class="px-2 py-2">
  <span class="brand-heading">Dezly Macauley</span>
</div>
