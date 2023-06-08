<script>
    import {
		TimelineSeparator,
		TimelineDot,
		TimelineConnector,
	} from 'svelte-vertical-timeline';
    export let item;
    $: height = "height: " + item.displayHeight + "px"
</script>

<TimelineSeparator>
    <TimelineDot style={
        'padding:0;'+
        'width:'+Math.max(0, .5-(item.borderSize))*2+'rem;'+
        'height:'+Math.max(0, .5-(item.borderSize))*2+'rem;'+
        'background-color:'+item.color+';'+
        'border-width:'+(item.borderSize)+'rem;'+
        'border-color: '+item.borderColor} />
    <TimelineConnector style={height}/>
</TimelineSeparator>