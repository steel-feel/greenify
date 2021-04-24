<script>
	import Header from "./Header.svelte";
	import { onMount } from 'svelte';
	import Fortmatic from 'fortmatic';

	let balance = 0,
	bLoading = true;

	//import { ethStore, web3, selectedAccount, connected } from 'svelte-web3'

	const fm = new Fortmatic("pk_test_7F64757BB0C010B6", "ropsten");
	
	//window.web3 = new Web3(fm.getProvider());

	
	//oWeb3 = new $web3(fm.getProvider());

	onMount(
    async () => {
  //  console.log(window.Web3)
	// await ethStore.setBrowserProvider(fm.getProvider());
	// await ethStore.setProvider(fm.getProvider());

	window.iWeb3 = new window.Web3(fm.getProvider());
	
		// Get your contract ABI from compiled smart contract json
	const contractAbi = [
		{
			anonymous: false,
			inputs: [
				{
					indexed: true,
					internalType: "address",
					name: "owner",
					type: "address",
				},
				{
					indexed: true,
					internalType: "address",
					name: "spender",
					type: "address",
				},
				{
					indexed: false,
					internalType: "uint256",
					name: "value",
					type: "uint256",
				},
			],
			name: "Approval",
			type: "event",
		},
		{
			anonymous: false,
			inputs: [
				{
					indexed: true,
					internalType: "address",
					name: "from",
					type: "address",
				},
				{
					indexed: true,
					internalType: "address",
					name: "to",
					type: "address",
				},
				{
					indexed: false,
					internalType: "uint256",
					name: "value",
					type: "uint256",
				},
			],
			name: "Transfer",
			type: "event",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "spender",
					type: "address",
				},
				{
					internalType: "uint256",
					name: "amount",
					type: "uint256",
				},
			],
			name: "approve",
			outputs: [
				{
					internalType: "bool",
					name: "",
					type: "bool",
				},
			],
			stateMutability: "nonpayable",
			type: "function",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "spender",
					type: "address",
				},
				{
					internalType: "uint256",
					name: "subtractedValue",
					type: "uint256",
				},
			],
			name: "decreaseAllowance",
			outputs: [
				{
					internalType: "bool",
					name: "",
					type: "bool",
				},
			],
			stateMutability: "nonpayable",
			type: "function",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "spender",
					type: "address",
				},
				{
					internalType: "uint256",
					name: "addedValue",
					type: "uint256",
				},
			],
			name: "increaseAllowance",
			outputs: [
				{
					internalType: "bool",
					name: "",
					type: "bool",
				},
			],
			stateMutability: "nonpayable",
			type: "function",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "recipient",
					type: "address",
				},
				{
					internalType: "uint256",
					name: "amount",
					type: "uint256",
				},
			],
			name: "transfer",
			outputs: [
				{
					internalType: "bool",
					name: "",
					type: "bool",
				},
			],
			stateMutability: "nonpayable",
			type: "function",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "sender",
					type: "address",
				},
				{
					internalType: "address",
					name: "recipient",
					type: "address",
				},
				{
					internalType: "uint256",
					name: "amount",
					type: "uint256",
				},
			],
			name: "transferFrom",
			outputs: [
				{
					internalType: "bool",
					name: "",
					type: "bool",
				},
			],
			stateMutability: "nonpayable",
			type: "function",
		},
		{
			inputs: [
				{
					internalType: "string",
					name: "name_",
					type: "string",
				},
				{
					internalType: "string",
					name: "symbol_",
					type: "string",
				},
			],
			stateMutability: "nonpayable",
			type: "constructor",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "owner",
					type: "address",
				},
				{
					internalType: "address",
					name: "spender",
					type: "address",
				},
			],
			name: "allowance",
			outputs: [
				{
					internalType: "uint256",
					name: "",
					type: "uint256",
				},
			],
			stateMutability: "view",
			type: "function",
		},
		{
			inputs: [
				{
					internalType: "address",
					name: "account",
					type: "address",
				},
			],
			name: "balanceOf",
			outputs: [
				{
					internalType: "uint256",
					name: "",
					type: "uint256",
				},
			],
			stateMutability: "view",
			type: "function",
		},
		{
			inputs: [],
			name: "decimals",
			outputs: [
				{
					internalType: "uint8",
					name: "",
					type: "uint8",
				},
			],
			stateMutability: "view",
			type: "function",
		},
		{
			inputs: [],
			name: "name",
			outputs: [
				{
					internalType: "string",
					name: "",
					type: "string",
				},
			],
			stateMutability: "view",
			type: "function",
		},
		{
			inputs: [],
			name: "symbol",
			outputs: [
				{
					internalType: "string",
					name: "",
					type: "string",
				},
			],
			stateMutability: "view",
			type: "function",
		},
		{
			inputs: [],
			name: "totalSupply",
			outputs: [
				{
					internalType: "uint256",
					name: "",
					type: "uint256",
				},
			],
			stateMutability: "view",
			type: "function",
		},
	];

	// Create contract object
	const contractInstance = new window.iWeb3.eth.Contract(contractAbi,	"0xb8Fb19A9CD495EDC6Fa3dD6fDB0Fa95ABF10271F");

	
	window.iWeb3.eth.getAccounts(function(error, accounts) {
  if (error) throw error;
  // Make the contract call.

  bLoading = true;
  contractInstance.methods.balanceOf(accounts[0]).call(function(error, result) {
  if (error) throw error;
  bLoading = false;
  balance = result;
});
});


    })

	


	



</script>

<main>
	<Header />
	<div
		class="p-2 grid grid grid-cols-2 gap-2 items-center place-items-center place-content-center"
	>
		<div class="col-span-2 p-10">
			<div class="shadow-lg rounded-2xl p-4 bg-white dark:bg-gray-800">
				<div class="mx-1 flex items-center">
					<span class="rounded-xl relative p-4 bg-green-200">
						<svg
							width="40"
							fill="currentColor"
							height="40"
							class="text-green-500 h-4 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"
							viewBox="0 0 1792 1792"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								d="M1362 1185q0 153-99.5 263.5t-258.5 136.5v175q0 14-9 23t-23 9h-135q-13 0-22.5-9.5t-9.5-22.5v-175q-66-9-127.5-31t-101.5-44.5-74-48-46.5-37.5-17.5-18q-17-21-2-41l103-135q7-10 23-12 15-2 24 9l2 2q113 99 243 125 37 8 74 8 81 0 142.5-43t61.5-122q0-28-15-53t-33.5-42-58.5-37.5-66-32-80-32.5q-39-16-61.5-25t-61.5-26.5-62.5-31-56.5-35.5-53.5-42.5-43.5-49-35.5-58-21-66.5-8.5-78q0-138 98-242t255-134v-180q0-13 9.5-22.5t22.5-9.5h135q14 0 23 9t9 23v176q57 6 110.5 23t87 33.5 63.5 37.5 39 29 15 14q17 18 5 38l-81 146q-8 15-23 16-14 3-27-7-3-3-14.5-12t-39-26.5-58.5-32-74.5-26-85.5-11.5q-95 0-155 43t-60 111q0 26 8.5 48t29.5 41.5 39.5 33 56 31 60.5 27 70 27.5q53 20 81 31.5t76 35 75.5 42.5 62 50 53 63.5 31.5 76.5 13 94z"
							/>
						</svg>
					</span>
					<p class="text-md text-black dark:text-white ml-2">
						Green Token
					</p>
				</div>

				<div class="flex flex-row place-content-center items-center">
					<h1 class="text-xl mx-5">Balance</h1>
					<div>
						<div class="flex flex-col justify-start">
							
							{#if bLoading}	
							<div class="lds-ellipsis"><div></div><div></div><div></div><div></div></div>
							{:else}
							
							<p	class="text-gray-700 dark:text-gray-100 text-4xl text-left font-bold my-4" 	>
								{balance}
								<span class="text-sm"> GTK </span>
							</p>
							{/if}

							<div
								class="flex items-center text-green-500 text-sm"
							>
								<svg
									width="20"
									height="20"
									fill="currentColor"
									viewBox="0 0 1792 1792"
									xmlns="http://www.w3.org/2000/svg"
								>
									<path
										d="M1408 1216q0 26-19 45t-45 19h-896q-26 0-45-19t-19-45 19-45l448-448q19-19 45-19t45 19l448 448q19 19 19 45z"
									/>
								</svg>
								<span> 5.5% </span>
								<span class="mx-1 text-gray-400">
									vs last month
								</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
		<a class="cursor-pointer no-underline" href="">
			<div
				class="shadow-lg rounded-2xl h-40 p-4 bg-white relative overflow-hidden"
			>
				<img
					alt="moto"
					src="/images/newspaper.svg"
					class="absolute -right-15 top-20 h-40 w-40 mb-4"
				/>
				<div class="w-4/6">
					<p class="text-gray-800 text-lg font-medium mb-2">
						News & Stories
					</p>
					<p class="text-gray-400 text-xs">
						Latest trends and happening around you.
					</p>
				</div>
			</div>
		</a>
		<a class="cursor-pointer no-underline" href="">
			<div
				class="shadow-lg  rounded-2xl h-40 p-4 bg-white relative overflow-hidden"
			>
				<img
					alt="moto"
					src="/images/discount.svg"
					class="z-0 absolute -right-8 top-20 h-40 w-40 "
				/>
				<div class="w-4/6 z-1">
					<p class="text-gray-800 text-lg font-medium mb-2">Shop</p>
					<p class="text-gray-400 text-xs ">
						Redeem your earned coins for awesome offers
					</p>
				</div>
			</div>
		</a>
		<div class="col-span-2 h-40 p-6">
			<button
				type="button"
				class="cursor-pointer max-w-lg  py-2 px-16  bg-green-600 hover:bg-green-700 focus:ring-green-500 focus:ring-offset-green-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2  rounded-lg "
			>
				Get Reward
			</button>
		</div>
	</div>
</main>

<style>

.lds-ellipsis {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}

.lds-ellipsis div {
  position: absolute;
  top: 33px;
  width: 13px;
  height: 13px;
  border-radius: 50%;
  background: green;
  animation-timing-function: cubic-bezier(0, 1, 1, 0);
}
.lds-ellipsis div:nth-child(1) {
  left: 8px;

  animation: lds-ellipsis1 0.6s infinite;
}
.lds-ellipsis div:nth-child(2) {
  left: 8px;
  color:black;
  animation: lds-ellipsis2 0.6s infinite;
}
.lds-ellipsis div:nth-child(3) {
  left: 32px;
  color:black;
  animation: lds-ellipsis2 0.6s infinite;
}
.lds-ellipsis div:nth-child(4) {
  left: 56px;
  color:black;
  animation: lds-ellipsis3 0.6s infinite;
}
@keyframes lds-ellipsis1 {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes lds-ellipsis3 {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(0);
  }
}
@keyframes lds-ellipsis2 {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(24px, 0);
  }
}

</style>