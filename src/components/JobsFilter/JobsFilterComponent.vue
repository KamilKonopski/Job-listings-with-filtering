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
		<div class="filtered__items">
			<span
				v-for="(text, index) in clickedButton"
				:key="index"
				class="filtered__text"
				>{{ text }}</span
			>
		</div>
		<button @click="clearFilteredJobs" class="filtered__clear-btn">
			Clear
		</button>
	</div>
</template>

<style scoped>
.filtered {
	background-color: var(--light-grayish-cyan-ft);
	border-radius: 5px;
	display: flex;
	justify-content: space-between;
	min-height: 1rem;
	margin: 0 auto;
	transform: translateY(-60%);
	width: 90%;
}

.filtered__items {
	display: flex;
	flex-basis: 60%;
	flex-wrap: wrap;
}

.filtered__text {
	font-size: 1.5rem;
}

.filtered__clear-btn {
	border: none;
	color: var(--very-dark-grayish-cyan);
	flex-basis: 40%;
	font-size: 1.5rem;
	font-weight: 700;
}
</style>
