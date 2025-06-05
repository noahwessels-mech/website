<script lang="ts">
    import { fade } from 'svelte/transition';
  
    // Props for the card group
    export let title = '';
    export let description = '';
    export let sections = [];
    export let maxWidth = 'max-w-7xl';
    export let gap = 'gap-12';
    export let animationDelay = 200;
    export let animationDuration = 600;
    export let animationStartDelay = 400;
    export let titleColor = 'text-gray-900';
    export let descriptionColor = 'text-gray-600';
    export let headerSpacing = 'mb-16';
  
    // Track hovered image for each section
    let hoveredImageIndex = {};
  </script>
  
  <!-- Card Group Header -->
  {#if title || description}
    <div class="text-center {headerSpacing} {maxWidth} mx-auto px-4" 
         in:fade={{ delay: animationStartDelay / 2, duration: animationDuration }}>
      {#if title}
        <h2 class="text-4xl md:text-5xl font-bold {titleColor} mb-6 leading-tight">
          {title}
        </h2>
      {/if}
      {#if description}
        <p class="text-xl {descriptionColor} leading-relaxed max-w-3xl mx-auto">
          {description}
        </p>
      {/if}
    </div>
  {/if}
  
  <!-- Cards Grid -->
  <div class="grid grid-cols-1 lg:grid-cols-2 {gap} {maxWidth} mx-auto px-4">
    {#each sections as section, i}
      <div
        class="bg-white rounded-3xl shadow-xl overflow-hidden transition-all duration-500 hover:shadow-2xl hover:-translate-y-2 hover:scale-[1.02]"
        in:fade={{ delay: i * animationDelay + animationStartDelay, duration: animationDuration }}
      >
        <div class="p-10">
          <!-- Category Badge -->
          {#if section.category}
            <div class="inline-block {section.categoryColor} px-4 py-2 rounded-full text-sm font-semibold mb-6">
              {section.category}
            </div>
          {/if}
          
          <!-- Title -->
          <h3 class="text-3xl font-bold text-gray-800 leading-tight mb-6">
            {section.title}
          </h3>
          
          <!-- Content with floating image -->
          <div class="relative">
            <!-- Floating Image -->
            {#if section.images && section.images.length > 0}
              <div class="float-{i % 2 === 0 ? 'right' : 'left'} 
                          {i % 2 === 0 ? 'ml-6 mb-4' : 'mr-6 mb-4'} 
                          w-48 h-48 rounded-2xl overflow-hidden shadow-lg 
                          transition-transform duration-300 hover:scale-105">
                {#if section.images.length === 1}
                  <!-- Single image -->
                  <img
                    src={section.images[0]}
                    alt={section.title}
                    class="w-full h-full object-cover"
                  />
                {:else}
                  <!-- Stacked images -->
                  <div class="relative w-full h-full">
                    {#each section.images as img, idx}
                      <img
                        src={img}
                        alt={section.title}
                        class="absolute w-4/5 h-4/5 object-cover rounded-xl border-4 border-white shadow-lg 
                               transition-all duration-300 hover:scale-110 cursor-pointer"
                        style="top: {idx * 12}px; left: {idx * 12}px; z-index: {hoveredImageIndex[i] === idx ? 100 : section.images.length - idx};"
                        on:mouseenter={() => hoveredImageIndex[i] = idx}
                        on:mouseleave={() => hoveredImageIndex[i] = null}
                      />
                    {/each}
                  </div>
                {/if}
              </div>
            {/if}
            
            <!-- Text content that wraps around the image -->
            <div class="text-gray-600 text-lg leading-relaxed space-y-4">
              {#if section.description}
                <p class="text-justify">
                  {section.description}
                </p>
              {/if}
              
              <!-- Details -->
              {#if section.details && section.details.length > 0}
                <div class="clear-both pt-4">
                  {#if Array.isArray(section.details) && typeof section.details[0] === 'object'}
                    <div class="grid grid-cols-2 gap-4 text-sm">
                      {#each section.details as detail}
                        <div class="bg-gray-50 p-3 rounded-lg text-center">
                          <div class="font-bold text-gray-800">{detail.label}</div>
                          <div class="text-gray-600">{detail.value}</div>
                        </div>
                      {/each}
                    </div>
                  {:else}
                    <div class="flex items-center space-x-4 text-sm text-gray-500">
                      {#each section.details as detail, idx}
                        <span class="flex items-center">
                          {#if idx === 0}
                            <svg class="w-4 h-4 mr-1" fill="currentColor" viewBox="0 0 20 20">
                              <path fill-rule="evenodd" d="M6 2a1 1 0 00-1 1v1H4a2 2 0 00-2 2v10a2 2 0 002 2h12a2 2 0 002-2V6a2 2 0 00-2-2h-1V3a1 1 0 10-2 0v1H7V3a1 1 0 00-1-1zm0 5a1 1 0 000 2h8a1 1 0 100-2H6z" clip-rule="evenodd"></path>
                            </svg>
                          {/if}
                          {detail}
                        </span>
                        {#if idx < section.details.length - 1}
                          <span>•</span>
                        {/if}
                      {/each}
                    </div>
                  {/if}
                </div>
              {/if}
              
              <!-- Tags -->
              {#if section.tags && section.tags.length > 0}
                <div class="flex flex-wrap gap-2 clear-both pt-2">
                  {#each section.tags as tag}
                    <span class="bg-gray-100 text-gray-700 px-3 py-1 rounded-full text-sm">{tag}</span>
                  {/each}
                </div>
              {/if}
              
              <!-- Stats -->
              {#if section.stats}
                <div class="bg-gray-50 p-4 rounded-xl clear-both">
                  <div class="flex items-center justify-between text-sm">
                    <span class="text-gray-600">{section.stats.label}</span>
                    <span class="font-bold {section.stats.color}">{section.stats.value}</span>
                  </div>
                </div>
              {/if}
            </div>
            
            <!-- Clear float to prevent layout issues -->
            <div class="clear-both"></div>
          </div>
        </div>
      </div>
    {/each}
  </div>
  
  <style>
    /* Ensure proper text wrapping around floated images */
    .float-left {
      float: left;
      shape-outside: margin-box;
    }
    
    .float-right {
      float: right;
      shape-outside: margin-box;
    }
    
    /* Better text flow around images */
    p {
      text-align: justify;
      hyphens: auto;
      word-spacing: 0.05em;
    }
    
    /* Mobile responsiveness - no floating on small screens */
    @media (max-width: 768px) {
      .float-left,
      .float-right {
        float: none !important;
        display: block;
        margin: 0 auto 1.5rem auto !important;
        width: 12rem !important;
        height: 12rem !important;
      }
      
      p {
        text-align: left;
      }
    }
    
    /* Tablet adjustments */
    @media (max-width: 1024px) and (min-width: 769px) {
      .float-left,
      .float-right {
        width: 10rem !important;
        height: 10rem !important;
      }
    }
  </style>