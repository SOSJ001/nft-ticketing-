<script lang="ts">
	// @ts-nocheck
	import { DarkMode } from 'flowbite-svelte';
	import { walletStore } from '@svelte-on-solana/wallet-adapter-core';
	import { workSpace } from '@svelte-on-solana/wallet-adapter-ui';
	import {
		LAMPORTS_PER_SOL,
		type TransactionSignature,
		PublicKey,
		SystemProgram,
		Transaction,
		Connection,
		Keypair
	} from '@solana/web3.js';
	import { Button } from 'flowbite-svelte';
	import Hero from '$lib/hero.svelte';
	import Event from '../lib/event.svelte';
	import Buttontxn from '../lib/buttontxn.svelte';
	import Footer from '../lib/footer.svelte';
	let signature: TransactionSignature = '';
	const { connection } = $workSpace;
	const publicKey = $walletStore.publicKey as PublicKey;
	// console.log($walletStore.publicKey)
	let balance = 0;

	async function onClick() {
		balance++;

		let transaction = new Transaction();
		const recipientPubKey = new PublicKey('3ZPcjHB48wwrHmpj1pMkH3ohbEaajpTVHZJuAw4TwVzL');

		const sendSolInstruction = SystemProgram.transfer({
			fromPubkey: $walletStore.publicKey,
			toPubkey: recipientPubKey,
			lamports: LAMPORTS_PER_SOL * 0.1
		});

		transaction = transaction.add(sendSolInstruction);
		transaction.feePayer = $walletStore.publicKey; //setting the fee payer
		const { blockhash } = await connection.getRecentBlockhash(); //getting the recent block hash
		transaction.recentBlockhash = blockhash;
		const signedTransaction = await $walletStore.signTransaction(transaction); //this is to sign the transaction
		signature = await connection.sendRawTransaction(signedTransaction.serialize(), {
			skipPreflight: true,
			preflightCommitment: 'confirmed'
		}); //this is to send the transaction to the network after signing (signature is here too)
		const confirmation = await connection.confirmTransaction(signature, 'confirmed');
		// Log the transaction signature
		console.log('Transaction signature:', signature);
		console.log('Transaction confirmation:', confirmation);
	}
</script>

<div class="text-black dark:text-white">
	{#if $walletStore.connected}
		<div class="flex-col space-y-5">
			<div class="">
				<Hero />
			</div>
			<div class="px-5">
				<Event>
					<Button on:click={onClick} outline color="yellow">Buy now</Button>
				</Event>
			</div>

			<!-- <div class="text-white">
				Your balance is {balance}
			</div> -->
		</div>
	{:else}
		your wallet is not Connected
	{/if}
</div>

