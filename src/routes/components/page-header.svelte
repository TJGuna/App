<script lang="ts">
    export let Title: string;
</script>
<main class="flex items-center justify-between border-b p-2 bg-white rounded-md shadow-md">
    <h1 class="text-2xl font-bold">{Title}</h1>
    <div><slot /></div>
</main>