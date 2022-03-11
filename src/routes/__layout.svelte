<script lang="ts">
	// import { onMount } from 'svelte';

	let isPageLoaded = false;

	const pageLoaded = (_event: HTMLDivElement) => {
		isPageLoaded = true;
	};

	// 이방법도 존재
	// onMount(() => {
	// 	setTimeout(() => {
	// 		isPageLoaded = true;
	// 	}, 3000);
	// });
</script>

{#if !isPageLoaded}
	<div class="loader" use:pageLoaded>
		<img src="static/loader.svg" alt="" />
	</div>
{/if}

<slot />

<style>
	:global(*) {
		background-color: black;
		color: white;
	}
	img {
		width: 200px;
		height: 200px;
	}

	.loader {
		position: fixed;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		display: grid;
		place-items: center;
		background-color: black;
		z-index: 9999;
	}
</style>
