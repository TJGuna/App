<script lang="ts">
  import { createEventDispatcher, onMount } from 'svelte';
  export let updateIsOpen = () => {};

  export let options: any[] = []; 
  export let availableColumns: string[] = []; 


  export let selectedOptions: any[] = []; // array of selected options

  export let isOpen = false; // flag to track if dropdown is open
  const dispatch = createEventDispatcher();

  onMount(() => {
  // set the "checked" property for each option to false initially
  options = options.map(option => ({
    ...option,
    checked: availableColumns.includes(option.value)
  }));
});
  
  function toggleDropdown() {
    isOpen = !isOpen;
    updateIsOpen(isOpen);

  }

  function handleOptionClick(option: any) {
    
    option.checked = !option.checked;

    selectedOptions = options.filter((option) => option.checked);

    dispatch('selectedOptionsChange', selectedOptions);

  }
</script>
<div class="relative z-30">
  <button
    class="flex flex-wrap gap-2 py-1 px-2 bg-[#2fd5d2] border  rounded cursor-pointer"
    on:click={toggleDropdown}
  >
    <span class="text-white">Columns</span>

  </button>

  {#if isOpen}
    <div class="absolute z-10 -left-40 w-60 py-2 mt-1 overflow-y-auto bg-white border border-gray-400 rounded shadow-lg max-h-72">
      {#each options as option}
        <div class="flex items-center px-4 py-2 hover:bg-gray-100">
          <input
            type="checkbox"
            class="mr-2 leading-tight"
            bind:checked={option.checked}
            on:click={() => handleOptionClick(option)}
          />
          <span>{option.title}</span>
        </div>
      {/each}
    </div>
  {/if}
</div>

