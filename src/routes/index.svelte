<script context="module" lang="ts">
	export const prerender = true;
</script>

<script>
	import InputProduct from '$lib/components/InputProduct.svelte';
	import ListProduct from '$lib/components/ListProduct.svelte';
	
	let newProduct = {
		name: '',
		quantity: ''
	};
	let listProduct = new Array();
	
	function handleSubmit() {
		console.log(newProduct);
		let exist = false;
		//alert(`submitted ${newProduct}`);
		listProduct.forEach(function (pro) {
			if (pro.name == newProduct.name && !exist) {		
				pro.quantity = (pro.quantity + newProduct.quantity);
				exist = true;
				console.log(`${newProduct.quantity} + ${pro.quantity}`);
			}
		});
		if (!exist) {
			listProduct.push(newProduct);
		}
		newProduct = {
			name: '',
			quantity: ''
		};
		
		doRerender++;
	}
	
	const forceUpdate = async (_) => {};
	let doRerender = 0;

</script>

<style>
	#col-first, #col-second {
		padding-bottom: 15px;
	}
	#col-second {
		margin-bottom: 75px;
	}

	@media (min-width: 768px) and (max-width: 1199.98px) {
		.container{
		max-width: 960px !important;
	}
	}

</style>

<svelte:head>
<title>Contador de Productos</title>
</svelte:head>

<section>
	<div class="container">
		<div id="col-first" class="col-md-12">
			<!--<h3 class="text-center m-3">To-do List</h3>-->
			<InputProduct bind:product={newProduct} on:submit={handleSubmit} />
			<div class="col-md-3" />
		</div>
		<div id="col-second" class="col-md-12">
			<div class="col-md-7 card m-auto">
				{#await forceUpdate(doRerender) then _}
					<ListProduct bind:list={listProduct} />
				{/await}
			</div>
		</div>
	</div>
</section>
