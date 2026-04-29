<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, eventsAdded, click, replaceEvent } = $props();

    let events:string[] = $state([]);
    let eventButtonBinds:HTMLButtonElement[] = $state([]);

    let container:any;
    let ul:any;

    onMount(()=>{
        events=eventsAdded;
        container.addEventListener("click", (e:MouseEvent)=>{
            if(e.target==container || e.target==ul){
                click();
            }
        });
    });

    export function addEvent(event:string){
        events.push(event);
    }

    export function getEvents(){
        return events;
    }

    function replace(e:string){
        eventButtonBinds.splice(events.indexOf(e),1);
        events.splice(events.indexOf(e),1);
        replaceEvent(e);
    }
</script>

<div class="scrollbar bg-[#535170] hover:bg-[#494763] rounded-[12.5px] box-border p-[10px] h-[20vw] overflow-auto" bind:this={container}>
    <h1 class="istok-web-bold text-[white] text-center">{periodName}</h1>
    <ul class="text-center" bind:this={ul}>
        {#each events as e, i}
            <button bind:this={eventButtonBinds[i]} style="z-index: 5;" class="border-[1px] border-white rounded-[8px] mb-[5px] text-white p-[5px] hover:bg-[#3d3b54]" onclick={function(){replace(e)}}>{e}</button>
            <br>
        {/each}
    </ul>
    <br>
    <br>
</div>

<style>
    .istok-web-bold {
        font-family: "Istok Web", sans-serif;
        font-weight: 700;
        font-style: normal;
    }

    .scrollbar{
        scrollbar-width: thin;
    }
</style>