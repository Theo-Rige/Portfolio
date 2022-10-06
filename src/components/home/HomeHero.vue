<template>
	<section id="hero">
		<div class="noise"></div>
		<div class="intro">
			<h1 class="intro__title">
				<span class="intro__title_name">THÉO RIGÉ</span>
				<span class="intro__title_main">DESIGNER ET DÉVELOPPEUR WEB</span>
			</h1>
			<span class="intro__welcome">BIENVENUE SUR MON PORTFOLIO</span>
			<img src="@/assets/images/gem.webp" alt="Gem" data-lg-parallax data-lg-parallax-amplitude="-0.5" />
		</div>
	</section>
</template>

<style lang="scss">
$duration: 0.8s;
$easing: cubic-bezier(0.83, 0, 0.17, 1);
$text-duration: 3s;
$text-easing: cubic-bezier(0.16, 1, 0.3, 1);

#hero {
	position: relative;
	overflow: hidden;
	display: flex;
	align-items: center;
	justify-content: center;
	height: 100vh;
	background: linear-gradient(106.08deg, #3e465a -4.12%, #292a35 103.48%);
	animation: $duration extend 3s $easing forwards;

	&::before,
	&::after {
		content: '';
		position: absolute;
		border-radius: 50%;
		filter: blur(300px);
	}

	&::before {
		bottom: 0;
		left: 0;
		transform: translate(-50%, 50%);
		width: 1133px;
		height: 667px;
		background: $accent-200;
	}

	&::after {
		top: 0;
		right: 0;
		transform: translate(50%, -50%);
		width: 1133px;
		height: 667px;
		background: $accent-100;
	}

	.noise {
		min-height: 100vh;
		opacity: 0.8;
	}

	.intro {
		position: relative;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		z-index: 2;
		@include width;
		padding: 0 var(--space);
		@include monument;

		span {
			display: block;
		}

		&__title {
			&_name {
				// font-size: 2rem;
				font-size: 1rem;
				font-weight: 300;
				transform: translateY(100%) rotate3d(1, 0, 0, 90deg);
				opacity: 0;
				animation: $text-duration swipe-in $text-easing forwards;
			}

			&_main {
				// font-size: 3rem;
				font-size: 2rem;
				font-weight: bold;
				margin-top: space(1);
				transform: translateY(100%) rotate3d(1, 0, 0, 90deg);
				opacity: 0;
				animation: $text-duration swipe-in 0.2s $text-easing forwards;
			}
		}

		&__welcome {
			width: 100%;
			// font-size: 2rem;
			font-size: 1rem;
			font-weight: bold;
			margin-top: space(1);
			transform: translateY(100%) rotate3d(1, 0, 0, 90deg);
			opacity: 0;
			animation: $text-duration swipe-in 0.4s $text-easing forwards;
		}

		img {
			position: absolute;
			z-index: -1;
			max-height: 500px;
			transform: translateX(25%);
		}

		@keyframes swipe-in {
			0% {
				transform: translateY(100%) rotate3d(1, 0, 0, 90deg);
				opacity: 0;
			}
			50% {
				transform: translateY(50%) rotate3d(1, 0, 0, 90deg);
				opacity: 1;
			}
			100% {
				transform: translateY(0%) rotate3d(1, 0, 0, 0deg);
				opacity: 1;
			}
		}
	}

	@keyframes extend {
		0% {
			height: 100vh;
		}
		100% {
			height: calc(100vh - space(5));
		}
	}
}

@media screen and (min-width: $sm) {
	#hero {
		.intro {
			img {
				right: 0;
			}
		}
	}
}

@media screen and (min-width: $md) {
	#hero {
		.intro {
			&__title {
				&_name {
					font-size: 1.5rem;
				}

				&_main {
					font-size: 2.5rem;
				}
			}

			&__welcome {
				font-size: 1.5rem;
			}
		}
	}
}

@media screen and (min-width: $xxl) {
	#hero {
		.intro {
			&__title {
				&_name {
					font-size: 2rem;
				}

				&_main {
					font-size: 3rem;
				}
			}

			&__welcome {
				font-size: 2rem;
			}
		}
	}
}
</style>
