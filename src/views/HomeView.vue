<template>
	<main>
		<HomeHero />
		<HomeSkills />
		<HomeAbout />
		<HomeRibbon data-lg-scroll data-lg-scroll-inertia="0.7" data-lg-scroll-animate="{'rotate': ['4deg', '4deg'],'x': ['-8%', '-16%']}" />
		<!-- <Suspense> -->
		<HomeProjects />
		<!-- </Suspense> -->
		<HomeContact />
	</main>
</template>

<script setup>
import HomeHero from '@/components/home/HomeHero.vue'
import HomeSkills from '@/components/home/HomeSkills.vue'
import HomeAbout from '@/components/home/HomeAbout.vue'
import HomeRibbon from '@/components/home/HomeRibbon.vue'
import HomeProjects from '@/components/home/HomeProjects.vue'
import HomeContact from '@/components/home/HomeContact.vue'

const props = defineProps({
	luge: Object,
})
</script>

<style lang="scss">
main {
	position: relative;
	overflow: hidden;

	#about,
	#contact {
		@include width;
		padding: var(--space);
		margin: 0 auto;

		h2 {
			@include monument;
			font-weight: bold;
			font-size: 1rem;
		}
	}
}

@media screen and (min-width: $sm) {
	main {
		#about,
		#contact {
			h2 {
				font-size: 1.5rem;
			}
		}
	}
}
</style>
