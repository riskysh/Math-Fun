<script>

	function randomNumber() {
		return Math.floor(Math.random() * 9) + 1
	}

	const firstNum = randomNumber()
	const secondNum = randomNumber()

	function randomOperator() {
		const operators = ['+','-','×','÷']
		const randomIndex = Math.floor(Math.random() * operators.length)

		return operators[randomIndex]
	}

	let operator = ''

	function chooseOperator() {
		operator = randomOperator()
	}

	chooseOperator()

	let correctAnswer;

	function calculateAnswer() {
		switch (operator) {
			case '+':
				return firstNum + secondNum
			case '-':
				return firstNum - secondNum
			case '×':
				return firstNum * secondNum
			case '÷':
				return (secondNum !== 0) ? firstNum / secondNum : undefined	
		
			default:
				return null;
		}
	}

	function generateQuestion() {
		firstNum;
		secondNum;
		operator;
		correctAnswer = calculateAnswer()
	}

	let userAnswer;
	let feedback = ''

	function checkAnswer() {
		const userAnswerNumber = parseFloat(userAnswer)
		if (userAnswer == correctAnswer) {
			feedback = 'Correct!'
		} else {
			feedback = 'Try Again'
		}
	}

	generateQuestion()

</script>

<svelte:head>
	<title>Math Fun</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<main>

	<div class="h-48 w-96 my-14 justify-center flex mx-auto gap-4">
		<h1 class="text-white text-9xl mt-12">{firstNum}</h1>
		<h1 class="text-white text-9xl mt-12">{operator}</h1>
		<h1 class="text-white text-9xl mt-12">{secondNum}</h1>
	</div>
	<div class="flex mx-auto justify-center gap-2">
		<input class="w-80 h-20 bg-[#ffffff12] rounded-xl px-8 text-6xl text-white" 
		placeholder="01" bind:value={userAnswer} />
		<button class="h-20 w-28 rounded-lg bg-green-500" on:click={checkAnswer}>Button</button>
	</div>
	{#if feedback}
		<h1 class="text-white text-4xl text-center mt-4">{feedback}</h1>
	{/if}

</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');

	main {
		font-family: "JetBrains Mono", monospace;
	}
</style>
