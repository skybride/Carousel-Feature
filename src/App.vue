<script setup lang="ts"></script>

<template>
	<div class="carousel-container">
		<div class="image-container">Display Image</div>
		<div class="input-container">
			<input type="text" placeholder="Paste URL" />
			<button>Upload</button>
		</div>
	</div>
</template>

<style scoped>
.carousel-container {
	border: 1px solid darkgrey;
	border-radius: 15px;
	padding: 10px;
}

.image-container {
	margin: 30vh;
}

.input-container {
	margin: 10vh;
}

input {
	height: 3vh;
	width: 30vh;
}

button {
	height: 3.6vh;
}
</style>
