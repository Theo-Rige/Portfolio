<template>
	<header id="header">
		<RouterLink to="/"><AppLogo /></RouterLink>
		<div class="notice">
			<div class="notice__dot"></div>
			<LinkInline href="#contact" class="notice__text">Disponible en freelance</LinkInline>
		</div>
		<ButtonDefault label="Contact" href="#contact" />
	</header>
</template>

<script setup>
import { RouterLink } from 'vue-router'

import AppLogo from '@/components/app/AppLogo.vue'
import ButtonDefault from '@/components/buttons/ButtonDefault.vue'
import LinkInline from '@/components/links/LinkInline.vue'
</script>

<style lang="scss">
$duration: 0.8s;
$easing: cubic-bezier(0.83, 0, 0.17, 1);

#header {
	position: fixed;
	z-index: 3;
	top: var(--space);
	right: var(--space);
	left: var(--space);
	display: flex;
	align-items: center;
	justify-content: space-between;
	transform: translateY(-100%);
	opacity: 0;
	animation: $duration slide-down 3s $easing forwards;

	svg {
		width: space(4);
		height: space(4);
	}

	.notice {
		display: flex;
		align-items: center;
		gap: space(1);
		opacity: 0;

		&__dot {
			width: space(1);
			height: space(1);
			border-radius: 50%;
			background: $primary;
		}
	}

	@keyframes slide-down {
		0% {
			transform: translateY(-100%);
			opacity: 0;
		}
		100% {
			transform: translateY(0);
			opacity: 1;
		}
	}
}

@media screen and (min-width: $sm) {
	#header {
		.notice {
			opacity: 1;
		}

		svg {
			width: space(5);
			height: space(5);
		}
	}
}
</style>
