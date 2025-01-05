<script>
    import { createEventDispatcher } from 'svelte';
	import { Tone } from 'tone/build/esm/core/Tone';

    let buttonText = '';
    export let note;

    const dispatch = createEventDispatcher()

    const handleButton = () => {
        dispatch("clicked", note);
        // alert("click");
    }

</script>


<button 
    class="button" 
    on:touchstart|preventDefault|stopPropagation="{handleButton}" 
    on:click|preventDefault|stopPropagation="{handleButton}"
    >
    {buttonText}
    <div class="screen-reader-description">
        click button for sound
    </div>
</button>


<style>

    .button {
        background-color: yellow;
        font-size: 2rem;
        margin: 2em;
        padding: 2em;
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