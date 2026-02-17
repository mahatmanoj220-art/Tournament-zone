<!DOCTYPE html>
<html>
<head>
  <title>Tournament Section</title>
  <style>
    body { font-family: Arial; }
    .tournament { margin: 20px; }
    .match { margin: 10px; padding: 10px; border: 1px solid #ccc; display:flex; justify-content: space-between; }
    .winner { color: green; font-weight: bold; }
    .player { cursor: pointer; }
  </style>
</head>
<body>
  <div class="tournament">
    <h2>Active Tournament: Weekly FF Challenge</h2>
    <div class="matches">
      <div class="match" id="match1">
        <span class="player" onclick="selectWinner('player1','match1')">Player 1</span> VS 
        <span class="player" onclick="selectWinner('player2','match1')">Player 2</span>
      </div>
      <div class="match" id="match2">
        <span class="player" onclick="selectWinner('player3','match2')">Player 3</span> VS 
        <span class="player" onclick="selectWinner('player4','match2')">Player 4</span>
      </div>
      <div class="match" id="match3">
        <span class="player" onclick="selectWinner('player5','match3')">Player 5</span> VS 
        <span class="player" onclick="selectWinner('player6','match3')">Player 6</span>
      </div>
      <div class="match" id="match4">
        <span class="player" onclick="selectWinner('player7','match4')">Player 7</span> VS 
        <span class="player" onclick="selectWinner('player8','match4')">Player 8</span>
      </div>
    </div>
    <h3>Leaderboard</h3>
    <ul id="leaderboard"></ul>
  </div>

<script>
let leaderboard = {};

function selectWinner(player, matchId) {
  document.querySelectorAll(`#${matchId} .player`).forEach(el => el.classList.remove('winner'));
  let winnerEl = Array.from(document.querySelectorAll(`#${matchId} .player`)).find(el => el.textContent === player);
  winnerEl.classList.add('winner');

  leaderboard[player] = (leaderboard[player] || 0) + 1;
  updateLeaderboard();
}

function updateLeaderboard() {
  const lb = document.getElementById('leaderboard');
  lb.innerHTML = '';
  for (const [player, score] of Object.entries(leaderboard)) {
    const li = document.createElement('li');
    li.textContent = player + ' - ' + score + ' points';
    lb.appendChild(li);
  }
}
</script>
</body>
</html>
