<script>
    let count = (0);

    const increase = () => {
		count += 1;
	};

	const decrease = () => {
		count -= 1;
	};

	const decreaseBy = x => {
		count -= x;
	};
</script>

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

<style>
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

    .max-wrapper {
		width: 100%;
		max-width: 1200px;
		margin: 0 auto;
	}
</style>