<script>
import JobsListComponent from "./components/JobsList/JobsListComponent.vue";
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
	<main class="main"><JobsListComponent :jobs="data" /></main>
</template>

<style scoped>
.header {
	background: url("./images/bg-header-mobile.svg") no-repeat;
	background-color: hsl(180, 29%, 50%);
	height: 23vh;
	width: 100%;
}

.main {
	margin: 0 auto;
	width: 90%;
}

@media screen and (min-width: 1024px) {
	.header {
		background: url("./images/bg-header-desktop.svg") no-repeat top center;
		background-color: hsl(180, 29%, 50%);
		height: 15vh;
	}

	.main {
		width: 1024px;
	}
}
</style>
