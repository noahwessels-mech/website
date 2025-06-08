<script>
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';
  
    export let title = "";
    export let highlighted = "";
    export let subtitle = "";
    export let primaryButton = "";
    export let secondaryButton = "";
    export let showButtons = true;
  
    export let onPrimaryClick = () => {};
    export let onSecondaryClick = () => {};
  
    let mounted = false;
    onMount(() => {
      mounted = true;
    });
  </script>
  
  <section 
    class="relative bg-gradient-to-br from-gray-700 via-gray-600 to-slate-500 text-white py-32 px-6 flex flex-col items-center text-center overflow-hidden min-h-[70vh]"
    in:fade={{ duration: 800 }}
  >
    <div class="max-w-4xl z-10">
      {#if title || highlighted}
        <h1 class="text-5xl md:text-7xl font-extrabold mb-6 leading-tight">
          {@html title}<br>
          <span class="text-blue-200">{highlighted}</span>
        </h1>
      {/if}
  
      {#if subtitle}
        <p class="text-xl md:text-2xl text-gray-200 leading-relaxed max-w-3xl mx-auto mb-8">
          {subtitle}
        </p>
      {/if}
  
      {#if mounted && showButtons && (primaryButton || secondaryButton)}
        <div class="flex flex-col sm:flex-row gap-4 justify-center" in:fly={{ y: 30, delay: 400, duration: 600 }}>
          {#if primaryButton}
            <button
              class="bg-white text-gray-800 px-8 py-3 rounded-full font-semibold hover:bg-gray-100 transition-all duration-300 transform hover:scale-105"
              on:click={onPrimaryClick}
            >
              {primaryButton}
            </button>
          {/if}
  
          {#if secondaryButton}
            <button
              class="border-2 border-white text-white px-8 py-3 rounded-full font-semibold hover:bg-white hover:text-gray-800 transition-all duration-300"
              on:click={onSecondaryClick}
            >
              {secondaryButton}
            </button>
          {/if}
        </div>
      {/if}
    </div>
  
    <!-- Geometric Background Elements -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div class="absolute top-20 left-10 w-32 h-32 bg-white/5 rounded-full blur-xl"></div>
      <div class="absolute top-40 right-20 w-24 h-24 bg-blue-200/10 rounded-full blur-lg"></div>
      <div class="absolute bottom-40 left-1/4 w-40 h-40 bg-white/3 rounded-full blur-2xl"></div>
    </div>
  
    <!-- Hero Fade Overlay -->
    <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-b from-transparent via-gray-700/30 to-gray-700/80 pointer-events-none"></div>
  </section>
  
  <style>
    section :global(button) {
      cursor: pointer;
    }
  </style>
  