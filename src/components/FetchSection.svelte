<script>
    let activity = "";
	let type = false;

    const handleIdeaFetch = () => {
		activity = "Please wait, loading...";
		type = "";
		fetch("https://www.boredapi.com/api/activity/")
		.then(resp => resp.json())
		.then(data => {activity = data.activity; type = data.type})
	};
</script>

<section>
    <h1>Let's fetch some data!</h1>
    <p class="activity">{activity ? activity : "Click and get random activity idea"}</p>
    {#if type}
        <p class="type"><strong>Type:</strong> {type}</p>
    {/if}
    <button on:click={handleIdeaFetch}>What I can do?</button>
</section>

<style>
    .type {
		font-size: 2rem;
	}
</style>