<template>
	<div id="app">
		<!-- Array passed by reference  -->
		<!-- <PlayerListing v-if="currentState === 'selectPlayers'" :players="players"  v-on:next="next" /> -->
		<Task/>
	</div>
</template>

<script>
import PlayerListing from './components/PlayerListing';
import Task from './components/Task';

const tasks = require('./assets/tasks.json');

export default {
	name: 'app',
	components: {
		PlayerListing,
		Task,
	},
	data() {
		return {
			currentState: 'selectPlayers',
			players: [],
			tasks: tasks || 'hä',
		};
	},
	methods: {
		next() {
			if (this.currentState === 'selectPlayers') {
				this.currentState = 'listTasks';
			}
		},
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
	font-size: 20px;
	font-weight: 600;
	margin: 0;
}
#app {
	font-family: 'Poppins', sans-serif;
	height: 100vh;
}
button {
	background: $black;
	border: none;
	color: #fff;
	cursor: pointer;
	text-decoration: underline;
	font-size: 1.1rem;
	font-family: "Poppins", sans-serif;
	margin: 0;
	padding: .6rem;
	width: 100%;
	-webkit-appearance: none;
	&:hover {
		background: #000;
	}
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
	&.cancel {
		background: #e43333;
		&:hover {
			background: #d62828;
		}
	}
}
</style>
