<script lang="ts">
	import { onMount } from 'svelte';
	import perspective from '@finos/perspective';
	import { assets, base } from '$app/paths';

	import "@finos/perspective-viewer/dist/css/themes.css";

    import type { PerspectiveViewerConfig } from '@finos/perspective-viewer/dist/esm/viewer';

	let table:any = [];

	let perspectiveSvelte: any;
	let viewerModule;
	let dataGrid;
	let d3fc;
	let mounted = false

	export let LAYOUT: PerspectiveViewerConfig;
	export let file: String
	// export let refresh: boolean;

	// $:{console.log(refresh)};

	onMount(async () => {
		dataGrid = await import('@finos/perspective-viewer-datagrid');
		d3fc = await import('@finos/perspective-viewer-d3fc');
		viewerModule = await import('@finos/perspective-viewer');

		let plugin = await perspectiveSvelte.getPlugin('Y Area')
		plugin.max_cells = 10000000;
		plugin.max_columns = 10000000;		

		let WORKER = perspective.worker();
		let REQ = fetch(assets + '/' + file);

		const resp = await REQ;
		const csv = await resp.text();
		table = WORKER.table(csv);
		perspectiveSvelte.load(table);
		perspectiveSvelte.restore(LAYOUT);
		perspectiveSvelte.toggleConfig();
		mounted = true
	});

	$:{
		if(mounted)
		{
		perspectiveSvelte.restore(LAYOUT);
	}
}

</script>

<!-- <div> -->
	<perspective-viewer bind:this={perspectiveSvelte} />
<!-- </div> -->

<style>
	perspective-viewer {
		position: relative;
		min-height: 400px;
		height: 100%;
		bottom: 0px;
		flex:1
}

@media screen and (max-width: 990px) {
	perspective-viewer {
		top: 50px;
		left: 0px;
		right: 0px;
		bottom: 0px;
  }
}

</style>
