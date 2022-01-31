<script context="module" lang="ts">
	export const prerender = true;
</script>

<script>
	import InputProduct from '$lib/components/InputProduct.svelte';
	import ListProduct from '$lib/components/ListProduct.svelte';

	let newProduct;
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
		newProduct=new Object();
		doRerender++;
	}

	const forceUpdate = async (_) => {};
	let doRerender = 0;
	/*
// variables
var count = 0;
// targets
var $add_button = $('#add_button');
// when #add_button is clicked
$add_button.on('click', function () {
	// console.log('#add_button was clicked!');
	// targets
	var $user_input = $('#user_input').val().trim();
	var $things_todo_ul = $('#things_todo');
	var $thing = $(`<li class="list-group-item todo_li" id="todo-${count++}">
							<div class="row mr-5">
								<div class="col-md-10">
									<p>${$user_input}</p>
								</div>
								<div class="col-md-2">
									<button class="btn btn-outline-danger remove_button" item="${count}">Remove</button>
								</div>
							</div>
						</li>`);
	$things_todo_ul.append($thing);
	// when .remove_button is clicked
	$('.remove_button').on('click', function() {
		$(this).parents('.todo_li').fadeOut();
	});
});
*/
	// NOTES:

	// 	1. $(this) can be used on targeted jQuery elements.
	// 	2. parents() method traverses the DOM for the targeted parameter
	// 	3. fadeOut() is a cool jQuery function that performs an animation on a targeted element as it is removed from the DOM
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<section>
	<div class="container">
		<div class="col-md-12">
			<h3 class="text-center m-3">To-do List</h3>
			<InputProduct bind:product={newProduct} on:submit={handleSubmit} />
			<div class="col-md-3" />
		</div>
		<div class="col-md-12">
			<div class="col-md-12" />
			<div class="col-md-12">
				<div class="col-md-3" />
				<div class="col-md-6 card m-auto">
					{#await forceUpdate(doRerender) then _}
						<ListProduct bind:list={listProduct} />
					{/await}
				</div>
			</div>
		</div>
	</div>
</section>
