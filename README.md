<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Bananapeeely's Community</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Poppins,sans-serif;
}

body{

background:linear-gradient(-45deg,#ffcb05,#ffd94d,#ffea87,#ffe38b);
background-size:400% 400%;
animation:bg 12s ease infinite;

display:flex;
justify-content:center;
align-items:center;

height:100vh;
overflow:hidden;
color:white;

}

@keyframes bg{

0%{background-position:0% 50%;}
50%{background-position:100% 50%;}
100%{background-position:0% 50%;}

}

.glass{

width:700px;
max-width:92%;

background:rgba(255,255,255,.15);
backdrop-filter:blur(18px);

border-radius:25px;

padding:40px;

box-shadow:0 15px 40px rgba(0,0,0,.25);

text-align:center;

}

h1{

font-size:34px;
margin-bottom:15px;

}

p{

opacity:.9;

}

button{

margin-top:20px;

padding:14px 35px;

border:none;
border-radius:14px;

background:#ffd400;

font-size:18px;
font-weight:600;

cursor:pointer;

transition:.3s;

}

button:hover{

transform:scale(1.05);

background:#fff176;

}

input,textarea{

width:100%;

padding:15px;

margin-top:15px;

border:none;
border-radius:12px;

font-size:16px;

background:rgba(255,255,255,.2);

color:white;

outline:none;

}

textarea{

resize:none;
height:120px;

}

::placeholder{

color:white;

opacity:.8;

}

.hidden{

display:none;

}

#banana{

font-size:120px;
animation:bounce 1s infinite;

}

@keyframes bounce{

50%{

transform:translateY(-15px);

}

}

.progress{

width:100%;
height:18px;

background:rgba(255,255,255,.2);

border-radius:50px;

margin-top:30px;

overflow:hidden;

}

.bar{

height:100%;
width:0%;

background:white;

transition:.1s;

}

#percent{

margin-top:10px;
font-size:22px;

}

.success{

font-size:30px;
font-weight:600;

}

</style>

</head>

<body>

<div class="glass" id="loading">

<div id="banana">🍌</div>

<h1>Bananapeeely's Community</h1>

<div class="progress">

<div class="bar" id="bar"></div>

</div>

<div id="percent">0%</div>

</div>

<div class="glass hidden" id="welcome">

<h1>Fill out Ban Appeal Form</h1>

<p>Please answer honestly.</p>

<button onclick="startForm()">Yes</button>

</div>

<div class="glass hidden" id="formBox">

<h1>Ban Appeal</h1>

<input id="discordUser" placeholder="Discord Username">

<input id="discordID" placeholder="Discord ID">

<input id="robloxUser" placeholder="Roblox Username">

<textarea id="reason" placeholder="Reason for ban"></textarea>

<button onclick="confirmSend()">Submit</button>

</div>

<div class="glass hidden" id="success">

<div class="success">✅ Appeal Sent!</div>

<p>Thank you for submitting your appeal.</p>

</div>

<script>

let percent=0;

let interval=setInterval(()=>{

percent++;

document.getElementById("bar").style.width=percent+"%";

document.getElementById("percent").innerHTML=percent+"%";

if(percent>=100){

clearInterval(interval);

setTimeout(()=>{

document.getElementById("loading").classList.add("hidden");

document.getElementById("welcome").classList.remove("hidden");

},800);

}

},35);

function startForm(){

document.getElementById("welcome").classList.add("hidden");

document.getElementById("formBox").classList.remove("hidden");

}

async function confirmSend(){

let discordUser=document.getElementById("discordUser").value.trim();

let discordID=document.getElementById("discordID").value.trim();

let roblox=document.getElementById("robloxUser").value.trim();

let reason=document.getElementById("reason").value.trim();

if(discordUser==""||discordID==""||roblox==""||reason==""){

alert("Please fill out all fields.");

return;

}

let okay=confirm("Are you happy with this?");

if(!okay) return;

const webhook="https://discord.com/api/webhooks/1524320929956630639/gMfu-AsRphFY3QQqUXiKw3I0hUNCS4NzM5mLW1cPOWOQb9Ajz26CtJbVsf-wIiB5KgQb";

let embed={

title:"🍌 New Ban Appeal",

color:16766720,

fields:[

{

name:"Discord Username",

value:discordUser,

inline:false

},

{

name:"Discord ID",

value:discordID,

inline:false

},

{

name:"Roblox Username",

value:roblox,

inline:false

},

{

name:"Reason for Ban",

value:reason,

inline:false

}

],

footer:{

text:"Bananapeeely's Community"

},

timestamp:new Date()

};

try{

await fetch(webhook,{

method:"POST",

headers:{

"Content-Type":"application/json"

},

body:JSON.stringify({

embeds:[embed]

})

});

document.getElementById("formBox").classList.add("hidden");

document.getElementById("success").classList.remove("hidden");

}catch(e){

alert("Failed to send.");

}

}

</script>

</body>
</html>
