<script>
	import Column from './column.svelte';
 import { flip } from 'svelte/animate';
  import { dndzone } from 'svelte-dnd-action';
	const flipDurationMs = 300;
	
  export let columns;
	// will be called any time a card or a column gets dropped to update the parent data
	export let onFinalUpdate;
 
  function handleDndConsiderColumns(e) {
    columns = e.detail.items;
  }
  function handleDndFinalizeColumns(e) {
    onFinalUpdate(e.detail.items);
  }
 	function handleItemFinalize(columnIdx, newItems) {
		columns[columnIdx].items = newItems;
		onFinalUpdate([...columns]);
	}
</script>

<section class="flex space-x-2 px-2" use:dndzone={{items:columns, flipDurationMs, type:'column'}} on:consider={handleDndConsiderColumns} on:finalize={handleDndFinalizeColumns}>
  {#each columns as {id, name,items,category,status,imageUrl,task}, idx (id)}
    <div class="w-full"animate:flip="{{duration: flipDurationMs}}" >    
      <Column name={name} items={items} {category} {status} {task} {imageUrl} onDrop={(newItems) => handleItemFinalize(idx, newItems)} />
    </div>
  {/each}
</section>