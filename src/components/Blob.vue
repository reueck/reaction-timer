<template>
	<div class="blob" v-if="showBlob" @click="stopTimer">click me xd</div>
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
mounted(){
    setTimeout(() => {
        this.showBlob = true
        this.startTimer()
    }, this.delay)},
methods:{
    startTimer(){
        this.timer= setInterval(() => {
            this.reactionTime+=10
        }, 10)
    },
    stopTimer(){
        clearInterval(this.timer)
        console.log(this.reactionTime);
        this.$emit('reaction', this.reactionTime)
    }
}

}
</script>

<style lang="scss">
.blob {
	width: 200px;
	height: 50px;
	background-color: red;
	border-radius: 50%;
	text-align: center;
	padding: 5px 0;
	margin: 40px auto;
}
</style>
