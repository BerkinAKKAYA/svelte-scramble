<script>
	import Scramble from '../Scramble'
</script>

<Scramble>
	<h1>YOU HAVE BEEN HACKED</h1>
	<p>svelte-scramble</p>
</Scramble>

<style>
	:global(body) {
		width: 100vw;
		height: 100vh;
		margin: 0;

		display: grid;
		place-items: center;

		background: black;
		color: lightgreen;

		cursor: default;
		font-size: 2.5vw;
		text-align: center;
	}

	:global(p) {
		font-size: 1.5vw;
		opacity: .5;
	}
</style>
