<script>
	export let list;   
    function removeProduct(index){
        list.splice(index, 1);
        list=list;
    }
</script>

<ul class="list-group list-group-flush" id="things_todo">
	{#each list as pro,index}
        <li class="list-group-item">
            <div class="row mr-5">
                <div class="col-md-7">
                    <p>{pro.name}</p>
                </div>
                <div class="col-md-3">
                    <p>{pro.quantity}</p>
                </div>
                <div class="col-md-2">
                    <button on:click={()=>removeProduct(index)} class="btn btn-outline-danger">Eliminar</button>
                </div>
            </div>
        </li>
	{/each}
	
</ul>
