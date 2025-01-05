<script>
    import * as Tone from "tone";
	import PlayButton from "../components/PlayButton.svelte";

    const reverb = new Tone.Reverb().toDestination();

    const synth = new Tone.PolySynth();

    synth.connect(reverb);

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

<div class="container" on:touchmove|preventDefault>
    <div class="buttons">
        <PlayButton
        on:clicked={handlePlayClick}
        on:touched={handlePlayTouch}
        note = "C4"
        colour = "yellow"/>
        
        <PlayButton
        on:clicked={handlePlayClick}
        on:touched={handlePlayTouch}
        note = "E4"
        colour = "red"/>
        
        <PlayButton
        on:clicked={handlePlayClick}
        on:touched={handlePlayTouch}
        note = "G4"
        colour = "blue"/>
        
        <PlayButton
        on:clicked={handlePlayClick}
        on:touched={handlePlayTouch}
        note = "C5"
        colour = "green"/>
    </div>
</div>

<style>
    .container{
        display: flex;
        height: 100vh;
    }
    .buttons {
        margin-top: 20%;
        margin-left: auto;
        margin-right: auto;
        display: grid;
        grid-template-rows: 10rem 10rem ;
        grid-template-columns: 10rem 10rem;
        column-gap: 2em;
        row-gap: 6em;
    }
</style>

