<template>
	<section>
		<div class="placeholder"></div>
		<p>{{text}}</p>
		<div class="stack">
			<button class="cancel" @click="solved">Abgebrochen</button>
			<button class="primary" @click="cancel">Absolviert</button>
		</div>
	</section>
</template>

<script>
export default {
	methods: {
		solve() {
			this.$emit('solved');
		},
		cancel() {
			this.$emit('canceled');
		},
	},
};
</script>

<style lang="scss" scoped>
section {
	height: 100vh;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-between;
}
.stack {
	display: flex;
	flex-direction: column;
	width: 100%;
}
p {
	word-break: break-all;
}
</style>
