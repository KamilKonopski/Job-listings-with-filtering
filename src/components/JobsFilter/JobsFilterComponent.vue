<script>
export default {
	name: "JobsFilterComponent",
	props: [
		"jobs",
		"clickedButton",
		"clearFilteredJobs",
		"removeFromFilteredArray",
	],
};
</script>

<template>
	<div class="filtered">
		<div
			class="filtered__items"
			v-for="(text, index) in clickedButton"
			:key="index"
		>
			<span class="filtered__item">{{ text }}</span>
			<img
				@click="removeFromFilteredArray"
				src="/images/icon-remove.svg"
				alt="remove button"
			/>
		</div>
		<button @click="clearFilteredJobs" class="filtered__clear-btn">
			Clear
		</button>
	</div>
</template>

<style scoped></style>
