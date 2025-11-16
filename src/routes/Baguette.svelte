<script lang="ts">
    import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';

    let currentDate : Date = new Date();

    let day = currentDate.getDate();
    let month = currentDate.getMonth() + 1;
    let year = currentDate.getFullYear();

    let map = new Map<string, string>([
        ["12/11/2025", "Chicken Salad Baguette"],
        ["13/11/2025", "Tuna Salad Baguette"],
        ["14/11/2025", "Ham Salad Baguette"],
        ["15/11/2025", "Ham & Cheese Baguette"],
        ["16/11/2025", "Cheese Salad Baguette"],
        ["17/11/2025", "Egg & Tomato Baguette"],
    ]);

    let baguetteOfTheDay = map.get(day + "/" + month + "/" + year)

</script>

<div>
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
</div>

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