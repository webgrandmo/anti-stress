<template>
	<div id="app">
		<header-component></header-component>
		<div class="container">
			<div class="row">
				<div class="col-12">
					<h1 class="mt-5 mb-5 text-center">Check-out Doggy</h1>
					<br />

					<image-component
						@get-image="fetchImg"
						:randomImage="random_img_url"
					></image-component>
					<br />
					<br />
					<h2 class="mt-5 mb-5 text-center">Or explore by breed</h2>
					<carousel-component
						:breeds="breeds"
						:images="images"
						:img_url="random_img_url"
					></carousel-component>
				</div>
			</div>
		</div>
	</div>
</template>

<style lang="css">
	.vs-carousel .vs-carousel__arrows {
		text-indent: -9999px;
		border: none;
		display: block;
		width: 40px;
		height: 40px;
	}
	.vs-carousel__arrows--right {
		background: url('./assets/next.svg') no-repeat center;
	}
	.vs-carousel__arrows--left {
		background: url('./assets/back.svg') no-repeat center;
	}
</style>

<script>
	import CarouselComponent from './components/CarouselComponent.vue';
	import ImageComponent from './components/ImageComponent.vue';

	import HeaderComponent from './components/layout/HeaderComponent.vue';

	export default {
		name: 'App',
		components: {
			HeaderComponent,
			CarouselComponent,
			ImageComponent,
		},
		data() {
			return {
				items: [],
				images: [],
				breeds: {},
				random_img_url: '',
				limit: 100,
			};
		},
		methods: {
			async fetchImg() {
				const result = await fetch(`https://dog.ceo/api/breeds/image/random`);
				const data = await result.json();
				this.random_img_url = data.message;
			},
		},

		async beforeMount() {
			const f = await fetch(`https://dog.ceo/api/breeds/image/random`);
			const data = await f.json();
			const r = await fetch(`https://dog.ceo/api/breeds/list/all`);
			const breeds = await r.json();
			this.breeds = breeds.message;
			this.random_img_url = data.message;
		},
	};
</script>
