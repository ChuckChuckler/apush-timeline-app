<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, correctEvents, incorrectEvents } = $props();

    let corrects:string[] = $state([]);
    let incorrects:string[] = $state([]);

    let container:any;

    onMount(()=>{
        corrects=correctEvents;
        incorrects=incorrectEvents;
    });

    export function addCorrect(event:string){
        corrects.push(event);
    }

    export function addIncorrect(event:string){
        incorrects.push(event);
    }

    export function getCorrects(){
        return corrects;
    }

    export function getIncorrects(){
        return incorrects;
    }
</script>

<div class="bg-red-100 h-[20vw] overflow-auto" bind:this={container}>
    <h1>{periodName}</h1>
    <ul>
        {#each corrects as e}
            <li class="text-[#1FAB27]">{e}</li>
        {/each}
        {#each incorrects as e}
            <li class="text-red-500">{e}</li>
        {/each}
    </ul>
</div>