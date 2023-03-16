<script lang="ts">
  import { orderBy } from 'lodash';
	import { createEventDispatcher, onMount } from 'svelte';
	import MultiSelect from '../elements/multiSelect.svelte';
  import editIcon from '../../../assets/svg/edit.svg';
  import deleteIcon from '../../../assets/svg/trash.svg';
  interface Row {
    [key: string]: any;
    checked: boolean;
  }

  interface Column {
	value: any;
    key: string;
    title: string;
    sortable?: boolean;
  }

  export let rows: Row[] = [];
  export let columns: Column[] = [];
  export let availableColumns: string[] = [];
  export let actionList: string[] = [];
  export let bulckActions: string[] = [];


  export let actions = false;

  let isAction = false;
  let masterToggle = false;
  let masterIndeterminate = false;
  let sortBy: string = '';
  let sortDirection: 'asc' | 'desc' = 'asc';
  const dispatch = createEventDispatcher();
  let columnKeys:any;
  let selectedTitles: any;
  let searchTerm = '';
  let isOpen = false;
   onMount(() => {
    console.log("onMount");
    // updateColumn();
    // getPageData();
  });
// trouggle section
  function toggleAll() {
    rows = rows.map((item) => ({
      ...item,
      checked: masterToggle,
    }));
    masterIndeterminate = false;
  }

  function toggleRow(item: Row) {
    masterToggle = rows.every((item) => item.checked);
    masterIndeterminate = !masterToggle && rows.some((item) => item.checked);
  }

  $: selectedRows = rows.filter((item) => item.checked);

  // sorting section
  function sortByColumn(columnKey: string) {
    if (sortBy === columnKey) {
      sortDirection = sortDirection === 'asc' ? 'desc' : 'asc';
    } else {
      sortBy = columnKey;
      sortDirection = 'asc';
    }
    const sortedRows = orderBy(rows, [columnKey], [sortDirection]);

    rows = [...sortedRows];
  }

  // search section
  $: filteredRows = rows.filter((row) =>
  Object.values(row).some(
    (value) => String(value).toLowerCase().includes(searchTerm.toLowerCase())
  )
);
//pagination section
const options = columns.map((column) => ({
  title: column.title,
  value: column.key,
  checked: true,
}));
let selectedOptions:Column[] = [];

  function handleSelectedOptionsChange(event:any) {
    selectedOptions = event.detail;
    
    console.log(selectedOptions);
    console.log(options);
    updateColumn();

  }
  function updateIsOpen(value:any) {
    isOpen = value;
  }
 
function updateColumn(){
  columnKeys = columns.map(column => column.title);
  selectedTitles = selectedOptions.map(option => option.value);
  availableColumns = selectedOptions.map(option => option.value);
  console.log("test");
  console.log('selectedOptions '+ JSON.stringify(selectedOptions));
  console.log('options '+JSON.stringify(options));

  console.log('selectedTitles '+selectedTitles);
  console.log('columnKeys '+columnKeys);
}
</script>

<!-- {JSON.stringify(selectedOptions)} -->
<!-- {JSON.stringify(selectedColumns)} -->

{#if isOpen || isAction}
<div  class="absolute w-full md:w-[calc(100%_-_180px)] z-20 h-full " on:click={() => isOpen = false} on:click={() => isAction = false}></div>
{/if}
<section class="container mx-auto bg-white">
  <div class="overflow-x-auto shadow-lg rounded-lg">
    <div class='flex  justify-between items-center p-2'>
      <div class="flex flex-1">
        <input type="text" class="border rounded py-1 px-3 w-full" placeholder="Search" bind:value={searchTerm}/>
      </div>
     
      <div class="flex justify-between items-center space-x-2 px-2">
        <button class="bg-blue-500 text-white py-1 px-2 rounded z-30" on:click={()=> isAction = !isAction}>Actions</button>
        
        <div>
          {#if isAction}
          <div class="absolute z-30  w-40 py-2 mt-6 -ml-40 overflow-y-auto bg-white border border-gray-400 rounded shadow-lg max-h-72">
            {#each bulckActions as action}
              <div class="flex items-center px-4 py-2 hover:bg-gray-100">
                
                <span>{action}</span>
              </div>
            {/each}
          </div>
        {/if}
        </div>
        
        <div class="relative">
          <MultiSelect {availableColumns} bind:isOpen={isOpen} updateIsOpen={updateIsOpen} {options} on:selectedOptionsChange={handleSelectedOptionsChange}/>
        </div>
      </div>
    </div>
    <table class="w-full table-auto">
      <thead class="bg-gray-50 border">
        <tr class="text-gray-500 uppercase text-xs leading-normal">
          <th class="py-2 px-3 text-left"> 
            <input
              type="checkbox"
              class="form-checkbox text-blue-500"
              bind:checked={masterToggle}
              bind:indeterminate={masterIndeterminate}
              on:change={toggleAll}
            />
          </th>
          {#each columns as column}
          {#if availableColumns.includes(column.key) }
            <th class="py-2 px-3 cursor-pointer" on:click={() => column.sortable ? sortByColumn(column.key) : null}>
              <div class="flex items-center">
                <span>{column.title}</span>
                {#if column.sortable}
                  {#if sortBy === column.key}
                    <span>{sortDirection === 'asc' ? '▲' : '▼'}</span>
                  {:else}
                    <span></span>
                  {/if}
                {/if}
              </div>
            </th>
            {/if}
          {/each}
          {#if actions}
          <th class="py-2 px-3">Action</th>
          {/if}
        </tr>
      </thead>
      <tbody class="text-gray-500 text-sm font-light">
        {#each filteredRows as item}
          <tr class="{item.checked ? 'bg-blue-100' : ''}">
            <td class="py-2 px-3">
              <input
                type="checkbox"
                class="form-checkbox text-blue-500"
                bind:checked={item.checked}
                on:change={() => toggleRow(item)}
              />
            </td>
            {#each Object.entries(item) as [key, value]}
              {#if key !== 'checked' && availableColumns.includes(key)}
                <td class="py-2 px-3">{value}</td>
              {/if}
            {/each}
            {#if actions}
              <td class="py-2 px-3">
                {#each actionList as action}
                {#if action === 'Edit'}
                  <button class="border py-1 px-3 rounded" ><img src='{editIcon}' class="w-4" alt=""/></button>
                {/if}
                {#if action === 'Delete'}
                  <button class="border py-1 px-3 rounded" ><img src='{deleteIcon}' class="w-4" alt=""/></button>
                {/if}
                {/each}
              </td>
            {/if}
          </tr>
        {/each}
      </tbody>
    </table>
    <!-- <div>
      <button on:click={prevPage}>Previous</button>
      {#each Array.from(Array(numPages()).keys()) as i}
        <button on:click={() => setcurrentPage(i)}>{i + 1}</button>
      {/each}
      <button on:click={nextPage}>Next</button>
    </div> -->
    <!-- <div class="flex justify-center items-center space-x-2">
      <button class="bg-gray-200 hover:bg-gray-300 px-3 py-1 rounded-lg" disabled={currentPage === 1} on:click={() => setcurrentPage(1)}>
        <span>&laquo;</span>
      </button>
      
      {#each Array.from(Array(numPages()).keys()) as i,Index}
        <button class="bg-gray-200 hover:bg-gray-300 px-3 py-1 rounded-lg" class:font-bold={i+1 === currentPage} on:click={() => setcurrentPage(i+1)}>
          <span>{i + 1}</span>
        </button>
      {/each}
      
      <button class="bg-gray-200 hover:bg-gray-300 px-3 py-1 rounded-lg" disabled={currentPage === numPages()} on:click={() => setcurrentPage(numPages())}>
        <span>&raquo;</span>
      </button>
    </div> -->
  </div>
</section>
