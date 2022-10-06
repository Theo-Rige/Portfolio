<template>
	<section id="contact" ref="contact">
		<h2>CONTACT</h2>
		<form name="contact" ref="form" @submit.prevent="submit">
			<label>
				Nom
				<input type="text" name="lastname" required />
			</label>
			<label>
				Prénom
				<input type="text" name="name" required />
			</label>
			<label class="full">
				Email
				<input type="email" name="email" required />
			</label>
			<label class="full">
				Entreprise (optionnel)
				<input type="text" name="compagny" />
			</label>
			<label class="full">
				Sujet
				<input type="text" name="compagny" required />
			</label>
			<label class="full">
				Message
				<textarea name="message" required></textarea>
			</label>
			<div class="full">
				<ButtonSubmit :label="label" :class="{ disabled: disabled }" />
			</div>
		</form>
		<hr />
		<div class="alt">
			<span>Ou envoyer moi un mail à <LinkInline href="mailto:contact@rigetheo.com">contact@rigetheo.com</LinkInline></span>
			<div class="alt__socials">
				<LinkInline href="www.linkedin.com/in/rigetheo" target="_blank">LI</LinkInline>
				<LinkInline href="https://www.instagram.com/rigetheo" target="_blank">IG</LinkInline>
				<LinkInline href="https://github.com/Theo-Rige" target="_blank">GH</LinkInline>
			</div>
		</div>
	</section>
</template>

<script setup>
import { ref } from 'vue'
import LinkInline from '@/components/links/LinkInline.vue'
import ButtonSubmit from '@/components/buttons/ButtonSubmit.vue'

const form = ref(null)
const label = ref('Envoyer')
const disabled = ref(false)

const submit = async () => {
	let formdata = new FormData(form.value)
	try {
		// const { solution } = await botpoison.value.challenge()
		await $fetch('https://submit-form.com/8vsDjOO1', {
			method: 'POST',
			body: {
				...Object.fromEntries(formdata.entries()),
				// _botpoison: solution,
			},
		})
		disabled.value = true
		label.value = 'Formualire envoyé avec succès'
	} catch (error) {
		label.value = 'Sorry an error occured : ' + error.message
	}
}
</script>

<style lang="scss">
#contact {
	form {
		margin-top: space(3);
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: min(var(--space), space(5));

		label {
			display: block;
			font-size: 0.875rem;
			color: $accent-100;

			input,
			textarea {
				all: unset;
				box-sizing: border-box;
				display: block;
				width: 100%;
				margin-top: space(1);
				color: $white;
				font-size: 1rem;
				font-weight: 400;
				transition: border-color 0.4s cubic-bezier(0.215, 0.61, 0.355, 1);
			}

			input {
				height: space(5);
				border-bottom: 1px solid $accent-200;
			}

			textarea {
				overflow-wrap: break-word;
				white-space: pre-wrap;
				min-height: 160px;
				border: 1px solid $accent-200;
				padding: space(2);
			}

			:where(input, textarea):focus {
				border-color: $primary;
			}
		}

		.full {
			grid-column: span 2;
		}

		button[type='submit'] {
			display: block;
			margin: 0 auto;
		}
	}

	hr {
		border: 0;
		margin: space(5) 0;
		width: 100%;
		height: 1px;
		background: $accent-200;
	}

	.alt {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: min(var(--space), space(5));

		a {
			@include monument;
			font-weight: bold;

			&[href^='mailto'] {
				font-size: 13px;
			}
		}

		&__socials {
			width: 100%;
			display: flex;
			justify-content: space-between;
			gap: space(3);
		}
	}
}

@media screen and (min-width: $sm) {
	#contact {
		.alt {
			flex-direction: row;

			&__socials {
				width: fit-content;
				display: flex;
				justify-content: space-between;
				gap: space(3);
			}
		}
	}
}
</style>
