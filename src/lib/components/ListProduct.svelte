<script>
	export let list;   
    function removeProduct(index){
        list.splice(index, 1);
        list=list;
    }
</script>
<style>
    #btnRemove{
        width: 100%;
    }
</style>

<ul class="list-group list-group-flush" id="things_todo">
	{#each list as pro,index}
        <li class="list-group-item">
            <div class="row mr-5">
                <div class="col col-7 col-sm-6">
                    <p>{pro.name}</p>
                </div>
                <div class="col col-5 col-sm-3">
                    <p>{pro.quantity}</p>
                </div>
                <div class="col col-12 col-sm-3">
                    <button id='btnRemove' on:click={()=>removeProduct(index)} class="btn btn-outline-danger">Eliminar</button>
                </div>
            </div>
        </li>
	{/each}
	
</ul>
