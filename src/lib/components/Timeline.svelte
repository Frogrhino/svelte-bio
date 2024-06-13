<script lang="ts">
	import { onMount } from 'svelte';
	import Branch from './Branch.svelte';
	import type { Event } from '$lib/types';
	import Button from './Button.svelte';

	export let events: Event[] = [];
	let orderTimeline = 'asc';

	function getTimeDifference(event1: any, event2: any) {
		const date1: any = new Date(event1.date);
		const date2: any = new Date(event2.date);
		return Math.abs(date2 - date1);
	}

	function sortEvents() {
		events = [...events].sort((a, b) => {
			const dateA = new Date(a.date);
			const dateB = new Date(b.date);
			if (orderTimeline === 'asc') {
				return dateA.getTime() - dateB.getTime();
			} else if (orderTimeline === 'desc') {
				return dateB.getTime() - dateA.getTime();
			} else {
				throw new Error('Invalid sort order. Use "asc" or "desc".');
			}
		});
		orderTimeline = orderTimeline === 'asc' ? 'desc' : 'asc';
	}

	function isElementInViewport(el: Element) {
		const rect = el.getBoundingClientRect();
		return (
			rect.top >= 0 && rect.bottom <= (window.innerHeight || document.documentElement.clientHeight)
		);
	}

	onMount(() => {
		sortEvents();
		window.addEventListener('scroll', () => {
			const branches = document.querySelectorAll('.branch');
			branches.forEach((branch) => {
				if (isElementInViewport(branch)) {
					branch.classList.add('animate');
				}
			});
		});
	});
</script>

<Button onClick={sortEvents} className="sortButton" label="Sort {orderTimeline}" />

<div class="timeline">
	{#each events as event, index}
		<div
			class="timeline-event"
			style={index > 0
				? `margin-top: ${getTimeDifference(events[index - 1], event) / (1000 * 60 * 60 * 24)}px`
				: ''}
		>
			{#if index % 2 === 0}
				<Branch {event} orientation="left" />
			{:else}
				<Branch {event} orientation="right" />
			{/if}
		</div>
	{/each}
</div>

<style>
	.timeline {
		position: relative;
		padding: 20px 0;
		width: 100%;
		margin: auto;
	}

	.timeline::before {
		content: '';
		position: absolute;
		width: 6px;
		background-color: #ccc;
		top: 0;
		bottom: 0;
		left: 50%;
		margin-left: -3px;
		border-radius: 5px;
		z-index: 0;
	}
</style>
