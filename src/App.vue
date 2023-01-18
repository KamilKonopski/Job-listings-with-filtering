<script>
import { ref } from "vue";
import JobsListComponent from "./components/JobsList/JobsListComponent.vue";
import JobsFilterComponent from "./components/JobsFilter/JobsFilterComponent.vue";
import jsonData from "./data/data.json";
export default {
	components: {
		JobsListComponent,
		JobsFilterComponent,
	},
	setup() {
		const filteredArray = ref([]);
		let clicked = ref([]);
		const data = jsonData;

		function addToFilteredArray(filteredJob, clickedButton) {
			filteredArray.value = filteredJob;
			if (clicked.value.includes(clickedButton)) {
				return;
			}
			clicked.value.push(clickedButton);
		}

		return { clicked, filteredArray, addToFilteredArray, data };
	},
};
</script>
>

<template>
	<header class="header"></header>
	<JobsFilterComponent
		v-if="filteredArray.length"
		:jobs="filteredArray"
		:clickedButton="clicked"
	/>
	<main class="main">
		<JobsListComponent
			:jobs="data"
			:filteredArray="filteredArray"
			:addToFilteredArray="addToFilteredArray"
		/>
	</main>
</template>

<style scoped>
.header {
	background: url("./images/bg-header-mobile.svg") no-repeat;
	background-color: hsl(180, 29%, 50%);
	height: 23vh;
	width: 100%;
}

.main {
	margin: 0 auto;
	width: 90%;
}

@media screen and (min-width: 1024px) {
	.header {
		background: url("./images/bg-header-desktop.svg") no-repeat top center;
		background-color: hsl(180, 29%, 50%);
		height: 15vh;
	}

	.main {
		width: 1024px;
	}
}
</style>
