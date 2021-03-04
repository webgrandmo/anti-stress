<template>
	<div class="breed-component-container">
		<div class="card">
			<div class="card-body">
				<div class="form-group">
					<select
						name="breed"
						id="breed"
						class="form-control"
						@change="fetchBreed($event)"
					>
						<option value="boxer">Select a breed</option>
						<option v-for="(value, name) in breeds" :key="name" :value="name">{{
							name
						}}</option>
					</select>
				</div>
				<carousel v-if="dog_breed_imgs.length">
					<img :src="img_url" class="img-placeholder" alt="Dog image" />
					<slide
						ref="imageSlider"
						v-for="(item, index) in dog_breed_imgs"
						:key="index"
					>
						<img :src="item" alt="Dog image" />
					</slide>
				</carousel>
			</div>
		</div>
	</div>
</template>

<style scoped>
	.breed-component-container {
		margin: 3rem 0;
	}

	.vs-carousel__wrapper {
		height: 300px;
	}
	.vs-carousel {
		height: 300px;
	}

	@media screen and (min-width: 768px) {
		.vs-carousel {
			height: 500px;
		}
		.vs-carousel__wrapper {
			height: 500px;
		}
	}

	#breed {
		width: 50%;
		margin: 0 auto;
	}

	@media screen and (min-width: 768px) {
		.vs-carousel__slide {
			height: 500px;
		}
	}

	.vs-carousel img {
		max-width: 100%;
		height: 100%;
	}
	.img-placeholder {
		margin: 0 auto;
	}
</style>

<script>
	import { Carousel, Slide } from 'vue-snap';
	import 'vue-snap/dist/vue-snap.css';
	export default {
		name: 'CarouselComponent',
		components: {
			Carousel,
			Slide,
		},
		data() {
			return {
				dog_breed_imgs: this.images,
			};
		},
		props: {
			images: Array,
			breeds: Object,
			img_url: String,
		},
		methods: {
			async fetchBreed(e) {
				const result = await fetch(
					`https://dog.ceo/api/breed/${e.target.value}/images`
				);
				const dogs = await result.json();
				this.dog_breed_imgs = dogs.message.slice(0, this.limit);

				setTimeout(() => {
					if (this.dog_breed_imgs.length) {
						this.handleChange();
					}
				}, 300);
			},
			handleChange() {
				const slideImg = document.querySelector('.vs-carousel__slide');
				slideImg.scrollIntoView({
					block: 'center',
					behavior: 'smooth',
				});
			},
		},
	};
</script>
