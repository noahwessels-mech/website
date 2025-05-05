<!-- Svelte head changes the title of the tab -->
<svelte:head>
    <title>UVEEC</title>
</svelte:head>

<script>
    import { onMount } from 'svelte';
    
    import img1 from '/static/USV.jpg'; // replace with your image paths
    import img2 from '/static/testing.jpg'; // replace with your image paths
    import img3 from '/static/hullManufacturing.JPG';
    import img4 from '/static/gliderRender.jpeg'; 
  
    onMount(() => {
      // Any setup logic can be placed here
    });
  </script>





<h1 class="py-4 flex justify-center font-semibold text-3xl">UVEEC</h1>
<div class="flex justify-center">
<p class="w-1/2">The <a class="px-1 text-blue-500 underline" href="https://uveec.ca/" target="_blank">UVic Environmental Engineering Club</a> (UVEEC) is focused on creating engineering solutions to environmental issues. I joined the mechanical team in 2021 in my first semester at UVic. I am the current project manager for the underwater glider project.</p>
</div>

<div class="container mx-auto px-4 md:px-8">

    <!--Main Image and Description Section-->
    <h2 class="text-2xl font-semibold text-center py-4">Microplastic Collecting Unmanned Surface Vehicle</h2>
    <div class="flex flex-wrap items-center mt-4">
      <div class="w-full md:w-1/2">
        <img alt="Unmanned Surface Vehicle" class="block h-auto w-full" src="{img1}">
      </div>
  
      <div class="w-full md:w-1/2 px-6">
        <p class="text-grey-darker">
          This unmanned surface vehicle (USV) was equipped with a filtration module using microbubble filtration technology to collect microplastics.
        </p>
      </div>
    </div>
  
    <!--Mechanical Team Section-->
    <div class="flex flex-wrap items-center mt-4">
  
      <!--Sub Images and Description Section-->
      <div class="w-full md:w-1/2">
  
        <div class="flex flex-wrap items-center">
  
          <!--Sub Image 1-->
          <div class="w-full md:w-1/3">
            <img alt="testing" class=" px-1 block w-full" src="{img3}">
          </div>
  
          <!--Sub Image 2-->
          <div class="w-full md:w-2/3">
            <img alt="Sub2" class=" px-1 block w-full" src="{img2}">
          </div>
  
        </div>
      </div>
  
      <!--Sub Description-->
      <div class="w-full md:w-1/2 px-6">
        <p class="">
          As a member of the mechanical team, I helped design the joining structure for the hulls and was involved in the fiberglass hull manufacturing.
        </p>
      </div>
  
    </div>
  </div>


  <div class="container mx-auto px-4 md:px-8">

  <!--Main Image and Description Section-->
  <h2 class="text-2xl font-semibold text-center py-4">Underwater Glider Project</h2>

  <div class="flex flex-wrap md:flex-nowrap items-center justify-center mt-4 gap-6">
    
    <!-- Image on the left -->
    <div class="w-full md:w-1/2 px-6">
      <img src={img4} alt="Underwater glider photo" class="w-full h-64 object-cover" />
    </div>

    <!-- Text on the right -->
    <div class="w-full md:w-1/2 px-6">
      <p class="text-gray-700">
        The underwater glider project began in the summer of 2023. UVEEC is designing and manufacturing a glider capable of traversing the Saanich Inlet, a local uniquely anoxic inlet. CTD data will be collected to create salinity stratification profiles to display the mixing effects of runoff water into the ocean and the impacts of the tide.
      </p>
    </div>

  </div>
</div>