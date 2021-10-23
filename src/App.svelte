

<script>
import { onMount } from 'svelte';

let infiniteWrapper;
const src = "./favicon.png";
	let name = "";
	let secondName = "";
	let count = (0);
	let activity = "";
	let type = false;

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

	const handleIdeaFetch = () => {
		activity = "Please wait, loading...";
		type = "";
		fetch("http://www.boredapi.com/api/activity/")
		.then(resp => resp.json())
		.then(data => {activity = data.activity; type = data.type})
	};

	const getContent = () => {
		let i = 0;
		while (i < 25) {
			const paragraph = document.createElement("p");
			paragraph.innerText = "Lorem ipsum dolor sit amet.";
			console.log(infiniteWrapper);
			infiniteWrapper.append(paragraph);
			i ++;
		};
	};

	onMount(()=> {
		getContent();
		window.addEventListener("scroll", ()=>{
			if (window.scrollY + window.innerHeight >= document.documentElement.scrollHeight) {
				getContent();
			}
		})
	});

</script>

<main>
	<section>
	<img {src} alt="Svelte logo" />
		<h1>Welcome to TSSAOTP!</h1>
	<p>The Smallest Svelte Application On The Planet</p>
	<h1>Hello {`${name} ${secondName}`}</h1>
	<input type="text" on:input={handleInputChange} value={name} placeholder="Write your name"/>
	<button on:click={resetName}>Set name to UKNNOWN</button>
	</section>

	<section>
	<p>Counter: {count}</p>
	
	<div class="actions">
		<button on:click={increase}>INCERASE</button>
		<button on:click={decrease}>DECREASE</button>
		<button on:click={() => {
			decreaseBy(3);
		}}>DECREASE BY 3</button>
		
	</div>
	</section>
	<section>
		<h1>Let's fetch some data!</h1>
		<p class="activity">{activity ? activity : "Click and get random activity idea"}</p>
		{#if type}
			<p class="type"><strong>Type:</strong> {type}</p>
		{/if}
		<button on:click={handleIdeaFetch}>What I can do?</button>
	</section>
	<section>
		<h1>Endless Scroll</h1>
		<div class="infinite-wrapper" bind:this={infiniteWrapper}>
		<p>Lorem Ipsum</p>
		</div>
	</section>
</main>

<style>

html {
	font-size: 62.5%;
}

* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

section {
	display: flex;
	justify-content: center;
	flex-direction: column;
}

img {
	align-self: flex-start;
	width: 80px;
}

	h1 {
		font-size: 45px;
		text-align: center;
		margin-bottom: 20px;
		color: #ACACAC;
	}	

	p, .infinite-wrapper > p {
		font-size: 26px;
		text-align: center;
		color: #97c2b6;
		margin-bottom: 24px;
	}

	input {
		display: block;
		margin: 0 auto;
		margin-bottom: 20px;
		padding: 7px;
		border-radius: 5px;
	}

	input:focus {
		border: 1px solid grey;
	}

	button {
		width: 220px;
		max-width: 90%;
		margin: 0 auto;
		padding: 7px;
		border-radius: 8px;
		background: #d4d4d4;
		transition: background 0.3s;
	}

	button:hover {
		background: #CECBCB;
		cursor: pointer;
	}

	.actions {
		display: flex;
		justify-content: space-around;
	}

	section {
		padding-bottom: 50px;
	}

	section:nth-child(2n) {
		background: #F5F5F5;
		padding-top: 30px;
	}

	section:nth-child(2) p {
		color: #7fa69b;
		font-size: 29px;
		font-weight: bold;
	}

	section:nth-child(3) {
		padding-top: 40px;
	}

	.type {
		font-size: 20px;
	}


</style>