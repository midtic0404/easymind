<script>
	import Header from './Header.svelte';
	import NoteCard from './NoteCard.svelte';
	let description;
	let notes = [];

	function addNotes() {
		if(description === ''){
			return;
		}

		notes = [...notes, description];
		description = '';
	}

	function deleteNote(index) {
		notes = notes.filter((note, idx) => {
			return idx !== index;
		});
	}

	function checkKey(event) {
		if(event.which !== 13){
			return;
		}
		addNotes();	
	}
	
</script>


<style>

</style>



<Header />
<div class="columns is-centered">
  <div class="column is-half">
	<div class="field">
		<label class="label">What is on your mind?</label>
		<div class="control">
			<input 
			class="input" 
			type="text" 
			on:keydown="{checkKey}"
			bind:value="{description}" 
			placeholder="I hate snow!">
		</div>
	</div>
	<div class="field is-grouped">
		<div class="control">
			<button class="button is-primary" on:click={addNotes}>Submit</button>
		</div>
	</div>
  </div>
</div>

<div class="columns is-multiline">
	{#each notes as note, index (index)}
		 <NoteCard 
		 description="{note}"
		 on:delete={deleteNote(index)} />
	{/each}
</div>

