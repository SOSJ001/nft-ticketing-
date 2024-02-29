<script lang="ts">
	import '../app.pcss';
	import '$lib/global.css';

	import { onMount } from 'svelte';
	import * as web3 from '@solana/web3.js';
	import {
		workSpace,
		WalletProvider,
		WalletMultiButton,
		ConnectionProvider
	} from '@svelte-on-solana/wallet-adapter-ui';
	import {
		Navbar,
		NavBrand,
		NavLi,
		NavUl,
		NavHamburger,
		Avatar,
		Dropdown,
		DropdownItem,
		DropdownHeader,
		DropdownDivider,
		DarkMode
	} from 'flowbite-svelte';
	import Footer from '../lib/footer.svelte';

	const localStorageKey = 'walletAdapter';
	const network = web3.clusterApiUrl('devnet'); // localhost or mainnet

	let wallets;

	onMount(async () => {
		const {
			PhantomWalletAdapter,
			// SlopeWalletAdapter,
			SolflareWalletAdapter,
			// SolletExtensionWalletAdapter,
			TorusWalletAdapter
		} = await import('@solana/wallet-adapter-wallets');

		const walletsMap = [
			new PhantomWalletAdapter(),
			// new SlopeWalletAdapter(),
			new SolflareWalletAdapter(),
			// new SolletExtensionWalletAdapter(),
			new TorusWalletAdapter()
		];

		wallets = walletsMap;
	});
</script>

<WalletProvider {localStorageKey} {wallets} autoConnect />
<ConnectionProvider {network} />
<div class="h-full w-screen flex-col items-center justify-center">
	<Navbar>
		<NavBrand href="/">
			<a href="/" class="font-extrabold text-white">SOS SEATS</a>
		</NavBrand>
		<div class="flex items-center space-x-2 md:order-2">
			<WalletMultiButton />
			<NavHamburger class1="w-full md:flex md:w-auto md:order-1" />
			<DarkMode />
		</div>
		<NavUl>
			<NavLi href="/" active={true}>Home</NavLi>
			<NavLi href="/dashboard">Dashboad</NavLi>
			<NavLi href="/about">About</NavLi>
			<NavLi href="/pricing">Pricing</NavLi>
			<NavLi href="/contact">Contact</NavLi>
		</NavUl>
	</Navbar>
	<div class="w-screen flex-col">
		<slot />
	</div>
	<Footer/>
</div>
