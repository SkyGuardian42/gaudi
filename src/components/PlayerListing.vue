<template>
	<section>
		<div class="top">
			<!-- Input components -->
			<input type="text" v-model="playerInput" @keyup.enter="addPlayer">
			<button class="secondary" @click="addPlayer">+ SPIELER HINZUFÜGEN +</button>

			<!-- List players -->
			<div v-for="(player, index) in playersInternal" v-bind:key="player" class="listing">
				<p> {{ player }} </p>
				<span class="delete" @click="removePlayer(index)">x</span>
			</div>
		</div>

		<!-- Next screen -->
		<button class="primary">ANFANGEN</button>
	</section>
</template>

<script>
export default {
	props: ['players'],
	data() {
		return {
			playerInput: 'everything working?',
			playersInternal: [],
		};
	},
	created: function copyFromProp() {
		// We initially sync the internalValue with the value passed in by the parent
		this.playersInternal = this.players;
	},
	// watch: {
	// 	playersInternal: function passPlayers() {
	// 		// When the internal value changes, we $emit an event. Because this event is
	// 		// named 'input', v-model will automatically update the parent value
	// 		this.$emit('input', this.playersInternal);
	// 	},
	// },
	methods: {
		addPlayer: function addPlayer() {
			if (this.playerInput === '') {
				return;
			}

			this.playersInternal.push(this.playerInput);
			this.playerInput = '';
		},
		removePlayer: function removePlayer(index) {
			this.playersInternal.splice(index, 1);
		},
		next: function next() {
		},
	},
};
</script>

<style lang="scss" scoped>
	$border: .4rem solid #121212;
	$black: #121212;
section {
	height: 100vh;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-between;
}	
.top {
	width: 100%;
}
input[type="text"] {
	background: #fff;
	border: .4rem solid $black;
	font-size: 1rem;
	font-family: 'Poppins', sans-serif;
	padding: .6rem; 
	width: 100%;
}
button {
	background: $black;
	border: none;
	color: #fff;
	cursor: pointer;
	text-decoration: underline;
	font-size: 1.2rem;
	font-family: "Poppins", sans-serif;
	margin: 0;
	padding: .6rem;
	width: 100%;
	-webkit-appearance: none;
	&.primary {
		background: #0ec325;
		&:hover {
			background: #0da220;
		}
	}
	&.secondary {
		background: #3e17d4;
		&:hover {
			background: #3b1abb;
		}
	}
}
.listing {
	$red: #ea2828;
	display: flex;
	align-items: stretch;
	justify-content: space-between;
	p {
		border: $border;
		flex-grow: 1;
		font-size: 1.1rem;
		margin: 0;
		padding: .3rem;
	}
	.delete {
		background: #fff;
		border: .4rem solid $red;
		color: $red;
		margin: 0;
		font-size: 1.6rem;
		padding: 0 .6rem;
		cursor: pointer;
	}
}
</style>
