<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<style>
  @reference "./page.css";

  .outdoor-couple-container {
    @apply h-screen;
    @apply bg-[url(/images/outdoor_couple_2.png)];
    @apply bg-cover;
  }
</style>

<div class="outdoor-couple-container">
</div>
