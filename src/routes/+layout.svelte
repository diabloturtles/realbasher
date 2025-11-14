<script>
	import favicon from '$lib/assets/favicon.svg';
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<nav> <a href="/photoapp">Photo App</a></nav>
<nav> <a href="/start">hem </a></nav>
{@render children?.()}
