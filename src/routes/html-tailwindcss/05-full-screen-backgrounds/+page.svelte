<script lang="ts">
  import favicon from "$lib/svg/svelte_logo.svg";
  import "$lib/css/default.css"
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!---------------------------------------------------------------------------->

<style>
  @reference "$lib/css/default.css";

  .outdoor-couple-container {
    @apply h-screen;
    @apply bg-[url(/images/outdoor_couple_2.png)];
    @apply bg-cover;
  }
</style>

<div class="outdoor-couple-container">
</div>
