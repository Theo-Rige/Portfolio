<template>
	<div id="ribbon" ref="ribbon">
		<template v-for="n in 3">
			<template v-for="tech in techs" :key="tech">
				<IconStar />
				<a :href="tech.link" target="_blank">{{ tech.name }}</a>
			</template>
		</template>
	</div>
</template>

<script setup>
import { ref } from 'vue'

import IconStar from '@/components/icons/IconStar.vue'

const techs = ref([
	{
		name: 'Figma',
		link: 'https://www.figma.com/',
	},
	{
		name: 'Gridsome',
		link: 'https://gridsome.org/',
	},
	{
		name: 'Nuxt 3',
		link: 'https://v3.nuxtjs.org/',
	},
	{
		name: 'Vue 3',
		link: 'https://v3.vuejs.org/',
	},
	{
		name: 'Tailwind',
		link: 'https://tailwindcss.com/',
	},
	{
		name: 'Sass',
		link: 'https://sass-lang.com/',
	},
	{
		name: 'Strapi',
		link: 'https://strapi.io/',
	},
	{
		name: 'Netlify',
		link: 'https://www.netlify.com/',
	},
	{
		name: 'Wordpress',
		link: 'https://wordpress.org/',
	},
])
</script>

<style lang="scss">
#ribbon {
	position: absolute;
	display: flex;
	align-items: center;
	gap: space(2);
	margin: space(20) 0 0 0;
	padding: space(1);
	color: $dark;
	@include monument;
	background: linear-gradient(92.27deg, #aadcb8 -2.2%, $primary 23.42%, #ade6bd 102.48%);

	a {
		display: block;
		color: $dark;
		white-space: nowrap;
		font-size: 0.875rem;
	}

	svg {
		width: space(3);
		height: space(3);
		flex-shrink: 0;
	}
}

@media screen and (min-width: $lg) {
	#ribbon {
		a {
			font-size: 1rem;
		}
	}
}
</style>
