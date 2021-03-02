<template>
	<div class="card">
		<div class="card-body">
			<div class="form-group">
				<select
					name="breed"
					id="breed"
					class="form-control"
					@change="fetchBreed($event)"
				>
					<option v-for="(value, name) in breeds" :key="name" :value="name">{{
						name
					}}</option>
					<option value="boxer">Boxer</option>
				</select>
			</div>
			<carousel>
				<slide v-for="(item, index) in images" :key="index">
					<img :src="item" alt="Dog image" />
				</slide>
			</carousel>
		</div>
	</div>
</template>

<style lang="css" scoped>
	.vs-carousel {
		height: 500px;
	}

	.vs-carousel img {
		max-width: 100%;
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
				dog_breed: '',
			};
		},
		props: {
			images: Array,
			breeds: Array,
		},
		// async beforMount(e) {
		// 	const result = await fetch(
		// 		`https://dog.ceo/api/breed/${e.target.value}/images`
		// 	);
		// 	const dogs = await result.json();
		// 	this.images = dogs.message.slice(0, this.limit);
		// 	console.log(dogs);
		// },
		methods: {
			async fetchBreed(e) {
				const result = await fetch(
					`https://dog.ceo/api/breed/${e.target.value}/images`
				);
				const dogs = await result.json();
				this.images = dogs.message.slice(0, this.limit);
				console.log(dogs);
			},
		},
	};
</script>
