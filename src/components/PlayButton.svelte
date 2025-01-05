<script>
    import { createEventDispatcher } from 'svelte';
	import { Tone } from 'tone/build/esm/core/Tone';

    let buttonText = '';
    export let note;
    export let colour;

    const dispatch = createEventDispatcher()

    const handleButton = (e) => {        
        if (e.type === "touchstart"){
            const touch = e.targetTouches[0].identifier;
            dispatch('touched', {note, touch})
        } else {
            dispatch("clicked", note);
        }
        console.log(e.type);
    }

</script>


<button 
    class="button" 
    on:touchstart|preventDefault|stopPropagation="{handleButton}" 
    on:click|preventDefault|stopPropagation="{handleButton}"
    style={`background-color:${colour};`}
    >
    {buttonText}
    <div class="screen-reader-description">
        click button for sound
    </div>
</button>


<style>

    .button {
        margin: 0.5em;
        border-radius: 50%;
        border-color: black;
    }

    .screen-reader-description {
        clip: rect(0 0 0 0);
        clip-path: inset(50%);
        height: 1px;
        overflow: hidden;
        position: absolute;
        white-space: nowrap;
        width: 1px;
    }

</style>