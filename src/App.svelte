<script>
  let userChoise = null;
  let computerChoise = null;
  let result = "";

  const choise = ["Rock", "Paper", "Scissors"];

  function getComputerChoice() {
    const randomIndex = Math.floor(Math.random() * 3);
    return choise[randomIndex];
  }

  function determenWinner(user, computer) {
    if (user === computer) return "It's a draw!";
    if (
      (user === "Rock" && computer === "Scissors") ||
      (user === "Paper" && computer === "Rock") ||
      (user === "Scissors" && computer === "Paper")
    ) {
      return "You win!";
    }
    return "Computer wins";
  }

  function playGame(choice) {
    userChoise = choice;
    computerChoise = getComputerChoice();
    result = determenWinner(userChoise, computerChoise);
  }
</script>

<main>
  <h1>Rock Paper Scissors</h1>

  <div>
    {#each choise as choise}
      <button on:click={() => playGame(choise)}>{choise}</button>
    {/each}
  </div>

  {#if userChoise}
    <p>You chose: {userChoise}</p>
    <p>Computer chose: {computerChoise}</p>
    <p><strong>{result}</strong></p>
  {/if}
</main>

<style>
  main {
    text-align: center;
    padding: 20px;
    font-family: "Times New Roman", Times, serif;
  }

  button {
    margin: 10px;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }
</style>
