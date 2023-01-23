<script>
export default {
	name: "SingleJobComponent",
	props: ["jobs", "addToFilteredArray"],
	setup(props) {
		function getJobRole(event) {
			const target = event.target.innerText;
			const filteredJob = props.jobs.filter((job) => job.role === target);
			props.addToFilteredArray(filteredJob, target);
		}

		function getJobLevel(event) {
			const target = event.target.innerText;
			const filteredJob = props.jobs.filter((job) => job.level === target);
			props.addToFilteredArray(filteredJob, target);
		}

		function getJobLanguage(event) {
			const target = event.target.innerText;
			const filteredJob = props.jobs.filter((job) =>
				job.languages.some((language) => language === target)
			);
			props.addToFilteredArray(filteredJob, target);
		}

		function getJobTools(event) {
			const target = event.target.innerText;
			const filteredJob = props.jobs.filter((job) =>
				job.tools.some((tool) => tool === target)
			);
			props.addToFilteredArray(filteredJob, target);
		}

		return { getJobRole, getJobLevel, getJobLanguage, getJobTools };
	},
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
			<span class="job__info-add">{{ job.postedAt }}</span>
			<span class="job__info-add">{{ job.contract }}</span>
			<span class="job__info-add">{{ job.location }}</span>
		</div>
		<div class="job__buttons">
			<button @click="getJobRole" class="job__skill">
				{{ job.role }}
			</button>
			<button @click="getJobLevel" class="job__skill">
				{{ job.level }}
			</button>
			<button
				@click="getJobLanguage"
				class="job__skill"
				v-for="(language, index) in job.languages"
				:key="index"
			>
				{{ language }}
			</button>
			<button
				@click="getJobTools"
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
	box-shadow: 0px 8px 20px -8px rgba(91, 164, 164, 1);
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
	top: -10%;
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
	cursor: pointer;
	flex-basis: 100%;
	font-weight: 700;
	margin: 1.5rem 0;
	transition: all 0.2s linear;
}

.job__position:hover {
	color: var(--desaturated-dark-cyan);
}

.job__info-add {
	color: var(--dark-grayish-cyan);
	font-weight: 500;
	margin-right: 1.5rem;
}

.job__info-add:nth-last-child(1)::before,
.job__info-add:nth-last-child(2)::before {
	background-color: var(--dark-grayish-cyan);
	border-radius: 50%;
	content: "";
	display: inline-block;
	height: 4px;
	margin: 0 1rem 0.2rem 0;
	width: 4px;
}

.job__buttons {
	display: flex;
	flex-wrap: wrap;
	border-top: 1px solid var(--dark-grayish-cyan);
	margin-top: 2rem;
}

.job__skill {
	background-color: var(--light-grayish-cyan-ft);
	border: none;
	color: var(--desaturated-dark-cyan);
	cursor: pointer;
	flex-basis: 25%;
	font-size: 1.5rem;
	font-weight: 700;
	margin: 1rem 1.5rem 1rem 0;
	padding: 5px;
	transition: all 0.2s linear;
}

.job__skill:hover {
	background-color: var(--desaturated-dark-cyan);
	color: var(--light-grayish-cyan-ft);
}

@media screen and (min-width: 1024px) {
	.job {
		align-items: start;
		display: grid;
		grid-template-columns: auto auto 1fr;
		grid-template-rows: auto auto auto;
		padding-bottom: 3rem;
	}

	.job__icon {
		position: static;
		width: 7rem;
	}

	.job__info {
		margin-left: 2rem;
	}

	.job__position {
		margin: 0.5rem 35rem 1rem 0;
	}

	.job__buttons {
		border: none;
		flex-wrap: nowrap;
		margin: 1rem 0 0 0;
	}

	.job__skill {
		font-size: 1.4rem;
	}
}
</style>
