<script lang="ts">
	import { Accordion, AccordionItem } from '@skeletonlabs/skeleton';
</script>


<Accordion>
	<AccordionItem open>
		<svelte:fragment slot="summary">Tables</svelte:fragment>
		<svelte:fragment slot="content">
			<nav class="list-nav p-2">
				<ul>
					<li><a href="/" >1 Table</a></li>
					<li><a href="/Page2" >2 Tables</a></li>
				</ul>
			</nav>
	</svelte:fragment>
	</AccordionItem>
	<AccordionItem>
		<svelte:fragment slot="summary">Other</svelte:fragment>
		<svelte:fragment slot="content">
			<nav class="list-nav p-2">
				<ul>
					<li><a href="/Page3" >Credits</a></li>
					<li><a href="/Page4" >More</a></li>
				</ul>
			</nav>
		</svelte:fragment>
	</AccordionItem>
	<!-- ... -->
</Accordion>
