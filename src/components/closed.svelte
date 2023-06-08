<script>
    import {
		TimelineItem,
		TimelineContent,
		TimelineOppositeContent
	} from 'svelte-vertical-timeline';
    import Title from './title.svelte';
    import { onMount } from 'svelte';
    import Seperator from './seperator.svelte';

    export let item;
    export let index;
    $: height = "height: " + item.displayHeight + "px"
    onMount(() => {
        if (!item.toggled) {
            item.displayHeight = 0;
        }
        setTimeout(() => {
            document.getElementById(index+"content").remove()
            document.getElementById(index+"img").remove()
        }, 400)
    })
</script>

<TimelineItem>
    <TimelineOppositeContent slot="opposite-content">
        {#if index % 2 != 0}
            <Title bind:item={item} index={index}/>
            {#if item.toggled}
                <p class="content" id={index+"content"}>{item.description}</p>
            {/if}
        {:else} 
            {#if item.toggled}
                <img src={item.image} id={index+"img"} class="closeRight"> 
            {/if}
        {/if}
    </TimelineOppositeContent>
    <Seperator item={item}/>
    <TimelineContent>
        {#if index % 2 == 0}
            <Title bind:item={item} index={index}/>
            {#if item.toggled}
                <p class="content" id={index+"content"}>{item.description}</p>
            {/if}
        {:else} 
            {#if item.toggled}
                <img src={item.image} id={index+"img"} class="closeLeft"> 
            {/if}
        {/if}
    </TimelineContent>
</TimelineItem>

<style>
    p {
        animation: .5s ease-out 0s 1 closeText;
    }
    .closeRight {
        animation: .5s ease-out 0s 1 closeImageR;
    }
    .closeLeft {
        animation: .5s ease-out 0s 1 closeImageL;
    }
    img {
		height: 15rem;
		width: auto;
		border-radius: 10px;
		border-color: #B83B5E;
		border-style: solid;
		border-width: 2px;
	}
    @keyframes closeText {
        0% {
            opacity: 1;
            filter:blur(0px)
        }
        100% {
            opacity: 0;
            filter:blur(3px)
        }
    }
    @keyframes closeImageR {
        0% {
            transform: translateX(0);
        }
        100% {
            transform: translateX(200%);
        }
    }
    @keyframes closeImageL {
        0% {
            transform: translateX(0);
        }
        100% {
            transform: translateX(-200%);
        }
    }
</style>