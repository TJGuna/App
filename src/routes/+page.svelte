<script lang="ts">
	import Cards from "./components/charts/card/cards.svelte";
	import Card from "./components/charts/card/card.svelte";

    import PageBody from "./components/page-body.svelte";
    import PageHeader from "./components/page-header.svelte";
    import  icon1  from "../assets/svg/menu-burger.svg";
	import Bars from "./components/charts/bar/bars.svelte";
	import Bar from "./components/charts/bar/bar.svelte";
	import Pie from "./components/charts/pie/pie.svelte";
	import Pies from "./components/charts/pie/pies.svelte";
    import Doughnut from "./components/charts/doughnut/doughnut.svelte";
    import Doughnuts from "./components/charts/doughnut/doughnuts.svelte";
	import Lines from "./components/charts/line/lines.svelte";
    import Line from "./components/charts/line/line.svelte";


</script>
<section>
    <PageHeader Title="Dashboard" >
        <div class="flex items-center space-x-4">
            <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                New
            </button>
            <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                New
            </button>
        </div>
    </PageHeader>
    <PageBody>
        <Cards >
            <div class="flex w-full  space-x-4">
                <div class="grid col-span-1 w-full "> <Card Title="Total Sales" Value="100" ColorFrom="from-cyan-400" ColorTo="to-blue-500" Icon="{icon1}" Time="2:15 PM"/> </div>
                <div class="grid col-span-1 w-full "> <Card Title="Total Sales" Value="100" ColorFrom="from-green-400" ColorTo="to-green-600" Icon="{icon1}" Time="2:15 PM"/> </div>
                <div class="grid col-span-1 w-full "> <Card Title="Total Sales" Value="100" ColorFrom="from-orange-300" ColorTo="to-red-400" Icon="{icon1}" Time="2:15 PM"/> </div>
                <div class="grid col-span-1 w-full "> <Card Title="Total Sales" Value="100" ColorFrom="from-purple-500" ColorTo="to-violet-700" Icon="{icon1}" Time="2:15 PM"/> </div>
                <div class="grid col-span-1 w-full "> <Card Title="Total Sales" Value="100" ColorFrom="from-fuchsia-500" ColorTo="to-pink-600" Icon="{icon1}" Time="2:15 PM"/> </div>
           </div>
            
        </Cards>
        <div class=' grid grid-cols-3 gap-2'>            
            <div class="grid col-span-3 lg:col-span-2 ">
                <Bars>
                    <Bar></Bar> 
                </Bars>
            </div>
            <div class="grid col-span-3 lg:col-span-1 ">
                <Doughnuts>
                    <Doughnut></Doughnut>
                </Doughnuts>
            </div>
            
        </div>
        <div class=' grid grid-cols-3 gap-2'>
            <div class="grid col-span-3 lg:col-span-1  ">
                <Pies>
                    <Pie></Pie> 
                </Pies>
            </div>
            <div class="grid col-span-3 lg:col-span-2  ">
                <Lines>
                    <Line></Line>
                </Lines>
            </div>
        </div>
        
    </PageBody>
</section>