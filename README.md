# r-vis-a
site de révisions pour lycéens
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>R-Vis-A - Révision intelligente</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
font-family:Arial, sans-serif;
background:#0f172a;
color:white;
padding:30px;
}

.container{
max-width:1000px;
margin:auto;
}

header{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:40px;
}

.logo{
font-size:32px;
font-weight:bold;
}

.logo span{
color:#38bdf8;
}

.compteur{
background:#1e293b;
padding:10px 15px;
border-radius:10px;
}

.card{
background:#1e293b;
padding:25px;
border-radius:15px;
margin-bottom:25px;
}

textarea{
width:100%;
height:250px;
background:#0f172a;
color:white;
border:1px solid #334155;
border-radius:10px;
padding:15px;
font-size:16px;
resize:none;
}

button{
background:#38bdf8;
color:black;
border:none;
padding:15px 25px;
font-size:16px;
font-weight:bold;
border-radius:10px;
cursor:pointer;
margin-top:15px;
}

button:hover{
opacity:0.9;
}

.result{
margin-top:20px;
display:none;
}

.result-card{
background:#0f172a;
padding:20px;
border-radius:10px;
margin-top:15px;
border:1px solid #334155;
}

h2{
margin-bottom:15px;
}

h3{
margin-bottom:10px;
color:#38bdf8;
}
</style>
</head>

<body>

<div class="container">

<header>
<div class="logo">
R-<span>Vis</span>-A 📚
</div>

<div class="compteur" id="compteur">
2 révisions gratuites restantes aujourd'hui
</div>
</header>

<div class="card">

<h2>Colle ton cours</h2>

<textarea
id="cours"
placeholder="Colle ici ton cours d'histoire, maths, SVT..."
></textarea>

<button onclick="generer()">
Générer la révision
</button>

<div class="result" id="result">

<div class="result-card">
<h3>📝 Résumé</h3>
<p id="resume"></p>
</div>

<div class="result-card">
<h3>📚 Fiche de révision</h3>
<p id="fiche"></p>
</div>

<div class="result-card">
<h3>❓ Quiz</h3>
<p id="quiz"></p>
</div>

</div>

</div>

</div>

<script>

let utilisations =
Number(localStorage.getItem("utilisations")) || 0;

function generer(){

if(utilisations >= 2){
alert("Tu as utilisé tes 2 révisions gratuites aujourd'hui.");
return;
}

let cours =
document.getElementById("cours").value;

if(cours.length < 100){
alert("Colle un cours plus complet.");
return;
}

utilisations++;

localStorage.setItem(
"utilisations",
utilisations
);

document.getElementById("compteur").innerText =
(2 - utilisations) +
" révisions gratuites restantes aujourd'hui";

document.getElementById("result").style.display =
"block";

document.getElementById("resume").innerText =
"Résumé généré prochainement par l'IA.";

document.getElementById("fiche").innerText =
"Fiche de révision générée prochainement par l'IA.";

document.getElementById("quiz").innerHTML =
`
1. Question exemple ?<br><br>
2. Question exemple ?<br><br>
3. Question exemple ?
`;
}

document.getElementById("compteur").innerText =
(2 - utilisations) +
" révisions gratuites restantes aujourd'hui";

</script>

</body>
</html>
