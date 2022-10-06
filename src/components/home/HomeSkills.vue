<template>
	<section id="skills">
		<div class="noise"></div>
		<div class="cards" data-lg-reveal data-lg-reveal-stagger="0.4">
			<template v-for="mission in missions">
				<div class="card">
					<div class="card__heading">
						<h2>{{ mission.title }}</h2>
						<IconStar />
					</div>
					<hr />
					<p>{{ mission.description }}</p>
				</div>
			</template>
		</div>
	</section>
</template>

<script setup>
import { ref } from 'vue'

import IconStar from '@/components/icons/IconStar.vue'

const missions = ref([
	{
		title: 'UI Design',
		description:
			'La combinaison de ma passion pour le design, le code et les interactions me permet de créer des interfaces pertinentes et pixel-perfect pour un site web, une application web ou mobile.',
	},
	{
		title: 'Développement',
		description: "Mes connaissances en développement web me permettent aujourd'hui de créer de zéro votre projet avec toute la logique dont vous avez besoin pour répondre à vos besoins.",
	},
	{
		title: 'E-Commerce',
		description: "En plus de l'UI Design et d'un site classique, je peux vous aider à développer votre business en développant votre site e-commerce sur mesure et administrable.",
	},
])
</script>

<style lang="scss">
$duration: 1.2s;
$easing: cubic-bezier(0, 0.55, 0.45, 1);

#skills {
	position: relative;
	overflow: hidden;
	padding: var(--space);

	background: linear-gradient(92.27deg, #aadcb8 -2.2%, $primary 23.42%, #ade6bd 102.48%);

	.noise {
		opacity: 0.6;
	}

	.cards {
		position: relative;
		z-index: 1;
		display: flex;
		flex-direction: column;
		gap: var(--space);

		.card {
			display: flex;
			flex-direction: column;
			gap: space(1);
			color: $dark;

			&__heading {
				display: flex;
				align-items: center;
				justify-content: space-between;
				overflow: hidden;

				h2 {
					@include monument;
					font-weight: bold;
					font-size: 1rem;
					opacity: 0;
					transform: translateY(100%);
					transition: $duration opacity $easing, $duration transform $easing;
				}

				svg {
					height: space(3);
					opacity: 0;
					transform: translateX(-100%);
					transition: $duration opacity 1s $easing, $duration transform 1s $easing;
				}
			}

			hr {
				border: 0;
				margin: 0;
				height: 1px;
				width: 0%;
				background: $dark;
				transition: $duration width 0.4s $easing;
			}

			p {
				font-weight: 500;
				opacity: 0;
				transform: translateY(50%);
				transition: $duration opacity 0.6s $easing, $duration transform 0.6s $easing;
			}

			&.lg-reveal {
				opacity: 1;
			}

			&.is-in {
				h2,
				p {
					opacity: 1;
					transform: translateY(0);
				}

				hr {
					width: 100%;
				}

				svg {
					opacity: 1;
					transform: translateX(0);
				}
			}
		}
	}
}

@media screen and (min-width: $md) {
	#skills {
		.cards {
			.card {
				gap: space(2);

				&__heading {
					h2 {
						font-size: 1.25rem;
					}
				}
			}
		}
	}
}

@media screen and (min-width: $xl) {
	#skills {
		.cards {
			flex-direction: row;
		}
	}
}
</style>
