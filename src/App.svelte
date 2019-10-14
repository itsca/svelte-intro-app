<script>
	import Button from './Button.svelte';
	import Product from './Product.svelte';
	import Cart from './Cart.svelte';

	// export let name;
	let title = 'Starting title';
	let price = 0;
	let description = '';

	let products = [];
	let cartItems = [];

	function setTitle(event) {
		title = event.target.value;
	}
	
	function createProduct(values) {
		const newProduct = {
			title,
			price,
			description
		};	

		products = products.concat(newProduct)
	}

	function addToCart(event) {
		const selectedTitle =  event.detail;
		cartItems = cartItems.concat({
			...products.find(prod => prod.title === selectedTitle)
			});
			console.log(cartItems);
	}
</script>

<style>
	section {
		width: 50%;
		margin: 0 auto;
	}
	.inputs {
		width: 100%;
		display: flex;
		justify-content: center;
	}
	label, input, textarea {
		width: 100%;
	}
</style>

<section>
	<Cart items={cartItems} />
</section>

<hr>

<section class="inputs">
	<div>
		<div>
			<label for="title">Title</label>
			<input type="text" it="title" value={title} on:input={setTitle} >
		</div>
		<div>
			<label for="price">Price</label>
			<input type="number" id="price" value={price} bind:value={price} >
		</div>
		<div>
			<label for="description">Description</label>
			<textarea name="" id="description " cols="30" rows="3" bind:value={description}></textarea>
		</div>
		<Button on:click={createProduct}>
			Create Product
		</Button>
	</div>
</section>

<section>
	{#if products.lenght === 0}
		<p>No products were added yet!</p>
		{:else}
			{#each products as product }
				<Product 
					productTitle={product.title}
					productPrice={product.price}
					productDescription={product.description}
					on:addcart={addToCart}
				/>
			{/each}
	{/if}
</section>


