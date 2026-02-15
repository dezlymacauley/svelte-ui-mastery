<script lang="ts">
  let sidebarOpen: boolean = true;
</script>

<!-- Sidebar -->
<div
  class="border-4 border-blue-500 items-end bg-gray-900 text-white transition-all duration-300 {sidebarOpen ? 'w-64' : 'w-32'} flex flex-col"
>
  <!-- Toggle button at top -->
  <!-- class="hover:bg-gray-800 p-2 cursor-w-resize" -->
  <div class="p-4">
    <button
      on:click={() => sidebarOpen = !sidebarOpen}
      class={`p-2 hover:bg-gray-800 ${
        sidebarOpen ? "cursor-w-resize" : "cursor-e-resize"
      }`}
    >
      {#if sidebarOpen}
        <!-- Display this icon when the sidebar is open -->
        <p class="text-xl">📂</p>
      {:else}
        <p class="text-xl">📁</p>
      {/if}
    </button>
  </div>

  <!-- Sidebar content (only show when open) -->
  {#if sidebarOpen}
    <div class="flex-1 overflow-y-auto">
      <div class="p-4">
        <!-- Your nav items -->
      </div>
    </div>
  {/if}
</div>
