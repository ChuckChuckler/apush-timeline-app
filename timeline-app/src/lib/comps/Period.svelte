<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, eventsAdded, click } = $props();
    let events:string[] = $state([]);

    let container:any;

    onMount(()=>{
        events=eventsAdded;
        container.onclick=click;
    });

    export function addEvent(event:string){
        events.push(event);
    }

    export function getEvents(){
        return events;
    }
</script>

<div class="bg-red-300 h-[20vw] overflow-auto" bind:this={container}>
    <h1>{periodName}</h1>
    <ul>
        {#each events as e}
            <li>{e}</li>
        {/each}
    </ul>
</div>