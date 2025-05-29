<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  
  import CardList from '../../components/card-list.svelte';
  import usvImg from '$lib/assets/images/USV.jpg';
  import testingImg from '$lib/assets/images/testing.jpg';
  import hullImg from '$lib/assets/images/hullManufacturing.JPG';
  import gliderImg from '$lib/assets/images/gliderRender.jpeg';
  import sectionImg from '$lib/assets/images/gliderSection.jpeg';
  import cfdImg from '$lib/assets/images/CFD.jpeg';
  import HeroSection from '../../components/sub-hero.svelte';
  
    function goToProjects() {
      // navigate or scroll to projects section
      console.log("Navigating to Projects");
    }
  
    function learnMore() {
      // navigate to About page or section
      console.log("Navigating to Learn More");
    }

  // Project sections data
  const featuredProjects = [
    {
      title: 'Microplastic Collecting Unmanned Surface Vehicle',
      category: 'Marine Technology',
      categoryColor: 'bg-blue-100 text-blue-800',
      description: `This USV uses microbubble filtration technology to collect microplastics from the surface waters of Saanich Inlet. I led the mechanical design of the filtration housing and oversaw field trials in summer 2022.`,
      images: [usvImg],
      details: ['Summer 2022', 'Mechanical Design Lead'],
      stats: null
    },
    {
      title: 'Mechanical Team Contributions',
      category: 'Manufacturing',
      categoryColor: 'bg-green-100 text-green-800',
      description: `As part of the mechanical team, I designed the joining structure for the hulls and managed the fiberglass hull manufacturing process. We achieved a 20% weight reduction over our initial prototype.`,
      images: [hullImg, testingImg],
      details: ['Hull Design', 'Manufacturing Process'],
      stats: { label: 'Weight Reduction', value: '20%', color: 'text-green-600' }
    },
    {
      title: 'Underwater Glider Project',
      category: 'Underwater Systems', 
      categoryColor: 'bg-purple-100 text-purple-800',
      description: `Launched in summer 2023, our glider traverses the anoxic depths of Saanich Inlet to collect CTD data, creating detailed salinity stratification profiles to study mixing effects of runoff and tidal flows.`,
      images: [gliderImg],
      details: [
        { label: 'Launch Date', value: 'Summer 2023' },
        { label: 'Data Type', value: 'CTD Profiles' }
      ],
      stats: null
    },
    {
      title: 'Design & Manufacturing',
      category: 'Leadership & CAD',
      categoryColor: 'bg-orange-100 text-orange-800',
      description: `In my role as project manager and club president, I led the detailed CAD design and oversaw manufacturing. Below are sectional CAD views and CFD results highlighting our optimization process.`,
      images: [sectionImg, cfdImg],
      details: null,
      tags: ['Project Manager', 'Club President', 'CAD Design', 'CFD Analysis'],
      stats: null
    }
  ];

  const stats = [
    { value: '2', label: 'Major Projects', color: 'text-blue-400' },
    { value: '20%', label: 'Weight Reduction', color: 'text-green-400' },
    { value: '2023', label: 'Latest Launch', color: 'text-purple-400' },
    { value: '∞', label: 'Innovation', color: 'text-orange-400' }
  ];

  let mounted = false;

  onMount(() => {
    mounted = true;
  });
</script>

<svelte:head>
  <title>UVEEC Projects | Noah Wessel</title>
  <meta name="description" content="Noah Wessels's contributions to the UVic Environmental Engineering Club's USV and glider projects." />
</svelte:head>

<main class="pt-20 bg-gray-50">
  <!-- Hero Section -->
  <script>
    
  </script>
  
  <HeroSection 
    title="UVic Environmental"
    highlighted="Engineering Club"
    subtitle="Explore student-led innovations in marine and environmental engineering."
    primaryButton="Explore Projects"
    secondaryButton="Meet the Team"
    showButtons={true}
    onPrimaryClick={() => document.getElementById('gallery').scrollIntoView({ behavior: 'smooth' })}
    onSecondaryClick={() => document.getElementById('video').scrollIntoView({ behavior: 'smooth' })}
/>


<!-- Featured Projects Section -->
<section class="py-20 bg-gray-50">
  <div class="max-w-7xl mx-auto px-6">
      <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">Featured Projects</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            Innovative engineering solutions addressing critical environmental challenges through cutting-edge technology and sustainable design.
          </p>
      </div>
      
      <CardList sections={featuredProjects} />
  </div>
</section>

  <!-- Stats Section -->
  <section class="bg-gray-800 text-white py-20">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" in:fade={{ delay: 100, duration: 600 }}>
        <h2 class="text-4xl font-bold mb-4">Project Impact</h2>
        <p class="text-xl text-gray-300">Measurable results from our environmental engineering initiatives</p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8 max-w-5xl mx-auto">
        {#each stats as stat, i}
          <div 
            class="text-center"
            in:fly={{ y: 50, delay: i * 100 + 300, duration: 600 }}
          >
            <div class="text-5xl font-bold {stat.color} mb-2">{stat.value}</div>
            <div class="text-gray-300">{stat.label}</div>
          </div>
        {/each}
      </div>
    </div>
  </section>
</main>



<style>
  :global(html) {
    scroll-behavior: smooth;
  }
  
  :global(::-webkit-scrollbar) {
    width: 8px;
  }
  
  :global(::-webkit-scrollbar-track) {
    background: #f1f5f9;
  }
  
  :global(::-webkit-scrollbar-thumb) {
    background: #64748b;
    border-radius: 4px;
  }
  
  :global(::-webkit-scrollbar-thumb:hover) {
    background: #475569;
  }
</style>