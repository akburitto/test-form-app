<script lang="ts">
	export let checked = false;
	export let label = 'I accept';
	export let highlight_label = 'Terms and Privacy policy';
	export let onChange: (event: Event) => void;
</script>

<div class="checkbox">
	<input id="checkbox__id" class="substituted" type="checkbox" bind:checked on:change={onChange} />

	<label class="checkbox__label" for="checkbox__terms">
		{label} <span class="checkbox__terms">{highlight_label}</span>
	</label>
</div>

<style>
	@supports (-webkit-appearance: none) or (-moz-appearance: none) {
		.checkbox {
			display: flex;
			align-items: center;
			gap: 10px;
		}
		.checkbox input[type='checkbox'] {
			--active: #2c2f47;
			--active-inner: #fff;
			--border: #3f4363;
			--border-hover: #8f94b8cc;
			--background: transparent;
			--disabled: #f6f8ff;
			--disabled-inner: #e1e6f9;
			-webkit-appearance: none;
			-moz-appearance: none;
			height: 21px;
			outline: none;
			display: inline-block;
			vertical-align: top;
			position: relative;
			margin: 0;
			cursor: pointer;
			border: 1px solid var(--bc, var(--border));
			background: var(--b, var(--background));
			transition:
				background 0.3s,
				border-color 0.3s,
				box-shadow 0.2s;
		}
		.checkbox input[type='checkbox']:after {
			content: '';
			display: block;
			left: 0;
			top: 0;
			position: absolute;
			transition:
				transform var(--d-t, 0.3s) var(--d-t-e, ease),
				opacity var(--d-o, 0.2s);
		}
		.checkbox input[type='checkbox']:checked {
			--b: var(--active);
			--bc: var(--active);
			--d-o: 0.3s;
			--d-t: 0.6s;
			--d-t-e: cubic-bezier(0.2, 0.85, 0.32, 1.2);
		}
		.checkbox input[type='checkbox']:disabled {
			--b: var(--disabled);
			cursor: not-allowed;
			opacity: 0.9;
		}
		.checkbox input[type='checkbox']:disabled:checked {
			--b: var(--disabled-inner);
			--bc: var(--border);
		}
		.checkbox input[type='checkbox']:disabled + label {
			cursor: not-allowed;
		}
		.checkbox input[type='checkbox']:hover:not(:checked):not(:disabled) {
			--bc: var(--border-hover);
		}
		.checkbox input[type='checkbox']:focus {
			box-shadow: 0 0 0 var(--focus);
		}
		.checkbox input[type='checkbox']:not(.switch) {
			width: 30px;
			height: 30px;
		}
		.checkbox input[type='checkbox']:not(.switch):after {
			opacity: var(--o, 0);
		}
		.checkbox input[type='checkbox']:not(.switch):checked {
			--o: 1;
		}
		.checkbox input[type='checkbox'] + label {
			display: inline-block;
			vertical-align: middle;
			cursor: pointer;
			margin-left: 4px;
		}

		.checkbox input[type='checkbox']:not(.switch) {
			border-radius: 7px;
		}
		.checkbox input[type='checkbox']:not(.switch):after {
			width: 9px;
			height: 13px;
			border: 2px solid var(--active-inner);
			border-top: 0;
			border-left: 0;
			left: 9px;
			top: 5px;
			transform: rotate(var(--r, 20deg));
		}
		.checkbox input[type='checkbox']:not(.switch):checked {
			--r: 43deg;
		}
	}

	.checkbox * {
		box-sizing: inherit;
	}
	.checkbox *:before,
	.checkbox *:after {
		box-sizing: inherit;
	}

	.checkbox__label {
		font-weight: 300;
		font-size: 15px;
		color: #797ea3;
	}

	.checkbox__terms {
		color: #b9bee5;
		text-decoration: underline;
		cursor: pointer;
	}
</style>
