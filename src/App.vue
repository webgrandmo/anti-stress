<template>
	<div id="app">
		<header-component
			fullList="Full List"
			random="Random Doggy"
			subBreed="Sub Breed"
			breed="Breed"
		></header-component>
		<div class="container">
			<div class="row">
				<div class="col-12">
					<br />
					<div class="form-group">
						<button class="btn btn-primary" @click="fetchImg">
							Get Random Doggy
						</button>
					</div>

					<div class="card text-center">
						<div class="card-body">
							<div class="doggy-img">
								<img :src="random_img_url" alt="asdasd" />
							</div>
						</div>
					</div>
					<br />
					<carousel-component
						:breeds="breeds"
						:images="images"
					></carousel-component>
				</div>
			</div>
		</div>
	</div>
</template>

<style lang="css">
	.doggy-img {
		width: 300px;
		height: auto;
		margin: auto;
	}

	.doggy-img img {
		max-width: 100%;
	}

	@media screen and (min-width: 768px) {
		.doggy-img {
			width: 600px;
		}
	}
	.vs-carousel .vs-carousel__arrows {
		text-indent: -9999px;
		border: none;
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

	import HeaderComponent from './components/layout/HeaderComponent.vue';
	export default {
		name: 'App',
		components: {
			HeaderComponent,
			CarouselComponent,
		},
		data() {
			return {
				items: [],
				images: [],
				breeds: {},
				random_img_url: '',
				breed_img_url: '',
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
