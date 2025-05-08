<script lang="ts">
	import { onMount } from 'svelte';
	import { page } from '$app/state';
	import { fly } from 'svelte/transition';

	const navItems = [
		{ href: '/', label: 'Home' },
		{ href: '/shop', label: 'Shop' },
		{ href: '/about', label: 'About' },
		{ href: '/contact', label: 'Contact' },
		{ href: '/blog', label: 'Blog' }
	];

	// Active link class
	const activeClass = 'border-primary text-primary border-b-2 font-medium';

	// Inactive link class with hover effect
	const inactiveClass =
		'after:bg-primary hover:text-primary relative font-medium text-gray-800 ' +
		'after:absolute after:bottom-[-4px] after:left-0 after:h-0.5 after:w-0 ' +
		'after:transition-all after:duration-300 hover:after:w-full';

	// Props for the component
	let { cartCount = 0 } = $props();

	// State variables
	let mobileMenuOpen = $state(false);

	function toggleMobileMenu() {
		mobileMenuOpen = !mobileMenuOpen;
	}

	function closeMobileMenu() {
		mobileMenuOpen = false;
	}

	onMount(() => {
		// Close mobile menu when pressing escape key
		const handleEscape = (e: KeyboardEvent) => {
			if (e.key === 'Escape' && mobileMenuOpen) {
				closeMobileMenu();
			}
		};

		window.addEventListener('keydown', handleEscape);

		return () => {
			window.removeEventListener('keydown', handleEscape);
		};
	});
</script>

<header class="sticky top-0 z-50 bg-white shadow-md">
	<div class="bg-primary px-6 py-2 text-white">
		<div class="container mx-auto flex justify-between text-sm">
			<div class="flex items-center space-x-4">
				<span><i class="bi bi-telephone"></i> +254 (044) 756-16-52</span>
				<span class="hidden sm:inline">|</span>
				<span class="hidden items-center sm:flex"
					><i class="bi bi-envelope"></i> info@nyanamf-ish.com</span
				>
			</div>
			<div>
				<span class="hidden sm:inline">Free delivery on orders above KSH 3500</span>
			</div>
		</div>
	</div>
	<nav class="container mx-auto flex items-center justify-between px-6 py-4">
		<div class="flex items-center">
			<!-- Logo image instead of text -->
			<a href="/" class="block h-15" aria-label="Nyanam Fish - Home">
				<img
					src="/nyanamFishLogo.webp"
					alt="Nyanam Fish Logo"
					class="h-full w-auto object-contain"
				/>
			</a>
		</div>
		<div class="hidden space-x-6 md:flex">
			{#each navItems as { href, label }}
				<a {href} class={page.url.pathname === href ? activeClass : inactiveClass}>
					{label}
				</a>
			{/each}
		</div>
		<div class="flex items-center space-x-4">
			<button class="hover:text-primary transition-colors" aria-label="Search">
				<i class="bi bi-search text-xl"></i>
			</button>
			<button class="hover:text-primary transition-colors" aria-label="Account">
				<i class="bi bi-person text-xl"></i>
			</button>
			<button class="hover:text-primary relative transition-colors" aria-label="Cart">
				<i class="bi bi-cart text-xl"></i>
				{#if cartCount > 0}
					<span
						class="bg-accent absolute -top-2 -right-2 flex h-5 w-5 items-center justify-center rounded-full text-xs font-bold text-white"
						>{cartCount}</span
					>
				{/if}
			</button>
			<button
				class="hover:text-primary transition-colors md:hidden"
				aria-label="Menu"
				aria-expanded={mobileMenuOpen}
				onclick={toggleMobileMenu}
			>
				<i class="bi bi-list text-2xl"></i>
			</button>
		</div>
	</nav>

	<!-- Mobile Menu Overlay -->
	{#if mobileMenuOpen}
		<div
			class="fixed inset-0 z-50 bg-black/50 md:hidden"
			onclick={closeMobileMenu}
			aria-hidden="true"
		></div>
	{/if}

	<!-- Mobile Menu -->
	{#if mobileMenuOpen}
		<div
			class="fixed top-0 right-0 z-50 h-full w-72 overflow-y-auto bg-white shadow-lg transition-transform duration-300"
			transition:fly={{ duration: 300, x: 280 }}
		>
			<div class="flex items-center justify-between border-b p-6">
				<div class="text-primary text-xl font-bold">Nyanam Fish</div>
				<button
					class="hover:text-primary text-gray-600 transition-colors"
					aria-label="Close menu"
					onclick={closeMobileMenu}
				>
					<i class="bi bi-x-lg text-2xl"></i>
				</button>
			</div>

			<nav class="p-6">
				<ul class="space-y-4">
					{#each navItems as { href, label }}
						<li>
							<a
								{href}
								class={href === page.url.pathname
									? 'text-primary border-primary block border-l-4 px-4 py-2 font-medium'
									: 'hover:text-primary hover:border-primary block border-l-4 border-transparent px-4 py-2 font-medium text-gray-800 transition-colors'}
								onclick={closeMobileMenu}
							>
								{label}
							</a>
						</li>
					{/each}
				</ul>
			</nav>

			<div class="border-t p-6">
				<div class="mb-4 flex flex-col space-y-3 text-sm">
					<div class="flex items-center">
						<i class="bi bi-telephone text-primary mr-2"></i>
						<span>+254 (044) 756-16-52</span>
					</div>
					<div class="flex items-center">
						<i class="bi bi-envelope text-primary mr-2"></i>
						<span>info@nyanam-fish.com</span>
					</div>
				</div>

				<div class="flex space-x-3">
					<a
						href="/#"
						aria-label="Facebook"
						class="hover:bg-primary/10 flex h-8 w-8 items-center justify-center rounded-full transition-colors"
					>
						<i class="bi bi-facebook text-primary"></i>
					</a>
					<a
						href="/#"
						aria-label="Twitter"
						class="hover:bg-primary/10 flex h-8 w-8 items-center justify-center rounded-full transition-colors"
					>
						<i class="bi bi-twitter-x text-primary"></i>
					</a>
					<a
						href="/#"
						aria-label="Instagram"
						class="hover:bg-primary/10 flex h-8 w-8 items-center justify-center rounded-full transition-colors"
					>
						<i class="bi bi-instagram text-primary"></i>
					</a>
					<a
						href="/#"
						aria-label="Youtube"
						class="hover:bg-primary/10 flex h-8 w-8 items-center justify-center rounded-full transition-colors"
					>
						<i class="bi bi-youtube text-primary"></i>
					</a>
				</div>
			</div>
		</div>
	{/if}
</header>
