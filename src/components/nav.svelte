<script>
    let menuOpen = false;
    let projectsOpen = false;
    function toggleMenu() {
      menuOpen = !menuOpen;
    }
    function toggleProjects() {
      projectsOpen = !projectsOpen;
    }
  </script>
  
  <nav class="fixed top-0 w-full bg-white/90 backdrop-blur-md border-b border-gray-200 z-50">
    <div class="container mx-auto px-6 py-4 flex justify-between items-center">
      <div class="text-2xl font-bold text-gray-800">NW</div>
      <!-- Desktop Links -->
      <div class="hidden md:flex space-x-8 items-center">
        <a href="/" class="text-gray-600 hover:text-gray-900 transition-colors duration-200">Home</a>
        <!-- CSS-based hover dropdown with proper spacing -->
        <div class="relative group">
          <button class="flex items-center text-gray-600 hover:text-gray-900 transition-colors duration-200 focus:outline-none py-2">
            Projects
            <svg class="ml-1 w-4 h-4 transition-transform duration-200 group-hover:rotate-180" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
            </svg>
          </button>
          <!-- Invisible bridge to prevent gap -->
          <div class="absolute top-full left-0 w-48 h-2 bg-transparent group-hover:block hidden"></div>
          <!-- Actual dropdown menu -->
          <div class="absolute top-full left-0 mt-2 bg-white shadow-lg rounded-md py-2 w-48 opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-200 transform translate-y-1 group-hover:translate-y-0">
            <a href="/uveec" class="block px-4 py-2 text-gray-600 hover:bg-gray-100 hover:text-gray-900 transition-colors duration-150">UVEEC</a>
            <a href="/machiningPortfolio" class="block px-4 py-2 text-gray-600 hover:bg-gray-100 hover:text-gray-900 transition-colors duration-150">Machining</a>
            <a href="/violinMaking" class="block px-4 py-2 text-gray-600 hover:bg-gray-100 hover:text-gray-900 transition-colors duration-150">Violin Making</a>
          </div>
        </div>
        <a href="/experiences" class="text-gray-600 hover:text-gray-900 transition-colors duration-200">Experiences</a>
      </div>
      <!-- Mobile toggle -->
      <button class="md:hidden text-gray-600 focus:outline-none" on:click={toggleMenu}>
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          {#if menuOpen}
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          {:else}
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          {/if}
        </svg>
      </button>
    </div>
    <!-- Mobile menu -->
    {#if menuOpen}
      <div class="md:hidden bg-white border-t border-gray-200">
        <a href="/" class="block px-6 py-3 text-gray-600 hover:text-gray-900">Home</a>
        <button class="w-full text-left px-6 py-3 flex justify-between items-center text-gray-600 hover:text-gray-900 focus:outline-none" on:click={toggleProjects}>
          Projects
          <svg class="w-4 h-4 transition-transform duration-200 {projectsOpen ? 'rotate-180' : ''}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
          </svg>
        </button>
        {#if projectsOpen}
          <div class="bg-gray-50">
            <a href="/uveec" class="block px-8 py-2 text-gray-600 hover:bg-gray-100">UVEEC</a>
            <a href="/machiningPortfolio" class="block px-8 py-2 text-gray-600 hover:bg-gray-100">Machining</a>
            <a href="/violinMaking" class="block px-8 py-2 text-gray-600 hover:bg-gray-100">Violin Making</a>
          </div>
        {/if}
        <a href="/experiences" class="block px-6 py-3 text-gray-600 hover:text-gray-900">Experiences</a>
      </div>
    {/if}
  </nav>
  
  <style>
    /* Shift body content down below navbar */
    :global(body) {
      margin-top: 4rem;
    }
  </style>