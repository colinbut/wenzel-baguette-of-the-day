<script lang="ts">
    import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';
	
	import tunaSaladBaguette from '$lib/images/tunasalad.jpeg';
	import chickenSaladBaguette from '$lib/images/chicken-salad.jpeg'
	import cheeseSaladBaguette from '$lib/images/cheese-salad.jpeg'
	import hamSaladBaguette from '$lib/images/ham-salad-baguette.jpeg'
	import hamCheeseSaladBaguette from '$lib/images/ham-and-cheese.jpeg'
	import eggTomatoSaladBaguette from '$lib/images/egg-and-tomato.jpeg'

	const baguettes: string[] = [];
	baguettes.push("Chicken Salad Baguette");
	baguettes.push("Tuna Salad Baguette");
	baguettes.push("Ham Salad Baguette");
	baguettes.push("Ham & Cheese Baguette");
	baguettes.push("Cheese Salad Baguette");
	baguettes.push("Egg & Tomato Baguette");

    let map = new Map<string, string>([]);

	const endDate = new Date("2026-01-31");

	let startingDate = new Date("2025-12-07");
	
	while (startingDate < endDate) {
		//console.log("Starting Date is:" + startingDate + " and EndDate is: " + endDate);
		for (var baguette of baguettes) {
			let tomorrowDate = new Date(startingDate);
			tomorrowDate.setDate(startingDate.getDate()+1);
			map.set(tomorrowDate.getDate()+"/"+(tomorrowDate.getMonth()+1)+"/"+tomorrowDate.getFullYear(), baguette);
			startingDate = tomorrowDate;
			//console.log("[Tomorrow date is]: " + tomorrowDate + "[new start date is]: " + startingDate + " and baguette is: " + baguette);
		}
	}
	console.log([...map.entries()]);
	
	let currentDate : Date = new Date();
    let day = currentDate.getDate();
    let month = currentDate.getMonth() + 1;
    let year = currentDate.getFullYear();
	
	//console.log(day + "/" + month + "/" + year)
    let baguetteOfTheDay = map.get(day + "/" + month + "/" + year)?.toUpperCase()
	console.log("Baguette of the Day is: " + baguetteOfTheDay)

</script>

<div>
    <h1>
		<table>
			<tbody>
				<tr>
					<td>
						<div class="display-bar-decoration"></div>
					</td>
					<td>
						<div class="display-text">
							BAGUETTE<br />OF THE DAY
						</div>
					</td>
				</tr>
			</tbody>
		</table>
	</h1>
	<span class="welcome">
		<picture>
			{#if baguetteOfTheDay == "TUNA SALAD BAGUETTE"}
				<source srcset={tunaSaladBaguette} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			{:else if baguetteOfTheDay == "CHICKEN SALAD BAGUETTE"}
				<source srcset={chickenSaladBaguette} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			{:else if baguetteOfTheDay == "HAM SALAD BAGUETTE"}
				<source srcset={hamSaladBaguette} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			{:else if baguetteOfTheDay == "CHEESE SALAD BAGUETTE"}
				<source srcset={cheeseSaladBaguette} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			{:else if baguetteOfTheDay == "HAM AND CHEESE BAGUETTE"}
				<source srcset={hamCheeseSaladBaguette} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			{:else if baguetteOfTheDay == "EGG AND TOMATO BAGUETTE"}
				<source srcset={eggTomatoSaladBaguette} type="image/webp" />
				<img src={welcomeFallback} alt="Welcome" />
			{:else}
				<img src={welcomeFallback} alt="Welcome" />
			{/if}
		</picture>
	</span>
	<h2 class="baguette-text-bg-panel">
		{baguetteOfTheDay}
	</h2>
</div>

<style>
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
		border-color: black;
		border-width: 1px;
	}

	.display-bar-decoration {
		width: 10px;
		height: 60px;
		background-color: #540884;
		/* padding: 2px; */
	}

	.display-text {
		text-align: left;
		color: white;
	}

	.baguette-text-bg-panel {
  		border-radius: 25px;
  		background-color: #540884;
  		padding: 20px;
  		width: 250px;
  		height: 10px;
		color: white;
		text-align: center;
    }
</style>