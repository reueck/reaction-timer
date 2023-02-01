<template>
	<div class="blob" v-if="showBlob">click me xd</div>
</template>

<script>
export default {
    props: ['delay'],
data() {
    return {
        showBlob: false
    }
},
mounted(){
    setTimeout(() => {
        this.showBlob = true
        console.log(this.delay);
    }, this.delay)},
updated() {
    console.log('updated');
},
unmounted() {
    this.showBlob = false
},
// to się odpali dopiero jak to będzie zmountowane do dom
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
