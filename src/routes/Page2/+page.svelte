<script lang="ts">
	import Perspective from '$lib/Perspective/Perspective.svelte';

	let today = new Date();
	let plugin = 'Y Line'

	let file1 = 'sampledata.csv'
	let file2 = 'sampledata2.csv'

	let newDate = new Date(today.setMonth(today.getMonth() - 12));
	$: datefilter = newDate.toISOString().slice(0, 10);

	let initial_layout = {
			plugin: plugin,
			plugin_config: {
				legend: {
					height: '106px',
					left: '100px',
					top: '25px',
					width: ''
				}
			},
			settings: false,
			group_by: [],
			split_by: [],
			columns: [],
			filter: [],
			sort: [],
			expressions: [],
			aggregates: {}
		};

</script>


<div class="container p-10  h-full bg-white dark:bg-surface-900">

	<flex class="flex">
	<Perspective LAYOUT={initial_layout} file={file1}/>
	<Perspective LAYOUT={initial_layout} file={file2}/>
	<br/>
</flex>

</div>
