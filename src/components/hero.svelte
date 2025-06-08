<script>
    import portraitUrl from "$lib/assets/images/lathe.jpg";
    import Contact from "../components/contact.svelte";
    
    // Animation trigger for content
    let contentVisible = false;
    
    // Trigger animation on mount
    import { onMount } from 'svelte';
    onMount(() => {
        setTimeout(() => {
            contentVisible = true;
        }, 100);
    });
</script>

<!-- Hero Section -->
<section class="relative w-full h-screen overflow-hidden flex">
    <!-- Left half - Image -->
    <div class="relative w-1/2 h-full overflow-hidden">
        <!-- Image with subtle parallax effect -->
        <div class="absolute inset-0 transform scale-105 transition-transform duration-1000 ease-out">
            <img 
                src={portraitUrl}
                alt="Noah Wessels working in the engineering lab"
                class="w-full h-full object-cover object-center"
            />
        </div>
        
        <!-- Subtle overlay on image for depth -->
        <div class="absolute inset-0 bg-black/10"></div>
        
        <!-- Fade effect on the right edge of the image -->
        <div class="absolute inset-0 bg-image-fade"></div>
        
        <!-- Floating geometric elements on image side -->
        <div class="absolute top-20 right-10 w-32 h-32 border border-white/30 rotate-45 animate-float hidden lg:block"></div>
        <div class="absolute bottom-40 left-1/4 w-16 h-16 bg-blue-500/20 rounded-full animate-pulse hidden md:block"></div>
    </div>
    
    <!-- Right half - White background with content -->
    <div class="relative w-1/2 h-full bg-white flex items-center justify-center px-8 lg:px-12">
        <!-- Subtle texture overlay for the white area -->
        <div class="absolute inset-0 bg-subtle-grain opacity-5"></div>
        
        <!-- Content container -->
        <div class="relative z-10 w-full max-w-lg">
            <!-- Animated content container -->
            <div class="content-container" class:visible={contentVisible}>
                <!-- Enhanced greeting with subtle animation -->
                <div class="greeting-container mb-3">
                    <p class="text-sm text-gray-600 font-medium tracking-wide uppercase">
                        Hi, I am
                    </p>
                    <div class="w-12 h-0.5 bg-gradient-to-r from-blue-500 to-green-500 mt-2"></div>
                </div>
                
                <!-- Enhanced name with gradient text -->
                <h1 class="text-4xl lg:text-5xl xl:text-6xl font-bold mb-6 leading-tight">
                    <span class="bg-gradient-to-r from-gray-900 via-gray-800 to-gray-900 bg-clip-text text-transparent">
                        Noah Wessels
                    </span>
                </h1>
                
                <!-- Enhanced description with better typography -->
                <div class="space-y-4 mb-8">
                    <p class="text-gray-700 text-lg leading-relaxed font-light">
                        <span class="font-medium text-gray-800">4th year mechanical engineering student</span> 
                        at the University of Victoria and the 
                        <span class="font-medium text-gray-800">UVic Environmental Engineering Club Project Manager.</span>
                    </p>
                    <p class="text-gray-600 text-base leading-relaxed">
                        In my free time I enjoy 
                        <span class="inline-flex items-center gap-1">
                            <span class="text-green-700 font-medium">playing the banjo</span>,
                        </span>
                        <span class="inline-flex items-center gap-1">
                            <span class="text-blue-700 font-medium">rock climbing</span>,
                        </span>
                        and 
                        <span class="inline-flex items-center gap-1">
                            <span class="text-amber-700 font-medium">making violins</span>.
                        </span>
                    </p>
                </div>
                
                <!-- Enhanced Contact Component with wrapper -->
                <div class="contact-wrapper">
                    <Contact />
                </div>
            </div>
        </div>
    </div>
    
    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
        <div class="w-6 h-10 border-2 border-gray-400 rounded-full flex justify-center">
            <div class="w-1 h-3 bg-gray-400 rounded-full mt-2 animate-pulse"></div>
        </div>
    </div>
</section>

<style>
    /* Image fade effect */
    .bg-image-fade {
        background: linear-gradient(
            to right,
            transparent 0%,
            transparent 70%,
            rgba(255, 255, 255, 0.1) 80%,
            rgba(255, 255, 255, 0.3) 85%,
            rgba(255, 255, 255, 0.6) 90%,
            rgba(255, 255, 255, 0.8) 95%,
            rgba(255, 255, 255, 1) 100%
        );
    }
    
    /* Subtle texture overlay */
    .bg-subtle-grain {
        background-image: 
            radial-gradient(circle at 1px 1px, rgba(0,0,0,0.15) 1px, transparent 0);
        background-size: 20px 20px;
    }
    
    /* Content animation */
    .content-container {
        opacity: 0;
        transform: translateY(30px);
        transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
    }
    
    .content-container.visible {
        opacity: 1;
        transform: translateY(0);
    }
    
    /* Staggered animation for child elements */
    .greeting-container {
        opacity: 0;
        transform: translateX(-20px);
        animation: slideInLeft 0.6s ease-out 0.2s forwards;
    }
    
    .contact-wrapper {
        opacity: 0;
        transform: translateY(20px);
        animation: slideInUp 0.6s ease-out 0.6s forwards;
    }
    
    /* Custom animations */
    @keyframes slideInLeft {
        to {
            opacity: 1;
            transform: translateX(0);
        }
    }
    
    @keyframes slideInUp {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }
    
    @keyframes float {
        0%, 100% { transform: translateY(0px) rotate(45deg); }
        50% { transform: translateY(-20px) rotate(45deg); }
    }
    
    .animate-float {
        animation: float 6s ease-in-out infinite;
    }
    
    /* Mobile responsive - stack vertically */
    @media (max-width: 768px) {
        .bg-image-fade {
            background: linear-gradient(
                to bottom,
                transparent 0%,
                transparent 50%,
                rgba(255, 255, 255, 0.1) 55%,
                rgba(255, 255, 255, 0.3) 60%,
                rgba(255, 255, 255, 0.6) 65%,
                rgba(255, 255, 255, 0.8) 70%,
                rgba(255, 255, 255, 0.95) 75%,
                rgb(255, 255, 255) 80%
            );
        }
        section {
            flex-direction: column;
        }
        
        section > div {
            width: 100% !important;
            height: 50% !important;
        }
        
        /* Adjust image positioning for mobile */
        .object-cover {
            object-position: center top;
        }
        
        /* Enhanced mobile typography */
        h1 {
            font-size: 2.5rem;
            line-height: 1.1;
        }
        
        /* Reduce padding on mobile */
        section > div:last-child {
            padding: 1rem;
        }
    }
    
    /* Better spacing for small screens */
    @media (max-width: 640px) {
        .bg-image-fade {
            background: linear-gradient(
                to bottom,
                transparent 0%,
                transparent 50%,
                rgba(255, 255, 255, 0.1) 55%,
                rgba(255, 255, 255, 0.3) 60%,
                rgba(255, 255, 255, 0.6) 65%,
                rgba(255, 255, 255, 0.8) 70%,
                rgba(255, 255, 255, 0.95) 75%,
                rgb(255, 255, 255) 80%
            );
        }
        h1 {
            font-size: 2rem;
        }
        
        section > div:last-child {
            padding: 0.75rem;
        }
    }
    
    /* Enhanced focus states for accessibility */
    .contact-wrapper :global(a:focus),
    .contact-wrapper :global(button:focus) {
        outline: 2px solid #3b82f6;
        outline-offset: 2px;
        border-radius: 0.25rem;
    }
</style>