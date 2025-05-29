<svelte:head>
    <title>Noah Wessels Fine Violins</title>
</svelte:head>

<script>
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';
    import Hero from '../../components/sub-hero.svelte';
    import CardList from '../../components/card-list.svelte';
    
    import img1 from '$lib/assets/images/back.JPG';
    import img2 from '$lib/assets/images/carvingScroll.jpg';
    import img3 from '$lib/assets/images/second.JPG'; 
    import img4 from '$lib/assets/images/front.JPG'; 
    import img5 from '$lib/assets/images/oldFiddle.JPG'; 
    import img6 from '$lib/assets/images/purfling.jpg'; 
    import img7 from '$lib/assets/images/ribs.JPG'; 
    import img8 from '$lib/assets/images/sawnback.jpg'; 
    import img9 from '$lib/assets/images/scroll.JPG'; 
    import img10 from '$lib/assets/images/Stradivarius.jpg'; 
    import img11 from '$lib/assets/images/stradFront.JPG'; 
    import img12 from '$lib/assets/images/stradBack.JPG'; 

    let mounted = false;
    onMount(() => {
        mounted = true;
    });

    // Data for featured projects section
    const featuredProjects = [
        {
            category: "Current Project",
            categoryColor: "bg-blue-100 text-blue-800",
            title: "Third Violin Creation",
            description: "Currently working on my third handcrafted violin, incorporating advanced techniques learned from traditional Italian masters and modern precision methods.",
            images: [img4, img1],
            details: [
                { label: "Project Year", value: "2024" },
                { label: "Status", value: "In Progress" },
                { label: "Wood Type", value: "Spruce & Maple" },
                { label: "Completion", value: "75%" }
            ],
            tags: ["Handcrafted", "Traditional Methods", "Precision Work"],
            stats: {
                label: "Progress",
                value: "75%",
                color: "text-green-600"
            }
        },
        {
            category: "Documentation",
            categoryColor: "bg-purple-100 text-purple-800",
            title: "Video Process Documentation",
            description: "Comprehensive video documentation of the violin-making process, from wood selection to final varnishing, showcasing traditional craftsmanship techniques.",
            images: [img2, img6],
            details: ["Senior Year Project", "YouTube Documentation", "Educational Content"],
            tags: ["Video Production", "Education", "Craftsmanship"],
            stats: {
                label: "Views",
                value: "2.5K+",
                color: "text-blue-600"
            }
        },
        {
            category: "Heritage",
            categoryColor: "bg-amber-100 text-amber-800",
            title: "Cremona Experience",
            description: "Studied the birthplace of modern violin making in Cremona, Italy. Immersed in the rich tradition of Italian luthiers and historical violin craftsmanship.",
            images: [img10, img11],
            details: [
                { label: "Visit Year", value: "2023" },
                { label: "Duration", value: "2 Weeks" },
                { label: "Focus", value: "Traditional Methods" },
                { label: "Language", value: "Italian Study" }
            ],
            tags: ["Cultural Immersion", "Traditional Learning", "Historical Study"],
            stats: {
                label: "Experience",
                value: "Invaluable",
                color: "text-amber-600"
            }
        }
    ];

    // Gallery images with enhanced data
    const galleryImages = [
        { src: img1, alt: "Violin Back Plate", category: "Construction" },
        { src: img2, alt: "Carving Scroll Detail", category: "Craftsmanship" },
        { src: img3, alt: "Second Violin Progress", category: "Work in Progress" },
        { src: img4, alt: "Completed Front Plate", category: "Finished Work" },
        { src: img5, alt: "Historical Reference", category: "Reference" },
        { src: img6, alt: "Purfling Detail", category: "Detail Work" },
        { src: img7, alt: "Rib Construction", category: "Construction" },
        { src: img8, alt: "Sawn Back Preparation", category: "Preparation" },
        { src: img9, alt: "Scroll Completion", category: "Finished Work" }
    ];

    const processSteps = [
        {
            step: "01",
            title: "Wood Selection",
            description: "Carefully selecting premium tonewoods - European spruce for the top and flamed maple for the back and sides.",
            icon: "🌲"
        },
        {
            step: "02", 
            title: "Template Creation",
            description: "Creating precise templates based on classical violin proportions and historical measurements.",
            icon: "📐"
        },
        {
            step: "03",
            title: "Plate Carving",
            description: "Hand-carving the top and back plates with traditional tools, achieving optimal thickness graduation.",
            icon: "🔨"
        },
        {
            step: "04",
            title: "Assembly",
            description: "Carefully assembling all components with traditional hide glue and precise alignment techniques.",  
            icon: "🔧"
        },
        {
            step: "05",
            title: "Varnishing",
            description: "Applying multiple coats of traditional oil varnish for protection and tonal enhancement.",
            icon: "🎨"
        }
    ];
</script>

<!-- Hero Section -->
<Hero 
    title="Noah Wessels"
    highlighted="Fine Violins"
    subtitle="Crafting exceptional violins through traditional methods and modern precision. Four years of dedicated artisanship in the timeless craft of violin making."
    primaryButton="View Gallery"
    secondaryButton="Watch Process"
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
                Explore the journey of traditional violin making through innovative techniques and time-honored craftsmanship methods.
            </p>
        </div>
        
        <CardList sections={featuredProjects} />
    </div>
</section>

<!-- Process Section -->
<section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-6">
        <div class="text-center mb-16">
            <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">The Craft Process</h2>
            <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                Each violin follows a meticulous five-step process, honoring centuries of tradition while incorporating modern precision.
            </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5 gap-8">
            {#each processSteps as step, i}
                <div 
                    class="text-center group cursor-pointer"
                    in:fly={{ y: 50, delay: i * 150 + 200, duration: 600 }}
                >
                    <div class="relative mb-6">
                        <div class="w-20 h-20 mx-auto bg-gradient-to-br from-blue-500 to-purple-600 rounded-full flex items-center justify-center text-3xl mb-4 transform group-hover:scale-110 transition-all duration-300 shadow-lg">
                            {step.icon}
                        </div>
                        <div class="absolute -top-2 -left-2 w-8 h-8 bg-white rounded-full flex items-center justify-center font-bold text-sm text-gray-600 shadow-md">
                            {step.step}
                        </div>
                    </div>
                    <h3 class="text-xl font-bold text-gray-800 mb-3 group-hover:text-blue-600 transition-colors">
                        {step.title}
                    </h3>
                    <p class="text-gray-600 text-sm leading-relaxed">
                        {step.description}
                    </p>
                </div>
            {/each}
        </div>
    </div>
</section>

<!-- Video Section -->
<section id="video" class="py-20 bg-gradient-to-r from-gray-800 to-gray-900 text-white">
    <div class="max-w-6xl mx-auto px-6">
        <div class="text-center mb-12">
            <h2 class="text-4xl md:text-5xl font-bold mb-4">The Making Process</h2>
            <p class="text-xl text-gray-300 max-w-3xl mx-auto mb-8">
                Watch the detailed process of creating the top plate of my second violin, documented during my senior year of high school.
            </p>
        </div>
        
        <div class="relative rounded-3xl overflow-hidden shadow-2xl bg-black/20 backdrop-blur-sm p-8">
            <div class="aspect-video rounded-2xl overflow-hidden">
                <iframe 
                    class="w-full h-full" 
                    title="Violin Making Process" 
                    src="https://www.youtube.com/embed/fELBDT2yrxg" 
                    frameborder="0" 
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                    allowfullscreen
                ></iframe>
            </div>
        </div>
    </div>
</section>

<!-- Gallery Section -->
<section id="gallery" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-6">
        <div class="text-center mb-16">
            <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">Craftsmanship Gallery</h2>
            <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                A visual journey through the intricate details and stages of violin construction, showcasing traditional techniques and precision craftsmanship.
            </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            {#each galleryImages as image, i}
                <div 
                    class="group relative overflow-hidden rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-500 transform hover:-translate-y-2"
                    in:fly={{ y: 30, delay: i * 100 + 300, duration: 600 }}
                >
                    <div class="aspect-square overflow-hidden">
                        <img 
                            class="w-full h-full object-cover transition-all duration-700 group-hover:scale-110" 
                            src={image.src} 
                            alt={image.alt}
                        />
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-300"></div>
                    <div class="absolute bottom-0 left-0 right-0 p-6 text-white transform translate-y-full group-hover:translate-y-0 transition-all duration-300">
                        <div class="inline-block bg-blue-600 px-3 py-1 rounded-full text-xs font-semibold mb-2">
                            {image.category}
                        </div>
                        <h3 class="font-bold text-lg">{image.alt}</h3>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<!-- Cremona Heritage Section -->
<section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-6">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
            <div class="space-y-8">
                <div>
                    <div class="inline-block bg-amber-100 text-amber-800 px-4 py-2 rounded-full text-sm font-semibold mb-4">
                        Cultural Heritage
                    </div>
                    <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-6">
                        Cremona Experience
                    </h2>
                    <p class="text-xl text-gray-600 leading-relaxed mb-6">
                        Cremona is recognized as the birthplace of the modern violin. I had the pleasure of visiting this beautiful city in May of 2023, immersing myself in centuries of violin-making tradition.
                    </p>
                    <p class="text-lg text-gray-600 leading-relaxed">
                        Currently learning Italian with great anticipation of returning in the future to deepen my understanding of violin making through direct study with Italian masters.
                    </p>
                </div>
                
                <div class="grid grid-cols-2 gap-6 text-center">
                    <div class="bg-gray-50 p-6 rounded-xl">
                        <div class="text-3xl font-bold text-amber-600 mb-2">2023</div>
                        <div class="text-gray-600">Visit Year</div>
                    </div>
                    <div class="bg-gray-50 p-6 rounded-xl">
                        <div class="text-3xl font-bold text-amber-600 mb-2">🇮🇹</div>
                        <div class="text-gray-600">Learning Italian</div>
                    </div>
                </div>
            </div>

            <div class="relative">
                <div class="grid grid-cols-2 gap-4">
                    <div class="space-y-4">
                        <img 
                            class="w-full rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-1" 
                            src={img10} 
                            alt="Stradivarius Violin in Cremona"
                        />
                        <img 
                            class="w-full rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-1" 
                            src={img11} 
                            alt="Historical Violin Front"
                        />
                    </div>
                    <div class="pt-8">
                        <img 
                            class="w-full rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-1" 
                            src={img12} 
                            alt="Historical Violin Back"
                        />
                    </div>
                </div>
                
                <!-- Decorative elements -->
                <div class="absolute -top-4 -right-4 w-24 h-24 bg-amber-200/30 rounded-full blur-xl"></div>
                <div class="absolute -bottom-4 -left-4 w-32 h-32 bg-blue-200/20 rounded-full blur-2xl"></div>
            </div>
        </div>
    </div>
</section>

<!-- Resources Section -->
<section class="py-20 bg-gradient-to-br from-blue-50 to-purple-50">
    <div class="max-w-4xl mx-auto px-6 text-center">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-6">Learning Resources</h2>
        <p class="text-xl text-gray-600 mb-12">
            My journey began with carefully selected books and specialized tools from master craftsmen.
        </p>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            <a 
                href="https://www.abebooks.it/9780709058762/Art-Violin-Making-Johnson-Chris-0709058764/plp" 
                target="_blank"
                class="group bg-white p-8 rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2"
            >
                <div class="text-4xl mb-4">📚</div>
                <h3 class="text-2xl font-bold text-gray-800 mb-4 group-hover:text-blue-600 transition-colors">
                    Specialized Literature
                </h3>
                <p class="text-gray-600">
                    Essential books on the art of violin making, covering traditional techniques and historical methods.
                </p>
            </a>
            
            <a 
                href="https://www.cremonatools.com/violin-making.html?p=2" 
                target="_blank"
                class="group bg-white p-8 rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2"
            >
                <div class="text-4xl mb-4">🔨</div>
                <h3 class="text-2xl font-bold text-gray-800 mb-4 group-hover:text-blue-600 transition-colors">
                    Professional Tools
                </h3>
                <p class="text-gray-600">
                    High-quality specialized tools essential for precision violin construction and detail work.
                </p>
            </a>
        </div>
    </div>
</section>