<template>
	<div class="card text-center">
		<div class="card-body">
			<div class="doggy-img">
				<img :src="randomImage" alt="Dog Image" />
			</div>
		</div>
	</div>
</template>

<style scoped></style>

<script>
	export default {
		name: 'ImageComponent',
		props: {
			randomImage: String,
		},
	};
</script>
