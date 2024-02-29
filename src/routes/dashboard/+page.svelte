<script>
	import { Tabs, TabItem } from 'flowbite-svelte';
	import { Input, Label, Helper, Button, Checkbox, A } from 'flowbite-svelte';
	import { ButtonGroup } from 'flowbite-svelte';
</script>

<Tabs
	style="full"
	defaultClass="flex rounded-lg divide-x rtl:divide-x-reverse divide-gray-200 shadow dark:divide-gray-700"
>
	<TabItem class="w-full" open activeClasses="text-white border-2 w-full h-full">
		<span slot="title">MY EVENTS</span>
		<p class="text-sm text-gray-500 dark:text-gray-400">
			<b>Profile:</b>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore
			et dolore magna aliqua.
		</p>
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full">
        <!-- create Event Tab -->
		<span slot="title">CREATE EVENT</span>
		<div class=" flex items-center justify-center">
			<form class="w-3/5">
				<div class="mb-6 grid gap-6 md:grid-cols-2">
					<div>
						<Label for="first_name" class="mb-2">Event Name</Label>
						<Input type="text" id="first_name" placeholder="Christex Sport" required />
					</div>
					<div>
						<Label for="last_name" class="mb-2">Symbol</Label>
						<Input type="text" id="last_name" placeholder="christexfndn" required />
					</div>
					<div>
						<Label for="company" class="mb-2">Description</Label>
						<Input type="text" id="company" placeholder="Sport at the tennis Court" required />
					</div>
					<div>
						<Label for="website" class="mb-2">External URL</Label>
						<Input type="url" id="website" placeholder="christrx@fndn.com" required />
					</div>
				</div>
				<div class="m-2 flex-col space-y-3">
					<div><span class="text-lg font-extrabold text-white">Royalties</span></div>
					<div>
						<div>
							<span class="text-sm text-white"
								>Sets the royalties on secondary sales for assets within the Project</span
							>
						</div>
						<div><span class="text-sm text-white">We get 10% of that.</span></div>
					</div>

					<div>
						<ButtonGroup>
							<Button outline color="dark">None</Button>
							<Button outline color="dark">1.0%</Button>
							<Button outline color="dark">5.0%</Button>
							<Button outline color="dark">10.0%</Button>
						</ButtonGroup>
					</div>
				</div>
				<Button outline color="yellow">Create Event</Button>
			</form>
		</div>
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full ">
		<span slot="title">HISTORY</span>
		<p class="text-sm text-gray-500 dark:text-gray-400">
			<b>Settings:</b>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore
			et dolore magna aliqua.
		</p>
	</TabItem>
	<TabItem class="w-full" activeClasses="text-white border-2 w-full h-full">
		<span slot="title">POINTS</span>
		<p class="text-sm text-gray-500 dark:text-gray-400">
			<b>Users:</b>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore
			et dolore magna aliqua.
		</p>
	</TabItem>
</Tabs>
