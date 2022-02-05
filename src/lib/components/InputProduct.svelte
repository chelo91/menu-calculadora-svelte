<script>
	import { createEventDispatcher } from 'svelte';
	import Autocomplete, { ListOption } from "./autocomplete/Autocomplete.svelte";
	import {products} from './autocomplete/productData.js'
	export let product;
	const dispatch = createEventDispatcher();
	let myValue = null;
	
	let open = false;
	const items = products;
	//$: value = "";
	//$: color = "";
	$: colors = items.filter(c => c.includes(product.name));
	const numbers = Array.from({ length: 50 }, (_, i) => i + 1);
	
	function returnProduct() {
		if(product.name != "" && product.quantity>0) {
			product.name = product.name.charAt(0).toUpperCase() + product.name.slice(1);
			dispatch('submit');
		}
	}
</script>

<style>
	#addButton {
		width: 100%;
	}
	.col{
		margin-bottom: 15px;
	}
</style>

<div class="col-md-6 m-auto">

<div class="row">
	<div class="col col-7 col-sm-6">
		<Autocomplete 
		id="cbo-0" 
		name='example-1'
		placeholder="Ingrese el producto"
		bind:value={product.name}
		>
			{#if colors.length}
				{#each colors as color (color)}
					<ListOption value={color} />
				{/each}
			{:else} 
				<em>Sin resultados...</em>
			{/if}
		</Autocomplete>	
	</div>
	<div class="col col-5 col-sm-3">
		<input
		type="number"
		class="form-control"
		placeholder="Cantidad"
		aria-label="Cantidad"
		id="inputNumber"
		bind:value={product.quantity} />	
		
  </div>
  <div class="col col-12 col-sm-3">
	<button class="btn btn-outline-success" type="button" id="addButton"  on:click={returnProduct}>Agregar</button>
</div>
</div>
</div>
