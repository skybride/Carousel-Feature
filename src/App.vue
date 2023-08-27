<script setup lang="ts">
import { ref } from "vue";
import ModalComponent from "./components/ModalComponent.vue";

const userInput = ref("");
const imageArray = ref([""]);
const openModal = ref(false);

let currentImageNumber: number = 0;
let currentImage: string = "";

function addImage() {
	imageArray.value.push(userInput.value);
	imageArray.value = imageArray.value.filter((str) => str !== "");
	userInput.value = "";
}

function showImageModal(key: number, image: string) {
	openModal.value = true;
	currentImageNumber = key;
	currentImage = image;
}

function deleteImage() {
	imageArray.value.splice(currentImageNumber, 1);
	openModal.value = false;
}

function closeModal() {
	openModal.value = false;
}
</script>

<template>
	<div class="carousel-container">
		<ModalComponent
			:openModal="openModal"
			@deleteImage="deleteImage"
			@closeModal="closeModal"
		/>
		<div class="image-container" v-if="imageArray">
			<img
				v-for="(image, key) in imageArray"
				:src="image"
				@click="showImageModal(key, image)"
			/>
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
	width: 100%;
}

.image-container {
	display: flex;
	max-width: 100%;
	padding: 2rem;
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
	margin: 1rem;
	max-width: 200vh;
	max-height: 200vh;
}

img:hover {
	cursor: pointer;
}
</style>
