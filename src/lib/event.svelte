<script>
	import { Gallery, Search } from 'flowbite-svelte';
	import { Card, Button, Rating, Badge } from 'flowbite-svelte';
	const images = [
		{
			alt: 'shoes',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-1.jpg',
			price: 0.4
		},
		{
			alt: 'small bag',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-2.jpg',
			price: 0.5
		},
		{
			alt: 'plants',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-3.jpg',
			price: 0.6
		},
		{
			alt: 'watch',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-4.jpg',
			price: 0.7
		},
		{
			alt: 'shoe',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-5.jpg',
			price: 0.8
		}
	];
</script>

<div class="mb-1 flex w-full justify-center">
	<div class=" w-1/2">
		<Search>
			<Button outline color="yellow">Search</Button>
		</Search>
	</div>
</div>
<p class="text-2xl text-center">Events :</p>
<div class="mx-auto flex flex-wrap items-center justify-center gap-3 pb-4 md:pb-8 md:pt-4">
	<Button pill size="xl" color="yellow" outline>All categories</Button>
	<Button pill size="xl" color="alternative">Hackathon</Button>
	<Button pill size="xl" color="alternative">Breakpoint</Button>
	<Button pill size="xl" color="alternative">Conference</Button>
	<Button pill size="xl" color="alternative">Solana Beach</Button>
	<Button pill size="xl" color="alternative">This Month</Button>
	<Button pill size="xl" color="alternative">Today</Button>
</div>

<Gallery class="grid-cols-3 gap-4" items={images} let:item>
	<div class="flex justify-center rounded p-1 ring-1 ring-purple-600 dark:ring-yellow-300">
		<!-- ///////////////////////////////////////////////// -->
		<Card padding="none">
			<a href="/">
				<img src={item.src} alt={item.alt} class="h-auto max-w-full" />
			</a>
			<div class="px-5 pb-5">
				<a href="/">
					<h5 class="text-xl font-semibold tracking-tight text-gray-900 dark:text-white">
						Christex Foundation Sport
					</h5>
				</a>
				<p class="mb-3 font-normal leading-tight text-gray-700 dark:text-gray-400">
					Description: Lorem Lorem Lorem ipsum dolor sit amet consectetur adipisicing elit.s
					accusantium iste. Quis..
				</p>
				<div class="flex items-center justify-between">
					<span class="text-3xl font-bold text-gray-900 dark:text-white">{`${item.price} Sol`}</span
					>
					<slot />
					<Button color="alternative">Share Link</Button>
				</div>
			</div>
		</Card>
		<!-- /////////////////////////////////////////////// -->
	</div>
</Gallery>
