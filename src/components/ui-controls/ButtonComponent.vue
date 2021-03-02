<template>
	<div class="form-group">
		<button class="btn btn-primary" @click="getImage">
			Get Random Doggy
		</button>
	</div>
</template>

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
