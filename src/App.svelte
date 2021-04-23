<script>
	export let name;
	import Header from './Header.svelte';

</script>

<main>
	<Header />
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>
<style global>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;

	@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

	body{
		  font-family: 'Poppins', sans-serif;
	}
</style>