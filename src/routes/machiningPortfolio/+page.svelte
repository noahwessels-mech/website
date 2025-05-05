<svelte:head>
    <title>Noah Wessels' Machining Portfolio</title>
</svelte:head>

<script>
    import { onMount } from 'svelte';

    let footerNote;
  
    import img1 from '/static/headPlate.JPG';
    import img2 from '/static/mounts.jpg';
    import img3 from '/static/machineCap.jpg';
    import img4 from '/static/capOnSub.jpg';
    import img5 from '/static/rod.jpg';
    import img6 from '/static/frame.jpg';
    import img7 from '/static/program.JPG';
    import img8 from '/static/wheel.jpg';
    import img9 from '/static/aluminumForks.JPG';
    import img10 from '/static/brassFork.JPG';
    import img11 from '/static/flywheelCart.jpeg';
     import img11 from '/static/laserWood.JPG';
  
    onMount(() => {
    document.querySelector("#footerNote").addEventListener('click', () => {
      noteSection.scrollIntoView({behavior: "smooth"});
    });
  });


  </script>

<h1 class="text-3xl py-4 text-center font-semibold">Machining Portfolio</h1>

<section id="top" class="px-4 py-8">
    <div class="flex justify-center">
        <p class="mb-4 w-1/2">This page contains a few of the parts I have machined. The manufacturing of these parts took place both within my co-op placement at the UVic Mechanical Engineering Machine Shop as well as afterwards when making parts for various university engineering clubs <a id="#footerNote">*</a>.</p>
    </div>



    <h2 class="text-2xl font-semibold text-center py-4">Mild Steel Parts</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 place-items-center mb-4">
      <div>
        <p>This project involved milling and turning operations on mild steel. These parts were used for helmet impact testing.</p>
      </div>
      <div class="md:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4">
        <img class="w-full h-64 object-cover" src={img1} alt="Description of the machining process" />
        <img class="w-full h-64 object-cover" src={img2} alt="End product of the machining process" />
      </div>
    </div>




    <h2 class="text-2xl font-semibold text-center py-4">Laser Cut Parts</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 place-items-center mb-4">
        <div class="md:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4">
            <img class="w-full h-80 object-cover" src={img11} alt="Description of the machining process" />
            <img class="w-full object-contain" src={img12} alt="End product of the machining process" />
            </div>
          <div>
            <p>During my co-op, the MECH Machine Shop laser was frequently used for cutting parts for student projects. I also cut several flywheel powered carts from plywood for a 3rd year design project, as shown in the photos.</p>
          </div>
        </div>



    <h2 class="text-2xl font-semibold text-center py-4">Tuning Forks</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 place-items-center mb-4">
        <div>
            <p>Aluminum, brass, and Delrin turning forks were cut on the waterjet for a material science lab experiment.</p>
          </div>
        <div class="md:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4">
            <img class="w-full h-80 object-cover" src={img9} alt="Description of the machining process" />
            <img class="w-full h-80 object-cover" src={img10} alt="End product of the machining process" />
            </div>
        </div>


    <h2 class="text-2xl font-semibold text-center py-4">AUV Parts</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 place-items-center mb-4">
    <div class="md:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4">
        <img class="w-full h-80 object-cover" src={img3} alt="Description of the machining process" />
        <img class="w-full h-80 object-cover" src={img4} alt="End product of the machining process" />
        </div>
      <div>
        <p>This endcap was milled for the <a class="px-1 text-blue-500 underline" target="_blank" href="https://onlineacademiccommunity.uvic.ca/auvic/"> Autonomous Underwater Vehicle Interdisciplinary Club</a>(AUVIC). 20 holes were spot-faced and drilled into a large aluminum plate for WetLink penetrators, with 4 additional holes for the internal mounting system to be attached.</p>
      </div>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 place-items-center mb-4">
        <div class="md:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4">
            <img class="w-full h-80 object-cover" src={img5} alt="Description of the machining process" />
            <img class="w-full h-80 object-cover" src={img6} alt="End product of the machining process" />
            </div>
          <div>
            <p>Posts and plates were turned and milled from aluminum to hold the electronics inside of the AUV.</p>
          </div>
        </div>


  
    <div id="footerNote" bind:this={footerNote}>
        <p class="mt-4 py-4 flex justify-center">*Permission was granted by all relevant parties to share the images featured in this portfolio.</p>
    </div>

    
  </section>
  
