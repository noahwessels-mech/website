<script>
  import { page } from '$app/stores'; // Import page store to get current route
  
  let menuOpen = false;
  let projectsOpen = false;
  
  function toggleMenu() {
    menuOpen = !menuOpen;
  }
  
  function toggleProjects() {
    projectsOpen = !projectsOpen;
  }
  
  // Helper function to check if current path matches menu item
  $: currentPath = $page.url.pathname;
  
  // Check if any project submenu is active
  $: isProjectsActive = currentPath === '/uveec' || currentPath === '/machiningPortfolio' || currentPath === '/violinMaking';
  
  // Helper function to get menu item classes
  function getMenuClass(path, isActive = false) {
    const baseClass = "transition-colors duration-200";
    if (isActive) {
      return `${baseClass} text-blue-600 font-semibold`;
    }
    return `${baseClass} text-gray-600 hover:text-gray-900`;
  }
  
  // Helper function for mobile menu classes
  function getMobileMenuClass(path, isActive = false) {
    const baseClass = "block px-6 py-3 transition-colors duration-200";
    if (isActive) {
      return `${baseClass} text-blue-600 font-semibold bg-blue-50 border-r-4 border-blue-600`;
    }
    return `${baseClass} text-gray-600 hover:text-gray-900 hover:bg-gray-50`;
  }
  
  // Helper function for submenu classes
  function getSubmenuClass(path, isActive = false) {
    const baseClass = "block px-4 py-2 transition-colors duration-150";
    if (isActive) {
      return `${baseClass} text-blue-600 font-semibold bg-blue-50`;
    }
    return `${baseClass} text-gray-600 hover:bg-gray-100 hover:text-gray-900`;
  }
  
  // Helper function for mobile submenu classes
  function getMobileSubmenuClass(path, isActive = false) {
    const baseClass = "block px-8 py-2 transition-colors duration-150";
    if (isActive) {
      return `${baseClass} text-blue-600 font-semibold bg-blue-100 border-r-4 border-blue-600`;
    }
    return `${baseClass} text-gray-600 hover:bg-gray-100`;
  }
</script>

<nav class="fixed top-0 w-full bg-white/90 backdrop-blur-md border-b border-gray-200 z-50">
  <div class="container mx-auto px-6 py-4 flex justify-between items-center">
    <div class="text-2xl font-bold text-gray-800">NW</div>
    <!-- Desktop Links -->
    <div class="hidden md:flex space-x-8 items-center">
      <a href="/" class={getMenuClass('/', currentPath === '/')}>Home</a>
      <!-- CSS-based hover dropdown with proper spacing -->
      <div class="relative group">
        <button class="flex items-center transition-colors duration-200 focus:outline-none py-2 {isProjectsActive ? 'text-blue-600 font-semibold' : 'text-gray-600 hover:text-gray-900'}">
          Projects
          <!-- Add active indicator dot -->
          {#if isProjectsActive}
            <span class="ml-1 w-1.5 h-1.5 bg-blue-600 rounded-full"></span>
          {/if}
          <svg class="ml-1 w-4 h-4 transition-transform duration-200 group-hover:rotate-180" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
          </svg>
        </button>
        <!-- Invisible bridge to prevent gap -->
        <div class="absolute top-full left-0 w-48 h-2 bg-transparent group-hover:block hidden"></div>
        <!-- Actual dropdown menu -->
        <div class="absolute top-full left-0 mt-2 bg-white shadow-lg rounded-md py-2 w-48 opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-200 transform translate-y-1 group-hover:translate-y-0">
          <a href="/uveec" class={getSubmenuClass('/uveec', currentPath === '/uveec')}>
            UVEEC
            {#if currentPath === '/uveec'}
              <span class="ml-2 w-2 h-2 bg-blue-600 rounded-full inline-block"></span>
            {/if}
          </a>
          <a href="/machiningPortfolio" class={getSubmenuClass('/machiningPortfolio', currentPath === '/machiningPortfolio')}>
            Machining
            {#if currentPath === '/machiningPortfolio'}
              <span class="ml-2 w-2 h-2 bg-blue-600 rounded-full inline-block"></span>
            {/if}
          </a>
          <a href="/violinMaking" class={getSubmenuClass('/violinMaking', currentPath === '/violinMaking')}>
            Violin Making
            {#if currentPath === '/violinMaking'}
              <span class="ml-2 w-2 h-2 bg-blue-600 rounded-full inline-block"></span>
            {/if}
          </a>
        </div>
      </div>
      <a href="/experiences" class={getMenuClass('/experiences', currentPath === '/experiences')}>Experiences</a>
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
      <a href="/" class={getMobileMenuClass('/', currentPath === '/')}>Home</a>
      <button class="w-full text-left px-6 py-3 flex justify-between items-center focus:outline-none transition-colors duration-200 {isProjectsActive ? 'text-blue-600 font-semibold bg-blue-50 border-r-4 border-blue-600' : 'text-gray-600 hover:text-gray-900 hover:bg-gray-50'}" on:click={toggleProjects}>
        <span class="flex items-center">
          Projects
          {#if isProjectsActive}
            <span class="ml-2 w-1.5 h-1.5 bg-blue-600 rounded-full"></span>
          {/if}
        </span>
        <svg class="w-4 h-4 transition-transform duration-200 {projectsOpen ? 'rotate-180' : ''}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
        </svg>
      </button>
      {#if projectsOpen}
        <div class="bg-gray-50">
          <a href="/uveec" class={getMobileSubmenuClass('/uveec', currentPath === '/uveec')}>
            UVEEC
            {#if currentPath === '/uveec'}
              <span class="ml-2 w-2 h-2 bg-blue-600 rounded-full inline-block"></span>
            {/if}
          </a>
          <a href="/machiningPortfolio" class={getMobileSubmenuClass('/machiningPortfolio', currentPath === '/machiningPortfolio')}>
            Machining
            {#if currentPath === '/machiningPortfolio'}
              <span class="ml-2 w-2 h-2 bg-blue-600 rounded-full inline-block"></span>
            {/if}
          </a>
          <a href="/violinMaking" class={getMobileSubmenuClass('/violinMaking', currentPath === '/violinMaking')}>
            Violin Making
            {#if currentPath === '/violinMaking'}
              <span class="ml-2 w-2 h-2 bg-blue-600 rounded-full inline-block"></span>
            {/if}
          </a>
        </div>
      {/if}
      <a href="/experiences" class={getMobileMenuClass('/experiences', currentPath === '/experiences')}>Experiences</a>
    </div>
  {/if}
</nav>

<style>
  /* Shift body content down below navbar */
</style>