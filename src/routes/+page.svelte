<svelte:head>
    <title>Noah Wessels</title>
</svelte:head>

<script>
    import Contact from "../components/contact.svelte"
    import lathe from "/static/lathe.jpg"
</script>

<h1 class="py-4 flex justify-center font-semibold text-3xl">Noah Wessels</h1>

<Contact/>
<div class="py-4 flex justify-center items-center space-x-8">
    <img src={lathe} alt="MENG shop" class="p-2 w-1/2 flex justify-center"/>
    <div class="w-96">
        <p class="">4th year mechanical engineering student at the University of Victoria and the UVic Environmental Engineering Club Project Manager.</p>
        <p class="">In my free time I enjoy playing the banjo, rock climbing, and making violins.</p>
    </div>
</div>   


