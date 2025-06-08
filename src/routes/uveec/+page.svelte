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
	import CardGroup from '../../components/card-group.svelte';
  let groupSpacing = 'mb-32';
	// Project sections data
  const cardGroups = [
	{
		title: 'Marine Research & Technology',
		description:
			'Innovative underwater systems and marine technology projects focused on environmental monitoring and ocean conservation in Saanich Inlet.',
		sections: [
			{
				title: 'Microplastic Collecting Unmanned Surface Vehicle',
				category: 'Marine Technology',
				categoryColor: 'bg-blue-100 text-blue-800',
				description: `This USV uses microbubble filtration technology to collect microplastics from the surface waters of Saanich Inlet. I led the mechanical design of the filtration housing and oversaw field trials in summer 2022.`,
				images: [usvImg],
				details: ['Summer 2022', 'Mechanical Design Lead'],
				tags: ['Environmental Tech', 'Filtration Systems', 'Field Testing'],
				stats: null
			},
			{
				title: 'Underwater Glider Project',
				category: 'Underwater Systems',
				categoryColor: 'bg-purple-100 text-purple-800',
				description: `Launched in summer 2023, our glider traverses the anoxic depths of Saanich Inlet to collect CTD data, creating detailed salinity stratification profiles to study mixing effects of runoff and tidal flows.`,
				images: [gliderImg],
				details: [
					{ label: 'Launch Date', value: 'Winter 2025' },
					{ label: 'Data Type', value: 'CTD Profiles' },
					{ label: 'Environment', value: 'Anoxic Waters' },
					{ label: 'Purpose', value: 'Salinity Analysis' }
				],
				tags: ['Oceanography', 'Data Collection', 'Autonomous Systems'],
				stats: null
			}
		]
	},
	{
		title: 'Engineering Design & Manufacturing',
		description:
			'Advanced mechanical design, manufacturing processes, and leadership in developing high-performance marine vehicle systems.',
		sections: [
			{
				title: 'Hull Design & Manufacturing Excellence',
				category: 'Manufacturing',
				categoryColor: 'bg-green-100 text-green-800',
				description: `As part of the mechanical team, I designed the joining structure for the hulls and managed the fiberglass hull manufacturing process. We achieved a 20% weight reduction over our initial prototype through innovative design and material optimization.`,
				images: [hullImg, testingImg],
				details: [
					{ label: 'Process', value: 'Hull Design' },
					{ label: 'Material', value: 'Fiberglass' },
					{ label: 'Role', value: 'Manufacturing Lead' },
					{ label: 'Achievement', value: '20% Weight Reduction' }
				],
				tags: ['Composite Materials', 'Weight Optimization', 'Quality Control'],
				stats: { 
					label: 'Weight Reduction', 
					value: '20%', 
					color: 'text-green-600' 
				}
			},
			{
				title: 'Project Leadership & CAD Engineering',
				category: 'Leadership & CAD',
				categoryColor: 'bg-orange-100 text-orange-800',
				description: `In my role as project manager and club president, I led the detailed CAD design and oversaw manufacturing operations. This comprehensive approach included sectional design analysis and CFD optimization to ensure optimal performance and manufacturability.`,
				images: [sectionImg, cfdImg],
				details: [
					{ label: 'Leadership Role', value: 'Project Manager & President' },
					{ label: 'Design Tool', value: 'Advanced CAD' },
					{ label: 'Analysis', value: 'CFD Optimization' },
					{ label: 'Scope', value: 'End-to-End Development' }
				],
				tags: ['Project Management', 'Club Leadership', 'CAD Design', 'CFD Analysis', 'Team Coordination'],
				stats: null
			}
		]
	}
];

	const stats = [
		{ value: '2', label: 'Major Projects', color: 'text-blue-400' },
		{ value: '+40', label: 'Students Mentored', color: 'text-green-400' },
		{ value: '2022', label: 'Latest Launch', color: 'text-purple-400' },
		{ value: '∞', label: 'Innovation', color: 'text-orange-400' }
	];

	let mounted = false;

	onMount(() => {
		mounted = true;
	});
</script>

<svelte:head>
	<title>UVEEC Projects | Noah Wessel</title>
	<meta
		name="description"
		content="Noah Wessels's contributions to the UVic Environmental Engineering Club's USV and glider projects."
	/>
</svelte:head>

<HeroSection
	title="UVic Environmental"
	highlighted="Engineering Club"
	subtitle="Explore student-led innovations in marine and environmental engineering."
	primaryButton="Explore Projects"
	secondaryButton="Meet the Team"
	showButtons={true}
	onPrimaryClick={() => document.getElementById('projects').scrollIntoView({ behavior: 'smooth' })}
	onSecondaryClick={() => window.open('https://uveec.ca/about', '_blank')}
/>

<!-- Featured Projects Section -->
<section id="projects" class="py-20 bg-gray-50">
	<div class="max-w-7xl mx-auto px-6">
		<div class="text-center mb-16">
			<h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">Featured Projects</h2>
			<p class="text-xl text-gray-600 max-w-3xl mx-auto">
				Innovative engineering solutions addressing critical environmental challenges through
				cutting-edge technology and sustainable design.
			</p>
		</div>

    {#each cardGroups as group, index}
    <div class={index < cardGroups.length - 1 ? groupSpacing : ''}>
      <CardGroup 
        title={group.title}
        description={group.description}
        sections={group.sections}
        maxWidth="max-w-7xl"
        gap="gap-12"
        titleColor="text-gray-900"
        descriptionColor="text-gray-600"
        headerSpacing="mb-16"
      />
    </div>
  {/each}
	</div>
</section>


<!-- Stats Section -->
<section class="bg-gray-800 text-white py-20">
	<div class="container mx-auto px-6">
		<div class="text-center mb-16" in:fade={{ delay: 100, duration: 600 }}>
			<h2 class="text-4xl font-bold mb-4">Project Impact</h2>
			<p class="text-xl text-gray-300">
				Measurable results from our environmental engineering initiatives
			</p>
		</div>
		<div class="grid grid-cols-1 md:grid-cols-4 gap-8 max-w-5xl mx-auto">
			{#each stats as stat, i}
				<div class="text-center" in:fly={{ y: 50, delay: i * 100 + 300, duration: 600 }}>
					<div class="text-5xl font-bold {stat.color} mb-2">{stat.value}</div>
					<div class="text-gray-300">{stat.label}</div>
				</div>
			{/each}
		</div>
	</div>
</section>
