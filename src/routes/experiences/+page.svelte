<script>
  import HeroSection from '../../components/sub-hero.svelte';
  
    // experience entries
    export let experiences = [
      {
        title: 'Mechanical Design Co-op',
        company: 'D-Wave Systems Quantum Computing',
        period: 'Jan 2025 – Apr 2025',
        location: 'Burnaby, BC',
        description: `• Designed a platform for a superconducting PCB within the Hardware Engineering team.
  • Machined prototype pulse tube mounts on a manual milling machine for hardware benchmarking.
  • Created and installed rigid aluminum structures to strengthen desiccator housing for quantum processors.
  • Generated detailed assembly drawings for sensors, power supplies, and lab maintenance equipment.
  • Performed cryogenic lab operations: cooldowns, pulse tube swaps, and dilution refrigerator assembly.`
      },
      {
        title: 'Mechanical Engineering Intern',
        company: 'Babcock Canada',
        period: 'May 2024 – Aug 2024',
        location: 'Victoria, BC',
        description: `• Authored Initial Deficiency Assessment Reports (IDARs) for Victoria Class Submarine equipment.
  • Produced isometric AutoCAD drawings for modified submarine drainage systems per standards.
  • Validated submarine FEA geometry in LS-PrePost to support analysis accuracy.
  • Compiled an overview training document of the Victoria Class propulsion system.`
      },
      {
        title: 'Machining Assistant',
        company: 'UVIC Mechanical Engineering Machine Shop',
        period: 'Jan 2023 – Apr 2023',
        location: 'Victoria, BC',
        description: `• Operated lathes, Anilam CNC mills, laser cutters, and waterjet to fabricate research and student project parts.
  • Served as Teaching Assistant in labs covering manufacturing methods, engineering drawings, and metrology.
  • Reviewed design drawings and manufactured parts to tight GD&T tolerances, providing feedback.`
      }
    ];
  </script>
  
  <!-- Hero Section -->
  <HeroSection
    title="Co-op & Internship"
    highlighted="Experiences"
    subtitle="Hands-on engineering roles across quantum computing, marine systems, and precision machining."
    showButtons={false}
  />
  
  <!-- Experiences Grid -->
  <section class="bg-white py-16">
    <div class="container mx-auto px-6">
      <div class="grid gap-8 md:grid-cols-2 lg:grid-cols-3">
        {#each experiences as exp}
          <div class="bg-gray-50 rounded-2xl shadow-md p-6 flex flex-col hover:shadow-lg transition-shadow duration-200">
            <div class="mb-4">
              <div class="flex justify-between items-baseline">
                <span class="text-gray-500 text-sm">{exp.period}</span>
                <span class="text-gray-500 text-sm">{exp.location}</span>
              </div>
              <h3 class="mt-2 text-xl font-semibold text-gray-800">{exp.title}</h3>
              <sub class="text-indigo-600 font-medium">@ {exp.company}</sub>
            </div>
            <p class="flex-grow whitespace-pre-line text-gray-700 leading-relaxed">{exp.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <style>
    :global(body) {
      margin-top: 0;
    }
  </style>
  