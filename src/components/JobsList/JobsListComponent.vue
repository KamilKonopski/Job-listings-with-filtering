<script>
import SingleJobComponent from "./SingleJobComponent.vue";
export default {
	components: { SingleJobComponent },
	name: "JobsListComponent",
	props: ["jobs", "addToFilteredArray", "filteredArray"],
	setup(props) {
		function addToFilteredJobs(filteredJob, clickedButton) {
			props.addToFilteredArray(filteredJob, clickedButton);
		}

		return { addToFilteredJobs };
	},
};
</script>

<template>
	<div class="jobs">
		<SingleJobComponent :jobs="jobs" :addToFilteredArray="addToFilteredJobs" />
	</div>
</template>

<style scoped>
.jobs {
	margin-top: 5rem;
}
</style>
