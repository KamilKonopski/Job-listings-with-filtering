<script>
import SingleJobComponent from "./SingleJobComponent.vue";
export default {
	components: { SingleJobComponent },
	name: "JobsListComponent",
	props: ["jobs"],
};
</script>

<template>
	<div class="jobs">
		<SingleJobComponent :jobs="jobs" />
	</div>
</template>

<style scoped>
.jobs {
	margin-top: 5rem;
}
</style>
