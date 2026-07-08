<html lang="en">
<head>
<meta charset="UTF-8">
<title>Bananapeeely's Community</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    body {
        margin: 0;
        font-family: 'Poppins', sans-serif;
        background: #0f0f0f;
        color: white;
        overflow: hidden;
    }

    /* Loading Screen */
    #loadingScreen {
        position: fixed;
        top: 0; left: 0;
        width: 100%; height: 100%;
        background: #111;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-size: 2rem;
        animation: fadeOut 1s ease forwards;
        animation-delay: 3s;
    }

    #banana {
        font-size: 5rem;
        animation: bounce 1s infinite;
    }

    @keyframes bounce {
        0% { transform: translateY(0); }
        50% { transform: translateY(-20px); }
        100% { transform: translateY(0); }
    }

    #progress {
        margin-top: 20px;
        font-size: 1.5rem;
    }

    @keyframes fadeOut {
        to { opacity: 0; visibility: hidden; }
    }

    /* Main Container */
    #main {
        display: none;
        text-align: center;
        padding-top: 80px;
    }

    .btn {
        background: #f7d84b;
        color: black;
        padding: 15px 30px;
        border-radius: 10px;
        font-size: 1.3rem;
        cursor: pointer;
        transition: 0.3s;
    }

    .btn:hover {
        background: #ffe680;
    }

    /* Form */
    #formContainer {
        display: none;
        width: 90%;
        max-width: 500px;
        margin: auto;
        margin-top: 40px;
        background: #1a1a1a;
        padding: 25px;
        border-radius: 12px;
        animation: fadeIn 0.5s ease;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    input, textarea {
        width: 100%;
        padding: 12px;
        margin-top: 10px;
        border-radius: 8px;
        border: none;
        font-size: 1rem;
    }

    #confirmScreen {
        display: none;
        margin-top: 40px;
        font-size: 1.4rem;
    }
</style>
</head>
<body>

<!-- Loading Screen -->
<div id="loadingScreen">
    <div id="banana">🍌</div>
    <div id="progress">Loading 0%</div>
</div>

<!-- Main Screen -->
<div id="main">
    <h1>Bananapeeely's Community</h1>
    <p>Fill out ban appeal form</p>
    <button class="btn" onclick="showForm()">Yes</button>
</div>

<!-- Form -->
<div id="formContainer">
    <h2>Ban Appeal Form</h2>

    <input id="discordUser" placeholder="Discord Username">
    <input id="discordID" placeholder="Discord ID">
    <input id="robloxUser" placeholder="Roblox Username">
    <textarea id="reason" placeholder="Reason for ban"></textarea>

    <button class="btn" onclick="confirmForm()">Continue</button>
</div>

<!-- Confirmation -->
<div id="confirmScreen">
    <p>Are you happy with this?</p>
    <button class="btn" onclick="submitForm()">Yes, submit</button>
</div>

<script>
    /* Loading Animation */
    let progress = 0;
    const progressText = document.getElementById("progress");

    const interval = setInterval(() => {
        progress += 10;
        progressText.innerText = `Loading ${progress}%`;
        if (progress >= 100) {
            clearInterval(interval);
            setTimeout(() => {
                document.getElementById("main").style.display = "block";
            }, 500);
        }
    }, 300);

    /* Show Form */
    function showForm() {
        document.getElementById("formContainer").style.display = "block";
    }

    /* Confirm Screen */
    function confirmForm() {
        const fields = [
            "discordUser",
            "discordID",
            "robloxUser",
            "reason"
        ];

        for (let f of fields) {
            if (document.getElementById(f).value.trim() === "") {
                alert("Please fill out all fields");
                return;
            }
        }

        document.getElementById("confirmScreen").style.display = "block";
    }

    /* Submit to Webhook */
    function submitForm() {
        const webhook = "https://discord.com/api/webhooks/1524320929956630639/gMfu-AsRphFY3QQqUXiKw3I0hUNCS4NzM5mLW1cPOWOQb9Ajz26CtJbVsf-wIiB5KgQb";

        const payload = {
            embeds: [{
                title: "New Ban Appeal",
                color: 16763904,
                fields: [
                    { name: "Discord Username", value: document.getElementById("discordUser").value },
                    { name: "Discord ID", value: document.getElementById("discordID").value },
                    { name: "Roblox Username", value: document.getElementById("robloxUser").value },
                    { name: "Reason for Ban", value: document.getElementById("reason").value }
                ]
            }]
        };

        fetch(webhook, {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(payload)
        });

        alert("Your appeal has been submitted!");
    }
</script>

</body>
</html>
