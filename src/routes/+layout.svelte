<script lang="ts">
	import '../app.css';
	import NavBar from '$lib/components/NavBar.svelte';

	let { children } = $props();

	// Default cart count for the navbar
	const cartCount = $state(3);
</script>

<NavBar {cartCount} />

{@render children()}
