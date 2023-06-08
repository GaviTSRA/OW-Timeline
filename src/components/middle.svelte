<script>
	import {
		Timeline,
		TimelineItem,
		TimelineSeparator,
		TimelineDot,
		TimelineConnector,
		TimelineContent,
		TimelineOppositeContent
	} from 'svelte-vertical-timeline';
	
	export let item;
</script>

<TimelineItem>
    <TimelineSeparator>
        <TimelineDot style={
            'padding:0;'+
            'width:'+Math.max(0, .5-(item.borderSize))*2+'rem;'+
            'height:'+Math.max(0, .5-(item.borderSize))*2+'rem;'+
            'background-color:'+item.color+';'+
            'border-width:'+(item.borderSize)+'rem;'+
            'border-color: '+item.borderColor} />
    </TimelineSeparator>
    <TimelineContent>
    </TimelineContent>
</TimelineItem>
<p class="middle">{item.content}</p>
<TimelineItem>
    <TimelineSeparator>
        <TimelineDot style={
            'padding:0;'+
            'width:'+Math.max(0, .5-(item.borderSize))*2+'rem;'+
            'height:'+Math.max(0, .5-(item.borderSize))*2+'rem;'+
            'background-color:'+item.color+';'+
            'border-width:'+(item.borderSize)+'rem;'+
            'border-color: '+item.borderColor} />
        <TimelineConnector/>
    </TimelineSeparator>
    <TimelineContent>

    </TimelineContent>
</TimelineItem>

<style>
    .middle {
		color: lightblue;
		font-family: "Cabin";
		font-weight: 500;
		font-size: 3rem;
		display: flex;
		justify-content: center;
		width: 100%;
		margin-top: 0;
	}
</style>