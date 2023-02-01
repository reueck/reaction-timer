<template>
	<header>
		<h1>Reakcją tajmer</h1>
		<div>
      	<Blob v-if="isPlaying" :delay="delay" />
			<button @click="start" :hidden="isPlaying">Nowa gra</button>
		</div>
	</header>

</template>

<script>
import Blob from './components/Blob.vue'
export default {
	name: 'App',
	components: {
		Blob,
	},
	data() {
		return {
			isPlaying: false,
			delay: null,
		}
	},
	methods: {
		start() {
			this.isPlaying = true
			this.delay = 2000 + Math.random() * 5000
		},
	},
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
button {
	font-size: 6rem;
	font-weight: bold;
	letter-spacing: 0.6rem;
	background: linear-gradient(90deg, #fc466b 0%, #3f5efb 100%);
	background-clip: text;
	--webkit-text-fill-color: transparent;
	letter-spacing: -0.04em;
	user-select: none;
	text-shadow: -15px 5px 20px rgba(61, 0, 77, 0.38);
	margin: 0;
	text-align: center;
	font-family: Bangers, cursive;
}

button {
	font-size: 4rem;
	color: white;
	background: linear-gradient(90deg, #fc466b 0%, #3f5efb 100%);
	background-clip: text;
	--webkit-text-fill-color: transparent;
	letter-spacing: -0.04em;
	border: none;
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
</style>
