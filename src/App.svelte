<script>
import Router from "svelte-spa-router";
import Home from "./routes/Home.svelte";
</script>

<Router	routes = {{
		'/' : Home
	}}
/>