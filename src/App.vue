<template>
	<header>
		<h1>Reakcją tajmer</h1>
		<p>Jak szybko złapiesz kosmitę?</p>
	</header>
	<main>
		<div>
			<Blob v-if="isPlaying" :delay="delay" @end="endGame" />
			<Results v-if="showMissionSummary" :time="time" />
			<button @click="start" :hidden="isPlaying">
				<span v-if="!hasBeenPlayed">Nowa gra</span>
				<span v-else>Zagraj ponownie</span>
			</button>
		</div>
	</main>
</template>

<script>
import Blob from './components/Blob.vue'
import Results from './components/Results.vue'
export default {
	name: 'App',
	components: {
		Blob,
		Results,
	},
	data() {
		return {
			isPlaying: false,
			delay: null,
			time: null,
			showMissionSummary: false,
			hasBeenPlayed: false,
			// results: [],
			// average: null,
		}
	},
	methods: {
		start() {
			this.isPlaying = true;
			(this.delay = 2000 + Math.random() * 5000), (this.showMissionSummary = false)
		},
		endGame(reactionTime) {
			(this.time = reactionTime), (this.isPlaying = false)
			this.showMissionSummary = true
			this.hasBeenPlayed = true
		},
		// calculateAverage() {
		// 	if(hasBeenPlayed){
		// 		this.results.push(this.time)
		// 	const sum = this.results.reduce((a, b) => a + b, 0)
		// 	this.average = Math.round(sum / this.results.length)
		// 	}
		}
	}

</script>

<style lang="scss" scoped>
header {
	display: flex;
	flex-direction: column;
	align-items: center;
	padding: var(--section-gap);
}

@media (min-width: 1024px) {
	header {
		display: flex;
		place-items: center;
	}
}

h1,
button,p {
	font-size: 6rem;
	font-weight: bold;
	color: hsla(305, 73%, 41%, 0.4);
	background: linear-gradient(90deg, #fc466b 0%, #3f5efb 100%);
	background-clip: text;
	--webkit-text-fill-color: transparent;
	letter-spacing: -0.04em;
	user-select: none;
	-webkit-user-select: none;
	text-shadow: -15px 5px 20px rgba(62, 0, 77, 0.103);
	margin: 0;
	padding: 0;
	text-align: center;
	font-family: Bangers, cursive;
	cursor: default;
}

p{
	font-size: 2rem;
}

main {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	padding: var(--section-gap);
	height: 80vh;

	button {
		font-size: 3rem;
		text-align: center;
		color: hsl(305, 73%, 41%);
		background: linear-gradient(90deg, #fc466b 0%, #3f5efb 100%);
		background-clip: text;
		--webkit-text-fill-color: transparent;
		user-select: none;
		-webkit-user-select: none;
		letter-spacing: -0.04em;
		border: none;
		place-self: center;
		padding: 1rem 2rem;
		cursor: pointer;
		transition: all 0.2s ease-in-out;
		&:hover {
			transform: scale(1.1);
		}
		&:active {
			transform: scale(0.9);
		}
	}
}
</style>
