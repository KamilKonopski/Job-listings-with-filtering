<script>
export default {
	name: "JobsFilterComponent",
	props: ["jobs", "clickedButton"],
};
</script>

<template>
	<div v-for="(text, index) in clickedButton" :key="index">
		<span>{{ text }}</span>
	</div>
	<button>Clear</button>
</template>

<style scoped></style>
