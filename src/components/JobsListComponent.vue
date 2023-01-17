<script>
export default {
	name: "JobsListComponent",
	props: ["jobs"],
};
</script>

<template>
	<div v-for="job in jobs" :key="job.id">
		<span>{{ job.company }}</span>
		<img :src="job.logo" :alt="job.company" />
		<span v-if="job.new">new!</span>
		<span v-if="job.featured">featured</span>
		<span>{{ job.position }}</span>
		<ul>
			<li>{{ job.postedAt }}</li>
			<li>{{ job.contract }}</li>
			<li>{{ job.location }}</li>
		</ul>
		<div>
			<button v-for="(language, index) in job.languages" :key="index">
				{{ language }}
			</button>
			<button v-for="(tool, index) in job.tools" :key="index">
				{{ tool }}
			</button>
		</div>
	</div>
</template>

<style scoped></style>
