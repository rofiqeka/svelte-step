<script context="module">
	/** @type {import('./__types/[slug]').Load} */
	export async function load({ params, fetch, session, stuff }) {
		return {
			props: {
				slug: params.slug
			}
		};
	}
</script>

<script>
	import { goto } from '$app/navigation';
	import Begin from '$lib/components/pages/begin.svelte';
	import Doctor from '$lib/components/pages/doctor.svelte';
	export let slug = 'begin';

	let appointment = {};

	const _paths = {
		begin: { next: 'doctor' },
		doctor: { next: 'date' }
	};

	$: stringify = JSON.stringify(appointment);

	function onNext(values) {
		appointment = { ...appointment, ...values.detail };
		console.log(appointment);

		goto('./' + _paths[slug].next);
	}
</script>

{#if slug === 'begin'}
	<Begin on:submit={onNext} />
{:else if slug === 'doctor'}
	<Doctor on:submit={onNext} />
{/if}
