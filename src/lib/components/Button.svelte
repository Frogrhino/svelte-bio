<script lang="ts">
	export let type: 'button' | 'submit' | 'reset' = 'button';
	export let disabled: boolean = false;
	export let onClick: () => void = () => {};
	export let className: string = '';
	export let label: string = '';
</script>

<button {type} class={`button ${className}`} {disabled} on:click={onClick}>
	<span>{label}</span>
</button>

<style>
	.button {
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 10px 20px;
		min-width: 120px;
		font-size: 16px;
		color: white;
		background-color: #6200ea;
		border: none;
		border-radius: 4px;
		cursor: pointer;
		transition: background-color 0.3s ease;
	}

	.button:hover {
		background-color: #3700b3;
	}

	.button:disabled {
		background-color: #aaa;
		cursor: not-allowed;
	}
</style>
