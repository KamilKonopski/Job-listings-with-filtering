<script>
export default {
	name: "JobsFilterComponent",
	props: ["jobs", "clickedButton"],
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
			<button class="filtered__text-btn">
				<img src="/images/icon-remove.svg" alt="remove button" />
			</button>
		</div>
		<button class="filtered__clear-btn">Clear</button>
	</div>
</template>

<style scoped></style>
