<script>
    import Nav from "../components/nav.svelte";
    import Footer from "../components/footer.svelte";
</script>

<div class="min-h-screen flex flex-col pt-16"> 
    <Nav />

    <main class="flex-1">
        <slot />
    </main>

    <Footer />
</div>

<style>
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
</style>
