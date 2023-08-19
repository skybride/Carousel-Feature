<script setup lang="ts">
import { ref } from "vue";

const userInput = ref("");
const imageDescription = ref("");
</script>

<template>
	<div class="carousel-container">
		<div class="image-container">
			<img :src="userInput" :alt="imageDescription" />
		</div>
		<div class="input-container">
			<input type="text" placeholder="Paste URL" v-model="userInput" />
			<input
				type="text"
				placeholder="Image Description"
				v-model="imageDescription"
			/>
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
	margin: 4vh;
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

img {
	max-width: 200vh;
	max-height: 200px;
}
</style>
