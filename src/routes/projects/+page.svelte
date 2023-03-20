<script lang="ts">
	import Input from './../components/elements/input.svelte';
	import { myStore } from './../../store/store.js';
    import PageHeader from "../components/page-header.svelte";
    import PageBody from "../components/page-body.svelte";
  import DragAndDrop from "../components/dragAndDrop/dragAndDrop.svelte";
  import SideOver from "../components/side-over.svelte";
  import tasks from "../../mock/tasks.json";
  import TextArea from '../components/elements/textArea.svelte';
  let show = false;
  let id = 0;
  let columnsData = tasks;
  let title = "Task Details";

	function handleBoardUpdated(newColumnsData:any) {
		// if you wanted to update a database or a server, this is where you would do it
		columnsData = newColumnsData;
	}
  let filteredData;
  let task = {
    id: 0,
    name: "",
    createdDate:'',
    endDate:'',
    lead:'',
    category: "",
    status: "",
    imageUrl: "",
    task: "",
  };
  myStore.subscribe(value => {
    id = value;
    if(id !== 0){
      show = true;
       filteredData = tasks.filter(obj => obj.items.some(item => item.id === id));
      console.log(filteredData);
      task = filteredData[0].items.filter(obj => obj.id === id)[0];
      console.log(task);
    }
    else{
      show = false;

    }

  });
</script>
{id}
{#if id !== 0 }
<div  class="absolute w-full md:w-[calc(100%_-_180px)] z-20  h-full " on:click={() => show = false} on:click={() => myStore.set(0)}></div>
{/if}
<SideOver {title} {show}>
    <form class="mt-2">
      <div class="flex flex-col space-y-20">
        <div class="flex ">
          <Input label="Name" value={task.name}/>
        </div>
        <div class="flex ">
          <TextArea label="Description" value={task.task}/>
        </div>
      </div>
    </form>
  <div >
    <!-- {#each filteredData as item}
      {item.name}
      {#each item.items as tas}
        {tas.name}
      {/each}
    {/each} -->
  </div>
</SideOver> 
<PageHeader Title="Projects" >
        <button class="px-2 py-1 border rounded text-white bg-[#62CDFF]">Add New Task</button>
</PageHeader>
<PageBody>
    <DragAndDrop columns={columnsData}  onFinalUpdate={handleBoardUpdated}/>
</PageBody>
