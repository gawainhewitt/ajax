<script>
    import * as Tone from "tone";
	import PlayButton from "../components/PlayButton.svelte";

    const synth = new Tone.PolySynth().toDestination();

    synth.set({
        "envelope": {
            "attack": 0.5
        }
    });

    const handlePlayClick = (element) => {
        Tone.start();
        console.log(element.detail);
        const note = element.detail;
        playSound(note);
    }

    const handlePlayTouch = (element) => {
        Tone.start();
        console.log(element);
        const note = element.detail.note;
        playSound(note);
    }

    const playSound = (note)=> {
        synth.triggerAttackRelease(note, "8n");
    }

</script> 

<div class="buttons">
    <PlayButton
    on:clicked={handlePlayClick}
    on:touched={handlePlayTouch}
    note = "C4"/>
    
    <PlayButton
    on:clicked={handlePlayClick}
    on:touched={handlePlayTouch}
    note = "E4"/>
    
    <PlayButton
    on:clicked={handlePlayClick}
    on:touched={handlePlayTouch}
    note = "G4"/>
    
    <PlayButton
    on:clicked={handlePlayClick}
    on:touched={handlePlayTouch}
    note = "A4"/>
</div>

<style>
    .buttons {
        display: grid;
        grid-template-rows: 10rem 10rem ;
        grid-template-columns: 10rem 10rem;
    }
</style>

