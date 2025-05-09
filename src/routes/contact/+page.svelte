<script lang="ts">
	import { onMount } from 'svelte';
	import { fly, fade } from 'svelte/transition';

	// State for form fields
	let name = $state('');
	let email = $state('');
	let subject = $state('');
	let message = $state('');
	let isSubmitting = $state(false);
	let isSubmitted = $state(false);
	let formError = $state('');
	let isVisible = $state(false);

	/**
	 * Handles the form submission
	 *
	 * Reason: Validates form data and processes submission with feedback
	 */
	const handleSubmit = () => {
		// Form validation
		if (!name || !email || !message) {
			formError = 'Please fill out all required fields';
			return;
		}

		isSubmitting = true;

		// Simulate form submission
		setTimeout(() => {
			isSubmitting = false;
			isSubmitted = true;

			// Clear form
			name = '';
			email = '';
			subject = '';
			message = '';
			formError = '';
		}, 1500);
	};

	// Contact information
	const contactInfo = {
		location: {
			title: 'Location',
			content: 'Nairobi, Kenya',
			postalBox: 'P.O. Box 1338-00200',
			icon: 'bi-geo-alt'
		},
		email: {
			title: 'Email',
			content: 'info@nyanamfish.com',
			icon: 'bi-envelope'
		},
		phone: {
			title: 'Phone',
			content: '+254 108 383 505',
			icon: 'bi-telephone'
		}
	};

	onMount(() => {
		isVisible = true;
	});
</script>

<svelte:head>
	<title>Contact Us - Nyanam Fish | Fresh Tilapia from Lake Victoria</title>
	<meta
		name="description"
		content="Get in touch with Nyanam Fish for fresh tilapia from Lake Victoria delivered to your doorstep."
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
				class="mb-4 text-4xl leading-tight font-bold tracking-tighter md:text-5xl"
				transition:fly={{ y: 50, duration: 800 }}
			>
				We're Here to Help
			</h1>
			<p
				class="mb-6 max-w-3xl text-xl leading-relaxed"
				transition:fly={{ y: 50, duration: 800, delay: 200 }}
			>
				At Nyanam Fish, we value your questions, feedback, and suggestions. Whether you're placing
				an order, tracking a delivery, or have general inquiries, feel free to reach out to us
				anytime.
			</p>
		{/if}
	</div>
</section>

<main class="bg-gray-50 px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto max-w-7xl">
		<div class="grid gap-12 md:grid-cols-2">
			<!-- Contact Information -->
			<div>
				<div class="rounded-xl bg-white p-8 shadow-sm">
					<h2 class="text-primary-dark mb-6 text-2xl font-bold">Reach Out To Us</h2>

					<div class="space-y-6">
						<div class="flex items-start">
							<div
								class="bg-primary/10 mr-4 flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full"
							>
								<i class="text-primary bi bi-geo-alt text-2xl"></i>
							</div>
							<div>
								<h3 class="font-semibold">{contactInfo.location.title}</h3>
								<p class="mt-1 text-gray-600">{contactInfo.location.content}</p>
								<p class="text-gray-600">{contactInfo.location.postalBox}</p>
							</div>
						</div>

						<div class="flex items-start">
							<div
								class="bg-primary/10 mr-4 flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full"
							>
								<i class="text-primary bi bi-envelope text-2xl"></i>
							</div>
							<div>
								<h3 class="font-semibold">{contactInfo.email.title}</h3>
								<p class="mt-1 text-gray-600">{contactInfo.email.content}</p>
							</div>
						</div>

						<div class="flex items-start">
							<div
								class="bg-primary/10 mr-4 flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full"
							>
								<i class="text-primary bi bi-telephone text-2xl"></i>
							</div>
							<div>
								<h3 class="font-semibold">{contactInfo.phone.title}</h3>
								<p class="mt-1 text-gray-600">{contactInfo.phone.content}</p>
							</div>
						</div>
					</div>

					<div class="mt-8">
						<h3 class="mb-4 font-semibold">Follow Us</h3>
						<div class="flex space-x-4">
							<a
								href="/#"
								class="hover:text-primary text-gray-600 transition-colors"
								aria-label="Visit our Facebook page"
							>
								<i class="bi bi-facebook text-xl"></i>
							</a>
							<a
								href="/#"
								class="hover:text-primary text-gray-600 transition-colors"
								aria-label="Visit our Instagram profile"
							>
								<i class="bi bi-instagram text-xl"></i>
							</a>
							<a
								href="/#"
								class="hover:text-primary text-gray-600 transition-colors"
								aria-label="Visit our Twitter/X profile"
							>
								<i class="bi bi-twitter-x text-xl"></i>
							</a>
							<a
								href="/#"
								class="hover:text-primary text-gray-600 transition-colors"
								aria-label="Visit our YouTube channel"
							>
								<i class="bi bi-youtube text-xl"></i>
							</a>
						</div>
					</div>
				</div>

				<!-- Map placeholder (we can add a real map later) -->
				<div class="mt-8 rounded-xl bg-white p-8 shadow-sm">
					<h2 class="text-primary-dark mb-4 text-xl font-bold">Find Us</h2>
					<div class="h-64 rounded-lg bg-gray-200">
						<!-- Map would go here -->
						<div class="flex h-full items-center justify-center">
							<p class="text-gray-500">Map loading...</p>
						</div>
					</div>
				</div>
			</div>

			<!-- Contact Form -->
			<div class="rounded-xl bg-white p-8 shadow-sm">
				<h2 class="text-primary-dark mb-6 text-2xl font-bold">Send Us a Message</h2>

				{#if isSubmitted}
					<div class="bg-primary/10 rounded-lg p-6 text-center" transition:fade>
						<div class="mb-4 flex justify-center">
							<div class="bg-primary/20 rounded-full p-3">
								<i class="text-primary bi bi-check-lg text-3xl"></i>
							</div>
						</div>
						<p class="text-primary-dark font-medium">Thank you for your message!</p>
						<p class="text-primary-dark mt-2">
							We've received your inquiry and will be in touch soon.
						</p>
					</div>
				{:else}
					<form onsubmit={handleSubmit} class="space-y-6">
						{#if formError}
							<div class="bg-accent/10 text-accent rounded-lg p-4" transition:fade>
								<p>{formError}</p>
							</div>
						{/if}

						<div>
							<label for="name" class="mb-1 block text-sm font-medium text-gray-700"
								>Your Name *</label
							>
							<input
								type="text"
								id="name"
								bind:value={name}
								required
								class="focus:border-primary focus:ring-primary/20 w-full rounded-lg border border-gray-300 px-4 py-3 focus:ring-2 focus:outline-none"
							/>
						</div>

						<div>
							<label for="email" class="mb-1 block text-sm font-medium text-gray-700"
								>Email Address *</label
							>
							<input
								type="email"
								id="email"
								bind:value={email}
								required
								class="focus:border-primary focus:ring-primary/20 w-full rounded-lg border border-gray-300 px-4 py-3 focus:ring-2 focus:outline-none"
							/>
						</div>

						<div>
							<label for="subject" class="mb-1 block text-sm font-medium text-gray-700"
								>Subject</label
							>
							<input
								type="text"
								id="subject"
								bind:value={subject}
								class="focus:border-primary focus:ring-primary/20 w-full rounded-lg border border-gray-300 px-4 py-3 focus:ring-2 focus:outline-none"
							/>
						</div>

						<div>
							<label for="message" class="mb-1 block text-sm font-medium text-gray-700"
								>Message *</label
							>
							<textarea
								id="message"
								bind:value={message}
								required
								rows="4"
								class="focus:border-primary focus:ring-primary/20 w-full rounded-lg border border-gray-300 px-4 py-3 focus:ring-2 focus:outline-none"
							></textarea>
						</div>

						<button
							type="submit"
							disabled={isSubmitting}
							class="bg-primary hover:bg-primary-dark w-full rounded-lg px-6 py-3 font-medium text-white transition-colors disabled:opacity-70"
						>
							{#if isSubmitting}
								<span class="inline-flex items-center">
									<i class="bi bi-arrow-repeat mr-2 animate-spin"></i>
									Sending...
								</span>
							{:else}
								Send Message
							{/if}
						</button>
					</form>
				{/if}
			</div>
		</div>
	</div>
</main>
