<template>
	<div class="image-component-container">
		<button-component @get-image="getImage"></button-component>
		<div class="card text-center">
			<div class="card-body">
				<div class="doggy-img">
					<img :src="randomImage" alt="Dog Image" />
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped>
	.image-component-container {
		height: 300px;
		position: relative;
	}
	@media screen and (min-width: 768px) {
		.image-component-container {
			height: 500px;
		}
	}
	.doggy-img {
		width: 300px;
		height: 300px;
		margin: auto;
	}

	@media screen and (min-width: 768px) {
		.doggy-img {
			width: 480px;
			height: 500px;
		}
	}

	.doggy-img img {
		max-width: 100%;
		height: 100%;
	}
</style>

<script>
	import ButtonComponent from '../components/ui-controls/ButtonComponent';
	export default {
		name: 'ImageComponent',
		components: {
			ButtonComponent,
		},
		props: {
			randomImage: String,
		},

		methods: {
			getImage() {
				this.$emit('get-image');
			},
		},
	};
</script>
