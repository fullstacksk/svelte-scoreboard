<script>
    import {createEventDispatcher} from 'svelte'
    let player = {name:'',points:0}
    const dispatch = createEventDispatcher();
    const onSubmit = (e)=>{
        e.preventDefault();
        dispatch('addPlayer',player);
        player = {name:'',points:0}
    }
</script>
<div class="card">
    <div class="card-header ">Add Player</div>
    <div class="card-body">
        <div class="card-text"><form on:submit={onSubmit} >
    <div class="form-group mb-3">
        <label for="playerName">Name</label>
        <input type="text" class="form-control" bind:value={player.name} required>
    </div>
    <div class="form-group mb-3">
        <label for="playerName">Score</label>
        <input type="number" class="form-control" bind:value={player.points} required>
    </div>
      <button type="submit" class="btn btn-primary w-100">Submit</button>

</form>
</div>
    </div>
</div>