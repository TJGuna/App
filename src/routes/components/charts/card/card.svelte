<script lang="ts">
    import  clock  from "./../../../../assets/svg/time-forward.svg";

    export let Title: string;
    export let Value: string;
    export let ColorFrom: string;
    export let ColorTo: string;
    export let Icon: string;
    export let Time: string;
    

</script>
<div class="text-white h-28 w-full flex flex-col mx-auto shadow-lg bg-gradient-to-l { ColorFrom } { ColorTo} rounded-md">
    <div class=" p-2 h-18 flex justify-between items-center">
        <div class=" p-2 h-18 space-y-1 ">
            <div class=" text-md font-bold">{Value}  </div>
            <div class=" text-sm">{Title}</div>
        </div>
        <div class=" p-2 h-18 flex items-center justify-center"><img src={Icon} alt='' class="w-6 h-6 "></div>
    </div>
    <div class=" w-full border-t border-white h-10 flex items-center justify-around text-xs">
        <div class=" "><img src={clock} alt='' class="w-4 h-4 "></div>
        <div class="  ">update : {Time}</div>
    </div>
</div>
 