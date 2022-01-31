<script>
	export let list;
	console.log(list);
    
</script>

<ul class="list-group list-group-flush" id="things_todo">
	{#each list as pro}
        <li class="list-group-item">
            <div class="row mr-5">
                <div class="col-md-7">
                    <p>{pro.name}</p>
                </div>
                <div class="col-md-3">
                    <p>{pro.quantity}</p>
                </div>
                <div class="col-md-2">
                    <button class="btn btn-outline-danger">Remove</button>
                </div>
            </div>
        </li>
	{/each}
	
</ul>
