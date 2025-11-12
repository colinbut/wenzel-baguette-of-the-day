<script lang="ts">
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';
</script>

<svelte:head>
	<title>Wenzel Baguette of the Day</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			</picture>
		</span>

		baguette<br />of the day
	</h1>

	<h2 class="baguette-text-bg-panel">
		Tuna Salad Baguette
	</h2>

	<!-- <h2>
		try editing <strong>src/routes/+page.svelte</strong>
	</h2> -->

	<Counter />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}

	.baguette-text-bg-panel {
  		border-radius: 25px;
  		background-color: #540884;
  		padding: 20px;
  		width: 200px;
  		height: 10px;
		color: white;
}
</style>
