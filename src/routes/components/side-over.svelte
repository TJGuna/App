<script lang="ts">
    export let show = false; 
    export let title = ''; 

</script>
{#if show}
<div class=" bg-white right-0 bottom-0 h-[calc(100vh-64px)] w-1/2 md:w-1/3 z-30 fixed shadow-2xl transform-[width] duration-300">
    <div class="flex flex-col border-l-2">
        <h1 class="p-2 text-2xl bg-slate-100">{title}</h1>
        <slot></slot>
    </div>
  </div>
  {/if}