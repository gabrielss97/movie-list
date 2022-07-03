<script>
    import {goto} from '$app/navigation'
	let inputValue = '';
</script>

<!-- {#if !variavel} {/if} equivalente ao ngIf -->

<form class="search" on:submit|preventDefault={() => goto('/search/' + inputValue)} >
	<input bind:value={inputValue} type="text" placeholder="Search your movie" />
</form>

<style>
	input {
		border: 2px solid transparent;
		background-color: rgb(70, 70, 70);
		color: white;
		padding: 0.6rem;
		border-radius: 0.5rem;
		width: 30vw;
		transform: translateY(-200px);
		animation: dropdown 0.8s ease-out forwards;
		opacity: 0;
	}

	input::placeholder {
		color: rgba(255, 255, 255, 0.627);
	}

	input:focus {
		outline: none;
	}

	@keyframes dropdown {
		to {
			transform: translateY(0);
			opacity: 1;
		}
	}
</style>
