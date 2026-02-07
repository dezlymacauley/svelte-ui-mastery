<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";

  import MainArea from "./sections/MainArea.svelte";
  import SidebarArea from "./sections/SidebarArea.svelte";

  let sidebarOpen: boolean = true;
</script>

<style>
  @reference "./page.css";

  .ui-container {
    /* @apply flex; */
    @apply border-4 border-green-500 h-screen flex;
  }
</style>

<!---------------------------------------------------------------------------->

<div class="ui-container">
  <SidebarArea />
  <MainArea />
</div>
