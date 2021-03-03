<template>
	<header>
		<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
			<div class="container">
				<a class="navbar-brand" href="#">
					<img
						src="../../assets/logo.svg"
						width="60"
						height="60"
						class="d-inline-block align-center"
						alt=""
					/>
					Doggy Anti-stress
				</a>
			</div>
		</nav>
	</header>
</template>

<style>
	@media screen and (max-width: 768px) {
		.navbar-brand {
			margin: 0 auto;
		}
	}
</style>

<script>
	export default {
		name: 'HeaderComponent',
	};
</script>
