<template>
	<div id="app">
		<PlayerListing :players="players" />

	</div>
</template>

<script>
import PlayerListing from './components/PlayerListing';

export default {
	name: 'app',
	components: {
		PlayerListing,
	},
	data() {
		return {
			playerInput: 'everything working?',
			players: ['Malte'],
		};
	},
	methods: {
	},
};
</script>

<style lang="scss">
$border: .4rem solid #121212;
$black: #121212;

* {
	box-sizing: border-box;
	&:focus {
    outline: none;
	}
}
body, html {
	font-family: "Poppins", sans-serif;
	font-size: 18px;
	font-weight: 600;
	margin: 0;
}
#app {
	font-family: 'Poppins', sans-serif;
	height: 100vh;
}

</style>
