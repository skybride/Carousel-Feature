<script lang="ts" setup>
import { ref } from "vue";

// const fruitsList = ref([
// 	{ number: 1, name: "peaches" },
// 	{ number: 2, name: "mangoes" },
// 	{ number: 3, name: "kiwis" },
// ]);

const userInput = ref("");
const fruitsList = ref(["peaches", "mangoes", "kiwis"]);

const show = ref(true);

function addToList() {
	if (userInput.value !== "") fruitsList.value.push(userInput.value);
	userInput.value = "";
}

function deleteItem(index: number) {
	console.log(index);
	fruitsList.value.splice(index, 1);
}
</script>

<template>
	<input type="text" placeholder="what fruit?" v-model="userInput" />
	<button @click="addToList">Add</button>

	<ul v-if="show && fruitsList.length">
		<li v-for="(fruit, index) of fruitsList" @click="deleteItem(index)">
			{{ fruit }}
		</li>
	</ul>
</template>

<style scoped></style>
