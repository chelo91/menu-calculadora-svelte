<script>
	import { createEventDispatcher } from 'svelte';

	export let product = {
		name: '',
		quantity: 0
	};

    const dispatch = createEventDispatcher();

    function returnProduct() {
		dispatch('submit');
	}

</script>

<div class="col-md-6 m-auto">
	<div class="input-group mb-3">
		<input
			type="text"
			class="form-control"
			placeholder="something to do"
			aria-label="something to do"
			aria-describedby="input_todo"
			id="inputProduct"
			bind:value={product.name} />
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
