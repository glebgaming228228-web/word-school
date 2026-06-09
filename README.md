<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Französisch lernen</title>

<style>
body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 50px;
}

.container {
    max-width: 500px;
    margin: auto;
}

button {
    display: block;
    width: 100%;
    padding: 12px;
    margin: 10px 0;
    font-size: 18px;
    cursor: pointer;
}

#result {
    font-size: 20px;
    margin-top: 20px;
    font-weight: bold;
}
</style>
</head>
<body>

<div class="container">
    <h1>Französisch lernen</h1>

    <h2 id="word"></h2>

    <button onclick="checkAnswer(0)" id="btn0"></button>
    <button onclick="checkAnswer(1)" id="btn1"></button>
    <button onclick="checkAnswer(2)" id="btn2"></button>

    <p id="result"></p>

    <p>Punkte: <span id="score">0</span></p>
</div>

<script>
const questions = [
{
word: "der Apfel",
answers: ["la pomme", "le chien", "le chat"],
correct: 0
},
{
word: "der Hund",
answers: ["la maison", "le chien", "la voiture"],
correct: 1
},
{
word: "die Katze",
answers: ["le chat", "le livre", "la fleur"],
correct: 0
},
{
word: "das Haus",
answers: ["la porte", "la maison", "le jardin"],
correct: 1
}
];

let current = 0;
let score = 0;

function loadQuestion() {
document.getElementById("word").textContent =
questions[current].word;

for(let i=0;i<3;i++){
document.getElementById("btn"+i).textContent =
questions[current].answers[i];
}

document.getElementById("result").textContent = "";
}

function checkAnswer(choice) {
if(choice === questions[current].correct){
score++;
document.getElementById("result").textContent =
"✅ Richtig!";
} else {
document.getElementById("result").textContent =
"❌ Falsch!";
}

document.getElementById("score").textContent = score;

current++;

if(current < questions.length){
setTimeout(loadQuestion, 1000);
} else {
setTimeout(() => {
document.querySelector(".container").innerHTML =
`<h1>Test beendet!</h1>
<h2>Dein Ergebnis: ${score}/${questions.length}</h2>`;
}, 1000);
}
}

loadQuestion();
</script>

</body>
</html>
