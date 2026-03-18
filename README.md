<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<title>Aurora Spin 💱</title>
<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #0b0b1a, #3d0066);
  color: white;
  text-align: center;
  overflow: hidden;
}
h1 {
  color: gold;
  text-shadow: 2px 2px black;
  margin-top: 20px;
}
#moedas {
  font-size: 20px;
  margin-bottom: 20px;
}
#slot {
  font-size: 70px;
  margin: 30px auto;
  width: 200px;
  height: 200px;
  line-height: 200px;
  border: 5px solid gold;
  border-radius: 20px;
  background: rgba(255, 215, 0, 0.1);
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.05); }
  100% { transform: scale(1); }
}
button {
  padding: 15px 30px;
  font-size: 20px;
  background: gold;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  margin: 10px;
  transition: transform 0.2s;
}
button:hover { transform: scale(1.1); }
#ad {
  margin-top: 20px;
  background: #222;
  padding: 15px;
  border-radius: 10px;
  display: none;
  font-size: 18px;
}
</style>
</head>
<body>

<h1>AURORA SPIN 💱</h1>
<p id="moedas">Moedas: 1000</p>

<div id="slot">🎰</div>

<button onclick="girar()">GIRAR</button>
<button onclick="bonus()">BÔNUS DIÁRIO</button>
<button onclick="ganharGratis()">GANHAR MOEDAS GRÁTIS</button>

<p id="resultado"></p>
<div id="ad">📺 Anúncio Simulado - Aqui vai o AdMob</div>

<script>
let moedas = localStorage.getItem("moedas") || 1000;
atualizar();

function atualizar() {
  document.getElementById("moedas").innerText = "Moedas: " + moedas;
}

function girar() {
  if (moedas < 10) { alert("Sem moedas!"); return; }
  moedas -= 10;

  let symbols = ["🍒","💎","🏆","🍀","⭐"];
  let resultadoSymbol = symbols[Math.floor(Math.random() * symbols.length)];
  document.getElementById("slot").innerText = resultadoSymbol;

  let random = Math.floor(Math.random() * 100) + 1;
  let resultado = "";

  if (random <= 50) resultado = "❌ Perdeu!";
  else if (random <= 80) { moedas += 20; resultado = "🎉 Ganhou 20 moedas!"; }
  else if (random <= 95) { moedas += 50; resultado = "💎 Ganhou 50 moedas!"; }
  else { moedas += 100; resultado = "🏆 JACKPOT! 100 moedas!"; }

  document.getElementById("resultado").innerText = resultado;
  atualizar();
  localStorage.setItem("moedas", moedas);

  if (Math.random() < 0.3) mostrarAnuncio();
}

function bonus() {
  moedas += 50;
  alert("🎁 Bônus diário! +50 moedas");
  atualizar();
  localStorage.setItem("moedas", moedas);
}

function ganharGratis() {
  moedas += 50;
  alert("📺 Assista ao anúncio e ganhou 50 moedas!");
  atualizar();
  localStorage.setItem("moedas", moedas);
}

function mostrarAnuncio() {
  let ad = document.getElementById("ad");
  ad.style.display = "block";
  setTimeout(() => { ad.style.display = "none"; }, 5000);
}
</script>

</body>
</html>
