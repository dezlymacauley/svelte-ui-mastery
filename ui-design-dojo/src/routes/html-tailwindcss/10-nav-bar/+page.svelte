<svelte:head><link rel="icon" href={favicon} /></svelte:head>
<svelte:window on:click={handleClickOutside} />

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";

  let isDropdownOpen = false;
  
  function toggleDropdown() {
    isDropdownOpen = !isDropdownOpen;
  }
  
  // Close dropdown when clicking outside
  function handleClickOutside(event: MouseEvent) {
    const target = event.target as HTMLElement;
    if (isDropdownOpen && !target.closest('.dropdown-container')) {
      isDropdownOpen = false;
    }
  }
</script>

<style>
  @reference "./page.css";
</style>

<!---------------------------------------------------------------------------->

<div class="min-h-screen bg-slate-950">
  <nav class="fixed top-0 left-0 right-0 z-50 bg-slate-900 border-b border-slate-800">
    <div class="max-w-8xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Logo and Brand -->
        <div class="flex items-center gap-8">
          <a href="/" class="flex items-center gap-3">
            <div class="w-8 h-8 bg-cyan-400 rounded-lg flex items-center justify-center">
              <svg class="w-6 h-6 text-slate-900" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2L2 7v10c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V7l-10-5z"/>
              </svg>
            </div>
            <span class="text-white font-semibold text-lg">tailwindcss</span>
          </a>
          
          <!-- Version Dropdown -->
          <div class="relative dropdown-container">
            <button
              on:click|stopPropagation={toggleDropdown}
              class="flex items-center gap-2 px-3 py-1.5 text-sm text-slate-300 hover:text-white bg-slate-800 hover:bg-slate-700 rounded-md transition-colors"
            >
              <span>v4.1</span>
              <svg 
                class="w-4 h-4 transition-transform {isDropdownOpen ? 'rotate-180' : ''}" 
                fill="none" 
                stroke="currentColor" 
                viewBox="0 0 24 24"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
              </svg>
            </button>
            
            {#if isDropdownOpen}
              <div class="absolute top-full mt-2 left-0 w-32 bg-slate-800 rounded-lg shadow-xl border border-slate-700 py-1">
                <a href="/v4.1" class="block px-4 py-2 text-sm text-white bg-slate-700 hover:bg-slate-600">
                  <div class="flex items-center justify-between">
                    <span>v4.1</span>
                    <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
                      <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                    </svg>
                  </div>
                </a>
                <a href="/v3.4.17" class="block px-4 py-2 text-sm text-slate-300 hover:text-white hover:bg-slate-700">v3.4.17</a>
                <a href="/v2.2.19" class="block px-4 py-2 text-sm text-slate-300 hover:text-white hover:bg-slate-700">v2.2.19</a>
                <a href="/v1.9.6" class="block px-4 py-2 text-sm text-slate-300 hover:text-white hover:bg-slate-700">v1.9.6</a>
                <a href="/v0.7.4" class="block px-4 py-2 text-sm text-slate-300 hover:text-white hover:bg-slate-700">v0.7.4</a>
              </div>
            {/if}
          </div>
        </div>
        
        <!-- Navigation Links -->
        <div class="flex items-center gap-8">
          <button class="flex items-center gap-2 text-sm text-slate-400 hover:text-white transition-colors">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
            </svg>
            <span>Ctrl K</span>
          </button>
          
          <a href="/docs" class="text-sm text-slate-300 hover:text-white transition-colors">
            Docs
          </a>
          
          <a href="/blog" class="text-sm text-slate-300 hover:text-white transition-colors">
            Blog
          </a>
          
          <a href="/showcase" class="text-sm text-slate-300 hover:text-white transition-colors">
            Showcase
          </a>
          
          <a href="/sponsor" class="text-sm text-slate-300 hover:text-white transition-colors">
            Sponsor
          </a>
          
          <a 
            href="/plus" 
            class="px-3 py-1.5 text-sm text-cyan-400 border border-cyan-400 hover:bg-cyan-400 hover:text-slate-900 rounded-md transition-colors"
          >
            Plus
          </a>
          
          <a href="https://github.com" class="text-slate-300 hover:text-white transition-colors" aria-label="GitHub">
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </nav>
  
  <!-- Add padding-top to account for fixed navbar -->
  <main class="pt-16">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <h1 class="text-5xl font-bold text-white mb-8">
        Rapidly build modern websites without ever leaving your HTML
      </h1>
      
      <p class="text-xl text-slate-400 mb-12">
        A utility-first CSS framework packed with classes that can be composed to build any design, directly in your markup.
      </p>
      
      <!-- Demo content sections to enable scrolling -->
      {#each Array(10) as _, i}
        <section class="mb-16 bg-slate-900 rounded-lg p-8 border border-slate-800">
          <h2 class="text-3xl font-bold text-white mb-4">Section {i + 1}</h2>
          <p class="text-slate-400 mb-4">
            This is demo content to show the sticky navbar in action. Scroll down to see the navbar stay at the top of the page.
          </p>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div class="bg-slate-800 rounded p-4">
              <div class="w-12 h-12 bg-cyan-400 rounded-lg mb-3"></div>
              <h3 class="text-white font-semibold mb-2">Feature A</h3>
              <p class="text-slate-400 text-sm">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
            </div>
            <div class="bg-slate-800 rounded p-4">
              <div class="w-12 h-12 bg-purple-400 rounded-lg mb-3"></div>
              <h3 class="text-white font-semibold mb-2">Feature B</h3>
              <p class="text-slate-400 text-sm">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
            </div>
            <div class="bg-slate-800 rounded p-4">
              <div class="w-12 h-12 bg-pink-400 rounded-lg mb-3"></div>
              <h3 class="text-white font-semibold mb-2">Feature C</h3>
              <p class="text-slate-400 text-sm">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
            </div>
          </div>
        </section>
      {/each}
    </div>
  </main>
</div>
