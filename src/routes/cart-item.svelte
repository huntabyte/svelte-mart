<script lang="ts">
	import type { CartProduct } from '$lib/types';
	import Minus from 'phosphor-svelte/lib/Minus';
	import Plus from 'phosphor-svelte/lib/Plus';
	import Trash from 'phosphor-svelte/lib/Trash';

	type Props = {
		cartProduct: CartProduct;
		removeItem: (id: string) => void;
	};

	let { cartProduct = $bindable(), removeItem }: Props = $props();
</script>

<div class="flex items-center justify-between border-b border-gray-200 py-2">
	<div class="flex items-center">
		<img
			src={cartProduct.product.thumbnail}
			alt="Product"
			class="mr-4 size-12 rounded object-cover"
		/>
		<div>
			<p class="font-medium">{cartProduct.product.title}</p>
			<p class="text-sm">${cartProduct.product.price} each</p>
		</div>
	</div>
	<div class="flex items-center">
		<button
			onclick={() => {
				if (cartProduct.quantity === 1) {
					removeItem(cartProduct.id);
				} else {
					cartProduct.quantity--;
				}
			}}
			class="rounded p-1 hover:bg-gray-200"
			aria-label="Subtract 1 from quantity"
		>
			<Minus class="size-4" />
		</button>
		<span class="mx-2">
			{cartProduct.quantity}
		</span>
		<button
			class="rounded p-1 hover:bg-gray-200"
			aria-label="Add 1 to quantity"
			onclick={() => cartProduct.quantity++}
		>
			<Plus class="size-4" />
		</button>
		<button
			onclick={() => removeItem(cartProduct.id)}
			class="ml-4 rounded p-1 text-red-500 hover:bg-red-100"
		>
			<Trash class="size-4" />
		</button>
	</div>
</div>
