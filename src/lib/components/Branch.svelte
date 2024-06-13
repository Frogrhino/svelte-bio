<script lang="ts">
	import type { Event } from '$lib/types';
	export let event: Event;
	export let orientation: 'left' | 'right';
</script>

<div class="branch">
	<div class="node"></div>
	<div class="line {orientation}"></div>
	<div class="branch-container {orientation}">
		<h3>{event.date}</h3>
		<p>{event.info}</p>
	</div>
</div>

<style>
	@keyframes flyInLeft {
		0% {
			opacity: 0;
			transform: translateX(-50px);
		}
		100% {
			opacity: 1;
			transform: translateX(0);
		}
	}
	@keyframes flyInRight {
		0% {
			opacity: 0;
			transform: translateX(50px);
		}
		100% {
			opacity: 1;
			transform: translateX(0);
		}
	}
	@keyframes appear {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	.branch-container {
		padding: 20px;
		background-color: #f9f9f9;
		border-radius: 6px;
		opacity: 0;
		transition: transform 0.3s ease;
	}

	.branch-container.right {
		margin-left: 55%;
		animation: flyInRight 0.5s forwards ease-out;
	}

	.branch-container.left {
		margin-right: 55%;
		animation: flyInLeft 0.5s forwards ease-out;
	}

	.branch-container:hover {
		transform: scale(1.05);
	}

	.branch-container h3 {
		margin: 0 0 10px;
		font-size: 1.2em;
		color: #333;
	}

	.branch-container p {
		margin: 0;
		font-size: 1em;
		color: #666;
	}

	.node {
		position: absolute;
		width: 26px;
		height: 26px;
		left: 50%;
		margin-left: -17px;
		background-color: white;
		border: 4px solid #ccc;
		border-radius: 50%;
		z-index: 2;
		opacity: 0;
		animation: appear 0.5s forwards ease-out;
		animation-delay: 0.2s;
	}

	.line.right,
	.line.left {
		position: absolute;
		width: 6%;
		height: 2px;
		background-color: #ccc;
		margin-top: 17px;
		opacity: 0;
	}

	.line.left {
		left: calc(44% - 1px);
		animation: flyInLeft 0.5s forwards ease-out;
		animation-delay: 0.4s;
	}

	.line.right {
		left: calc(50% - 1px);
		animation: flyInRight 0.5s forwards ease-out;
		animation-delay: 0.4s;
	}
</style>
