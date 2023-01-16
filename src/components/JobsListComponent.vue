<script>
export default {
	name: "JobsListComponent",
	props: ["jobs"],
};
</script>

<template>
	<div v-for="job in jobs" :key="job.id">
		<div>{{ job.role }}</div>
	</div>
</template>

<style scoped></style>
