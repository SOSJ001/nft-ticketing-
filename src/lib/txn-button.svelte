<script lang="ts">
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
	const { connection } = $workSpace;
	const publicKey = $walletStore.publicKey as PublicKey;
    let signature: TransactionSignature = '';
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
<Button on:click={onClick} outline color="yellow"><slot>Buy Now</slot></Button>