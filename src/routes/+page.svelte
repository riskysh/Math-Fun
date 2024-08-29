<script>
import Header from './Header.svelte'


</script>

<svelte:head>
	<title>Untitled</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<Header />
<section>
	<h1 class="text-white text-center text-7xl font-extrabold mt-28">Tell your story <br>with Illustrations</h1>
	<p class="text-gray-400 text-center text-1xl font-semibold mt-3">Easily share your stunning Illustrations and Digital Art with artists across the globe.<br>
		 Try it! it's kinda fun</p>
	<div class="mt-4 flex w-full items-center justify-center gap-4">
	<button class="text-white bg-[#57F287] px-4 p-3 rounded-lg hover:bg-[#30c45f] transition-all">Get Started</button>
	<button class="text-white border border-[#27272a] px-4 p-3 rounded-lg hover:bg-[#27272a] transition-all">Learn more</button>
	</div>

	
</section>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@100..900&display=swap');

	section {
		font-family: 'Lexend', sans-serif;
	}
</style>

