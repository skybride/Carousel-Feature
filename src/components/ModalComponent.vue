<script setup lang="ts">
defineProps({
	openModal: Boolean,
});

const emit = defineEmits(["deleteImage", "closeModal"]);

const deleteImage = () => {
	emit("deleteImage");
};

const closeModal = () => {
	emit("closeModal");
};
</script>

<template>
	<div class="modal" v-if="openModal">
		<div class="modal-message">Are you sure you want to delete the image?</div>
		<button class="modal-button" @click="deleteImage">
			<i class="fa fa-trash-o"></i>
		</button>
		<button class="modal-button" @click="closeModal">
			<i class="fa fa-close"></i>
		</button>
	</div>
</template>

<style scoped>
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
