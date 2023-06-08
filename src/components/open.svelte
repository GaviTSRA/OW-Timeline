<script>
    import {
		TimelineItem,
		TimelineSeparator,
		TimelineDot,
		TimelineConnector,
		TimelineContent,
		TimelineOppositeContent
	} from 'svelte-vertical-timeline';
    import Title from './title.svelte';
    import { onMount } from 'svelte';
    import Seperator from './seperator.svelte';

    onMount(() => {
        item.displayHeight = item.height
    })

    export let item;
    export let index;
</script>

<TimelineItem>
    <TimelineOppositeContent slot="opposite-content">
        {#if index % 2 == 0}
            <img src={item.image} class="openRight">
        {:else} 
            <Title bind:item={item}/>
            <p class="content">{item.description}</p>
        {/if}
    </TimelineOppositeContent>
    <Seperator item={item}/>
    <TimelineContent>
        {#if index % 2 == 0}
            <Title bind:item={item} index={index}/>
            <p class="content">{item.description}</p>
        {:else} 
            <img src={item.image} class="openLeft"> 
        {/if}
    </TimelineContent>
</TimelineItem>

<style>
    img {
		height: 15rem;
		width: auto;
		border-radius: 10px;
		border-color: #B83B5E;
		border-style: solid;
		border-width: 2px;
	}
    .openRight {
        animation: .3s ease-out 0s 1 openImageR;
    }
    .openLeft {
        animation: .3s ease-out 0s 1 openImageL;
    }
    p {
        animation: .5s ease-out 0s 1 openText;
    }
    @keyframes openImageR {
        0% {
            transform: translateX(50%);
        }
        100% {
            transform: translateX(0);
        }
    }
    @keyframes openImageL {
        0% {
            transform: translateX(-50%);
        }
        100% {
            transform: translateX(0);
        }
    }
    @keyframes openText {
        0% {
            opacity: 0;
            filter:blur(3px)
        }
        100% {
            opacity: 1;
            filter:blur(0px)
        }
    }
</style>