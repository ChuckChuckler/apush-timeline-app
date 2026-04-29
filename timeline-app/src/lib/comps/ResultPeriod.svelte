<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, correctEvents, incorrectEvents, allInPeriod } = $props();

    let corrects:string[] = $state([]);
    let incorrects:string[] = $state([]);
    let notIncluded:string[] = $state([]);

    let container:any;

    let incorrectDisplay:string=$state("display:block");
    let correctMissingDisplay:string=$state("display:none");

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

    export function checkIncluded(){
        if(notIncluded.length==0){
            for(let i of allInPeriod){
            if(!corrects.includes(i)){
                notIncluded.push(i);
            }
        }
        
        }
        incorrectDisplay="display:none";
        correctMissingDisplay="display:block";
    }

    export function showIncorrect(){
        incorrectDisplay="display:block";
        correctMissingDisplay="display:none";
    }
</script>

<div class="bg-red-100 h-[20vw] overflow-auto" bind:this={container}>
    <h1>{periodName}</h1>
    <ul>
        {#each corrects as e}
            <li class="text-[#1FAB27]">{e}</li>
        {/each}
        <div style={incorrectDisplay}>
            {#each incorrects as e}
                <li class="text-red-500">{e}</li>
            {/each}
        </div>

        <div style={correctMissingDisplay}>
            {#each notIncluded as e}
                <li class="text-blue-500">{e}</li>
            {/each}
        </div>
    </ul>
</div>