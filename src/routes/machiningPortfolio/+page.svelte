<svelte:head>
    <title>Noah Wessels' Machining Portfolio</title>
</svelte:head>

<script>
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';

    let footerNote;
    import HeroSection from '../../components/sub-hero.svelte';
    import CardList from '../../components/card-list.svelte';
  
    import img1 from '$lib/assets/images/headPlate.JPG';
    import img2 from '$lib/assets/images/mounts.jpg';
    import img3 from '$lib/assets/images/machineCap.jpg';
    import img4 from '$lib/assets/images/capOnSub.jpg';
    import img5 from '$lib/assets/images/rod.jpg';
    import img6 from '$lib/assets/images/frame.jpg';
    import img7 from '$lib/assets/images/program.JPG';
    import img8 from '$lib/assets/images/wheel.jpg';
    import img9 from '$lib/assets/images/aluminumForks.JPG';
    import img10 from '$lib/assets/images/brassFork.JPG';
    import img11 from '$lib/assets/images/flywheelCart.jpeg';
    import img12 from '$lib/assets/images/laserWood.JPG';
  
    onMount(() => {
     // mounted = true;

    // document.querySelector("#footerNote").addEventListener('click', () => {
    //   noteSection.scrollIntoView({behavior: "smooth"});
    // });
  });
  const sections = [
  {
    title: 'Mild Steel Parts',
    category: 'Machining',
    categoryColor: 'bg-gray-100 text-gray-800',
    description: 'This project involved milling and turning operations on mild steel. These parts were used for helmet impact testing.',
    images: [img1, img2],
    details: ['Milling & Turning', 'Helmet Impact Testing'],
    tags: ['Mild Steel', 'Milling', 'Turning'],
    stats: null
  },
  {
    title: 'Laser Cut Parts',
    category: 'Laser Cutting',
    categoryColor: 'bg-red-100 text-red-800',
    description: 'During my co-op, the MECH Machine Shop laser was frequently used for cutting parts for student projects. I also cut several flywheel powered carts from plywood for a 3rd year design project, as shown in the photos.',
    images: [img12, img11],
    details: ['Co-op Project', '3rd Year Design Project'],
    tags: ['Laser Cutting', 'Plywood', 'Student Projects'],
    stats: null
  },
  {
    title: 'Tuning Forks',
    category: 'Waterjet Cutting',
    categoryColor: 'bg-blue-100 text-blue-800',
    description: 'Aluminum, brass, and Delrin tuning forks were cut on the waterjet for a material science lab experiment.',
    images: [img9, img10],
    details: ['Material Science Lab', 'Multiple Materials'],
    tags: ['Aluminum', 'Brass', 'Delrin', 'Waterjet'],
    stats: null
  },
  {
    title: 'AUV Endcap',
    category: 'AUV Components',
    categoryColor: 'bg-purple-100 text-purple-800',
    description: 'This endcap was milled for the Autonomous Underwater Vehicle Interdisciplinary Club (AUVIC). 20 holes were spot-faced and drilled into a large aluminum plate for WetLink penetrators, with 4 additional holes for the internal mounting system to be attached.',
    images: [img3, img4],
    details: [
      { label: 'Critical Sealing Surfaces', value: '21' },
      { label: 'Purpose', value: 'WetLink Penetrators' }
    ],
    tags: ['AUVIC', 'Aluminum', 'Spot-facing', 'Drilling'],
    stats: { label: 'Total Holes', value: '24', color: 'text-blue-600' }
  },
  {
    title: 'AUV Internal Components',
    category: 'AUV Components',
    categoryColor: 'bg-purple-100 text-purple-800',
    description: 'Post and plate parts were turned and milled from aluminum to hold the electronics and payloads inside of an AUV and a rocket for UVic student design teams.',
    images: [img5, img6],
    details: ['Electronics Mounting', 'Internal Structure'],
    tags: ['AUVIC', 'Aluminum', 'Electronics', 'Structural'],
    stats: null
  }
];

  </script>

<HeroSection
  title="Machining"
  highlighted="Portfolio"
  subtitle="This page contains a few of the parts I have machined. The manufacturing of these parts took place both within my co-op placement at the UVic Mechanical Engineering Machine Shop as well as afterwards when making parts for various university engineering clubs"
  showButtons={false}
/>
  <!-- Project Cards Section -->
  <section class="container mx-auto px-6 py-20">
    <div class="text-center mb-16" in:fade={{ delay: 200, duration: 600 }}>
      <h2 class="text-4xl font-bold text-gray-800 mb-4">Featured Projects</h2>
      <p class="text-xl text-gray-600 max-w-2xl mx-auto">
        Innovative engineering solutions addressing critical environmental challenges through cutting-edge technology and sustainable design.
      </p>
    </div>
<CardList
{sections}
maxWidth="max-w-6xl"
gap="gap-8"
animationDelay={150}
animationDuration={500}
animationStartDelay={300}
/>
</section>

  
