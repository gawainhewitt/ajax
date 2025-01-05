<script>
    import * as Tone from "tone";

    const synth = new Tone.Synth().toDestination();

</script> 


<h1>Welcome to Ajax</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<button onclick="{() => {synth.triggerAttackRelease("C4", "8n")}}">hello</button>