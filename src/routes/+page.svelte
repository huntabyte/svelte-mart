<script lang="ts">
	import CartItem from './cart-item.svelte';
	import ShoppingCart from 'phosphor-svelte/lib/ShoppingCart';
	import X from 'phosphor-svelte/lib/X';

	let { data } = $props();
</script>

<div class="p-4 flex items-center">
	<span class="font-bold text-lg">SvelteMart</span>
	<div class="relative flex items-center ml-auto">
		<button class="flex items-center bg-sky-600 px-4 py-2 rounded-full hover:bg-sky-700 text-white">
			<ShoppingCart class="size-5 mr-2" />
			<span>Cart (2)</span>
		</button>
		<div class="absolute right-0 top-8 mt-2 w-80 bg-white rounded-lg shadow-xl z-10">
			<div class="p-4 relative">
				<h2 class="text-lg font-semibold mb-4">Your Cart</h2>
				<button class="absolute top-4 right-4 hover:bg-gray-100 p-1 rounded-full">
					<X class="size-4" />
				</button>
				<CartItem />
				<div class="mt-4 pt-4 border-gray-200">
					<p class="text-lg font-semibold">Total: $39.98</p>
				</div>
			</div>
		</div>
	</div>
</div>

<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 p-8 bg-gray-100">
	{#each data.products as product}
		<div class="bg-white rounded-xl shadow-lg overflow-hidden">
			<img src={product.thumbnail} alt={product.title} class="w-full h-48 object-cover" />
			<div class="p-4">
				<p class="text-lg font-medium text-gray-800 mb-2 overflow-hidden truncate">
					{product.title}
				</p>
				<div class="flex items-center justify-between">
					<p class="text-xl font-bold">${product.price}</p>
					<button
						class="bg-sky-600 px-4 py-2 rounded-full hover:bg-sky-700 transition-colors duration-300 text-white"
					>
						Add to cart
					</button>
				</div>
			</div>
		</div>
	{/each}
</div>
