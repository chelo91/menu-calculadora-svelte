<script>
	import { createEventDispatcher } from 'svelte';
	import Autocomplete, { ListOption } from "./autocomplete/Autocomplete.svelte";
	import {products} from './autocomplete/productData.js'
	export let product = {
		name: '',
		quantity: 0
	};
    const dispatch = createEventDispatcher();
	let myValue = null;

	let open = false;
	const items = products;
	//$: value = "";
	//$: color = "";
	$: colors = items.filter(c => c.includes(product.name));
	const numbers = Array.from({ length: 50 }, (_, i) => i + 1);

    function returnProduct() {
		dispatch('submit');
	}
</script>

<div class="col-md-6 m-auto">
	<div class="input-group mb-3">
		
		<Autocomplete 
		id="cbo-0" 
		name='example-1'
		placeholder="Type a color…"
		bind:value={product.name}
	  >
		{#if colors.length}
		  {#each colors as color (color)}
			<ListOption value={color} />
		  {/each}
		{:else} 
		  <em>No Results…</em>
		{/if}
	  </Autocomplete>
<!--
		<input
			type="text"
			class="form-control"
			placeholder="something to do"
			aria-label="something to do"
			aria-describedby="input_todo"
			id="inputProduct"
			bind:value={product.name} />-->
		<input
			type="number"
			class="form-control"
			placeholder="something to do"
			aria-label="something to do"
			aria-describedby="input_todo"
			id="inputNumber"
			bind:value={product.quantity} />
		<div class="input-group-append">
			<button class="btn btn-outline-success" type="button" id="addButton"  on:click={returnProduct}>Add</button>
		</div>
	</div>
</div>
