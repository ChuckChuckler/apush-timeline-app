<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, eventsAdded, click } = $props();

    let events:string[] = $state([]);

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
</script>

<div class="bg-red-100 h-[20vw] overflow-auto" bind:this={container}>
    <h1>{periodName}</h1>
    <ul>
        {#each events as e}
            <button style="z-index: 5;" class="bg-blue-300">{e}</button>
        {/each}
    </ul>
</div>