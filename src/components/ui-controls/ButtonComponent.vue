<template>
	<div class="btn-component">
		<button class="arrow" @click="getImage"></button>
	</div>
</template>

<style scoped>
	.btn-component {
		position: absolute;
		top: 0;
		bottom: 0;
		right: 1rem;
		margin: auto;
		width: 44px;
		height: 44px;
		padding: 0;
		z-index: 1;
		cursor: pointer;
	}

	.btn-component .arrow {
		background: url('../../assets/next.svg') no-repeat center;
		border: none;
		width: 44px;
		height: 44px;
	}
</style>

<script>
	export default {
		name: 'ButtonComponent',
		methods: {
			getImage() {
				this.$emit('get-image');
			},
		},
	};
</script>
