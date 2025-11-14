<script>
	import favicon from '$lib/assets/favicon.svg';
	let { children } = $props();
	import { base } from '$app/paths';
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<nav> <a href="{base}/photoapp">Photo App</a></nav>
<nav> <a href="{base}/start">hem </a></nav>
{@render children?.()}
