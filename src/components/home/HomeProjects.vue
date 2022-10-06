<template>
	<section id="projects">
		<h2>PROJETS</h2>
		<div class="projects" data-lg-reveal data-lg-reveal-stagger="0.4">
			<RouterLink to="/" class="project" v-for="project in projects" :key="project.id">
				<div class="project__card" :style="{ backgroundImage: `url(${project.cover})` }">
					<div class="project__card_overlay"></div>
					<div class="hover-effect">
						<h3>{{ project.name }}</h3>
						<span>{{ project.name }}</span>
					</div>
				</div>
			</RouterLink>
		</div>
	</section>
</template>

<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

// const props = defineProps({
// 	luge: Object,
// })

const projects = ref([
	{
		id: 1,
		name: 'myFridge',
		cover: './images/projects/myFridge.webp',
	},
	{
		id: 2,
		name: 'Sleek',
		cover: './images/projects/sleek.webp',
	},
	{
		id: 3,
		name: 'Mobile Manager',
		cover: './images/projects/manager.webp',
	},
])

// const data = await fetch('http://localhost:4000/api/projects?populate=%2A&locale=fr')
// const { data: projects } = await data.json()

// fetch('http://localhost:4000/api/projects?populate=%2A&locale=fr')
// 	.then((resp) => resp.json())
// 	.then((data) => {
// 		projects.value = data.data
// 	})
// 	.finally(() => {
// 		props.luge.emitter.emit('resize')

// 		// props.luge.emitter.emit('update')
// 	})
</script>

<style lang="scss">
$duration: 1.2s;
$easing: cubic-bezier(0, 0.55, 0.45, 1);

#projects {
	@include width;
	padding: var(--space);
	margin: space(15) auto 0 auto;

	h2 {
		@include monument;
		font-weight: bold;
		font-size: 1rem;
	}

	.projects {
		display: flex;
		flex-direction: column;
		gap: space(3);
		margin-top: space(3);

		.project {
			overflow: hidden;

			&__card {
				position: relative;
				background-repeat: no-repeat;
				background-size: cover;
				background-position: center;
				padding: space(6) min(var(--space), space(5));
				opacity: 0;
				transform: translateY(75%);
				transition: $duration opacity 0.4s $easing, $duration transform 0.4s $easing;

				.hover-effect {
					max-height: 1.5rem;

					h3,
					span {
						position: relative;
						font-size: 1.25rem;
						line-height: 1.5rem;
						font-weight: 500;
						transition: transform 0.2s ease-in-out;
					}
				}

				&_overlay {
					position: absolute;
					inset: 0;
					background: linear-gradient(90deg, rgba(20, 21, 25, 0.8) 0%, rgba(0, 0, 0, 0) 40%);
				}
			}

			&:hover {
				.hover-effect {
					h3,
					span {
						transform: translateY(-1.5rem);
					}
				}
			}

			&.is-in {
				.project__card {
					opacity: 1;
					transform: translateY(0);
				}
			}
		}
	}
}

@media screen and (min-width: $sm) {
	#projects {
		h2 {
			font-size: 1.5rem;
		}

		.projects {
			.project {
				&__card {
					.hover-effect {
						max-height: 2rem;

						h3,
						span {
							position: relative;
							font-size: 1.75rem;
							line-height: 2rem;
							font-weight: 500;
							transition: transform 0.2s ease-in-out;
						}
					}
				}

				&:hover {
					.hover-effect {
						h3,
						span {
							transform: translateY(-2rem);
						}
					}
				}
			}
		}
	}
}
</style>
