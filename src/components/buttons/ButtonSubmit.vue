<template>
	<button type="submit">
		<LinkButton>{{ props.label }}</LinkButton>
	</button>
</template>

<script setup>
import LinkButton from '@/components/links/LinkButton.vue'
const props = defineProps({
	label: {
		type: String,
		required: true,
	},
})
</script>

<style lang="scss">
button[type='submit'] {
	all: unset;
	padding: space(1) space(2);
	color: $dark;
	font-weight: 700;
	background: $primary;
	border-radius: space(10);
	transition: background 0.2s ease-in-out;

	&:hover {
		cursor: pointer;

		.hover-effect span {
			transform: translateY(-1rem);
		}
	}

	&.disabled {
		pointer-events: none;
	}
}

@media screen and (min-width: $sm) {
	button[type='submit'] {
		padding: space(1.5) 20px;

		&:hover {
			.hover-effect span {
				transform: translateY(-1.25rem);
			}
		}
	}
}
</style>
