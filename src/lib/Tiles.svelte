<script>
    import { onMount } from "svelte";


    export let root = ""
    export let x = 0
    export let y = 0

    let CANVAS

    let x_ = []
    let y_ = []

    let canvas_x = 0
    let canvas_y = 0

    $: {
        x_ = Array.apply(null, Array(Number(x))).map(()=>{})
        y_ = Array.apply(null, Array(Number(y))).map(()=>{})
    }

    let screen = async () => {
        let imgs_r = document.getElementsByClassName('tile')
        let imgs_ = [...imgs_r]
        console.log(imgs_)
        for (let img of imgs_) {
            if (img.id.startsWith("0/")) {
                canvas_y+=img.height
            }
            if (img.id.endsWith("/0")){
                canvas_x+=img.width
            }
            
        }
        
        await new Promise((resolve) => setTimeout(() => resolve(),500))
        
        let ctx = CANVAS.getContext("2d")

        let brush_x = 0
        let brush_y = 0

        for (let i = 0; i < x; i++) {
            let img
            brush_y = 0
            for(let j = 0; j < y; j++) {
                img = document.getElementById(`${i}/${j}`)
                ctx.drawImage(img,brush_x,brush_y)
                brush_y+=img.height
            }
            brush_x += img.width
        }
        window.alert('right-click on the map and save the picture')

    }

</script>

<div class="container">
    
    <div style="display: {canvas_x?'none':'block'};">
        <div style="display:flex;">
            {#each x_ as _,x_i }
                <div class="column">
                    {#each y_ as _,y_i }
                        <img class="tile" id="{x_i}/{y_i}" src="{`${root}/${x_i}/${y_i}.png`}" alt=''/>
                    {/each}
                </div>
            {/each}
        </div>
    </div>
    {#key canvas_x+"_"+canvas_y}
        <canvas width="{canvas_x}" height="{canvas_y}" bind:this={CANVAS}>

        </canvas>
    {/key}
    <div class="XY">{canvas_x} - {canvas_y}</div>
</div>
<button on:click={screen}>MAKE IT A CANVA</button>

<style>

    .container {
        position: relative;
        flex-grow: 1;
        overflow: scroll;
        background-color: gainsboro;
    }

    .column {
        display: flex;
        flex-direction: column;
    }

    .XY {
        position: absolute;
        left: 0.5em;
        top: 0.5em;
    }

</style>
