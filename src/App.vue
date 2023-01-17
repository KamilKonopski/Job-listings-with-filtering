<script>
import JobsListComponent from "./components/JobsListComponent.vue";
import jsonData from "./data/data.json";
export default {
	components: {
		JobsListComponent,
	},
	setup() {
		const data = jsonData;

		return { data };
	},
};
</script>
>

<template>
	<header class="header"></header>
	<main><JobsListComponent :jobs="data" /></main>
</template>

<style scoped>
.header {
	background: url("./images/bg-header-mobile.svg") no-repeat;
	background-color: hsl(180, 29%, 50%);
	height: 23vh;
	width: 100%;
}

@media screen and (min-width: 1024px) {
	.header {
		background: url("./images/bg-header-desktop.svg") no-repeat top center;
		background-color: hsl(180, 29%, 50%);
		height: 15vh;
	}
}
</style>
