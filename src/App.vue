<template>
	<div data-lg-cursor data-lg-cursor-hide>
		<div data-lg-cursor-pointer data-lg-cursor-inertia="0.1"></div>
		<div data-lg-cursor-pointer></div>
	</div>
	<AppHeader />
	<div data-lg-smooth>
		<RouterView :luge="luge" />
	</div>
</template>

<script setup>
import luge from '@waaark/luge'

import AppHeader from '@/components/app/AppHeader.vue'
</script>

<style lang="scss">
:root {
	--space: #{space(4)};
}

@media screen and (min-width: $sm) {
	:root {
		--space: #{space(4)};
	}
}

@media screen and (min-width: $lg) {
	:root {
		--space: #{space(5)};
	}
}

@media screen and (min-width: $xxl) {
	:root {
		--space: #{space(10)};
	}
}

@mixin width {
	max-width: calc($max-width + 2 * var(--space));
}

body {
	font-family: $space-grotesk;
	color: $white;
	background: $dark;
}

.lg-cursor {
	.lg-cursor-pointer {
		&:nth-child(1):before {
			margin: -16px 0 0 -16px;
			width: 32px;
			height: 32px;
			border: 1px solid $accent-100;
			background: transparent;
			transition: all 0.3s ease-in-out;
		}
		&:nth-child(2):before {
			margin: -1px 0 0 -1px;
			width: 4px;
			height: 4px;
			background-color: $white;
			transition: all 0.3s ease-in-out;
		}
	}

	&--hover {
		.lg-cursor-pointer {
			&:nth-child(1):before {
				margin: -24px 0 0 -24px;
				width: 48px;
				height: 48px;
				border: 1px solid $accent-100;
				transform: none;
			}
			&:nth-child(2):before {
				margin: -3px 0 0 -3px;
				width: 6px;
				height: 6px;
				transform: none;
			}
		}
	}
}
</style>
