<script lang="ts">
	
	import '../theme.postcss';
	import '@skeletonlabs/skeleton/styles/all.css';
	import '../app.postcss';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
	import Navigation from '$lib/Navigation/Navigation.svelte';

	import { LightSwitch } from '@skeletonlabs/skeleton';

let sidebarVisible = ""

	function toggleSidebar(): void {
		sidebarVisible = sidebarVisible === ""?"hidden":""
}

</script>


<!-- App Shell -->
<AppShell slotSidebarLeft="bg-surface-500/5 {sidebarVisible}">
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<div class="flex items-center text-2xl">
						<button class="btn btn-sm mr-4" on:click={toggleSidebar}>
								<span>
										<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
												<rect width="100" height="20" />
												<rect y="30" width="100" height="20" />
												<rect y="60" width="100" height="20" />
										</svg>
								</span>
						</button>
						Data Viewer
				</div>
		</svelte:fragment>
			<svelte:fragment slot="trail">
				
				<LightSwitch  height="h-6" />
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>

	<svelte:fragment slot="sidebarLeft">
    <Navigation />
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
