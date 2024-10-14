<script lang="ts">
	export let label: string = '';
	export let name: string;
	export let type: string = 'text';
	export let value: string;
	export let placeholder: string = '';
	export let error: string = '';
	export let isMandatory: boolean = false;

	function handleInput(event: Event) {
		const target = event.target as HTMLInputElement | HTMLTextAreaElement;
		value = target.value;
	}
</script>

<div class="form__group">
	<div class="form__input-container">
		{#if type === 'textarea'}
			<textarea
				id={name}
				{name}
				{placeholder}
				bind:value
				on:input={handleInput}
				class="form__input form__input--textarea"
			></textarea>
		{:else}
			<input
				id={name}
				{...{ type }}
				{name}
				{placeholder}
				bind:value
				on:input={handleInput}
				class="form__input"
			/>
		{/if}
		{#if label}
			<label for={name} class="form__label">
				{label}{#if isMandatory}<span>*</span>{/if}
			</label>
		{/if}
	</div>
	{#if error}
		<p class="form__error-message">{error}</p>
	{/if}
</div>

<style>
	.form__group {
		margin-bottom: 1rem;
		width: 100%;
	}

	.form__input-container {
		display: flex;
		flex-direction: column-reverse; /* Visually move the label above the input */
	}

	.form__input {
		appearance: none;
		width: 100%;
		border: none;
		outline: none;
		border-bottom: 0.2em solid #3f4363;
		background: transparent;
		padding: 0.4em;
		color: #fff;
		transition:
			border-bottom-color 0.3s,
			color 0.3s;
	}

	.form__input:focus {
		border-bottom-color: #fff;
	}

	.form__label {
		display: block;
		margin-bottom: 0.5rem;
		font-weight: 300;
		color: #797ea3;
		transition: color 0.3s;
	}

	input:focus + label {
		color: #fff;
	}

	.form__error-message {
		color: red;
		font-size: 0.875rem;
		margin-top: 0.25rem;
	}

	.form__input--textarea {
		min-height: 100px;
	}
</style>
