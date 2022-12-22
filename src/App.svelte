
<script>
	import Timer from "./Timer.svelte"; 
	import HowTo from "./howTo.svelte"; 
	let audio ;
	let timerEnds = (e) =>{
		console.log(e.detail);
		audio.play();
	}
</script>
<style>
    h3 {
		text-align: center;
	}
</style>

<Timer  on:end={timerEnds}/>
<HowTo/>

<h3>
	<a href="https://www.who.int/gpsc/clean_hands_protection/en/">
		Picture source
	</a>

	<a href="https://freesound.org/people/metrostock99/sounds/345086/">
		Sound source
	</a>
</h3>

<audio bind:this={audio}>
	<source src="sound.wav">
</audio>