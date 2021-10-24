<script>
import { onMount } from 'svelte';

    let infiniteWrapper;

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

<section>
    <h1>Endless Scroll</h1>
    <div class="infinite-wrapper" bind:this={infiniteWrapper}>
    <p>Lorem Ipsum</p>
    </div>
</section>