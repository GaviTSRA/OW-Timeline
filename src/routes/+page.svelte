<script>
	import { onMount } from 'svelte';
	import {
		Timeline,
		TimelineItem,
		TimelineSeparator,
		TimelineDot,
		TimelineConnector,
		TimelineContent,
		TimelineOppositeContent
	} from 'svelte-vertical-timeline';
    import Middle from '../components/middle.svelte';
    import Closed from '../components/closed.svelte';
    import Open from '../components/open.svelte';
	
	let data = [];

	onMount(async () => {
		const res = await fetch("data.json")
		data = (await res.json()).items
		data.forEach(e => {
			e.closed = true;
			if (!e.height) e.height = 250;
			if (!e.displayHeight) e.displayHeight = e.height
		});
	})
</script>

<!--https://colorhunt.co/palette/f9ed69f08a5db83b5e6a2c70-->
<div id="timeline">
	<Timeline position="left">
		{#each data as item, index}
			{#if item.content}
				<Middle item={item}/>
			{:else}
				{#if item.closed}
					<Closed bind:item={item} index={index}/>
				{:else}
					<Open bind:item={item} index={index}/>
				{/if}
			{/if}
		{/each}
	</Timeline>
</div>

<style>
	:root::-webkit-scrollbar {
		display: none;
	}
	:root {
		-ms-overflow-style: none;
		scrollbar-width: none;
		background-image: url("../../../background.png"); 
		background-repeat: no-repeat;
		background-size: cover;
		background-attachment:fixed;
	}
	#timeline {
		position:absolute;
		width: 75rem;
	}
	:global(.content) {
		color: grey;
		font-family: "Cabin";
		font-weight: 500;
	}
</style>