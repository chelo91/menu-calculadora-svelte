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
		if(product.name != "" && product.quantity>1) {
			product.name = product.name.charAt(0).toUpperCase() + product.name.slice(1);
			dispatch('submit');
		}
	}
</script>

<div class="col-md-6 m-auto">

<div class="row">
	<div class="col">
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
	<div class="col">
		<input
		type="number"
		class="form-control"
		placeholder="something to do"
		aria-label="something to do"
		aria-describedby="input_todo"
		id="inputNumber"
		bind:value={product.quantity} />	
		
  </div>
  <div class="col">
	<button class="btn btn-outline-success" type="button" id="addButton"  on:click={returnProduct}>Agregar</button>
</div>
</div>
</div>