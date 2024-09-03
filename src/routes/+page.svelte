<script>

	function randomSingleDigit() {
		return Math.floor(Math.random() * 9) + 1
	}

	const firstNum = randomSingleDigit()
	const secondNum = randomSingleDigit()

</script>

<svelte:head>
	<title>Math Fun</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<main>

	<div class="h-80 w-72 flex mx-auto my-40">
		<h1 class="text-white text-9xl ml-36 h-2 w-2">{firstNum}</h1>
		<h1 class="text-white text-9xl mt-32 mr-24 h-2 w-2">{secondNum}</h1>
	</div>

</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');

	main {
		font-family: "JetBrains Mono", monospace;
	}
</style>
