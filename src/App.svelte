

<script>
import { onMount } from 'svelte';

let infiniteWrapper;
let input;
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
		fetch("https://www.boredapi.com/api/activity/")
		.then(resp => resp.json())
		.then(data => {activity = data.activity; type = data.type})
	};

	const getContent = () => {
		let i = 0;
		while (i < 25) {
			const paragraph = document.createElement("p");
			paragraph.innerText = "Lorem ipsum dolor sit amet.";
			
			infiniteWrapper.append(paragraph);
			i ++;
		};
	};

	onMount(()=> {
		getContent();
		window.addEventListener("scroll", ()=>{
			if (window.scrollY + window.innerHeight >= document.documentElement.scrollHeight - 100) {
				
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
	<input type="text" on:input={handleInputChange} value={name} placeholder="Write your name" bind:this={input}/>
	<button on:click={resetName}>Set name to UKNNOWN</button>
	</section>

	<section>
<div class="max-wrapper">
	<p>Counter: {count}</p>
	
	<div class="actions">
		<button on:click={increase}>INCERASE</button>
		<button on:click={decrease}>DECREASE</button>
		<button on:click={() => {
			decreaseBy(3);
		}}>DECREASE BY 3</button>
		
	</div>
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

section {
	display: flex;
	justify-content: center;
	flex-direction: column;
	padding: 8px;
}

@media (max-width: 400px) {
	section {
		justify-content: flex-start;
		padding-top: 20px;
	}
}

img {
	align-self: flex-start;
	width: 8rem;
}

@media (max-width: 600px) {
	img {
		align-self: center;
	}
}

	h1 {
		font-size: 5.5rem;
		text-align: center;
		margin-bottom: 2rem;
		color: #ACACAC;
	}	

	:global(p) {
		font-size: 2.6rem;
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
		font-size: 1.8rem;
	}

	input:focus {
		border: 1px solid grey;
	}

	button {
		width: 28rem;
		max-width: 90%;
		margin: 0 auto;
		padding: 7px;
		border-radius: 8px;
		background: #d4d4d4;
		transition: background 0.3s;
		font-size: 2rem;
		margin-bottom: 18px;
	}

	button:hover {
		background: #CECBCB;
		cursor: pointer;
	}

	.actions {
		display: flex;
		justify-content: space-around;
	}

	@media (max-width: 900px) {
		.actions {
			flex-direction: column;
			align-items: center;
		}
	}

	section {
		padding-bottom: 50px;
		min-height: 50vh;
	}

	section:nth-child(2n) {
		background: #F5F5F5;
		padding-top: 30px;
	}

	@media (max-width: 400px) {
		section:nth-child(2n) {
			padding-top: 40px;
		}
	}

	section:nth-child(2) p {
		color: #7fa69b;
		font-size: 2.9rem;
		font-weight: bold;
	}

	section:nth-child(3) {
		padding-top: 40px;
	}

	.type {
		font-size: 2rem;
	}

	.max-wrapper {
		width: 100%;
		max-width: 1200px;
		margin: 0 auto;
	}


</style>