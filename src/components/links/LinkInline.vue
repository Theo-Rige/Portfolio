<template>
	<a>
		<slot />
	</a>
</template>

<style lang="scss" scoped>
a {
	position: relative;
	color: $white;

	&:before {
		content: '';
		position: absolute;
		width: 100%;
		height: 1px;
		background: $primary;
		top: 100%;
		left: 0;
		pointer-events: none;
		transform-origin: 100% 50%;
		transform: scale3d(0, 1, 1);
		transition: transform 0.3s;
	}

	&:hover {
		cursor: pointer;

		&::before {
			transform-origin: 0% 50%;
			transform: scale3d(1, 1, 1);
		}
	}
}
</style>
