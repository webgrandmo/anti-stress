<template>
	<header>
		<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
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
			<button
				class="navbar-toggler"
				type="button"
				data-toggle="collapse"
				data-target="#navbarNav"
				aria-controls="navbarNav"
				aria-expanded="false"
				aria-label="Toggle navigation"
			>
				<span class="navbar-toggler-icon"></span>
			</button>
			<div
				class="collapse navbar-collapse d-flex justify-content-end"
				id="navbarNav"
			>
				<ul class="navbar-nav">
					<li class="nav-item active">
						<a class="nav-link" href="#"
							>{{ random }} <span class="sr-only">(current)</span></a
						>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="#">{{ breed }}</a>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="#">{{ subBreed }}</a>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="#">{{ fullList }}</a>
					</li>
				</ul>
			</div>
		</nav>
	</header>
</template>

<style></style>

<script>
	export default {
		name: 'HeaderComponent',
		props: {
			random: String,
			breed: String,
			subBreed: String,
			fullList: String,
		},
	};
</script>
