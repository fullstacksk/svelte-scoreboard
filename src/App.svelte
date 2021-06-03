<script>
	import Player from './Player.svelte'
	import Navbar from './Navbar.svelte'
	import AddPlayer from './AddPlayer.svelte'
import Svelte from './Svelte.svelte'
	 let players = [
		 {name:'M.S. Dhoni', points:123},
		 {name:'K L Rahul', points:97},
		 {name:'Rohit Sharma', points:143},
		 {name:'Virat Kohili', points:113},
	 ]

	 const addPlayer = (e)=>{
		//  e.preventDefault();
		 players = [e.detail, ...players]
	 }

	 const removePlayer = (e)=>{
		//  e.preventDefault();
		 players = players.filter(player => player.name !== e.detail );
	 }
</script>

<main>
	<Navbar />
	<div class="container my-5">
		<div class="row">
			<div class="col-md-4">
				<AddPlayer on:addPlayer={addPlayer} />
			</div>
			<div class="col-md-4">
				
		<div class="d-flex flex-column ">
			{#if players.length ===0 }
			<div class="bg-warning">No Player</div>
			{:else}
			{#each players as player}
				<Player name={player.name} points={player.points} on:removePlayer={removePlayer}/>
			{/each}
		{/if}
		</div>
			</div>
			<div class="col-md-4">
				<Svelte />
			</div>
		</div>
	</div>
</main>

<style>
	
</style>