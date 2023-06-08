<script>
    export let item;
    export let index;
    $: buttonText = item.closed ? "Expand" : "Collapse"

    function toggle() {
        let timeout;
        if (item.closed) {
            timeout = 300;
            let h = 0;
            for(let i = 0; i < 300; i += 1) {
                setTimeout(() => {
                    h += item.height / 300;
                    item.displayHeight = h;
                    item = item;
                }, 1 * i)
            }
        } else {
            timeout = 0;
            let h = item.height;
            for(let i = 0; i < 300; i += 1) {
                setTimeout(() => {
                    h -= item.height / 300;
                    item.displayHeight = h;
                    item = item;
                }, 500 + i)
            }
        }
        setTimeout(() => {
            item.closed = !item.closed
            item.displayHeight = item.height
            item.toggled = true;
            item = item;
        }, timeout)
    }
</script>

<h3 class="title">{item.title}</h3>
{#if index % 2 != 0}
    <span class="source">{item.source}</span>
    <span class="seperator"> - </span>
    <button class="buttonToggle" on:click={toggle}>{buttonText}</button>
{:else}
    <button class="buttonToggle" on:click={toggle}>{buttonText}</button>
    <span class="seperator"> - </span>
    <span class="source">{item.source}</span>
{/if}

<style>
    .title {
		color: #F08A5D;
		font-family: "Questrial";
		font-size: 3rem;
		margin: 0;
		padding: 0;
		font-weight: 800;
	}
    .source {
        color: rgb(78, 78, 78);
        font-family: "Questrial";
		font-size: 1rem;
		margin: 0;
		padding: 0;
		font-weight: 800;
    }
    .seperator {
        color: green;
        font-family: "Questrial";
		font-size: 1rem;
		margin: 0;
		padding: 0;
		font-weight: 800;
    }
    .buttonToggle {
        color: #F08A5D;
        border: none;
        background:none;
        cursor:pointer;
        text-decoration: underline;
        margin: 0;
        padding: 0;
    }
</style>