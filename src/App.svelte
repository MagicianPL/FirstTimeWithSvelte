<script>
	const src = "./favicon.png";
	let name = "";
	let secondName = "";
	let count = (0);

	const increase = () => {
		count += 1;
	};

	const decrease = () => {
		count -= 1;
	};

	const decreaseBy = x => {
		count -= x;
	}

	const handleInputChange = e => {
		name = e.target.value;
	}

	const handleSecondInputChange = e => {
		secondName = e.target.value;
	}

	const resetName = () => {
		name = "Unknown";
		input.value="";
	}

</script>

<main>
	<img {src} alt="Svelte logo" />
		<h1>Welcome to TSSAOTP!</h1>
	<p>The Smallest Svelte Application On The Planet</p>
	<h1>Hello {`${name} ${secondName}`}</h1>
	<input type="text" on:input={handleInputChange} value={name}/>
	<input type="text" on:input={handleSecondInputChange} value={secondName}/>
	<p>Counter: {count}</p>
	<div class="actions">
		<button on:click={increase}>INCERASE</button>
		<button>DECREASE</button>
		<button on:click={() => {
			decreaseBy(3);
		}}>DIVIDING BY 3</button>
		<button on:click={resetName}>Set name to UKNNOWN</button>
	</div>
</main>

<style>
	h1 {
		font-size: 45px;
		text-align: center;
		margin-bottom: 28px;
		color: rgb(220,220,220);
	}	

	p {
		font-size: 26px;
		fot-weight: bold;
		text-align: center;
		color: rgb(220,220,220);
	}

	input {
		display: block;
		margin: 0 auto;
	}

	.actions {
		display: flex;
		justify-content: space-around;
	}


</style>