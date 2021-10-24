<script>
    const src = "./favicon.png";
    let name = "";
	let secondName = "";
    let input;

    const handleInputChange = e => {
		name = e.target.value;
	}

    const resetName = () => {
		name = "Unknown";
		input.value="";
	}
</script>

<section>
	<img {src} alt="Svelte logo" />
		<h1>Welcome to TSSAOTP!</h1>
	<p>The Smallest Svelte Application On The Planet</p>
	<h1>Hello {`${name} ${secondName}`}</h1>
	<input type="text" on:input={handleInputChange} value={name} placeholder="Write your name" bind:this={input}/>
	<button on:click={resetName}>Set name to UKNNOWN</button>
</section>

<style>
    img {
	align-self: flex-start;
	width: 8rem;
}

@media (max-width: 600px) {
	img {
		align-self: center;
	}
}

input {
		display: block;
		margin: 0 auto;
		margin-bottom: 20px;
		padding: 7px;
		border-radius: 5px;
		font-size: 1.8rem;
	}

	input:focus {
		border: 1px solid grey;
	}
</style>