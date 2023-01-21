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
		let jobs = jsonData;
		const filteredJobs = ref(jobs);
		let clickedJobs = ref([]);

		function addToFilteredArray(filteredJob, clickedButton) {
			filteredJobs.value = filteredJob;
			if (clickedJobs.value.includes(clickedButton)) {
				return;
			}
			clickedJobs.value.push(clickedButton);
		}

		function removeFromFilteredArray(event) {
			const target = event.target.previousElementSibling.innerText;

			const searchResults = jobs.map((job) => [
				job.level,
				job.role,
				...job.languages,
				...job.tools,
			]);

			const union = searchResults
				.map((searchResult, i) => {
					if (
						clickedJobs.value.every((keyWord) => {
							return searchResult.includes(keyWord);
						})
					) {
						return i;
					}
				})
				.filter((item) => item !== undefined);

			const filteredData = jobs.filter((filteredJobs, i) => {
				return union.includes(i);
			});
			filteredJobs.value = filteredData;

			const newClickedJobs = clickedJobs.value.filter((element) => {
				return element !== target;
			});
			clickedJobs.value = newClickedJobs;
		}

		function clearFilteredJobs() {
			filteredJobs.value = [];
		}

		return {
			clickedJobs,
			jobs,
			filteredJobs,
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
		v-if="clickedJobs.length"
		:jobs="filteredJobs"
		:clickedButton="clickedJobs"
		:clearFilteredJobs="clearFilteredJobs"
		:removeFromFilteredArray="removeFromFilteredArray"
	/>
	<main class="main">
		<JobsListComponent
			:jobs="filteredJobs"
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
