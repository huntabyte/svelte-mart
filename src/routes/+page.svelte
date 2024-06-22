<script lang="ts">
	import CartItem from './cart-item.svelte';
	import ShoppingCart from 'phosphor-svelte/lib/ShoppingCart';
	import X from 'phosphor-svelte/lib/X';

	let { data } = $props();
</script>

<div class="flex items-center bg-gray-300 p-4">
	<span class="text-lg font-bold">SvelteMart</span>
	<div class="relative ml-auto flex items-center">
		<button class="flex items-center rounded-full bg-sky-600 px-4 py-2 text-white hover:bg-sky-700">
			<ShoppingCart class="mr-2 size-5" />
			<span>Cart (2)</span>
		</button>
		<div class="absolute right-0 top-8 z-10 mt-2 w-80 rounded-lg bg-white shadow-xl">
			<div class="relative p-4">
				<h2 class="mb-4 text-lg font-semibold">Your Cart</h2>
				<button class="absolute right-4 top-4 rounded-full p-1 hover:bg-gray-100">
					<X class="size-4" />
				</button>
				<CartItem />
				<div class="mt-4 border-gray-200 pt-4">
					<p class="text-lg font-semibold">Total: $39.98</p>
				</div>
			</div>
		</div>
	</div>
</div>

<div class="grid grid-cols-1 gap-6 bg-gray-100 p-8 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
	{#each data.products as product}
		<div class="overflow-hidden rounded-xl bg-white shadow-lg">
			<img src={product.thumbnail} alt={product.title} class="h-48 w-full object-cover" />
			<div class="p-4">
				<p class="mb-2 overflow-hidden truncate text-lg font-medium text-gray-800">
					{product.title}
				</p>
				<div class="flex items-center justify-between">
					<p class="text-xl font-bold">${product.price}</p>
					<button
						class="rounded-full bg-sky-600 px-4 py-2 text-white transition-colors duration-300 hover:bg-sky-700"
					>
						Add to cart
					</button>
				</div>
			</div>
		</div>
	{/each}
</div>
