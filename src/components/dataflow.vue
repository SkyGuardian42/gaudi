<template>
	<section>
		<p>{{ internalValue }}</p>
		<button @click="modData">return modified data</button>
	</section>
</template>

<script>
export default {
	props: ['value'],
	data: function componentdata() {
		return {
			internalValue: '',
		};
	},
	watch: {
		internalValue: function passInternalValue() {
			// When the internal value changes, we $emit an event. Because this event is
			// named 'input', v-model will automatically update the parent value
			this.$emit('input', this.internalValue);
		},
	},
	created: function copyValue() {
		this.internalValue = this.value;
	},
	methods: {
		modData: function modData() {
			this.internalValue += 'modified by child';
		},
	},
};
</script>

<style lang="scss">

</style>
