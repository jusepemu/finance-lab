<script>
    import Button from "$lib/components/ui/button/button.svelte";
</script>

<article class="flex flex-col gap-6 px-4 md:px-0 text-center">
    <div class="flex flex-col gap-2">
        <h2 class="text-4xl font-semibold">Toma el control de tu dinero.</h2>
        <p class="text-lg text-gray-500">
            Una forma simple y profesional de entender tus finanzas.
        </p>
    </div>

    <Button
        href="/onboarding/configure-profile"
        class="bg-primary text-secondary">Comenzar</Button
    >
</article>
