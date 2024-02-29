<script>
	import { Dropzone } from 'flowbite-svelte';
	import { Input, Label, Helper, Button } from 'flowbite-svelte';
	import { ButtonGroup } from 'flowbite-svelte';

	let value = [];
	const dropHandle = (event) => {
		value = [];
		event.preventDefault();
		if (event.dataTransfer.items) {
			[...event.dataTransfer.items].forEach((item, i) => {
				if (item.kind === 'file') {
					const file = item.getAsFile();
					value.push(file.name);
					value = value;
				}
			});
		} else {
			[...event.dataTransfer.files].forEach((file, i) => {
				value = file.name;
			});
		}
	};

	const handleChange = (event) => {
		const files = event.target.files;
		if (files.length > 0) {
			value.push(files[0].name);
			value = value;
		}
	};

	const showFiles = (files) => {
		if (files.length === 1) return files[0];
		let concat = '';
		files.map((file) => {
			concat += file;
			concat += ',';
			concat += ' ';
		});

		if (concat.length > 40) concat = concat.slice(0, 40);
		concat += '...';
		return concat;
	};
</script>

<form class="w-3/5">
	<div class="text-white font-semibold text-lg p-3 text-center">
		Manage Your collection of related NFT Ticket Metadata Data <br> stored on-chain and in the JSON metadata
	</div>
	<Dropzone
		id="dropzone"
		on:drop={dropHandle}
		on:dragover={(event) => {
			event.preventDefault();
		}}
		on:change={handleChange}
	>
		<svg
			aria-hidden="true"
			class="mb-3 h-10 w-10 text-gray-400"
			fill="none"
			stroke="currentColor"
			viewBox="0 0 24 24"
			xmlns="http://www.w3.org/2000/svg"
			><path
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"
			/></svg
		>
		{#if value.length === 0}
			<p class="mb-2 text-sm text-gray-500 dark:text-gray-400">
				<span class="font-semibold">Click to upload</span> or drag and drop
			</p>
			<p class="text-xs text-gray-500 dark:text-gray-400">SVG, PNG, JPG or GIF (MAX. 800x400px)</p>
		{:else}
			<p>{showFiles(value)}</p>
		{/if}
	</Dropzone>
	<div class="mb-6 mt-6 grid gap-6 md:grid-cols-2">
		<div>
			<Label for="first_name" class="mb-2">Total Ticket(s)</Label>
			<Input type="number" min="1" id="first_name" placeholder="200" required />
		</div>
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
