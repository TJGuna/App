<script>
    export let label = 'Text';
    export let value = '';
    export let type = 'text';
    export let placeholder = 'placeholder';

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
    <div class="relative flex flex-col h-24 items-start w-full">
      <textarea
        id={label}
        class="peer h-20 px-4 py-2 w-full border rounded-md border-slate-600 placeholder-transparent peer-placeholder-shown:border-blue-600 peer-placeholder-shown:text-base peer-focus:border-blue-600 peer-focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-300"
        placeholder=" "
        bind:value={value}
      ></textarea>
      <label
        for={label}
        class="absolute -top-8 left-0 px-2 py-1 text-blue-600 pointer-events-none transition-all duration-100 peer-placeholder-shown:text-base peer-placeholder-shown:text-gray-400 peer-placeholder-shown:mt-4   "
      >
        {label}
      </label>
    </div>
  
  