<template>
	<form class="form" :class="classDirection" @submit.prevent="onSubmit">
		<div class="form-group">
			<input
				type="email"
				name="email"
				placeholder="Enter your email..."
				v-model="formState.email"
				:class="formState.error && 'error'"
			/>
			<span class="error-tag" v-if="formState.error"
				>Please check your email</span
			>
		</div>

		<ButtonSubmit :text="buttonText" />
	</form>
</template>
<script setup>
	import { reactive } from '@vue/reactivity';
	import ButtonSubmit from './ButtonSubmit.vue';
	const { buttonText, classDirection } = defineProps([
		'buttonText',
		'classDirection',
	]);

	const formState = reactive({
		email: '',
		error: false,
	});

	const onSubmit = () => {
		const { email } = formState;
		if (!email) {
			formState.error = true;
		} else {
			formState.error = false;
		}
	};
</script>
<style scoped>
	.form {
		display: flex;
		gap: 1rem;
		flex: 0 1 40%;
	}

	input {
		padding: 15px 20px;
		font-size: 17px;
		width: 500px;
		border-radius: 5px;
		border: 1px solid;
	}

	input::placeholder {
		font-family: var(--raleway);
	}

	.column {
		flex-direction: column;
		gap: 2rem;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		position: relative;
	}

	.error {
		border: 1px solid var(--error);
	}

	.error-tag {
		margin-top: 10px;
		color: var(--errorText);
		font-weight: 700;
		position: absolute;
		top: 50px;
	}

	@media (max-width: 991px) {
		.form {
			flex-direction: column;
			align-items: center;
			gap: 2rem;
		}

		input {
			max-width: 300px;
		}
	}
</style>
