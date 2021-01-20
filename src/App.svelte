<script>
	import { onMount } from "svelte"
	let navn = "Aksel"
	let august = true

	let container

	onMount( () => {

		const date = new Date()
		const day = date.getDay()
		
			
		container.scrollTo({
			top: 0,
			left: window.innerWidth * (day - 1),
			behavior: 'smooth'
		});

	})

	let timeplanAugust = [
		{
			dag: "mandag",
			timer: [
				{fag: "Markedsføring og ledelse", tid: "08:00 - 09:35"},
				{fag: "Kroppsøving", tid: "09:40 - 11:15"},
				{fag: "Studietid/møtetid", tid: "11:20 - 12:05"},
				{fag: "Historie", tid: "12:45 - 14:20"}
			]
		},
		{
			dag: "tirsdag",
			timer: [
				{fag: "Religion og etikk", tid: "09:40 - 10:25"},
				{fag: "Norsk hovedmål", tid: "10:30 - 14:20"},
				{fag: "Sosialkunnskap", tid: "14:25 - 16:0"}				
			]
		},
		{
			dag: "onsdag",
			timer: [
				{fag: "Veiledning", tid: "10:00 - 10:25"},
				{fag: "Religion og etikk", tid: "10:30 - 12:05"},
				{fag: "Samfunnsfaglig engelsk", tid: "12:45 - 14:20"}				
			]
		},
		{
			dag: "torsdag",
			timer: [
				{fag: "Sosialkunnskap", tid: "08:00 - 10:25"},
				{fag: "Historie", tid: "10:30 - 12:05"},
				{fag: "Markedsføring og ledelse", tid: "12:45 - 15:10"}				
			]
		},
		{
			dag: "fredag",
			timer: [
				{fag: "Samfunnsfaglig engelsk", tid: "08:00 - 10:25"},
				{fag: "Kroppsøving", tid: "10:30 - 12:05"}
			]
		}
	]

	let timeplanAksel = [
		{
			dag: "mandag",
			timer: [
				{fag: "Veiledning", tid: "09:30 - 10:00"},
				{fag: "Musikk", tid: "10:15 - 11:15"},
				{fag: "Norsk", tid: "12:00 - 13:00"},
				{fag: "KRLE", tid: "13:15 - 14:15"},
				{fag: "Tysk", tid: "15:00 - 16:00"}
			]
		},
		{
			dag: "tirsdag",
			timer: [
				{fag: "Norsk", tid: "08:30 - 10:00"},
				{fag: "Naturfag", tid: "10:15 - 11:15"},
				{fag: "Matte", tid: "12:00 - 13:00"},				
				{fag: "Samfunnsfag", tid: "13:15 - 14:15"}		
			]
		},
		{
			dag: "onsdag",
			timer: [
				{fag: "Tysk", tid: "08:30 - 09:30"},
				{fag: "Matte", tid: "10:15 - 11:15"},
				{fag: "Samfunnsfag", tid: "12:00 - 13:00"},
				{fag: "Engelsk", tid: "13:15 - 14:15"},
				{fag: "Fysak", tid: "15:00 - 16:00"}			
			]
		},
		{
			dag: "torsdag",
			timer: [
				{fag: "Engelsk", tid: "09:00 - 10:00"},
				{fag: "Gym", tid: "10:15 - 11:15"},
				{fag: "Naturfag", tid: "12:00 - 13:00"},
				{fag: "Norsk", tid: "13:15 - 14:15"}			
			]
		},
		{
			dag: "fredag",
			timer: [
				{fag: "Samfunnsfag", tid: "08:30 - 09:00"},
				{fag: "Mø", tid: "09:00 - 10:00"},
				{fag: "Matte", tid: "10:15 - 11:15"},
				{fag: "Gym", tid: "12:00 - 13:00"},
				{fag: "Kunst og håndtverk", tid: "13:15 - 15:00"}
			]
		}
	]

</script>

<main bind:this={container}>

	<section class="container">	
		{#if august}	
			{#each timeplanAugust as dag}
				<div>
					<article class="day"><h1>{dag.dag}</h1></article>
					<section class="grid">				
						{#each dag.timer as time}
							<article>
								<h1>{time.fag}</h1>
								<p>{time.tid}</p>
							</article>
						{/each}
					</section>
				</div>
			{/each}
		{:else}
		{#each timeplanAksel as dag}
			<div>
				<article class="day"><h1>{dag.dag}</h1></article>
				<section class="grid">				
					{#each dag.timer as time}
						<article>
							<h1>{time.fag}</h1>
							<p>{time.tid}</p>
						</article>
					{/each}
				</section>
			</div>
		{/each}
		{/if}
	</section>
	<button on:click={ () => august = false } class={!august ? "aksel selected" : "aksel"}>Aksel</button>
	<button on:click={ () => august = true } class={august ? "august selected" : "august"}>August</button>

</main>


<style>
	main {
		background-color: black;
		height: 100vh;
		width: 100vw;
		overflow: auto;	
		scroll-snap-type: x mandatory;
	}
	.container {
		height: 100%;
		width: 500vw;
		background-color: white;
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		
	}
	div {
		
	}
	.grid {
		scroll-snap-align: center;
		display: grid;
		align-content: start;
		gap: 2px;
		height: calc(100vh - 3rem);
	}

	article {
		font-size: 1.25rem;
		background-color: #eee;
		padding: 5px;
		text-align: center;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.day {
		background-color: rgb(152, 17, 17);
		color: white;
		text-transform: uppercase;
		height: 3rem;
	}
	button {
		position: absolute;
		bottom: 1rem;
		background-color: steelblue;
		color: white;
		border-radius: 0.5rem;
		font-size: 1.5rem;
		cursor: pointer;
	}
	.aksel {
		left: 1rem;
	}
	.august {
		right: 1rem;
	}
	.selected {
		padding: 1rem;
		font-weight: bold;
	}
</style>

