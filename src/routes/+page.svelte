<script>

	// Generates random numbers
	function randomNumber() {
		return Math.floor(Math.random() * 9) + 1
	}

	let firstNum = randomNumber()
	let secondNum = randomNumber()

	// Picks random operator
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

	// Logic to calculate answer
	let correctAnswer;

	function calculateAnswer() {
		console.log("cal",firstNum,secondNum)
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

	// Logic to generate new questions
	function generateQuestion() {
		firstNum = randomNumber();
		secondNum =randomNumber();
		operator = randomOperator();
		correctAnswer = calculateAnswer()
	}

	// Logic to check answer
	let userAnswer = ''
	let feedback = ''

	function checkAnswer() {
		console.log("user",userAnswer)
		console.log("correct",correctAnswer)
		if (userAnswer == correctAnswer) {
			feedback = 'Correct!'
		} if (userAnswer != correctAnswer) {
			feedback = 'Wrong!'
		}
	}

	generateQuestion()

	// Logic to check answer and generate new question
	function handleSubmit() {
		checkAnswer()
		generateQuestion()
	}

	// Manages minimal functionalities
	let inputValue = ''

	function handleInput() {
		userAnswer = inputValue
	}

	$: userAnswer = inputValue

</script>

<svelte:head>
	<title>Math Speedrun</title>
	<meta name="description" content="Math Speedrun" />
</svelte:head>

<main>

	<div class="h-48 w-96 my-14 justify-center flex mx-auto gap-4">
		<h1 class="text-white text-9xl mt-12">{firstNum}</h1>
		<h1 class="text-white text-9xl mt-12">{operator}</h1>
		<h1 class="text-white text-9xl mt-12">{secondNum}</h1>
	</div>
	<div class="flex mx-auto justify-center gap-2">
		<form on:submit|preventDefault={handleInput}>
		<input class="w-80 h-20 bg-[#ffffff12] rounded-xl px-8 text-6xl text-white" 
		placeholder="01" type="text" bind:value={userAnswer}
		on:keydown={(event) => {
			if (event.key === 'Enter') {
				handleSubmit()
			}
		}}
		/>
		</form>
	</div>
	{#if feedback}
		<h1 class="text-white text-2xl text-center mt-4">{feedback}</h1>
	{/if}

</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');

	main {
		font-family: "JetBrains Mono", monospace;
	}
</style>
