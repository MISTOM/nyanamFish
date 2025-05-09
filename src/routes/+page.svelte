<script lang="ts">
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	// Dummy product data
	const featuredProducts = [
		{
			id: 1,
			name: 'Fresh Tilapia',
			description: 'Fresh, whole tilapia sourced from Lake Victoria. Cleaned and ready to cook.',
			price: 700,
			salePrice: 650,
			image: '/freshTilapia.webp',
			onSale: true
		},
		{
			id: 2,
			name: 'Fried Tilapia',
			description: 'Pre-cooked, crispy fried tilapia. Simply heat and serve for a quick meal.',
			price: 850,
			salePrice: 800,
			image: '/friedTilapia.webp',
			onSale: true
		},
		{
			id: 3,
			name: 'Tilapia Fillets',
			description:
				'Boneless, skinless tilapia fillets with a mild, flaky texture. Ideal for various recipes.',
			price: 1000,
			salePrice: 700,
			image: '/tilapiaFillet.jpg',
			onSale: true
		},
		{
			id: 4,
			name: 'Smoked Tilapia',
			description:
				'Naturally smoked tilapia with a rich, savory flavor. Great for sandwiches or appetizers.',
			price: 500,
			salePrice: 350,
			image: '/smokedTilapia.webp',
			onSale: false
		}
	];

	// Category data
	const categories = [
		{ name: 'Fresh Fish', image: '/freshTilapia.webp', url: '/shop/fresh' },
		{ name: 'Fried Fish', image: '/friedTilapia.webp', url: '/shop/fried' },
		{ name: 'Fish Fillets', image: '/tilapiaFillet.jpg', url: '/shop/fillets' },
		{ name: 'Specialty Items', image: '/tilapiaSteak.webp', url: '/shop/specialty' }
	];
</script>

<svelte:head>
	<title>Nyanam Fish - Fresh Tilapia from Lake Victoria</title>
	<meta
		name="description"
		content="Fresh tilapia, sourced from Lake Victoria, available in various sizes with delivery options. Bringing the best of Lake Victoria to your table."
	/>
</svelte:head>

<main>
	<!-- Hero Section -->
	<section
		class="relative flex h-[80vh] min-h-[500px] items-center bg-cover bg-center"
		style="background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('/tilapias.jpg')"
	>
		<div class="relative z-10 container mx-auto px-6 text-white">
			<h1 class="mb-4 text-4xl leading-tight font-bold tracking-tight md:text-5xl">
				Fresh Tilapia, Just a Tap Away!
			</h1>
			<p class="mb-8 max-w-xl text-xl">
				From Lake Victoria to Your Plate – Fresh, Fried, and Delivered.
			</p>
			<div class="flex flex-col gap-4 sm:flex-row">
				<a
					href="/shop"
					class="bg-accent hover:bg-accent/90 rounded px-6 py-3 text-center font-semibold text-white transition-colors"
					>ORDER NOW</a
				>
				<a
					href="/about"
					class="bg-primary hover:bg-primary-dark rounded px-6 py-3 text-center font-semibold text-white transition-colors"
					>LEARN MORE</a
				>
			</div>
		</div>
	</section>

	<!-- Categories Section -->
	<section class="px-6 py-16">
		<div class="container mx-auto">
			<div class="mb-10 text-center">
				<h2 class="text-primary-dark mb-2 text-3xl font-bold">Shop by Category</h2>
				<p class="mx-auto max-w-2xl text-lg text-gray-700">
					Explore our wide range of tilapia products
				</p>
			</div>

			<div class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-4">
				{#each categories as category}
					<a
						href={category.url}
						class="group block overflow-hidden rounded-lg shadow-md transition-transform duration-300 hover:-translate-y-2"
					>
						<div
							class="relative h-48 bg-cover bg-center"
							style="background-image: url({category.image})"
						>
							<div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent"></div>
							<h3 class="absolute bottom-4 left-4 text-xl font-semibold text-white">
								{category.name}
							</h3>
						</div>
					</a>
				{/each}
			</div>
		</div>
	</section>

	<!-- Value Proposition Section -->
	<section class="bg-gray-50 px-6 py-16">
		<div class="container mx-auto grid grid-cols-1 gap-8 md:grid-cols-3">
			<div class="rounded-lg bg-white p-8 text-center shadow-sm">
				<div class="text-primary mb-4 text-5xl">
					<i class="bi bi-water"></i>
				</div>
				<h3 class="text-primary-dark mb-4 text-xl font-bold">Sourced from Lake Victoria</h3>
				<p class="text-gray-700">
					Our fresh tilapia comes directly from the world's second-largest freshwater lake, ensuring
					top quality and unmatched freshness in every order.
				</p>
			</div>

			<div class="rounded-lg bg-white p-8 text-center shadow-sm">
				<div class="text-primary mb-4 text-5xl">
					<i class="bi bi-flower1"></i>
				</div>
				<h3 class="text-primary-dark mb-4 text-xl font-bold">Fresh and Natural</h3>
				<p class="text-gray-700">
					We pride ourselves on offering sustainably sourced fish with no additives—just pure,
					organic goodness straight to your table.
				</p>
			</div>

			<div class="rounded-lg bg-white p-8 text-center shadow-sm">
				<div class="text-primary mb-4 text-5xl">
					<i class="bi bi-truck"></i>
				</div>
				<h3 class="text-primary-dark mb-4 text-xl font-bold">Reliable and Fast Delivery</h3>
				<p class="text-gray-700">
					Enjoy weekly or fortnightly deliveries, tailored to your schedule. We ensure your tilapia
					arrives fresh, every time.
				</p>
			</div>
		</div>
	</section>

	<!-- Featured Products Section -->
	<section class="px-6 py-16">
		<div class="container mx-auto">
			<div class="mb-10 text-center">
				<h2 class="text-primary-dark mb-2 text-3xl font-bold">Featured Products</h2>
				<p class="mx-auto max-w-2xl text-lg text-gray-700">
					From fresh, raw tilapia to crispy fried options and gourmet fillets, explore diverse
					culinary preferences.
				</p>
			</div>

			<div class="mb-10 grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-4">
				{#each featuredProducts as product}
					<div
						class="overflow-hidden rounded-lg bg-white shadow-md transition-transform duration-300 hover:-translate-y-1"
					>
						<div
							class="relative h-100 bg-cover bg-center"
							style="background-image: url({product.image})"
						>
							{#if product.onSale}
								<span
									class="bg-accent absolute top-4 left-4 rounded px-2 py-1 text-xs font-semibold text-white"
								>
									SALE
								</span>
							{/if}
						</div>
						<div class="p-6">
							<h3 class="text-primary-dark mb-2 text-lg font-bold">{product.name}</h3>
							<p class="mb-4 line-clamp-2 text-sm text-gray-600">{product.description}</p>
							<div class="mb-4 flex items-center">
								{#if product.onSale}
									<span class="mr-2 text-gray-500 line-through">KSH{product.price}</span>
									<span class="text-accent font-bold">KSH{product.salePrice}</span>
								{:else}
									<span class="text-primary-dark font-bold">KSH{product.price}</span>
								{/if}
							</div>
							<button
								class="bg-primary hover:bg-primary-dark w-full cursor-pointer rounded-md px-4 py-2 font-medium text-white transition-colors"
							>
								<i class="bi bi-cart-plus mr-2"></i>ORDER
							</button>
						</div>
					</div>
				{/each}
			</div>

			<div class="text-center">
				<a
					href="/shop"
					class="bg-primary hover:bg-primary-dark inline-block rounded px-6 py-3 font-semibold text-white transition-colors"
				>
					View All Products
				</a>
			</div>
		</div>
	</section>

	<!-- About Us Preview Section -->
	<section class="bg-primary px-6 py-16 text-white">
		<div class="container mx-auto flex flex-col items-center justify-between gap-8 md:flex-row">
			<div class="max-w-xl">
				<h2 class="mb-4 text-3xl font-bold">Meet the Team Behind Nyanam Fish</h2>
				<p class="text-primary-light mb-6">
					Dedicated professionals bringing the freshest tilapia from Lake Victoria to your table
					with care and expertise.
				</p>
				<a
					href="/about"
					class="inline-block rounded border-2 border-white px-6 py-3 font-semibold transition-colors hover:bg-white/10"
				>
					MORE ABOUT US
				</a>
			</div>
			<div class="text-center">
				<div class="text-6xl font-bold">17</div>
				<div class="text-lg tracking-wider uppercase">Years Experience</div>
			</div>
		</div>
	</section>
</main>
