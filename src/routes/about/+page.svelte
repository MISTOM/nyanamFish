<script lang="ts">
    import { onMount } from 'svelte';
    import { fly, fade } from 'svelte/transition';
    import type { PageData } from './$types';

    let { data }: { data: PageData } = $props();

    // Team members data
    const teamMembers = [
        {
            name: 'David Ndolo',
            role: 'CEO and Founder',
            bio: 'With over 17 years in fish farming, David leads our mission to bring fresh tilapia to every Kenyan household.',
            image: '/images/david-placeholder.jpg'
        },
        {
            name: 'Eric Gitonga',
            role: 'Co-Founder',
            bio: 'Eric oversees our sustainable fishing practices and ensures the highest quality standards.',
            image: '/images/eric-placeholder.jpg'
        },
        {
            name: 'Christine',
            role: 'Service Assistant',
            bio: 'Christine ensures exceptional customer service and smooth delivery operations.',
            image: '/images/christine-placeholder.jpg'
        }
    ];

    // Stats data
    const stats = [
        { value: '17+', label: 'Years of Experience' },
        { value: '1000+', label: 'Happy Customers' },
        { value: '5000+', label: 'Deliveries Made' },
        { value: '100%', label: 'Quality Assurance' }
    ];

    // Values data
    const values = [
        {
            title: 'Sustainable Fishing',
            description: 'We practice responsible fishing to protect Lake Victoria\'s ecosystem.',
            icon: 'bi-water'
        },
        {
            title: 'Quality First',
            description: 'Every tilapia meets our strict freshness and quality standards.',
            icon: 'bi-award'
        },
        {
            title: 'Community Impact',
            description: 'Supporting local fishing communities and creating sustainable livelihoods.',
            icon: 'bi-people'
        }
    ];

    let isVisible = $state(false);

    onMount(() => {
        isVisible = true;
    });
</script>

<svelte:head>
    <title>About Us - Nyanam Fish | Fresh Tilapia from Lake Victoria</title>
    <meta name="description" content="Learn about Nyanam Fish's journey, our dedicated team, and our commitment to delivering fresh tilapia from Lake Victoria to your table." />
</svelte:head>

<!-- Hero Section -->
<section class="relative flex h-[60vh] min-h-[400px] items-center bg-cover bg-center" style="background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('/lakeVictoria.jpg')">
    <div class="container relative z-10 mx-auto px-6 text-white">
        {#if isVisible}
            <h1 class="mb-4 text-4xl font-bold leading-tight md:text-5xl" transition:fly={{ y: 50, duration: 1000 }}>
                Our Story
            </h1>
            <p class="mb-6 max-w-2xl text-xl leading-relaxed" transition:fly={{ y: 50, duration: 1000, delay: 200 }}>
                From humble beginnings on the shores of Lake Victoria to becoming Kenya's trusted source for fresh tilapia.
            </p>
        {/if}
    </div>
</section>

<!-- Mission Section -->
<section class="bg-gray-50 px-6 py-16">
    <div class="container mx-auto">
        <div class="grid gap-12 md:grid-cols-2">
            <div class="space-y-6">
                <h2 class="text-primary-dark text-3xl font-bold">Our Mission</h2>
                <p class="text-gray-700 text-lg leading-relaxed">
                    At Nyanam Fish, we're committed to delivering the freshest tilapia from Lake Victoria directly to your table. Our journey began with a simple vision: to make quality fish accessible to every Kenyan household while supporting local fishing communities.
                </p>
                <p class="text-gray-700 text-lg leading-relaxed">
                    Today, we combine traditional fishing wisdom with modern delivery systems to ensure you receive the best tilapia, whether fresh, fried, or filleted, exactly how you prefer it.
                </p>
            </div>
            <div class="grid grid-cols-2 gap-4">
                {#each stats as stat}
                    <div class="bg-white rounded-lg p-6 text-center shadow-md">
                        <div class="text-primary mb-2 text-3xl font-bold">{stat.value}</div>
                        <div class="text-gray-600">{stat.label}</div>
                    </div>
                {/each}
            </div>
        </div>
    </div>
</section>

<!-- Values Section -->
<section class="px-6 py-16">
    <div class="container mx-auto">
        <h2 class="text-primary-dark mb-12 text-center text-3xl font-bold">Our Values</h2>
        <div class="grid gap-8 md:grid-cols-3">
            {#each values as value}
                <div class="bg-white rounded-lg p-8 text-center shadow-md transition-transform duration-300 hover:-translate-y-2">
                    <div class="text-primary mb-4 text-4xl">
                        <i class={value.icon}></i>
                    </div>
                    <h3 class="text-primary-dark mb-4 text-xl font-bold">{value.title}</h3>
                    <p class="text-gray-700">{value.description}</p>
                </div>
            {/each}
        </div>
    </div>
</section>

<!-- Team Section -->
<section class="bg-gray-50 px-6 py-16">
    <div class="container mx-auto">
        <h2 class="text-primary-dark mb-4 text-center text-3xl font-bold">Meet Our Team</h2>
        <p class="mx-auto mb-12 max-w-2xl text-center text-gray-700 text-lg">
            Our dedicated team works tirelessly to ensure you receive the finest tilapia, backed by years of experience and a passion for excellence.
        </p>
        <div class="grid gap-8 md:grid-cols-3">
            {#each teamMembers as member}
                <div class="bg-white overflow-hidden rounded-lg shadow-md transition-transform duration-300 hover:-translate-y-2">
                    <div class="aspect-w-1 aspect-h-1 bg-gray-200">
                        <img
                            src={member.image}
                            alt={member.name}
                            class="h-full w-full object-cover"
                            
                        />
                    </div>
                    <div class="p-6">
                        <h3 class="text-primary-dark mb-2 text-xl font-bold">{member.name}</h3>
                        <p class="text-accent mb-4 font-medium">{member.role}</p>
                        <p class="text-gray-700">{member.bio}</p>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<!-- Call to Action -->
<section class="bg-primary px-6 py-16 text-white">
    <div class="container mx-auto text-center">
        <h2 class="mb-6 text-3xl font-bold">Experience the Nyanam Fish Difference</h2>
        <p class="mx-auto mb-8 max-w-2xl text-lg text-primary-light">
            Join thousands of satisfied customers who trust us for their tilapia needs. Fresh, sustainable, and delivered right to your doorstep.
        </p>
        <a
            href="/shop"
            class="bg-accent hover:bg-accent/90 inline-block rounded-md px-8 py-3 font-semibold text-white transition-colors"
        >
            Shop Now
        </a>
    </div>
</section>
