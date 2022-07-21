<script>
	import { createEventDispatcher } from 'svelte';

	let doctor = '';

	const dispatch = createEventDispatcher();

	function onNext() {
		console.log();
		dispatch('submit', { doctor });
	}
</script>

<select name="doctor" id="doctors" bind:value={doctor}>
	<option value="1">Dr. Amelia</option>
	<option value="2">Dr. Wijaya</option>
</select>

<button on:click={onNext}>Pilih Jadwal</button>
