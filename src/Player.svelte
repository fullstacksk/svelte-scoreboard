<script>
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();
	 export let name;
     export let points;
	 let showControl = false;
	 const addPoint = ()=> points += 1;
	 const removePoint = ()=> points -= 1;
	 const handleShow = () => showControl = !showControl;

     const onDelete =()=> dispatch('removePlayer',name);
</script>

		<div class="card mb-3">
			<div class="d-flex justify-content-between card-header">
				<div>{name}</div>
				{#if showControl }
						<div class="btn-group" role="group" aria-label="Basic example">
				<button class="btn btn-sm btn-warning" on:click={handleShow}>-</button>
				<button class="btn btn-sm btn-danger" on:click={onDelete}>x</button>
                        </div>
				
				{:else}
				
						<div class="btn-group" role="group" aria-label="Basic example">
				<button class="btn btn-sm btn-primary" on:click={handleShow}>+</button>
				<button class="btn btn-sm btn-danger" on:click={onDelete}>x</button>
                </div>
				{/if}
			</div>
			<div class="card-body">
				<div class="card-text">
					
					<div class="d-flex justify-content-between mb-3">
						<div>{points}</div>
						{#if showControl}
						<div class="btn-group" role="group" aria-label="Basic example">
							<button type="button" class="btn btn-sm btn-secondary" on:click={addPoint} >+</button>
							<button type="button" class="btn btn-sm btn-warning"  on:click={removePoint}>-</button>
						</div>
						{/if}
					</div>
					{#if showControl}
					<input type="number"  bind:value={points} class="w-100" />
					{/if}
				</div>
			</div>
		</div>
