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

    export function resetEvents(){
        corrects=[];
        incorrects=[];
        notIncluded=[];
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

<div class="scrollbar bg-[#535170] hover:bg-[#494763] rounded-[12.5px] box-border p-[10px] h-[20vw] overflow-auto overflow-auto" bind:this={container}>
    <h1 class="istok-web-bold text-[white] text-center">{periodName}</h1>
    <ul class="text-center">
        {#each corrects as e}
            <li class="text-[#83e888] mb-[5px]">{e}</li>
        {/each}
        <div style={incorrectDisplay}>
            {#each incorrects as e}
                <li class="text-[#f58686] mb-[5px]">{e}</li>
            {/each}
        </div>

        <div style={correctMissingDisplay}>
            {#each notIncluded as e}
                <li class="text-[#a8d2fa]">{e}</li>
            {/each}
        </div>
    </ul>
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