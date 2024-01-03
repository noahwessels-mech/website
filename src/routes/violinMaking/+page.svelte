<svelte:head>
    <title>Noah Wessels Fine Violins</title>
</svelte:head>


<script>
    import img1 from '/static/back.JPG'; // replace with your image paths
    import img2 from '/static/carvingScroll.jpg'; // replace with your image paths
    import img3 from '/static/second.JPG'; 
    import img4 from '/static/front.JPG'; 
    import img5 from '/static/oldFiddle.JPG'; 
    import img6 from '/static/purfling.jpg'; 
    import img7 from '/static/ribs.JPG'; 
    import img8 from '/static/sawnback.jpg'; 
    import img9 from '/static/scroll.JPG'; 
    import img10 from '/static/Stradivarius.jpg'; 
    import img11 from '/static/stradFront.JPG'; 
    import img12 from '/static/stradBack.JPG'; 
  
  </script>


<style>
    .video-div{
        display: flex;
        justify-content: center;
    }
    .video{
        width: 50%;
        aspect-ratio: 16/9;
    }

</style>

<h1 class="py-4 flex justify-center font-semibold text-3xl">Violin Making</h1>

<div class="flex justify-center">
    <p class="p-4 w-1/2">For the past four years I have been making violins. I started by buying specialized <a class="px-1 text-blue-500 underline" href="https://www.abebooks.it/9780709058762/Art-Violin-Making-Johnson-Chris-0709058764/plp" target="_blank">books</a> and <a class="px-1 text-blue-500 underline" href="https://www.cremonatools.com/violin-making.html?p=2" target="_blank">tools</a>. I am currently working on my third violin.</p>
</div>


<div class="flex justify-center">
    <p class="p-2 w-1/2 flex">Here is a video I made in my senior year of highschool where I recorded the process of making the top of my second violin</p>
</div>

<div class="video-div">
    <iframe class="video" title="" src="https://www.youtube.com/embed/fELBDT2yrxg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>


  
<section class="px-4 py-8">
    <h2 class="text-3xl font-bold text-center py-4">Gallery</h2>
  
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 place-items-center">
      <img class="w-full h-64 object-cover" src={img1} alt="Description  1" />
      <img class="w-full h-64 object-cover" src={img2} alt="Description  2" />
      <img class="w-full h-64 object-cover" src={img3} alt="Description  3" />
      <img class="w-full h-64 object-cover" src={img4} alt="Description  4" />
      <img class="w-full h-64 object-cover" src={img5} alt="Description  5" />
      <img class="w-full h-64 object-cover" src={img6} alt="Description  6" />
      <img class="w-full h-64 object-cover" src={img7} alt="Description  7" />
      <img class="w-full h-64 object-cover" src={img8} alt="Description  8" />
      <img class="w-full h-64 object-cover" src={img9} alt="Description  9" />
    </div>
  </section>


  <section class="px-4 py-8">
    <h2 class="text-3xl font-bold text-center py-4">Cremona</h2>
  
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 place-items-center mb-4">
      <div>
        <p>Cremona is recognized as the birthplace of the modern violin. I had the pleasure of visiting this beautiful city in May of 2023, and am currently learning Italian with great anticipation of returning in the future to deepen my understanding of violin making.</p>
      </div>
      <img class="h-80 object-cover" src={img10} alt="Description 1" />
    </div>
  
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 place-items-center">
      <img class="w-full h-72 object-cover" src={img11} alt="something" />
      <img class="w-full h-72 object-cover" src={img12} alt="something" />
    </div>
  </section>