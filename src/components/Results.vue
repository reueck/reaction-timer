<template>
	<div class="results">
		<h1>Misja zaliczona</h1>
		<p>Twój ostatni czas reakcji wynosił: {{ time }} ms</p>
        <p class="rank">Ranga: {{ rank }}</p>
	</div>
</template>

<script>
export default {
	name: 'Results',
	props: {
		time: {
			type: Number,
			required: true,
		},
	},
    data(){
        return {
            rank: null
        }
    },
    mounted() {
        // this.calculateAverage()
        if(this.time < 250){
            this.rank = 'Ale z Ciebie Chad'
        } else if (
            this.time > 250 && this.time < 500
        ) {
            this.rank = 'Normik'
        } else if (
            this.time > 500 && this.time < 1000
        ) {
            this.rank = 'Lager'
        } else if (
            this.time > 1000
        ) {
            this.rank = 'Twoja babcia robi to szybciej'
        }
        
    },
    }
    
</script>

<style lang="scss">
.results{
    text-align: center;
    h1, p, .rank{
        font-size: 5rem;
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
	text-align: center;
	font-family: Bangers, cursive;
	cursor: default;
    }
    p{
        font-size: 1.8rem;
    }
    .rank{
        font-size: 2rem;
        font-weight: bold;
        
    }
}
</style>
