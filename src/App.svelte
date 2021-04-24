<script>
import Router from "svelte-spa-router";
import Home from "./routes/Home.svelte";
import AcoountQr from "./routes/Qrcode.svelte";
import ErrorPage from "./routes/Error.svelte";
import {replace} from 'svelte-spa-router';

import { onMount } from 'svelte';

onMount(
    async () => {
		if(window.innerWidth > 640 )
	{	
		
		replace("/error/0");
		throw new Error('Required Mobile browser');
	}
	});


</script>

<Router	routes = {{
		'/' : Home,
		'/getReward' : AcoountQr,
		'/error/:msg' : ErrorPage
	}}
/>