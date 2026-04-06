[Diva Camelia 241011060014 (1).index.html](https://github.com/user-attachments/files/26496116/Diva.Camelia.241011060014.1.index.html)
<!DOCTYPE html>
<html lang="id">

<head>
<meta charset="UTF-8">
<title>Scanner Notasi Ilmiah</title>

<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">

<style>

body{
    margin:0;
    height:100vh;
    font-family:'Quicksand', sans-serif;
    display:flex;
    justify-content:center;
    align-items:center;
    background: linear-gradient(to bottom, #c7ecff, #66b3ff);
    overflow:hidden;
    transition:0.5s;
}

/* 🌙 DARK MODE */
.dark{
    background: linear-gradient(to bottom, #001933, #003366);
}

.dark .container{
    background: rgba(0,0,50,0.85);
    color:white;
}

.dark h2{
    color:#66ccff;
}

.dark input{
    background:#001933;
    color:white;
    border:1px solid #3399ff;
}

.dark #hasil{
    color:#66ccff;
}

/* 🌊 WAVE */
.wave{
    position:absolute;
    bottom:0;
    width:200%;
    height:150px;
    background: rgba(0, 102, 255, 0.25);
    border-radius:50%;
    animation: waveMove 6s infinite linear;
}
.wave:nth-child(2){ animation-duration:8s; opacity:0.5; }
.wave:nth-child(3){ animation-duration:10s; opacity:0.3; }

@keyframes waveMove{
    from{transform:translateX(0);}
    to{transform:translateX(-50%);}
}

/* 🫧 BUBBLE */
.bubble{
    position:absolute;
    bottom:-50px;
    width:15px;
    height:15px;
    background:rgba(255,255,255,0.6);
    border-radius:50%;
    animation: rise 10s infinite;
}

@keyframes rise{
    0%{transform:translateY(0); opacity:0;}
    50%{opacity:1;}
    100%{transform:translateY(-100vh); opacity:0;}
}

/* 🪼 JELLYFISH */
.jelly{
    position:absolute;
    width:40px;
    height:40px;
    background: radial-gradient(circle, #66ccff, #3399ff);
    border-radius:50%;
    opacity:0.7;
    animation: float 6s ease-in-out infinite;
}

.jelly::before,
.jelly::after{
    content:"";
    position:absolute;
    width:3px;
    height:25px;
    background:#66ccff;
    bottom:-20px;
    left:50%;
    transform:translateX(-50%);
    border-radius:10px;
    animation: tentacle 1s infinite alternate;
}

.jelly::after{
    left:30%;
}

@keyframes float{
    0%{transform:translateY(0) translateX(0);}
    50%{transform:translateY(-40px) translateX(10px);}
    100%{transform:translateY(0) translateX(0);}
}

@keyframes tentacle{
    from{height:20px;}
    to{height:30px;}
}

/* 📦 CARD */
.container{
    position:relative;
    background: rgba(255,255,255,0.9);
    backdrop-filter: blur(10px);
    padding:40px;
    border-radius:25px;
    box-shadow:0 10px 30px rgba(0,102,255,0.3);
    text-align:center;
    width:360px;
    z-index:2;
    animation: fadeIn 1s ease;
}

@keyframes fadeIn{
    from{opacity:0; transform:translateY(20px);}
    to{opacity:1; transform:translateY(0);}
}

.container:hover{
    transform: scale(1.05);
}

/* ✨ GLOW */
.container::before{
    content:"";
    position:absolute;
    top:-5px;
    left:-5px;
    right:-5px;
    bottom:-5px;
    border-radius:30px;
    background:linear-gradient(45deg,#66ccff,#0066ff,#66ccff);
    z-index:-1;
    filter:blur(15px);
    opacity:0.5;
}

/* TEXT */
h2{
    font-family:'Fredoka', cursive;
    color:#0047b3;
}

.author{
    font-size:14px;
    color:#0066ff;
    margin-bottom:15px;
}

/* INPUT */
input{
    padding:12px;
    border-radius:12px;
    border:1px solid #99ccff;
    width:80%;
    margin:10px 0;
    outline:none;
    transition:0.3s;
}

input:focus{
    border-color:#0066ff;
    box-shadow:0 0 10px rgba(0,102,255,0.3);
}

/* BUTTON */
button{
    background:#0066ff;
    color:white;
    border:none;
    padding:10px 20px;
    border-radius:12px;
    cursor:pointer;
    margin:5px;
    transition:0.3s;
}

button:hover{
    background:#0047b3;
}

button:active{
    transform:scale(0.95);
}

.valid{
    background:#3399ff;
}

.invalid{
    background:#cce6ff;
    color:#003366;
}

.reset{
    background:#99ccff;
    color:#003366;
}

#hasil{
    margin-top:15px;
    font-weight:600;
}

</style>

</head>

<body>

<!-- 🌊 WAVES -->
<div class="wave"></div>
<div class="wave"></div>
<div class="wave"></div>

<!-- 🫧 BUBBLES -->
<div class="bubble" style="left:10%"></div>
<div class="bubble" style="left:30%"></div>
<div class="bubble" style="left:50%"></div>
<div class="bubble" style="left:70%"></div>
<div class="bubble" style="left:90%"></div>

<!-- 🪼 JELLYFISH -->
<div class="jelly" style="left:10%; bottom:120px;"></div>
<div class="jelly" style="right:10%; bottom:150px;"></div>
<div class="jelly" style="left:20%; bottom:80px;"></div>

<div class="container">

<h2>🌊 Scanner Notasi Ilmiah</h2>
<p class="author">By Diva Camelia ✨</p>

<button onclick="toggleMode()" id="modeBtn">🌙 Dark Mode</button>

<input type="text" id="angka" placeholder="Masukkan format..." oninput="cek()">
<br>
<button onclick="cek()">Cek</button>
<button class="reset" onclick="resetInput()">Reset</button>

<p id="hasil"></p>

<h3>Contoh Valid</h3>

<button class="valid" onclick="isi('A.2e3')">A.2e3</button>
<button class="valid" onclick="isi('B.5e2')">B.5e2</button>
<button class="valid" onclick="isi('C.1e-4')">C.1e-4</button>

<h3>Contoh Tidak Valid</h3>

<button class="invalid" onclick="isi('ABC')">ABC</button>
<button class="invalid" onclick="isi('XYZ')">XYZ</button>
<button class="invalid" onclick="isi('Hello')">Hello</button>

</div>

<script>

function cek(){
    let angka = document.getElementById("angka").value;
    let pola = /^-?[A-Za-z]?\.\d+[eE][+-]?\d+$/;

    if(pola.test(angka)){
        document.getElementById("hasil").innerHTML = "✔ Valid Format";
        document.getElementById("hasil").style.color = "#0066ff";
    }else{
        document.getElementById("hasil").innerHTML = "✖ Tidak Valid";
        document.getElementById("hasil").style.color = "#003366";
    }
}

function isi(contoh){
    document.getElementById("angka").value = contoh;
    cek();
}

function resetInput(){
    document.getElementById("angka").value = "";
    document.getElementById("hasil").innerHTML = "";
}

function toggleMode(){
    document.body.classList.toggle("dark");

    let btn = document.getElementById("modeBtn");

    if(document.body.classList.contains("dark")){
        btn.innerHTML = "☀️ Light Mode";
    }else{
        btn.innerHTML = "🌙 Dark Mode";
    }
}

</script>

</body>

</html>
