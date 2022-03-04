<script>
	let networkParams = {
		chainId: '0x1', // A 0x-prefixed hexadecimal string
		chainName: 'Ethereum Pocket Portal',
		nativeCurrency: {
			// name: string,
			symbol: 'ETH', // 2-6 characters long
			decimals: 18
		},
		rpcUrls: ['https://eth-rpc.gateway.pokt.network'],
		blockExplorerUrls: ['https://etherscan.io']
		// iconUrls?: string[], // Currently ignored.
	};
	let error = null;
	async function addPOKT() {
		if (typeof window.ethereum === 'undefined') {
			console.log('MetaMask is installed!');
			alert('MetaMask is not installed!');
			return;
		}

		try {
			await window.ethereum.request({
				method: 'wallet_addEthereumChain',
				params: [networkParams]
			});
		} catch (e) {
			console.dir(e);
			error = e;
		}
	}
</script>

<svelte:head>
	<title>Pocket-powered RPC Endpoints | How to add the Ethereum (ETH) network in MetaMask with a Pocket-powered RPC Endpoint</title>
</svelte:head>

<section class="min-h-screen flex flex-col items-center justify-center text-xl p-4">

	{#if error}
		<div class="m-10 p-5 xlg:max-w-xlg max-w-full text-center bg-rose-700">
			<h3 class="text-4xl">
				Oh no! That's an error! 💥
				<br />
				<span class="text-2xl">{error.message}</span>
				<br />
				<br />
			</h3>
			<p>Sorry you need to manually add POKT RPC endpoint. Tried the following network params:</p>
			<div class="text-left">
				<pre>{JSON.stringify(networkParams, null, 2)}</pre>
			</div>
		</div>
	{/if}

	<a
		on:click={addPOKT}
		href="#_"
		class="lg:px-24 lg:py-8 px-5 py-4 relative rounded group font-medium text-white font-medium inline-block
		sm:text-4xl ">
		<span
			class="absolute top-0 left-0 w-full h-full rounded opacity-50 filter blur-sm bg-gradient-to-br
			from-purple-600 to-blue-500" />
		<span
			class="h-full w-full inset-0 absolute mt-0.5 ml-0.5 bg-gradient-to-br filter
			group-active:opacity-0 rounded opacity-50 from-purple-600 to-blue-500" />
		<span
			class="absolute inset-0 w-full h-full transition-all duration-200 ease-out rounded shadow-xl
			bg-gradient-to-br filter group-active:opacity-0 group-hover:blur-sm from-purple-600
			to-blue-500" />
		<span
			class="absolute inset-0 w-full h-full transition duration-200 ease-out rounded
			bg-gradient-to-br to-purple-600 from-blue-500" />
		<h1 class="relative tracking-tight font-extrabold">Add POKT RPC Network (ETH) to Metamask</h1>
	</a>

	<div class="mt-10 text-xl">
		<p>
			More details here
			<a

				href="https://docs.pokt.network/home/resources/public-rpc-endpoints/ethereum-eth-metamask"
				target="_blank"
				class="underline">
				"How to add the Ethereum (ETH) network in MetaMask with a Pocket-powered RPC Endpoint"
			</a>
		</p>
	</div>
</section>
