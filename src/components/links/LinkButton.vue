<template>
	<div class="hover-effect">
		<span><slot /></span>
		<span><slot /></span>
	</div>
</template>

<style lang="scss">
.hover-effect {
	overflow: hidden;
	display: flex;
	flex-direction: column;
	max-height: 1rem;

	span {
		font-size: 0.875rem;
		line-height: 1rem;
		transition: transform 0.2s ease-in-out;
	}
}

@media screen and (min-width: $sm) {
	.hover-effect {
		max-height: 1.25rem;

		span {
			font-size: 1rem;
			line-height: 1.25rem;
		}
	}
}
</style>
