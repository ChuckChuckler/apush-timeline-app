<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, eventsAdded, click, replaceEvent } = $props();

    let events:string[] = $state([]);
    let eventButtonBinds:HTMLButtonElement[] = $state([]);

    let container:any;

    onMount(()=>{
        events=eventsAdded;
        container.addEventListener("click", (e:MouseEvent)=>{
            if(e.target==container){
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

<div class="bg-red-100 h-[20vw] overflow-auto" bind:this={container}>
    <h1>{periodName}</h1>
    <ul>
        {#each events as e, i}
            <button bind:this={eventButtonBinds[i]} style="z-index: 5;" class="bg-blue-300" onclick={function(){replace(e)}}>{e}</button>
            <br>
        {/each}
    </ul>
    <br>
    <br>
</div>