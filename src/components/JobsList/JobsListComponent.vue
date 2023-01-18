<script>
import { ref } from "vue";
import SingleJobComponent from "./SingleJobComponent.vue";
export default {
	components: { SingleJobComponent },
	name: "JobsListComponent",
	props: ["jobs"],
	setup() {
		let filteredArray = ref([]);
		function addToFilteredArray(filteredJob) {
			filteredArray.value = filteredJob;
			console.log(filteredArray);
		}

		return { filteredArray, addToFilteredArray };
	},
};
</script>

<template>
	<div v-if="filteredArray.length" class="jobs">
		<SingleJobComponent
			:jobs="filteredArray"
			:addToFilteredArray="addToFilteredArray"
		/>
	</div>
	<div v-else class="jobs">
		<SingleJobComponent :jobs="jobs" :addToFilteredArray="addToFilteredArray" />
	</div>
</template>

<style scoped>
.jobs {
	margin-top: 5rem;
}
</style>
