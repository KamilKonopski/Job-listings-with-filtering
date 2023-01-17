<script>
export default {
	name: "SingleJobComponent",
	props: ["jobs"],
};
</script>

<template>
	<div
		class="job"
		:class="{ 'job--featured': job.featured }"
		v-for="job in jobs"
		:key="job.id"
	>
		<div class="job__icon">
			<img class="job__image" :src="job.logo" :alt="job.company" />
		</div>
		<div class="job__info">
			<span class="job__company">{{ job.company }}</span>
			<span class="job__new" v-if="job.new">new!</span>
			<span class="job__featured" v-if="job.featured">featured</span>
			<span class="job__position">{{ job.position }}</span>
			<span class="job__posted">{{ job.postedAt }}</span>
			<span class="job__contract">{{ job.contract }}</span>
			<span class="job__location">{{ job.location }}</span>
		</div>
		<div class="job__buttons">
			<button class="job__skill">
				{{ job.role }}
			</button>
			<button class="job__skill">
				{{ job.level }}
			</button>
			<button
				class="job__skill"
				v-for="(language, index) in job.languages"
				:key="index"
			>
				{{ language }}
			</button>
			<button
				class="job__skill"
				v-for="(tool, index) in job.tools"
				:key="index"
			>
				{{ tool }}
			</button>
		</div>
	</div>
</template>

<style scoped>
.job {
	background-color: #fff;

	border-radius: 5px;
	margin-bottom: 4rem;
	padding: 3.5rem 1.8rem 2rem;
	position: relative;
}

.job--featured {
	border-left: 5px solid var(--desaturated-dark-cyan);
}

.job__icon {
	height: 5rem;
	left: 5%;
	position: absolute;
	top: -25%;
	width: 5rem;
}

.job__image {
	width: 100%;
}

.job__info {
	align-items: center;
	display: flex;
	flex-wrap: wrap;
}

.job__company {
	color: var(--desaturated-dark-cyan);
	font-weight: 700;
	margin-right: 2rem;
}

.job__new {
	background-color: var(--desaturated-dark-cyan);
	border-radius: 50px;
	color: #fff;
	padding: 5px 8px;
	margin-right: 1rem;
	text-transform: uppercase;
}

.job__featured {
	background-color: var(--very-dark-grayish-cyan);
	border-radius: 50px;
	color: #fff;
	padding: 5px 8px;
	text-transform: uppercase;
}

.job__position {
	color: #000;
	flex-basis: 100%;
	font-weight: 700;
	margin: 1.5rem 0;
}

.job__buttons {
	display: flex;
	flex-wrap: wrap;
}
</style>
