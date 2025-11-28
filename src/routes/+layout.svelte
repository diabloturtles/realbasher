<script>
	import favicon from '$lib/assets/favicon.svg';
	let { children } = $props();
	import { base } from '$app/paths';
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<nav> <a href="{base}/photoapp">Photo App</a>
 <a href="{base}/start">hem </a>
 <a href="{base}/register">fruzz </a></nav>
{@render children?.()}

<style>


:global(body), :global(html){
  margin: 0%;
  padding: 0%;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top:0;
  left: 0;
  overflow: hidden;
  background-color: rgba(0, 255, 179, 0.434);
}    

</style>