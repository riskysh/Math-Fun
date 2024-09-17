<script>
    import { onMount } from "svelte";

    let firstNum = 0;
    let secondNum = 0;
    let operator = 0;
    let correctAnswer = 0;
    let feedback = "";
    let inputValue = "";

    // Generates random numbers
    function randomNumber() {
        return Math.floor(Math.random() * 9) + 1;
    }

    // Picks random operator
    function randomOperator() {
        const operators = ["+", "-", "×", "÷"];
        const randomIndex = Math.floor(Math.random() * operators.length);

        return operators[randomIndex];
    }

    // Logic to calculate answer
    function calculateAnswer() {
        switch (operator) {
            case "+":
                return firstNum + secondNum;
            case "-":
                return firstNum - secondNum;
            case "×":
                return firstNum * secondNum;
            case "÷":
                return firstNum / secondNum;
        }
    }

    // Logic to generate new questions
    function generateQuestion() {
        firstNum = randomNumber();
        secondNum = randomNumber();
        operator = randomOperator();
        correctAnswer = calculateAnswer();
    }

    // Logic to check answer
    function checkAnswer() {
        feedback = inputValue == correctAnswer ? "Correct!" : "Wrong!";
    }

    // Logic to check answer and generate new question
    function handleSubmit() {
        checkAnswer();
        generateQuestion();
        inputValue = "";
    }

    let mounted = false;
    onMount(() => {
        generateQuestion();
        mounted = true;
    });

    // Timer

    let seconds = 0
    let timer = null

    function startTimer() {
        if (timer === null) {
            timer = setInterval(() => {
                seconds += 1
            }, 1000)
        }
    }

    function stopTimer() {
        if (timer !== null) {
            clearInterval(timer)
            timer = null
            seconds = 0
        }
    }

    let buttonState = "Start";

    function togggleButton () {
        buttonState = buttonState === 'Start' ? 'Stop' : 'Start'
    }

    function startAndToggle() {
        startTimer()
        togggleButton()
    }

    function stopAndToggle() {
        stopTimer()
        togggleButton() 
    }
    
    

</script>

<svelte:head>
    <title>Math Speedrun</title>
    <meta name="description" content="Math Speedrun" />
</svelte:head>

{#if mounted}
    <main>
        <div class="flex justify-center h-48 gap-4 mx-auto w-96 my-14">
            <h1 class="mt-12 text-white text-9xl">{firstNum}</h1>
            <h1 class="mt-12 text-white text-9xl">{operator}</h1>
            <h1 class="mt-12 text-white text-9xl">{secondNum}</h1>
        </div>
        <div class="flex w-full justify-center gap-1 mx-auto">
            <form on:submit|preventDefault={startTimer}>
                <input
                    class="w-80 h-20 bg-[#ffffff12] rounded-xl px-8 text-6xl text-white"
                    placeholder="01"
                    type="text"
                    bind:value={inputValue}
                    on:keydown={(event) => {
                        event.key === "Enter" && handleSubmit();
                    }}
                />
            </form>
        </div>
        <h1 class="mt-4 text-2xl text-center text-white">
            {feedback ? feedback : ""}
        </h1>
        <h1 class="mt-4 text-2xl text-center text-white">
            {seconds}
        </h1>
        <div class="flex justify-center mx-auto mt-32">
            {#if buttonState === 'Start'}
            <button on:click={startAndToggle} class="px-6 py-2 bg-[#ffffff12] text-white rounded-xl">Start Timer</button>
            {:else}
            <button on:click={stopAndToggle} class="px-6 py-2 bg-[#ffffff12] text-white rounded-xl">Stop Timer</button>
            {/if}
        </div>
    </main>
{/if}
