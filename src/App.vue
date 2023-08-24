<script setup lang="ts">
import { ref } from "vue";

const userInput = ref("");
const imageArray = ref([""]);

function addImage() {
	imageArray.value.push(userInput.value);
	userInput.value = "";
}
</script>

<template>
	<div class="carousel-container">
		<div class="image-container" v-if="imageArray">
			<img v-for="image in imageArray" :src="image" />
		</div>
		<div class="input-container">
			<input type="text" placeholder="Paste URL" v-model="userInput" />
			<button @click="addImage">Upload</button>
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
	display: flex;
	max-width: 100%;
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
	max-height: 200vh;
}
</style>
