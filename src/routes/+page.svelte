<!-- +page.svelte -->
<script>
	import Form from '../components/Form.svelte';
</script>

<main>
	<h1 class="header__title">Hello</h1>

	<Form />
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-image: url('../assets/bg-cosmos.jpeg');
		background-size: cover;
		background-position: center;
	}

	.header__title {
		font-size: 3.4375rem;
		line-height: 4.125rem;
		text-align: center;
		color: #fff;
	}
	@media (max-width: 400px) {
		.header__title {
			font-size: 3rem;
			line-height: 3.525rem;
		}
	}
</style>
