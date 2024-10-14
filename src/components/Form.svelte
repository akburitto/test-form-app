<script lang="ts">
	import InputField from './InputField.svelte';
	import Checkbox from './Checkbox.svelte';
	import Button from './Button.svelte';

	let formData = {
		name: '',
		company: '',
		email: '',
		phone: '',
		subject: '',
		message: '',
		agreeToTerms: false
	};

	let errors = {
		name: '',
		company: '',
		email: '',
		message: ''
	};

	let notification = '';
	let notificationVisible = false;

	function validate() {
		let isValid = true;
		errors = { name: '', company: '', email: '', message: '' };

		if (!formData.name) {
			errors.name = 'Name is required';
			isValid = false;
		}

		if (!formData.company) {
			errors.company = 'Company is required';
			isValid = false;
		}

		if (!formData.email) {
			errors.email = 'Email is required';
			isValid = false;
		} else if (!/\S+@\S+\.\S+/.test(formData.email)) {
			errors.email = 'Please enter a valid email';
			isValid = false;
		}

		if (!formData.message) {
			errors.message = 'Message is required';
			isValid = false;
		}

		if (!formData.agreeToTerms) {
			alert('Please agree to the terms and privacy policy');
			isValid = false;
		}

		return isValid;
	}

	function submitForm() {
		if (validate()) {
			console.log(formData);
			notification = 'Form submitted successfully!';
			notificationVisible = true;

			setTimeout(() => {
				notificationVisible = false;
			}, 3000);
		}
	}

	function handleCheckboxChange(event: Event) {
		formData.agreeToTerms = (event.target as HTMLInputElement).checked;
	}
</script>

<form class="form__container" on:submit|preventDefault={submitForm}>
	<div class="form__header">
		<p class="form__description">For business enquiries please use the form below</p>
		<p class="form__required">*Required</p>
	</div>

	<InputField label="Name" name="name" isMandatory bind:value={formData.name} error={errors.name} />
	<InputField
		label="Company"
		name="company"
		isMandatory
		bind:value={formData.company}
		error={errors.company}
	/>
	<InputField
		label="E-mail"
		name="email"
		type="email"
		isMandatory
		bind:value={formData.email}
		error={errors.email}
	/>
	<InputField label="Phone" isMandatory name="phone" type="tel" bind:value={formData.phone} />
	<InputField label="Subject" isMandatory name="subject" bind:value={formData.subject} />
	<InputField
		label="Message"
		name="message"
		isMandatory
		bind:value={formData.message}
		error={errors.message}
	/>

	<Checkbox bind:checked={formData.agreeToTerms} onChange={handleCheckboxChange} label="I accept" />

	<div style="margin-top: 10px">
		<Button color="#2C2F47" onClick={submitForm}>Send</Button>
	</div>

	{#if notificationVisible}
		<div class="notification">
			{notification}
		</div>
	{/if}
</form>

<style>
	.form__container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		border-radius: 1.6875rem;
		padding: 2.5rem 2.8125rem;
		gap: 0.625rem;
		background-color: #171929;
		overflow: auto;
	}
	@media (max-width: 400px) {
		.form__container {
			padding: 2rem 2.3rem;
		}
	}
	p {
		margin: 0;
	}

	.form__header {
		display: flex;
		flex-direction: column;
		max-width: 14.875rem;
		gap: 5px;
	}

	.form__description {
		font-weight: 400;
		font-size: 1.125rem;
		line-height: 1.35rem;
		text-align: center;
		color: #fff;
	}

	.form__required {
		font-weight: 300;
		font-size: 0.9375rem;
		line-height: 1.125rem;
		text-align: center;
		color: #797ea3;
	}

	.notification {
		color: #797ea3;
	}
</style>
