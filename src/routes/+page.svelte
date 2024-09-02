<script>

	import { onMount, onDestroy } from "svelte";
	let timer;
	let seconds = 0
	let isRunning = false

	function startTimer() {
		if (!isRunning) {
			timer = setInterval(() => {
				seconds++
			}, 1000)
			isRunning = true
		}
	}

	function stopTimer() {
		if (isRunning) {
			clearInterval(timer)
			isRunning = false
		}
	}

	onMount(() => {
		startTimer()
	})

	onDestroy(() => {
		stopTimer()
	})





</script>

<svelte:head>
	<title>Math Fun</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<main>

	<h2 class="text-xl mt-4 text-white text-center">{seconds} Seconds</h2>
	<div class="mx-auto mt-80 justify-center flex grid-cols-2 gap-2">
	<button class="px-4 py-2 bg-white rounded-lg" on:click={startTimer} disabled={isRunning}>Start</button>
	<button class="px-4 py-2 bg-white rounded-lg" on:click={stopTimer} disabled={!isRunning}>Stop</button>
	</div>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');

	main {
		font-family: "JetBrains Mono", monospace;
	}
</style>
