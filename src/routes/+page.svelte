<script>
    import Tiles from "$lib/Tiles.svelte";
    import { onMount } from "svelte";

    let height
    onMount(() => height = window.innerHeight)

    let url = ""
    let root = ""
    let x = 0
    let y = 0

    let click = () => {
        if (!url.match(/^https:\/\/tiles\.legendkeeper\.com\/[^\/]+\/[^\/]+\/tiles\/\d+\/\d+\/\d+\.png$/))
            window.alert('bad format')
        else {
            let splittedURL = url.split('/')
            root = splittedURL.slice(0,splittedURL.length-2).join('/')
            x = splittedURL[splittedURL.length-2]
            y = splittedURL[splittedURL.length-1].split('.')[0]
        }
    }

</script>

<div>

    <input 
        bind:value="{url}" 
        type="text" 
        placeholder="https://tiles.legendkeeper.com/processed/id/tiles/6/63/29.png"
        />

    <button 
        on:click="{click}"
        disabled="{url?'':'true'}"
        >
        CHARGE TILES
    </button>

    {#key root+x+y}
        <Tiles {x} {y} {root} />
    {/key}

</div>

<style>

    div {
        gap : 0.5em;
        display: flex;
        flex-direction: column;
        height: 100vh;
    }
    
</style>