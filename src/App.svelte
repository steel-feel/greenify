<script>
import Router from "svelte-spa-router";
import Home from "./routes/Home.svelte";
import AcoountQr from "./routes/Qrcode.svelte";
import ErrorPage from "./routes/Error.svelte";
</script>

<Router	routes = {{
		'/' : Home,
		'/getReward' : AcoountQr,
		'/error/:msg' : ErrorPage
	}}
/>