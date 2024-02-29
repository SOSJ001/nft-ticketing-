<script>
	import { Gallery } from 'flowbite-svelte';
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

<div class="mx-auto mb-1 flex flex-wrap items-center justify-center gap-3 py-4 md:py-8">
	<Button pill size="xl" color="yellow" outline>All categories</Button>
	<Button pill size="xl" color="alternative">Hackathon</Button>
	<Button pill size="xl" color="alternative">Breakpoint</Button>
	<Button pill size="xl" color="alternative">Conference</Button>
	<Button pill size="xl" color="alternative">Solana Beach</Button>
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
				<Rating rating="4" size="24" class="mb-5 mt-2.5">
					<Badge slot="text" class="ms-3">4</Badge>
				</Rating>
				<div class="flex items-center justify-between">
					<span class="text-3xl font-bold text-gray-900 dark:text-white">{`${item.price} Sol`}</span
					>
					<slot />
				</div>
			</div>
		</Card>
		<!-- /////////////////////////////////////////////// -->
	</div>
</Gallery>
