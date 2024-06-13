<script>
	import Timeline from '$lib/components/Timeline.svelte';

	const events = [
		{
			date: 'January 1, 2020',
			info: 'Started learning Svelte',
			imgSrc: '',
			header: 'Learning Svelte'
		},
		{
			date: 'April 15, 2020',
			info: 'Built first Svelte app',
			imgSrc: '',
			header: 'First Svelte App'
		},
		{
			date: 'July 7, 2020',
			info: 'Started contributing to open source',
			imgSrc: '',
			header: 'Contributing to Open Source'
		},
		{
			date: 'May 20, 2021',
			info: 'Released a Svelte library',
			imgSrc: '',
			header: 'Svelte Library Release'
		},
		{
			date: 'June 17, 2022',
			info: 'Completed a Svelte course',
			imgSrc: '',
			header: 'Svelte Course Completion'
		},
		{
			date: 'September 3, 2022',
			info: 'Contributed to Svelte documentation',
			imgSrc: '',
			header: 'Svelte Documentation Contribution'
		},
		{
			date: 'August 8, 2021',
			info: 'Spoke at a Svelte conference',
			imgSrc: '',
			header: 'Svelte Conference Talk'
		},
		{
			date: 'November 11, 2021',
			info: 'Published a Svelte tutorial',
			imgSrc: '',
			header: 'Svelte Tutorial Publication'
		},
		{
			date: 'March 30, 2022',
			info: 'Started a Svelte project',
			imgSrc: '',
			header: 'Svelte Project Start'
		},
		{
			date: 'December 25, 2020',
			info: 'Landed a job as a Svelte developer',
			imgSrc: '',
			header: 'Job as Svelte Developer'
		},
		{
			date: 'February 12, 2021',
			info: 'Joined a Svelte community',
			imgSrc: '',
			header: 'Joining Svelte Community'
		},
		{
			date: 'December 12, 2022',
			info: 'Launched a Svelte-based startup',
			imgSrc: '',
			header: 'Svelte Startup Launch'
		}
	];
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<Timeline {events} />
</section>

<style>
</style>
