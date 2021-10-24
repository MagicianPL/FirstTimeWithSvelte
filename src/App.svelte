

<script>
import { onMount } from 'svelte';
import HelloSection from "./components/HelloSection.svelte";
import CounterSection from "./components/CounterSection.svelte";

let infiniteWrapper;


	
	
	let activity = "";
	let type = false;

	

	

	

	

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
	<HelloSection />
	<CounterSection />

	
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

:global(section) {
	display: flex;
	justify-content: center;
	flex-direction: column;
	padding: 8px;
	padding-bottom: 50px;
	min-height: 50vh;
}

@media (max-width: 400px) {
	:global(section) {
		justify-content: flex-start;
		padding-top: 20px;
	}
}

	:global(h1) {
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

	

	:global(button) {
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

	:global(button:hover) {
		background: #CECBCB;
		cursor: pointer;
	}


	:global(section:nth-child(2n)) {
		background: #F5F5F5;
		padding-top: 30px;
	}

	@media (max-width: 400px) {
		:global(section:nth-child(2n)) {
			padding-top: 40px;
		}
	}

	:global(section:nth-child(2) p) {
		color: #7fa69b;
		font-size: 2.9rem;
		font-weight: bold;
	}

	:global(section:nth-child(3)) {
		padding-top: 40px;
	}

	.type {
		font-size: 2rem;
	}

	


</style>