<script>
	import EventCard from './EventCard.svelte';
	import Button from "$lib/components/ui/button/button.svelte";
    import { goto } from '$app/navigation';
	let dummyDescription="Announcement/Event Description Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla.";
	let events = [
		{ club: "YACC", clublogo: "https://picsum.photos/100", title: "Web Dev BootCamp", description: dummyDescription, time: "10:10 PM", date: "12 March", venue: "Common Room", image: "https://picsum.photos/100/100" },
		{ club: "Shutterbug", clublogo: "https://picsum.photos/200", title: "Photography Workshop", description: dummyDescription, time: "10:10 PM", date: "12 March", venue: "Common Room", image: "https://picsum.photos/200/300" },
		{ club: "Voxel", clublogo: "https://picsum.photos/300", title: "Photoshop Workshop", description: dummyDescription, time: "10:10 PM", date: "12 March", venue: "Common Room", image: "https://picsum.photos/300/300" },
	];
</script>

<div class="main-content">
	<div class="flex justify-between">
		<div class="title">
			LIVE EVENTS
		</div>
		<Button type="button" on:click={() => goto("/dashboard/live_events/create")}>Create Live Events</Button>
	</div>
	{#each events as event}
		<EventCard {...event} />
	{/each}
</div>

<style>
	.main-content {
		flex: 1;
		padding: 20px;
		color: black;
		}
	.title {
		font-family: "Poppins", Helvetica, sans-serif;
		font-weight: 700;
		font-size: 32px;
		line-height: 48px;
		margin-left: 8px;
		margin-bottom: 48px;
		}
</style>
