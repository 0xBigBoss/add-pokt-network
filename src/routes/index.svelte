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
	<title>
		Pocket-powered RPC Endpoints | How to add the Ethereum (ETH) network in MetaMask with a
		Pocket-powered RPC Endpoint
	</title>
	<link rel="icon" href="/favicon.png" id="__link-icon" />
</svelte:head>

<section
	class="bg-slate-800 text-white min-h-screen flex flex-col items-center justify-center text-xl p-4
	pb-[25vh] xlg:max-w-xlg max-w-full">

	<div class="text-4xl text-center max-w-full w-100 my-10">
		<h1>
			<img src="/pokt-logo.svg" alt="POKT" class="m-auto" width="300" />
			<br />
			<br />
			Add POKT powered Ethereum network to metamask below.
			<br />
			Start by clicking the button below.
			<br />
			<br />
			<span class="text-8xl">👇👇👇</span>
		</h1>
	</div>

	<a
		on:click={addPOKT}
		href="#_"
		class="lg:px-24 lg:py-8 px-5 py-4 relative rounded group font-medium text-white font-medium
		inline-block sm:text-4xl ">
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

	{#if error}
		<div
			class="modal z-50 fixed w-full h-full top-0 left-0 flex items-center justify-center p-8 lg:p-0">
			<div class="modal-overlay fixed w-full h-full bg-gray-900 opacity-50" />
			<div
				class="bg-rose-700 w-full lg:h-max max-h-[100vh] lg:w-1/2 md:w-1/4 mx-auto rounded-lg shadow-xl z-50
				overflow-y-auto">
				<div class="head bg-rose-500 py-5 px-8 text-2xl font-extrabold">
					<h3 class="text-4xl">Oh no! That's an error! 💥</h3>
				</div>
				<div class="content p-8">
					<div class="">

						<span class="text-2xl">Reason: {error.message}</span>
						<br />
						<br />

						<p>
							Sorry you need to manually add POKT RPC endpoint. More details here
							<a
								href="https://docs.pokt.network/home/resources/public-rpc-endpoints/ethereum-eth-metamask"
								target="_blank"
								class="underline">
								"How to add the Ethereum (ETH) network in MetaMask with a Pocket-powered RPC
								Endpoint"
							</a>
						</p>
						<div class="pt-10 text-left">
							<div class="max-w-full overflow-scroll">
								<span class="font-bold">for the devs 👩🏻‍💻<br></span>
								Tried the following network params:
								<pre>{JSON.stringify(networkParams, null, 2)}</pre>

								<pre class="bg-slate-700 text-xs">{JSON.stringify(error, null, 2)}</pre>
							</div>
						</div>
					</div>

				</div>
			</div>
		</div>
	{/if}

</section>
