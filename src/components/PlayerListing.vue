<template>
	<section>
		<div class="top">
			<!-- Input components -->
			<input type="text" v-model="playerInput" @keyup.enter="addPlayer" placeholder="Namen hier reinschreiben">
			<button class="secondary" @click="addPlayer">+ SPIELER HINZUFÜGEN +</button>

			<!-- List players -->
			<div v-for="(player, index) in playersInternal" v-bind:key="player" class="listing">
				<p> {{ player }} </p>
				<span class="delete" @click="removePlayer(index)">x</span>
			</div>
		</div>

		<!-- Next screen -->
		<button class="primary" @click="next">ANFANGEN</button>
	</section>
</template>

<script>
export default {
	props: ['players'],
	data() {
		return {
			playerInput: '',
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
			if (this.players.length < 2) {
				return;
			}
			this.$emit('next');
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
