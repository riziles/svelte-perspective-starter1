<script lang="ts">
	import Perspective from '$lib/Perspective/Perspective.svelte';
	import { modeCurrent } from '@skeletonlabs/skeleton';
	import { SlideToggle } from '@skeletonlabs/skeleton';

	$: {
		console.log($modeCurrent);
	}

	let conf: false
	let LAYOUT: object;
	let today = new Date();
	let plugin = 'Y Line';

	let file1 = 'sampledata.csv';

	let newDate = new Date(today.setMonth(today.getMonth() - 12));
	$: datefilter = newDate.toISOString().slice(0, 10);

	$: {
		LAYOUT = {
			plugin: plugin,
			plugin_config: {
				legend: {
					height: '106px',
					left: '100px',
					top: '25px',
					width: ''
				}
			},
			settings: conf,
			group_by: [],
			split_by: [],
			columns: [],
			filter: [],
			sort: [],
			expressions: [],
			aggregates: {},
			theme: $modeCurrent ? 'Material Light' : 'Material Dark'
		};
	}
</script>

<div class="container p-10  h-full bg-white dark:bg-surface-900">
	
	<SlideToggle class = "m-0" name="slider-label" size = "sm" bind:checked={conf}>Show Config</SlideToggle>

	<Perspective {LAYOUT} file={file1} />
	<br />

</div>
