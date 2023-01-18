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
		let data = jsonData;
		const filteredArray = ref(data);
		let clicked = ref([]);

		function addToFilteredArray(filteredJob, clickedButton) {
			filteredArray.value = filteredJob;
			if (clicked.value.includes(clickedButton)) {
				return;
			}
			clicked.value.push(clickedButton);
		}

		function removeFromFilteredArray(event) {
			const target = event.target.previousElementSibling.innerText;

			const searchResults = data.map((job) => [
				job.level,
				job.role,
				...job.languages,
				...job.tools,
			]);

			const union = searchResults
				.map((searchResult, i) => {
					if (
						clicked.value.every((keyWord) => {
							return searchResult.includes(keyWord);
						})
					) {
						return i;
					}
				})
				.filter((item) => item !== undefined);

			const filteredData = data.filter((filteredArray, i) => {
				return union.includes(i);
			});
			filteredArray.value = filteredData;

			const newClicked = clicked.value.filter((element) => {
				return element !== target;
			});
			clicked.value = newClicked;
		}

		function clearFilteredJobs() {
			filteredArray.value = [];
		}

		return {
			clicked,
			data,
			filteredArray,
			addToFilteredArray,
			clearFilteredJobs,
			removeFromFilteredArray,
		};
	},
};
</script>
>

<template>
	<header class="header"></header>
	<JobsFilterComponent
		v-if="clicked.length"
		:jobs="filteredArray"
		:clickedButton="clicked"
		:clearFilteredJobs="clearFilteredJobs"
		:removeFromFilteredArray="removeFromFilteredArray"
	/>
	<main class="main">
		<JobsListComponent
			:jobs="filteredArray"
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
