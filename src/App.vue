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
					<div class="card">
						<div class="card-body">
							<carousel>
								<slide v-for="item in images.slice(0, 100)" :key="item.message">
									<img :src="item" alt="Dog image" />
								</slide>
							</carousel>
						</div>
					</div>
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

	.vs-carousel__arrows {
		background: rgba(0, 0, 0, 0.3);
		border: none;
		border-radius: 50%;
		color: white;
		text-indent: -9999px;
	}

	.vs-carousel__arrows--right {
		background: url('./assets/next.svg') no-repeat center;
	}
	.vs-carousel__arrows--left {
		background: url('./assets/back.svg') no-repeat center;
	}
</style>

<script>
	import { Carousel, Slide } from 'vue-snap';
	import 'vue-snap/dist/vue-snap.css';
	import HeaderComponent from './components/layout/HeaderComponent.vue';
	export default {
		name: 'App',
		components: {
			HeaderComponent,
			Carousel,
			Slide,
		},
		data() {
			return {
				items: [],
				images: [],
				random_img_url: '',
				breed_img_url: '',
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
			const result = await fetch(`https://dog.ceo/api/breed/hound/images`);
			const dogs = await result.json();
			this.random_img_url = data.message;
			this.images = dogs.message;
			console.log(dogs);
			console.log(this.items);
		},
	};
</script>
