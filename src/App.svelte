<script>
import HelloSection from "./components/HelloSection.svelte";
import CounterSection from "./components/CounterSection.svelte";
import FetchSection from "./components/FetchSection.svelte";
import EndlessScrollSection from "./components/EndlessScrollSection.svelte";
</script>

<main>
	<HelloSection />
	<CounterSection />
	<FetchSection />
	<EndlessScrollSection />	
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
</style>