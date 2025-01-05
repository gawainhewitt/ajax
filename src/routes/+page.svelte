<script>
    import * as Tone from "tone";

    const synth = new Tone.Synth().toDestination();

</script> 



<button class="button" onclick="{() => {synth.triggerAttackRelease("C4", "8n")}}"></button>


<style>

    .button {
        background-color: yellow;
        font-size: 2rem;
        margin: 2em;
        padding: 2em;
        border-radius: 50%;
    }

</style>