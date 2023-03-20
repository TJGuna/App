<script>
    export let label = 'Text';
    export let value = '';
    export let type = 'text';
  </script>
    
  <!-- <div >
    <input class="peer px-4 py-2 w-96 border border-slate-600 placeholder-transparent"
      type={type}
      value={value}
      id={label}
    />
    <label class="ml-4 -mt-11 text-xs text-blue-600 peer-placeholder-shown:text-gray-400 peer-placeholder-shown:-mt-8 peer-placeholder-shown:text-base duration-300"
     for={label}>
      {label}
    </label>
  </div>
    -->
  <div class="flex flex-col  h-10 items-start w-full ">
    <input bind:value={value} type="text" id='{label}' placeholder="John Doe" class=" peer px-4 py-2 w-full border rounded-md border-slate-600 placeholder-transparent" />
    <label  for="{label}" class="bg-white ml-[18px] rounded px-2 -mt-[50PX] text-xs text-blue-600 peer-placeholder-shown:text-gray-400 peer-placeholder-shown:-mt-8 peer-placeholder-shown:text-base duration-300">
        {label}
    </label>
</div>
  
  
  