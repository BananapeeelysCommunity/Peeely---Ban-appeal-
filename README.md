
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Bananapeeely's Community – Ban Appeal</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    :root {
        --bg: #05060a;
        --card: #11131b;
        --accent: #f7d84b;
        --accent-soft: #ffe680;
        --text-muted: #a5a7b5;
    }

    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "Poppins", sans-serif;
        background: radial-gradient(circle at top, #151827 0, #05060a 55%);
        color: #fff;
        overflow-x: hidden;
        overflow-y: auto;
        min-height: 100vh;
    }

    /* Center helper */
    .center {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    /* Loading screen */
    #loadingScreen {
        position: fixed;
        inset: 0;
        background: #05060a;
        z-index: 999;
        flex-direction: column;
        gap: 18px;
        text-align: center;
    }

    #bananaIcon {
        font-size: 4.5rem;
        animation: bounce 1s infinite;
    }

    #loadingText {
        font-size: 1.2rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--text-muted);
    }

    .progress-bar {
        width: 220px;
        height: 8px;
        border-radius: 999px;
        background: #1b1d27;
        overflow: hidden;
        margin-top: 6px;
    }

    .progress-fill {
        height: 100%;
        width: 0%;
        background: linear-gradient(90deg, #f7d84b, #ffe680);
        transition: width 0.25s ease-out;
    }

    @keyframes bounce {
        0% { transform: translateY(0); }
        50% { transform: translateY(-14px); }
        100% { transform: translateY(0); }
    }

    @keyframes fadeOut {
        to { opacity: 0; visibility: hidden; }
    }

    /* Main layout */
    #app {
        max-width: 900px;
        margin: 0 auto;
        padding: 40px 18px 60px;
    }

    header {
        text-align: center;
        margin-bottom: 32px;
    }

    header h1 {
        font-size: 2.1rem;
        margin: 0;
    }

    header p {
        margin-top: 10px;
        color: var(--text-muted);
        font-size: 0.98rem;
    }

    .pill {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        padding: 6px 12px;
        border-radius: 999px;
        background: rgba(247, 216, 75, 0.08);
        color: var(--accent-soft);
        font-size: 0.8rem;
        margin-bottom: 12px;
    }

    /* Card */
    .card {
        background: radial-gradient(circle at top left, #1b1d27 0, #10121a 55%);
        border-radius: 18px;
        padding: 22px 20px 24px;
        box-shadow: 0 18px 40px rgba(0, 0, 0, 0.55);
        border: 1px solid rgba(255, 255, 255, 0.04);
    }

    .card-title {
        font-size: 1.2rem;
        margin-bottom: 6px;
    }

    .card-sub {
        font-size: 0.9rem;
        color: var(--text-muted);
        margin-bottom: 18px;
    }

    /* Buttons */
    .btn {
        border: none;
        outline: none;
        cursor: pointer;
        border-radius: 999px;
        padding: 11px 22px;
        font-size: 0.95rem;
        font-weight: 500;
        display: inline-flex;
        align-items: center;
        gap: 8px;
        transition: transform 0.12s ease, box-shadow 0.12s ease, background 0.12s ease;
    }

    .btn-primary {
        background: linear-gradient(135deg, #f7d84b, #ffe680);
        color: #11131b;
        box-shadow: 0 10px 24px rgba(247, 216, 75, 0.35);
    }

    .btn-primary:hover {
        transform: translateY(-1px);
        box-shadow: 0 14px 30px rgba(247, 216, 75, 0.45);
    }

    .btn-ghost {
        background: transparent;
        color: var(--text-muted);
    }

    .btn-ghost:hover {
        background: rgba(255, 255, 255, 0.04);
    }

    /* Sections */
    #introSection,
    #formSection,
    #confirmSection,
    #successSection {
        display: none;
        animation: fadeIn 0.35s ease;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* Form */
    .form-grid {
        display: grid;
        grid-template-columns: 1fr;
        gap: 14px;
        margin-top: 10px;
    }

    .field-label {
        font-size: 0.85rem;
        color: var(--text-muted);
        margin-bottom: 4px;
    }

    .field-label span {
        color: var(--accent-soft);
        margin-right: 4px;
    }

    input, textarea {
        width: 100%;
        border-radius: 10px;
        border: 1px solid rgba(255, 255, 255, 0.06);
        background: rgba(10, 11, 16, 0.9);
        color: #fff;
        padding: 10px 11px;
        font-size: 0.92rem;
        outline: none;
        transition: border 0.12s ease, box-shadow 0.12s ease, background 0.12s ease;
    }

    input:focus, textarea:focus {
        border-color: rgba(247, 216, 75, 0.7);
        box-shadow: 0 0 0 1px rgba(247, 216, 75, 0.4);
        background: rgba(10, 11, 16, 1);
    }

    textarea {
        min-height: 90px;
        resize: vertical;
    }

    .error {
        border-color: #ff6b6b !important;
        box-shadow: 0 0 0 1px rgba(255, 107, 107, 0.4) !important;
    }

    .helper {
        font-size: 0.8rem;
        color: var(--text-muted);
        margin-top: 4px;
    }

    /* Footer note */
    .footer-note {
        margin-top: 18px;
        font-size: 0.8rem;
        color: var(--text-muted);
        text-align: right;
    }

    @media (min-width: 720px) {
        .form-grid {
            grid-template-columns: repeat(2, minmax(0, 1fr));
        }

        .form-grid textarea {
            grid-column: 1 / -1;
        }
    }
</style>
</head>
<body>

<!-- Loading -->
<div id="loadingScreen" class="center">
    <div>
        <div id="bananaIcon">🍌</div>
        <div id="loadingText">Preparing Bananapeeely's Community</div>
        <div class="progress-bar">
            <div id="progressFill" class="progress-fill"></div>
        </div>
    </div>
</div>

<!-- App -->
<div id="app">
    <header>
        <div class="pill">
            <span>🍌</span>
            <span>Bananapeeely's Community</span>
        </div>
        <h1>Ban Appeal Portal</h1>
        <p>Appeal your ban from the community with a clear, simple form. Staff will review your appeal as soon as possible.</p>
    </header>

    <!-- Intro -->
    <section id="introSection">
        <div class="card">
            <div class="card-title">Fill out ban appeal form</div>
            <div class="card-sub">You’ll be asked for your Discord and Roblox details, plus the reason you were banned.</div>
            <button class="btn btn-primary" id="startBtn">
                Yes, start appeal
                <span>→</span>
            </button>
        </div>
    </section>

    <!-- Form -->
    <section id="formSection">
        <div class="card">
            <div class="card-title">Ban Appeal Form</div>
            <div class="card-sub">Please answer honestly. False information may result in your appeal being denied.</div>

            <div class="form-grid">
                <div>
                    <div class="field-label"><span>🍌</span>Discord username</div>
                    <input id="discordUsername" placeholder="Example: Bananapeeely#1234">
                </div>

                <div>
                    <div class="field-label"><span>🆔</span>Discord ID</div>
                    <input id="discordID" placeholder="Right-click your profile → Copy ID">
                </div>

                <div>
                    <div class="field-label"><span>🎮</span>Roblox username</div>
                    <input id="robloxUsername" placeholder="Example: BananapeeelyOfficial">
                </div>

                <div>
                    <div class="field-label"><span>⚠️</span>Reason for ban</div>
                    <textarea id="banReason" placeholder="Explain what happened and why you believe you should be unbanned."></textarea>
                </div>
            </div>

            <div class="helper">All fields are required. Make sure everything is accurate before continuing.</div>

            <div style="margin-top: 18px; display: flex; gap: 10px; justify-content: flex-end; flex-wrap: wrap;">
                <button class="btn btn-primary" id="continueBtn">
                    Continue
                    <span>→</span>
                </button>
                <button class="btn btn-ghost" id="backToIntroBtn">
                    Back
                </button>
            </div>
        </div>
    </section>

    <!-- Confirm -->
    <section id="confirmSection">
        <div class="card">
            <div class="card-title">Are you happy with this?</div>
            <div class="card-sub">Check your details one more time. When you submit, your appeal will be sent directly to staff via Discord.</div>

            <div style="font-size: 0.9rem; color: var(--text-muted); margin-bottom: 16px;">
                <strong>Discord username:</strong> <span id="summaryDiscordUsername"></span><br>
                <strong>Discord ID:</strong> <span id="summaryDiscordID"></span><br>
                <strong>Roblox username:</strong> <span id="summaryRobloxUsername"></span><br>
                <strong>Reason for ban:</strong><br>
                <span id="summaryBanReason"></span>
            </div>

            <div style="display: flex; gap: 10px; justify-content: flex-end; flex-wrap: wrap;">
                <button class="btn btn-primary" id="submitBtn">
                    Yes, submit appeal
                    <span>✔</span>
                </button>
                <button class="btn btn-ghost" id="editBtn">
                    Go back and edit
                </button>
            </div>
        </div>
    </section>

    <!-- Success -->
    <section id="successSection">
        <div class="card">
            <div class="card-title">Appeal submitted</div>
            <div class="card-sub">Your ban appeal has been sent to the staff team. They’ll review it and contact you via Discord.</div>
            <div class="helper">You can close this page now. Please keep your DMs open so staff can reach you if needed.</div>
        </div>
    </section>

    <div class="footer-note">
        Powered by Bananapeeely's Community · Appeals are reviewed manually by staff.
    </div>
</div>

<script>
    // -------- Loading screen --------
    const loadingScreen = document.getElementById("loadingScreen");
    const progressFill = document.getElementById("progressFill");

    let progress = 0;
    const loadingInterval = setInterval(() => {
        progress += 10;
        if (progress > 100) progress = 100;
        progressFill.style.width = progress + "%";

        if (progress >= 100) {
            clearInterval(loadingInterval);
            setTimeout(() => {
                loadingScreen.style.animation = "fadeOut 0.5s forwards";
                setTimeout(() => {
                    loadingScreen.style.display = "none";
                    showSection("introSection");
                }, 500);
            }, 400);
        }
    }, 220);

    // -------- Sections --------
    const sections = ["introSection", "formSection", "confirmSection", "successSection"];

    function showSection(id) {
        sections.forEach(s => {
            document.getElementById(s).style.display = (s === id) ? "block" : "none";
        });
        window.scrollTo({ top: 0, behavior: "smooth" });
    }

    // -------- Elements --------
    const startBtn = document.getElementById("startBtn");
    const continueBtn = document.getElementById("continueBtn");
    const backToIntroBtn = document.getElementById("backToIntroBtn");
    const submitBtn = document.getElementById("submitBtn");
    const editBtn = document.getElementById("editBtn");

    const discordUsername = document.getElementById("discordUsername");
    const discordID = document.getElementById("discordID");
    const robloxUsername = document.getElementById("robloxUsername");
    const banReason = document.getElementById("banReason");

    const summaryDiscordUsername = document.getElementById("summaryDiscordUsername");
    const summaryDiscordID = document.getElementById("summaryDiscordID");
    const summaryRobloxUsername = document.getElementById("summaryRobloxUsername");
    const summaryBanReason = document.getElementById("summaryBanReason");

    // -------- Navigation --------
    startBtn.addEventListener("click", () => {
        showSection("formSection");
    });

    backToIntroBtn.addEventListener("click", () => {
        showSection("introSection");
    });

    continueBtn.addEventListener("click", () => {
        const fields = [discordUsername, discordID, robloxUsername, banReason];
        let valid = true;

        fields.forEach(f => {
            if (!f.value.trim()) {
                f.classList.add("error");
                valid = false;
            } else {
                f.classList.remove("error");
            }
        });

        if (!valid) {
            alert("Please fill out all fields before continuing.");
            return;
        }

        summaryDiscordUsername.textContent = discordUsername.value.trim();
        summaryDiscordID.textContent = discordID.value.trim();
        summaryRobloxUsername.textContent = robloxUsername.value.trim();
        summaryBanReason.textContent = banReason.value.trim();

        showSection("confirmSection");
    });

    editBtn.addEventListener("click", () => {
        showSection("formSection");
    });

    // -------- Webhook submit --------
    submitBtn.addEventListener("click", () => {
        const webhookURL = "https://discord.com/api/webhooks/1524320929956630639/gMfu-AsRphFY3QQqUXiKw3I0hUNCS4NzM5mLW1cPOWOQb9Ajz26CtJbVsf-wIiB5KgQb"; // ← replace with your Discord webhook

        const payload = {
            embeds: [
                {
                    title: "New Ban Appeal – Bananapeeely's Community",
                    color: 16763904,
                    fields: [
                        { name: "Discord Username", value: discordUsername.value.trim(), inline: true },
                        { name: "Discord ID", value: discordID.value.trim(), inline: true },
                        { name: "Roblox Username", value: robloxUsername.value.trim(), inline: false },
                        { name: "Reason for Ban", value: banReason.value.trim(), inline: false }
                    ],
                    footer: {
                        text: "Ban appeal submitted via Bananapeeely's Community portal"
                    },
                    timestamp: new Date().toISOString()
                }
            ]
        };

        fetch(webhookURL, {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(payload)
        }).catch(() => {
            // Silent fail; you can log if needed
        });

        showSection("successSection");
    });
</script>

</body>
</html>

