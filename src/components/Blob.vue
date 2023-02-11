<template>
	<div class="blob" v-if="showBlob">
		<img src="@/assets/img/alien.png" 
		@click="stopTimer" alt="blob" />
	</div>
	
</template>
<script>
export default {
	props: ['delay'],
	data() {
		return {
			showBlob: false,
			timer: null,
			reactionTime: 0,
		}
	},
	mounted() {
		setTimeout(() => {
			this.showBlob = true
			this.startTimer()
		}, this.delay)
	},
	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10
			}, 10)
		},
		stopTimer() {
			clearInterval(this.timer)
			this.$emit('end', this.reactionTime)
            this.$dmit
		},
	},
}
</script>

<style lang="scss">
.blob {
    cursor: pointer;
	width: 500px;
}
.blob img {
	width: 500px;
}
</style>
