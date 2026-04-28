<script lang="ts">
    import { onMount } from "svelte";

    let { periodName, eventsAdded } = $props();
    let events:string[] = $state([]);

    onMount(()=>{
        events=eventsAdded;
    })
</script>

<div class="bg-red-300 h-[20vw]">
    <h1>{periodName}</h1>
</div>