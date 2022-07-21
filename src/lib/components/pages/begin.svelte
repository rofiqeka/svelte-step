<script>
	import { createEventDispatcher } from 'svelte';

	let hospital = '';
	let specialty = '';

	const dispatch = createEventDispatcher();

	function onNext() {
		dispatch('submit', { hospital, specialty });
	}
</script>

<select name="hospital" id="hospitals" bind:value={hospital}>
	<option value="BSD">BSD</option>
	<option value="CBB">Cibubur</option>
</select>

<select name="specialty" id="specialties" bind:value={specialty}>
	<option value="ortho">Orthopedy</option>
	<option value="obgyn">Kandungan</option>
</select>

<button on:click={onNext}>Submit</button>
