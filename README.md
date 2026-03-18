<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<title>Aurora Spin 💱</title>
<style>
body {
  background: #0b0b1a;
  color: white;
  text-align: center;
  font-family: Arial;
}
h1 {
  color: gold;
}
#slot {
  font-size: 50px;
  margin: 20px;
}
button {
  padding: 15px 30px;
  font-size: 20px;
  background: gold;
  border: none;
  border-radius: 10px;
  cursor: pointer;
}
</style>
</head>
<body>

<h1>AURORA SPIN 💱</h1>
<p id="moedas">Moedas: 1000</p>

<div id="slot">🎰</div>

<button onclick="girar()">GIRAR</button>

<p id="resultado"></p>

<script>
let moedas = 1000;

function atualizar() {
  document.getElementById("moedas").innerText = "Moedas: " + moedas;
}

function girar() {
  if (moedas < 10) {
    alert("Sem moedas!");
    return;
  }

  moedas -= 10;

  let random = Math.floor(Math.random() * 100) + 1;
  let resultado = "";

  if (random <= 50) {
    resultado = "❌ Perdeu!";
  } else if (random <= 80) {
    moedas += 20;
    resultado = "🎉 Ganhou 20 moedas!";
  } else if (random <= 95) {
    moedas += 50;
    resultado = "💎 Ganhou 50 moedas!";
  } else {
    moedas += 100;
    resultado = "🏆 JACKPOT! 100 moedas!";
  }

  document.getElementById("resultado").innerText = resultado;
  atualizar();
}

atualizar();
</script>

</body>
</html>
