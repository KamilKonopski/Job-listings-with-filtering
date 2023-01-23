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
				class="filtered__item"
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
	background-color: #fff;
	border-radius: 5px;
	display: flex;
	justify-content: space-between;
	min-height: 1rem;
	margin: 0 auto;
	transform: translateY(-60%);
	padding: 2rem;
	width: 90%;
}

.filtered__items {
	display: flex;
	flex-basis: 60%;
	flex-wrap: wrap;
	gap: 10px;
}

.filtered__item {
	background-color: var(--light-grayish-cyan-ft);
	color: var(--desaturated-dark-cyan);
	font-size: 1.8rem;
	font-weight: 700;
	padding: 1rem;
}

.filtered__clear-btn {
	background-color: transparent;
	border: none;
	color: var(--very-dark-grayish-cyan);
	cursor: pointer;
	font-size: 1.6rem;
	font-weight: 700;
}
</style>
