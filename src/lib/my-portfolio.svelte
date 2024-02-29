<script>
	import { Card, Button, Toggle } from 'flowbite-svelte';
	let vCard = false;
	import { Gallery, Search } from 'flowbite-svelte';
	const images = [
		{
			alt: 'shoes',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-1.jpg',
			created: 'January 1 2024',
			date: 'December 4 2025',
			price: 0.4
		},
		{
			alt: 'small bag',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-2.jpg',
			created: 'January 1 2024',
			date: 'December 4 2026',
			price: 0.5
		},
		{
			alt: 'plants',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-3.jpg',
			created: 'January 1 2024',
			date: 'December 4 2027',
			price: 0.6
		},
		{
			alt: 'watch',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-4.jpg',
			created: 'January 1 2024',
			date: 'December 4 2028',
			price: 0.7
		},
		{
			alt: 'shoe',
			src: 'https://flowbite.s3.amazonaws.com/docs/gallery/square/image-5.jpg',
			created: 'January 1 2024',
			date: 'December 4 2029',
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
	<Button pill size="xl" color="alternative">Created This Month</Button>
	<Button pill size="xl" color="alternative">Created Today</Button>
</div>

<Gallery class="grid-cols-3 gap-4" items={images} let:item>
	<div class="flex justify-center rounded p-1 ring-1 ring-purple-600 dark:ring-yellow-300">
		<!-- ///////////////////////////////////////////////// -->
		<div class="space-y-4">
			<Card reverse={vCard}>
				<a href="/">
					<img src={item.src} alt={item.alt} class="h-auto max-w-full" />
				</a>
				<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
					Name : Christex Sport
				</h5>
				<h5 class="mb-2 text-md font-bold tracking-tight text-gray-900 dark:text-white">
					Date : {`${item.date}`} <br> Created : {`${item.created}`} <br>Total Tickets: 100 <br> Total Left: 20
				</h5>
				<p class="mb-3 font-normal leading-tight text-gray-700 dark:text-gray-400">
					Description:  Lorem Lorem Lorem ipsum dolor sit amet consectetur adipisicing elit.s accusantium iste. Quis..
				</p>
				<Button color="yellow" outline>More Details</Button>
			</Card>

			<Toggle bind:checked={vCard} class="italic dark:text-gray-500">Reverse</Toggle>
		</div>
		<!-- /////////////////////////////////////////////// -->
	</div>
</Gallery>
