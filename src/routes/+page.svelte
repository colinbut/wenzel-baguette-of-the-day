<script lang="ts">
	import Baguette from './Baguette.svelte';
</script>

<svelte:head>
	<title>Wenzel Baguette of the Day</title>
	<meta name="description" content="Wenzel's Baguette of the Day" />
</svelte:head>

<section>
	<Baguette />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}
	
</style>
