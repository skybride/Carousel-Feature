<script setup lang="ts">
import { ref } from "vue";

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
		<div class="image-container" v-if="imageArray">
			<img
				v-for="(image, key) in imageArray"
				:src="image"
				@click="showImageModal(key, image)"
			/>
			<div class="modal" v-if="openModal">
				<div class="modal-message">
					Are you sure you want to delete the image?
				</div>
				<button class="modal-button" @click="deleteImage">
					<i class="fa fa-trash-o"></i>
				</button>
				<button class="modal-button" @click="closeModal">
					<i class="fa fa-close"></i>
				</button>
			</div>
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

i {
	font-size: xx-large;
}

.modal {
	background-color: rgba(0, 0, 0, 0.4);
	display: flex;
	flex-direction: column;
	justify-content: center;
	position: fixed;
	overflow: auto;
	top: 0;
	left: 0;
	height: 100%;
	width: 100%;
	z-index: 1;
}

.modal-message {
	background-color: snow;
	font-size: xx-large;
	padding: 4%;
}

.modal-button {
	cursor: pointer;
	height: 6%;
	width: 100%;
}
</style>
