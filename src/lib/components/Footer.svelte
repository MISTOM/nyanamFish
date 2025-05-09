<script lang="ts">
	// Ensure the component is reactive and handles any possible props
	let props = $props();
</script>

<footer class="bg-primary-dark pt-12 text-white">
	<div class="container mx-auto px-6">
		<div class="mb-12 grid grid-cols-1 gap-12 md:grid-cols-2 lg:grid-cols-4">
			<div>
				<a href="/" class="block h-35 bg-white" aria-label="Nyanam Fish - Home">
					<img
						src="/nyanamFishLogo.webp"
						alt="Nyanam Fish Logo"
						class="h-full w-auto object-contain"
					/>
				</a>
				<p class="text-primary-light mb-4">
					From Lake Victoria to your plate - fresh, fried, and delivered.
				</p>
			</div>

			<div>
				<h3
					class="after:bg-accent relative mb-6 pb-2 text-lg font-bold after:absolute after:bottom-0 after:left-0 after:h-0.5 after:w-10"
				>
					Quick Links
				</h3>
				<ul class="space-y-3">
					<li>
						<a href="/" class="text-primary-light transition-colors hover:text-white">Home</a>
					</li>
					<li>
						<a href="/shop" class="text-primary-light transition-colors hover:text-white"
							>Online Shop</a
						>
					</li>
					<li>
						<a href="/about" class="text-primary-light transition-colors hover:text-white">About</a>
					</li>
					<li>
						<a href="/contact" class="text-primary-light transition-colors hover:text-white"
							>Contact</a
						>
					</li>
					<li>
						<a href="/blog" class="text-primary-light transition-colors hover:text-white">Blog</a>
					</li>
				</ul>
			</div>

			<div>
				<h3
					class="after:bg-accent relative mb-6 pb-2 text-lg font-bold after:absolute after:bottom-0 after:left-0 after:h-0.5 after:w-10"
				>
					Contact Us
				</h3>
				<ul class="text-primary-light space-y-3">
					<li class="flex items-start">
						<i class="bi bi-geo-alt mt-1 mr-2"></i>
						<span>Nairobi, Kenya</span>
					</li>
					<li class="flex items-start">
						<i class="bi bi-clock mt-1 mr-2"></i>
						<span>09:00 - 23:00</span>
					</li>
					<li class="flex items-start">
						<i class="bi bi-telephone mt-1 mr-2"></i>
						<span>+254 (044) 756-16-52</span>
					</li>
					<li class="flex items-start">
						<i class="bi bi-envelope mt-1 mr-2"></i>
						<span>info@nyanamfish.com</span>
					</li>
				</ul>
			</div>

			<div>
				<h3
					class="after:bg-accent relative mb-6 pb-2 text-lg font-bold after:absolute after:bottom-0 after:left-0 after:h-0.5 after:w-10"
				>
					Follow Us
				</h3>
				<div class="flex space-x-4">
					<a
						href="/#"
						aria-label="Facebook"
						class="hover:bg-accent flex h-10 w-10 items-center justify-center rounded-full bg-white/10 transition-colors"
					>
						<i class="bi bi-facebook"></i>
					</a>
					<a
						href="/#"
						aria-label="Twitter"
						class="hover:bg-accent flex h-10 w-10 items-center justify-center rounded-full bg-white/10 transition-colors"
					>
						<i class="bi bi-twitter-x"></i>
					</a>
					<a
						href="/#"
						aria-label="Instagram"
						class="hover:bg-accent flex h-10 w-10 items-center justify-center rounded-full bg-white/10 transition-colors"
					>
						<i class="bi bi-instagram"></i>
					</a>
					<a
						href="/#"
						aria-label="Youtube"
						class="hover:bg-accent flex h-10 w-10 items-center justify-center rounded-full bg-white/10 transition-colors"
					>
						<i class="bi bi-youtube"></i>
					</a>
				</div>
			</div>
		</div>
	</div>

	<div class="border-primary text-primary-light border-t py-6 text-center text-sm">
		<p>&copy; 2025 Nyanam Fish. All Rights Reserved.</p>
	</div>
</footer>
