<script lang="ts">
	import { Accordion, AccordionItem } from '@skeletonlabs/skeleton';
</script>


<Accordion>
	<AccordionItem open>
		<svelte:fragment slot="summary">Risk Snapshot</svelte:fragment>
		<svelte:fragment slot="content">
			<nav class="list-nav p-2">
				<ul>
					<li><a href="/" >Summary</a></li>
					<li><a href="/about" >Detail</a></li>
				</ul>
			</nav>
	</svelte:fragment>
	</AccordionItem>
	<AccordionItem>
		<svelte:fragment slot="summary">Performance</svelte:fragment>
		<svelte:fragment slot="content">
			<nav class="list-nav p-2">
				<ul>
					<li><a href="/index.html" >DoD</a></li>
					<li><a href="/about" >MtD</a></li>
				</ul>
			</nav>
		</svelte:fragment>
	</AccordionItem>
	<!-- ... -->
</Accordion>
