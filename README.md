<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Juliana 💖</title>

<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<style>
body{
    margin:0;
    padding:0;
    font-family: Arial, cursive;
    background: linear-gradient(to right, #ff4e88, #ff99ac);
    text-align:center;
    overflow:hidden;
}

.container{
    margin-top:40px;
    background:white;
    padding:30px;
    border-radius:20px;
    width:90%;
    max-width:500px;
    margin-left:auto;
    margin-right:auto;
    box-shadow:0 10px 30px rgba(0,0,0,0.2);
    position:relative;
}

.hidden{ display:none; }

button{
    padding:12px 25px;
    font-size:18px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    margin:10px;
    transition:0.3s;
    position:relative;
}

.yes{ background:#ff2e63; color:white; }
.no{ background:#ccc; position:absolute; }

.proposal{
    font-size:22px;
    color:#ff2e63;
    font-weight:bold;
    animation: pulse 1s infinite;
}

@keyframes pulse{
    0%{transform:scale(1);}
    50%{transform:scale(1.1);}
    100%{transform:scale(1);}
}

.heart{
    position:absolute;
    color:red;
    font-size:20px;
    animation: float 5s linear infinite;
}

@keyframes float{
    0%{transform:translateY(100vh); opacity:1;}
    100%{transform:translateY(-10vh); opacity:0;}
}

img{
    border-radius:15px;
    margin:10px 0;
}

</style>
</head>
<body>

<!-- PASSWORD LOCK -->
<div class="container" id="passwordBox">
    <h2>🔐 enter our secret word</h2>
    <input type="password" id="passwordInput" placeholder="type here">
    <br><br>
    <button onclick="checkPassword()">open 💌</button>
</div>

<!-- MAIN CONTENT -->
<div class="container hidden" id="mainContent">

<audio autoplay loop>
<source src="https://files.catbox.moe/7n0f6p.mp3" type="audio/mp3">
</audio>

<h1>💖 Juliana 💖</h1>

<img src="https://media.giphy.com/media/3oriO0OEd9QIDdllqo/giphy.gif" width="200">

<p id="typing"></p>

<h2>can you be my valentine? 💘</h2>

<button class="yes" onclick="yesClicked()">YES 💖</button>
<button class="no" id="noBtn">NO 💔</button>

<div id="dateDetails" class="hidden">
    <h2>YAY!!! 🥰</h2>
    <p>
        february 14 💕 <br>
        7:00 pm 🌙 <br>
        secret surprise date 🎁 <br><br>
        i promise to make you feel special all night 💞
    </p>

    <!-- SLIDESHOW -->
    <h3>our memories 📸</h3>
    <img id="slideshow" width="250">

    <p class="proposal">
        and one more thing…  
        will you stay with me forever? 💍❤️
    </p>
</div>

</div>

<script>

// PASSWORD (change mo kung gusto mo)
function checkPassword(){
    const pass = document.getElementById("passwordInput").value;
    if(pass === "jerickjuliana"){
        document.getElementById("passwordBox").classList.add("hidden");
        document.getElementById("mainContent").classList.remove("hidden");
        startTyping();
    } else {
        alert("wrong secret word 😢");
    }
}

// TYPING EFFECT
const message = "hi love, simula nung dumating ka sa buhay ko, nag-iba ang lahat. ikaw ang pahinga ko, ikaw ang tahanan ko. juliana, i love you more than yesterday and less than tomorrow. – jerick 💕";
let i = 0;

function startTyping(){
    const typing = document.getElementById("typing");
    function type(){
        if(i < message.length){
            typing.innerHTML += message.charAt(i);
            i++;
            setTimeout(type,50);
        }
    }
    type();
}

// YES CLICK
function yesClicked(){
    document.getElementById("dateDetails").classList.remove("hidden");

    confetti({
        particleCount:200,
        spread:100,
        origin:{y:0.6}
    });
}

// NO BUTTON MOVE
const noBtn = document.getElementById("noBtn");
noBtn.addEventListener("mouseover", function(){
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    let yesBtn = document.querySelector(".yes");
    let currentSize = parseFloat(window.getComputedStyle(yesBtn).fontSize);
    yesBtn.style.fontSize = (currentSize + 5) + "px";
});

// SLIDESHOW (palitan mo images ng pics niyo)
const images = [
"https://via.placeholder.com/250x200?text=Memory+1",
"https://via.placeholder.com/250x200?text=Memory+2",
"https://via.placeholder.com/250x200?text=Memory+3"
];

let slideIndex = 0;
const slide = document.getElementById("slideshow");

setInterval(()=>{
    slide.src = images[slideIndex];
    slideIndex = (slideIndex + 1) % images.length;
},2000);

// FLOATING HEARTS
function createHeart(){
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML="❤️";
    heart.style.left=Math.random()*100+"vw";
    heart.style.animationDuration=Math.random()*2+3+"s";
    document.body.appendChild(heart);
    setTimeout(()=>{heart.remove();},5000);
}
setInterval(createHeart,300);

</script>

</body>
</html>
