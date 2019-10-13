<script>
	import Product from './Product.svelte'

	// export let name;
	let title = 'Starting title';
	let price = 0;
	let description = '';

	function setTitle(event) {
		title = event.target.value;
	}
</script>

<style>
	section {
		width: 100%;
		display: flex;
		justify-content: center;
	}
	label, input, textarea {
		width: 100%;
	}
</style>

<p>
	{title}
</p>
<p>
	{price}
</p>
<section>
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
			<textarea name="" id="description " cols="30" rows="3" value={description}></textarea>
		</div>
	</div>
</section>

<Product />
