<script>
	import { onMount } from "svelte"
	let navn = "Aksel"

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
				{fag: "Religion og etikk", tid: "08:00 - 09:35"},
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
</script>

<main bind:this={container}>

	<section class="container">
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
	</section>

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
</style>

