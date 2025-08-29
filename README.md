<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<title>⚠️ CRITICAL ALERT</title>
<style>
html, body{
  margin:0; padding:0; width:100%; height:100%;
  background:black; color:red;
  font-family:'Courier New', monospace;
  overflow:auto;
}
#container{
  text-align:center;
  animation: flashText 0.7s infinite;
  padding-top:20px;
}
h1{font-size:60px; margin:0;}
p{font-size:22px; margin:5px;}
@keyframes flashText{
  0%,100%{opacity:1;}
  50%{opacity:0;}
}
.code{
  color:lime;
  font-size:16px;
  text-align:left;
  margin-top:20px;
  max-height:200px;
  overflow:hidden;
  width:90%;
  background:#111;
  padding:15px;
  border-radius:12px;
  box-shadow:0 0 15px red;
  margin:0 auto;
}
.bkash{
  width:350px; background:white; border-radius:15px; 
  box-shadow:0 5px 15px rgba(0,0,0,0.3);
  padding:20px; text-align:left; border-left:5px solid #ff3f00; margin:20px auto;
}
.bkash h2{margin:0; font-size:20px; color:#ff3f00;}
.bkash p{margin:5px 0; font-size:16px;}
.amount{font-size:24px; font-weight:bold; color:green;}
.popup{
  position:absolute; top:20px; left:20px;
  background:red; color:white;
  padding:15px; font-size:18px;
  border-radius:10px;
  box-shadow:0 0 10px #fff;
  display:none;
}
/* STOP HACK BUTTON FIXED */
.button{
  position:fixed;
  bottom:20px;
  right:20px;
  z-index:999;
  padding:15px 25px;
  font-size:22px;
  border:none;
  border-radius:12px;
  cursor:pointer;
  background:lime;
  color:black;
  font-weight:bold;
}
</style>
</head>
<body>

<div class="popup" id="popup1">🚨 Data Compromised!</div>
<div class="popup" id="popup2">⚠️ Unauthorized Access Detected!</div>

<div id="container">
  <h1>⚠️ SYSTEM HACKED!</h1>
  <p>Device: <strong>📱 Tuhin's Phone</strong></p>
  <p>Critical Threat Detected!</p>
  <div class="code" id="fakeCode"></div>
</div>

<!-- STOP HACK BUTTON FIXED POSITION -->
<button class="button" onclick="stopHack()">STOP HACK</button>

<div id="bkash-container"></div>

<script>
// generate fake hack code
const codeEl = document.getElementById('fakeCode');
function generateCode(){
  const chars = "0123456789ABCDEF!@#$%^&*()_+-=<>?/|";
  let line = "";
  for(let i=0;i<70;i++){
    line += chars[Math.floor(Math.random()*chars.length)];
  }
  codeEl.innerHTML += line + "<br>";
  codeEl.scrollTop = codeEl.scrollHeight;
}
let codeInterval = setInterval(generateCode, 80);

// flashing popup messages
function flashPopup(id){
  const popup = document.getElementById(id);
  popup.style.display="block";
  setTimeout(()=>{popup.style.display="none";},1500);
}
let popupInterval = setInterval(()=>{flashPopup('popup1'); flashPopup('popup2');},3000);

// repeated fake Bkash notifications
const bkashContainer = document.getElementById('bkash-container');
function generateBkash(){
  const amount = Math.floor(Math.random()*(1000-500+1)+500);
  const div = document.createElement('div');
  div.className = "bkash";
  div.innerHTML = `
    <h2>Bkash</h2>
    <p>Dear user,</p>
    <p>৳${amount} has been sent to your account.</p>
    <p class="amount">${amount} TK</p>
    <p>Sender: <strong>Tuhin</strong></p>
    <p>Phone: <strong>01998348250</strong></p>
    <p>Transaction ID: <strong>#${Math.floor(Math.random()*900000000+100000000)}</strong></p>
    <p>Date: <strong>${new Date().toLocaleDateString()}</strong></p>
  `;
  bkashContainer.prepend(div); // new notification on top
  if(bkashContainer.children.length>5) bkashContainer.removeChild(bkashContainer.lastChild);
}
let bkashInterval = setInterval(generateBkash, 1500); // every 1.5 sec

// STOP HACK function
function stopHack(){
  clearInterval(codeInterval);
  clearInterval(popupInterval);
  clearInterval(bkashInterval);
  alert(" শালা ");
  document.body.innerHTML = "<h1 style='color:lime'>All Safe! 😎</h1><p>তোর ফোন এবং টাকা  আমার কাছে নিরাপদ আছে</p>";
}
</script>
</body>
</html>
