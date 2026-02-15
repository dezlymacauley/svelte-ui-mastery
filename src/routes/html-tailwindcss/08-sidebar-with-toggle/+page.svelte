<script lang="ts">
  import favicon from "$lib/svg/svelte_logo.svg";
  import "$lib/css/default.css"

  import MainArea from "./sections/MainArea.svelte";
  import SidebarArea from "./sections/SidebarArea.svelte";
</script>

<style>
  @reference "$lib/css/default.css";

  .ui-container {
    /* @apply flex; */
    @apply border-4 border-green-500 h-screen flex;
  }
</style>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!---------------------------------------------------------------------------->

<div class="ui-container">
  <SidebarArea />
  <MainArea />
</div>
