<script>
    import Logo from "$lib/components/ui/logo/Logo.svelte";

    let { children } = $props();
</script>

<main
    class="flex flex-col justify-center items-center bg-background min-h-screen"
>
    <header class="mb-6">
        <Logo />
    </header>
    {@render children()}
</main>
