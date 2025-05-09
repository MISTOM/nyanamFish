<script lang="ts">
	import type { PageData } from './$types';
	import { slide } from 'svelte/transition';
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	let { data }: { data: PageData } = $props();

	// FAQ data with isOpen property for each FAQ
	let faqs = $state.raw([
		{
			question: 'How do I place an order for tilapia on your website?',
			answer:
				"Placing an order is simple! Browse through our menu, select your desired tilapia products, and add them to your cart. Once you've made your selection, proceed to checkout, fill in your details, and confirm your order.",
			isOpen: false
		},
		{
			question: 'Can I customize my order or add special instructions?',
			answer:
				"Yes, the system allows you to add special instructions during the checkout process. Whether you have specific preferences for cleaning or preparation, let us know, and we'll do our best to accommodate your request.",
			isOpen: false
		},
		{
			question: 'What payment methods do you accept?',
			answer:
				'We accept multiple payment options, including Mpesa, PayPal, and other secure payment methods listed during checkout.',
			isOpen: false
		},
		{
			question: 'How will I know my order has been received?',
			answer:
				"Once you place an order, you'll receive an email confirmation with your order details. You'll also receive updates via email or SMS when your order is being processed and out for delivery.",
			isOpen: false
		},
		{
			question: 'Can I track my order after placing it?',
			answer:
				"Currently, real-time tracking is not available, but you can contact our customer service team for updates about your order status. We'll also send notifications when your delivery is en route.",
			isOpen: false
		},
		{
			question: 'Is the website mobile-friendly?',
			answer:
				'Absolutely! Our website is fully responsive and works seamlessly on any mobile device. You can browse the menu, place orders, and make payments with ease, all from your phone or tablet.',
			isOpen: false
		}
	]);

	/**
	 * Toggle FAQ open/closed state without affecting other FAQs
	 *
	 * Reason: Allows users to open multiple FAQs simultaneously for better comparison
	 * of related information
	 *
	 * @param {number} index - The index of the FAQ to toggle
	 */
	function toggleFAQ(index: number) {
		faqs = faqs.map((faq, i) => {
			if (i === index) {
				return { ...faq, isOpen: !faq.isOpen };
			}
			return faq;
		});
	}

	let isVisible = $state(false);

	onMount(() => {
		isVisible = true;
	});
</script>

<svelte:head>
	<title>Frequently Asked Questions - Nyanam Fish | Fresh Tilapia from Lake Victoria</title>
	<meta
		name="description"
		content="Find answers to common questions about ordering, delivery, and our fresh tilapia products from Lake Victoria."
	/>
</svelte:head>

<!-- Hero Section -->
<section
	class="relative flex h-[60vh] min-h-[400px] items-center bg-cover bg-center"
	style="background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('/lakeVictoria.jpg')"
>
	<div class="relative z-10 container mx-auto px-6 text-white">
		{#if isVisible}
			<h1
				class="mb-4 text-4xl leading-tight font-bold tracking-tight md:text-5xl"
				transition:fly={{ y: 50, duration: 800 }}
			>
				Frequently Asked Questions
			</h1>
			<p
				class="mb-6 max-w-2xl text-xl leading-relaxed"
				transition:fly={{ y: 50, duration: 800, delay: 200 }}
			>
				Find answers to common questions about our fresh tilapia, ordering process, and delivery
				options.
			</p>
		{/if}
	</div>
</section>

<main class="min-h-screen px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto max-w-7xl">
		<!-- FAQ Section -->
		<div class="mb-16">
			{#each faqs as faq, index}
				<div class="border-b border-gray-200">
					<button
						class="flex w-full cursor-pointer items-center justify-between py-8 text-left focus:outline-none"
						onclick={() => toggleFAQ(index)}
					>
						<h2 class="pr-8 text-2xl font-semibold">{faq.question}</h2>
						<i
							class="bi bi-chevron-down text-xl transition-transform duration-300
                            {faq.isOpen ? 'rotate-180' : ''}"
							aria-label={faq.isOpen ? 'Collapse' : 'Expand'}
							aria-hidden="true"
						></i>
					</button>

					{#if faq.isOpen}
						<div class="mr-6 pb-8 text-justify text-black" transition:slide={{ duration: 300 }}>
							<p>{faq.answer}</p>
						</div>
					{/if}
				</div>
			{/each}
		</div>

		<!-- Additional Info -->
		<div class="mt-12 text-center">
			<h2 class="text-2xl font-bold text-gray-900">Still have questions?</h2>
			<p class="mt-4 text-gray-600">Contact our customer support team for more information.</p>
			<a
				href="/contact"
				class="mt-6 inline-block rounded-full bg-cyan-900 px-8 py-3 font-medium text-white transition-colors hover:bg-cyan-800"
			>
				Contact Us
			</a>
		</div>
	</div>
</main>
