<script>
	import { Card, Avatar } from 'flowbite-svelte';
	import { onMount, onDestroy } from 'svelte';

	let count = 1893;
	let interval;

	function startCounter() {
		// Prevent multiple intervals by clearing existing one before setting a new one
		clearInterval(interval);
		interval = setInterval(() => {
			count += 1;
		}, 1000);
	}

	onMount(startCounter); // Optionally start the counter automatically on mount

	onDestroy(() => {
		clearInterval(interval);
	});
</script>

<div class="flex w-full justify-center">
	<div>
		<Card href="/dashboard">
			<div class="flex items-center justify-between space-x-5">
				<div><Avatar rounded border /></div>
				<div>
					<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
						Earn By Your Works
					</h5>
					<p class="font-normal leading-tight text-gray-700 dark:text-gray-400">
						<span class="text-white">POINTS</span> : {count}
					</p>
				</div>
			</div>
		</Card>
	</div>
</div>
