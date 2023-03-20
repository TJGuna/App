<script lang="ts">
	import { myStore } from './../../../store/store.js';
import { flip } from 'svelte/animate';
  import { dndzone } from 'svelte-dnd-action';
	const flipDurationMs = 150;
	export let name: string;

	export let items;
	export let onDrop;
	
	function handleDndConsiderCards(e) {
    console.warn("got consider", name); 
		items = e.detail.items;
  }
  function handleDndFinalizeCards(e) {
    onDrop(e.detail.items);
  }
  function edit(id:number){
    myStore.set(id);
  }
</script>
<div class='border-2 border-gray-600 bg-gray-200 rounded-md p-2 w-full'>
    <div class="{name === "TODO" ? 'bg-cyan-300':''} {name === "PROCESS" ? 'bg-cyan-400':''} {name === "DONE" ? 'bg-cyan-500':''}  {name === "CHECKED" ? 'bg-cyan-600':''} {name === "DEPLOYED" ? 'bg-cyan-700':''} py-2 -mx-2 -mt-2 text-center">
       {name}
   </div>
   <div class="space-y-2 py-2 " use:dndzone={{items, flipDurationMs, zoneTabIndex: -1}}
         on:consider={handleDndConsiderCards} 
            on:finalize={handleDndFinalizeCards}>
               {#each items as item (item.id)}
               <div on:click={()=>edit(item.id)} class="flex flex-col p-1 border-2 bg-white border-gray-400 rounded-md cursor-move space-y-1" animate:flip="{{duration: flipDurationMs}}">
                <div class="flex justify-between items-center"  >
                  <div>{item.name}</div>
                </div>
                <div class="{item.imageUrl === ''?'hidden':'block'}">
                  <img class=" w-full h-full" src={item.imageUrl} alt=''>
                </div>
                <div class="bg-gray-100 text-sm "  >
                  {item.task}
                </div>
                <div class="flex justify-between items-center mr-1">
                  <div class="px-2 text-xs text-white {item.category === 'technical' ? 'bg-gray-400 ' :
                  item.category === 'financial' ? 'bg-zinc-500' :
                  item.category === 'law and order' ? 'bg-cyan-700' :
                  item.category === 'high' ? 'bg-orange-400' :''} rounded-full">{item.category}</div>
                  <div class="p-1.5 {item.status === 'highest' ? 'bg-red-400' :
                  item.status === 'medium' ? 'bg-blue-400' :
                  item.status === 'low' ? 'bg-green-400' :
                  item.status === 'high' ? 'bg-orange-400' :''}  rounded-full" ></div>
                </div>
               </div> 
        
       {/each}
   </div>
   <button class=" {name === 'TODO'? 'block':'hidden'} bg-cyan-500 hover:bg-cyan-700 text-white font-bold py-1 px-4 w-full rounded">
      Add
    </button>
</div>
