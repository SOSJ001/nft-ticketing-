<script>
	import { Tabs, TabItem } from 'flowbite-svelte';
	import CreateEvent from '../../lib/create-event.svelte';
	import Attending from '../../lib/attending.svelte';
	import MyPortfolio from '../../lib/my-portfolio.svelte';
	import History from '../../lib/history.svelte';
	import Point from '../../lib/point.svelte';
</script>

<Tabs
	style="full"
	defaultClass="flex rounded-lg divide-x rtl:divide-x-reverse divide-gray-200 shadow dark:divide-gray-700"
>
	<TabItem class="w-full" open activeClasses="text-white border-2 w-full h-full">
		<span slot="title">MY PORTFOLIO</span>
		<div class=" items-center justify-center">
			<!-- <MyPortfolio /> -->
			<MyPortfolio />
		</div>
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full">
		<!-- Attending -->
		<span slot="title">ATTENDING</span>
		<div class=" flex items-center justify-center">
			<Attending />
		</div>
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full">
		<!-- create Event Tab -->
		<span slot="title">CREATE EVENT</span>
		<div class=" flex items-center justify-center">
			<CreateEvent />
		</div>
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full ">
		<!-- history -->
		<span slot="title">HISTORY</span>
		<History />
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full">
		<!-- Points -->
		<span slot="title">POINTS</span>
		<Point />
	</TabItem>
</Tabs>
