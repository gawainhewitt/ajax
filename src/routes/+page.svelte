<script>
    import * as Tone from "tone";
	import PlayButton from "../components/PlayButton.svelte";

    const synth = new Tone.Synth().toDestination();

    synth.set({
        "envelope": {
            "attack": 0.5
        }
    });

    const handlePlayClick = (element) => {
        Tone.start();
        console.log(element.detail);
        const note = element.detail;
        synth.triggerAttackRelease(note, "8n");
    }

</script> 

<div class="buttons">
    <PlayButton
    on:clicked={handlePlayClick}
    note = "C4"/>
    
    <PlayButton
    on:clicked={handlePlayClick}
    note = "E4"/>
    
    <PlayButton
    on:clicked={handlePlayClick}
    note = "G4"/>
    
    <PlayButton
    on:clicked={handlePlayClick}
    note = "A4"/>
</div>

<style>
    .buttons {
        display: grid;
        grid-template-rows: 10rem 10rem ;
        grid-template-columns: 10rem 10rem;
    }
</style>

