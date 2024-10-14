<script lang="ts">
	export let onClick: () => void;
</script>

<button class="button" on:click={onClick}>
	<slot />
</button>

<style>
	.button {
		width: auto;
		height: auto;
		font-size: 18px;
		font-weight: 400;
		line-height: 21.6px;
		border-radius: 50px;
		padding: 0.625rem 2.5rem;
		background-color: var(--button-bg, #2c2f47);
		color: rgba(255, 255, 255, 0.7);
		border: none;
		cursor: pointer;
		transition: background-color 0.3s;
	}

	.button:hover {
		background-color: #404463;
	}
</style>
