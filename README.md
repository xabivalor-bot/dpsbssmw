# dpsbssmw
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DPSB SSMW</title>

    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

    <style>
        :root {
            --red: #C6284A;
            --dark-red: #7A1830;
            --purple: #6D28D9;
            --dark-purple: #32105C;
            --light-purple: #E9D5FF;

            --bg: #F4F1F8;
            --card: #FFFFFF;
            --soft: #F8F5FC;

            --text: #24152F;
            --muted: #75697D;
            --border: #E3DCE8;

            --green: #2E8B57;
            --danger: #B91C1C;
        }

        * {
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            margin: 0;
            font-family: Arial, Helvetica, sans-serif;
            background: var(--bg);
            color: var(--text);
        }

        button,
        input,
        textarea {
            font: inherit;
        }

        button {
            cursor: pointer;
        }

        /* =========================
           LOGIN
        ========================= */

        #auth-screen {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 25px;
            background:
                radial-gradient(circle at top left, #C6284A 0%, transparent 35%),
                radial-gradient(circle at bottom right, #6D28D9 0%, transparent 35%),
                var(--dark-purple);
        }

        .auth-card {
            width: min(430px, 100%);
            background: white;
            border-radius: 24px;
            padding: 35px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.25);
        }

        .auth-title {
            margin: 0;
            font-size: 38px;
            font-weight: 900;
            color: var(--dark-red);
            letter-spacing: -1.5px;
        }

        .auth-subtitle {
            margin: 7px 0 28px;
            color: var(--muted);
        }

        .auth-input {
            width: 100%;
            padding: 15px;
            border: 2px solid var(--border);
            border-radius: 12px;
            outline: none;
            margin-bottom: 12px;
            background: #fff;
        }

        .auth-input:focus {
            border-color: var(--purple);
        }

        .auth-button {
            width: 100%;
            border: none;
            padding: 14px;
            border-radius: 12px;
            color: white;
            font-weight: 800;
            background: linear-gradient(135deg, var(--red), var(--purple));
            margin-top: 4px;
        }

        .auth-switch {
            text-align: center;
            margin-top: 20px;
            color: var(--muted);
            font-size: 14px;
        }

        .auth-switch button {
            border: none;
            background: none;
            color: var(--purple);
            font-weight: 800;
        }

        #auth-message {
            min-height: 20px;
            margin-top: 15px;
            text-align: center;
            font-size: 14px;
            color: var(--danger);
        }

        /* =========================
           APP
        ========================= */

        #app {
            display: none;
        }

        .topbar {
            position: sticky;
            top: 0;
            z-index: 100;
            height: 68px;
            background: white;
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 10px rgba(50, 16, 92, 0.08);
        }

        .topbar-inner {
            width: min(1100px, 100%);
            padding: 0 18px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 15px;
        }

        .brand {
            font-size: 25px;
            font-weight: 900;
            color: var(--dark-red);
            white-space: nowrap;
        }

        .brand span {
            color: var(--purple);
        }

        .nav {
            display: flex;
            gap: 7px;
            align-items: center;
        }

        .nav-button {
            border: none;
            background: transparent;
            color: var(--muted);
            padding: 10px 14px;
            border-radius: 10px;
            font-weight: 700;
        }

        .nav-button:hover {
            background: var(--soft);
            color: var(--purple);
        }

        .logout-button {
            border: none;
            background: var(--dark-red);
            color: white;
            padding: 9px 13px;
            border-radius: 9px;
            font-weight: 700;
        }

        /* =========================
           MAIN
        ========================= */

        .app-container {
            width: min(1100px, 100%);
            margin: auto;
            padding: 22px 15px 60px;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        /* =========================
           FACEBOOK-STYLE HERO
        ========================= */

        .profile-banner {
            background: linear-gradient(
                135deg,
                var(--dark-purple),
                var(--dark-red),
                var(--red)
            );
            min-height: 230px;
            border-radius: 20px;
            padding: 30px;
            color: white;
            display: flex;
            align-items: flex-end;
            margin-bottom: 18px;
            box-shadow: 0 8px 25px rgba(50, 16, 92, 0.18);
        }

        .profile-banner h1 {
            margin: 0;
            font-size: clamp(35px, 7vw, 58px);
            line-height: 1;
            font-weight: 900;
        }

        .profile-banner p {
            margin: 9px 0 0;
            opacity: 0.9;
            font-size: 15px;
        }

        /* =========================
           CREATE POST
        ========================= */

        .create-post {
            background: var(--card);
            border-radius: 16px;
            border: 1px solid var(--border);
            padding: 18px;
            margin-bottom: 18px;
            box-shadow: 0 2px 10px rgba(50, 16, 92, 0.06);
        }

        .create-top {
            display: flex;
            gap: 12px;
            align-items: center;
        }

        .create-avatar {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--light-purple);
        }

        .post-input {
            flex: 1;
            min-height: 48px;
            border: none;
            outline: none;
            border-radius: 25px;
            background: var(--soft);
            padding: 13px 18px;
            resize: none;
        }

        .post-input:focus {
            outline: 2px solid var(--light-purple);
        }

        .create-actions {
            border-top: 1px solid var(--border);
            margin-top: 16px;
            padding-top: 12px;
            display: flex;
            gap: 8px;
        }

        .media-label {
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 7px;
            padding: 10px;
            border-radius: 9px;
            font-weight: 700;
            color: var(--muted);
            cursor: pointer;
        }

        .media-label:hover {
            background: var(--soft);
            color: var(--red);
        }

        .media-label input {
            display: none;
        }

        .media-icon {
            width: 19px;
            height: 19px;
            position: relative;
            display: inline-block;
        }

        .image-icon {
            border: 2px solid currentColor;
            border-radius: 4px;
        }

        .image-icon::before {
            content: "";
            position: absolute;
            left: 3px;
            bottom: 3px;
            width: 6px;
            height: 5px;
            border-left: 2px solid currentColor;
            border-top: 2px solid currentColor;
            transform: rotate(45deg);
        }

        .image-icon::after {
            content: "";
            position: absolute;
            right: 2px;
            top: 3px;
            width: 4px;
            height: 4px;
            border: 1.5px solid currentColor;
            border-radius: 50%;
        }

        .video-icon {
            border: 2px solid currentColor;
            border-radius: 4px;
        }

        .video-icon::after {
            content: "";
            position: absolute;
            left: 6px;
            top: 4px;
            border-left: 6px solid currentColor;
            border-top: 4px solid transparent;
            border-bottom: 4px solid transparent;
        }

        .post-button {
            width: 100%;
            margin-top: 12px;
            padding: 11px;
            border: none;
            border-radius: 9px;
            background: linear-gradient(90deg, var(--red), var(--purple));
            color: white;
            font-weight: 800;
        }

        #selected-file {
            margin-top: 8px;
            font-size: 13px;
            color: var(--muted);
        }

        /* =========================
           POST CARD
        ========================= */

        .post-card {
            background: white;
            border: 1px solid var(--border);
            border-radius: 16px;
            margin-bottom: 18px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(50, 16, 92, 0.06);
        }

        .post-header {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 15px 16px 10px;
        }

        .avatar {
            width: 46px;
            height: 46px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--light-purple);
        }

        .post-user {
            flex: 1;
        }

        .name-row {
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }

        .display-name {
            background: var(--dark-red);
            color: white;
            padding: 5px 9px;
            border-radius: 6px;
            font-weight: 800;
            font-size: 14px;
        }

        .post-time {
            color: var(--muted);
            font-size: 12px;
            margin-top: 4px;
        }

        .friend-button {
            border: none;
            background: var(--green);
            color: white;
            padding: 6px 9px;
            border-radius: 7px;
            font-size: 12px;
            font-weight: 800;
        }

        .friend-button.sent {
            background: var(--purple);
        }

        .friend-button.friend {
            background: var(--dark-purple);
        }

        .delete-button {
            border: none;
            background: transparent;
            color: var(--muted);
            font-size: 20px;
            padding: 5px 8px;
        }

        .delete-button:hover {
            color: var(--danger);
        }

        .post-content {
            padding: 5px 17px 14px;
            font-size: 17px;
            line-height: 1.55;
            color: #211729;
            white-space: pre-wrap;
            overflow-wrap: anywhere;
        }

        .post-media {
            width: 100%;
            max-height: 650px;
            display: block;
            object-fit: contain;
            background: #130B18;
        }

        /* =========================
           POST ACTIONS
        ========================= */

        .post-actions {
            border-top: 1px solid var(--border);
            display: flex;
            padding: 4px 10px;
        }

        .action-button {
            flex: 1;
            border: none;
            background: transparent;
            color: var(--muted);
            font-weight: 700;
            font-size: 13px;
            padding: 8px;
            border-radius: 7px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 7px;
        }

        .action-button:hover {
            background: var(--soft);
            color: var(--red);
        }

        .action-button.liked {
            color: var(--red);
        }

        /* Manual like icon */
        .like-icon {
            width: 15px;
            height: 15px;
            position: relative;
            display: inline-block;
            transform: rotate(-45deg);
            border-left: 2px solid currentColor;
            border-bottom: 2px solid currentColor;
        }

        .like-icon::before,
        .like-icon::after {
            content: "";
            position: absolute;
            border: 2px solid currentColor;
        }

        .like-icon::before {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            left: -2px;
            top: -5px;
            border-bottom: none;
        }

        .like-icon::after {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            left: 5px;
            top: 2px;
            border-left: none;
        }

        .comment-icon {
            width: 17px;
            height: 13px;
            border: 2px solid currentColor;
            border-radius: 7px;
            display: inline-block;
            position: relative;
        }

        .comment-icon::after {
            content: "";
            position: absolute;
            bottom: -5px;
            left: 3px;
            width: 6px;
            height: 6px;
            border-left: 2px solid currentColor;
            transform: skew(-25deg);
        }

        /* =========================
           COMMENTS
        ========================= */

        .comments {
            border-top: 1px solid var(--border);
            padding: 10px 15px 14px;
            background: #FCFAFD;
        }

        .comment {
            display: flex;
            gap: 9px;
            margin-bottom: 9px;
        }

        .comment-avatar {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            object-fit: cover;
        }

        .comment-bubble {
            background: var(--soft);
            border-radius: 13px;
            padding: 7px 11px;
            flex: 1;
        }

        .comment-name {
            font-weight: 800;
            color: var(--dark-red);
            font-size: 12px;
        }

        .comment-text {
            font-size: 13px;
            margin-top: 2px;
            line-height: 1.35;
        }

        .comment-form {
            display: flex;
            gap: 7px;
            margin-top: 8px;
        }

        .comment-input {
            flex: 1;
            border: 1px solid var(--border);
            background: white;
            border-radius: 20px;
            padding: 9px 13px;
            outline: none;
        }

        .comment-submit {
            border: none;
            background: var(--purple);
            color: white;
            border-radius: 20px;
            padding: 0 14px;
            font-weight: 700;
        }

        /* =========================
           PROFILE PAGE
        ========================= */

        .profile-card {
            background: white;
            border-radius: 18px;
            border: 1px solid var(--border);
            padding: 25px;
            text-align: center;
        }

        .profile-avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid var(--light-purple);
        }

        .profile-name {
            font-size: 28px;
            font-weight: 900;
            color: var(--dark-red);
            margin: 12px 0 2px;
        }

        .profile-username {
            color: var(--muted);
            margin-bottom: 10px;
        }

        .profile-bio {
            color: var(--text);
            margin-bottom: 20px;
        }

        .profile-edit {
            display: none;
            max-width: 500px;
            margin: 20px auto 0;
            text-align: left;
        }

        .profile-edit input,
        .profile-edit textarea {
            width: 100%;
            padding: 11px;
            border: 1px solid var(--border);
            border-radius: 9px;
            margin-bottom: 10px;
            resize: vertical;
        }

        .profile-edit button {
            width: 100%;
            border: none;
            padding: 11px;
            border-radius: 9px;
            background: var(--purple);
            color: white;
            font-weight: 800;
        }

        .edit-toggle {
            border: none;
            padding: 9px 15px;
            border-radius: 8px;
            background: var(--dark-red);
            color: white;
            font-weight: 700;
        }

        /* =========================
           SEARCH
        ========================= */

        .search-box {
            background: white;
            padding: 18px;
            border-radius: 16px;
            border: 1px solid var(--border);
            margin-bottom: 15px;
        }

        .search-input {
            width: 100%;
            padding: 14px;
            border: 2px solid var(--border);
            border-radius: 12px;
            outline: none;
        }

        .search-input:focus {
            border-color: var(--purple);
        }

        .search-result {
            background: white;
            border: 1px solid var(--border);
            border-radius: 14px;
            padding: 13px;
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 10px;
        }

        .search-result-info {
            flex: 1;
        }

        .search-result-name {
            font-weight: 900;
            color: var(--dark-red);
        }

        .search-result-username {
            font-size: 13px;
            color: var(--muted);
        }

        /* =========================
           EMPTY / STATUS
        ========================= */

        .status {
            text-align: center;
            color: var(--muted);
            padding: 30px 10px;
        }

        .error {
            color: var(--danger);
        }

        /* =========================
           MOBILE
        ========================= */

        @media (max-width: 700px) {

            .topbar {
                height: auto;
                min-height: 62px;
            }

            .topbar-inner {
                padding: 9px 10px;
            }

            .brand {
                font-size: 19px;
            }

            .nav {
                gap: 2px;
            }

            .nav-button {
                padding: 8px;
                font-size: 12px;
            }

            .logout-button {
                padding: 7px;
                font-size: 11px;
            }

            .app-container {
                padding: 12px 9px 40px;
            }

            .profile-banner {
                min-height: 190px;
                padding: 23px;
                border-radius: 15px;
            }

            .profile-banner h1 {
                font-size: 39px;
            }

            .create-actions {
                gap: 2px;
            }

            .media-label {
                font-size: 12px;
                padding: 8px 3px;
            }

            .post-card {
                border-radius: 13px;
            }

            .post-content {
                font-size: 16px;
            }

            .post-header {
                padding: 12px;
            }

            .display-name {
                font-size: 12px;
            }

            .friend-button {
                font-size: 10px;
                padding: 5px 7px;
            }

            .action-button {
                font-size: 12px;
            }
        }

        @media (max-width: 450px) {

            .brand {
                font-size: 16px;
            }

            .nav-button {
                font-size: 10px;
                padding: 6px;
            }

            .logout-button {
                font-size: 10px;
            }

            .profile-banner {
                min-height: 160px;
            }

            .profile-banner h1 {
                font-size: 32px;
            }
        }
    </style>
</head>

<body>

<!-- =========================
     AUTH SCREEN
========================= -->

<div id="auth-screen">

    <div class="auth-card">

        <h1 class="auth-title">DPSB SSMW</h1>

        <p class="auth-subtitle">
            Delhi Public School Budgam Secret Social Media Website
        </p>

        <input
            id="username"
            class="auth-input"
            type="text"
            placeholder="Username"
            autocomplete="username"
        >

        <input
            id="password"
            class="auth-input"
            type="password"
            placeholder="Password"
            autocomplete="current-password"
        >

        <button id="auth-button" class="auth-button">
            Log In
        </button>

        <div id="auth-message"></div>

        <div class="auth-switch">
            <span id="switch-text">Don't have an account?</span>
            <button id="switch-button">Sign Up</button>
        </div>

    </div>

</div>


<!-- =========================
     MAIN APP
========================= -->

<div id="app">

    <header class="topbar">

        <div class="topbar-inner">

            <div class="brand">
                DPSB <span>SSMW</span>
            </div>

            <nav class="nav">

                <button
                    class="nav-button"
                    onclick="showPage('home')"
                >
                    Home
                </button>

                <button
                    class="nav-button"
                    onclick="showPage('search')"
                >
                    Search
                </button>

                <button
                    class="nav-button"
                    onclick="showPage('profile')"
                >
                    Profile
                </button>

                <button
                    class="logout-button"
                    onclick="logout()"
                >
                    Log Out
                </button>

            </nav>

        </div>

    </header>


    <main class="app-container">

        <!-- HOME -->

        <section id="home-page" class="page active">

            <div class="profile-banner">

                <div>
                    <h1>DPSB SSMW</h1>
                    <p>
                        Delhi Public School Budgam Secret Social Media Website
                    </p>
                </div>

            </div>


            <!-- CREATE POST -->

            <div class="create-post">

                <div class="create-top">

                    <img
                        id="create-avatar"
                        class="create-avatar"
                        alt="Profile"
                    >

                    <textarea
                        id="post-content"
                        class="post-input"
                        placeholder="What's on your mind?"
                        maxlength="1000"
                    ></textarea>

                </div>


                <div class="create-actions">

                    <label class="media-label">

                        <span class="media-icon image-icon"></span>

                        <span>Image</span>

                        <input
                            type="file"
                            id="image-input"
                            accept="image/*"
                        >

                    </label>


                    <label class="media-label">

                        <span class="media-icon video-icon"></span>

                        <span>Video</span>

                        <input
                            type="file"
                            id="video-input"
                            accept="video/*"
                        >

                    </label>

                </div>

                <div id="selected-file"></div>

                <button
                    class="post-button"
                    onclick="createPost()"
                >
                    Post
                </button>

            </div>


            <div id="feed">

                <div class="status">
                    Loading posts...
                </div>

            </div>

        </section>


        <!-- SEARCH -->

        <section id="search-page" class="page">

            <div class="search-box">

                <h2>Search People</h2>

                <input
                    id="search-input"
                    class="search-input"
                    placeholder="Search by username..."
                    oninput="searchProfiles()"
                >

            </div>

            <div id="search-results"></div>

        </section>


        <!-- PROFILE -->

        <section id="profile-page" class="page">

            <div class="profile-card">

                <img
                    id="profile-avatar"
                    class="profile-avatar"
                    alt="Profile"
                >

                <div
                    id="profile-display-name"
                    class="profile-name"
                >
                    Loading...
                </div>

                <div
                    id="profile-username"
                    class="profile-username"
                ></div>

                <div
                    id="profile-bio"
                    class="profile-bio"
                ></div>

                <button
                    class="edit-toggle"
                    onclick="toggleProfileEdit()"
                >
                    Edit Profile
                </button>


                <div
                    id="profile-edit"
                    class="profile-edit"
                >

                    <input
                        id="edit-display-name"
                        placeholder="Display name"
                    >

                    <textarea
                        id="edit-bio"
                        placeholder="Bio"
                        maxlength="300"
                    ></textarea>

                    <input
                        type="file"
                        id="avatar-input"
                        accept="image/*"
                    >

                    <button onclick="saveProfile()">
                        Save Profile
                    </button>

                </div>

            </div>

        </section>

    </main>

</div>


<script>

    /* =========================================
       SUPABASE
    ========================================= */

    const SUPABASE_URL =
        "https://soirkzbrsmgxydmikerx.supabase.co";

    const SUPABASE_KEY =
        "sb_publishable_YfZn0IZdTs8L-EThj6lxOg_uFQCDxIp";

    const supabaseClient =
        supabase.createClient(
            SUPABASE_URL,
            SUPABASE_KEY
        );


    let currentUser = null;
    let currentProfile = null;
    let loginMode = true;


    /* =========================================
       INTERNAL EMAIL
    ========================================= */

    function usernameToInternalEmail(username) {

        return username
            .toLowerCase()
            .trim()
            + "@dpsbssmw.local";

    }


    /* =========================================
       DEFAULT AVATAR
    ========================================= */

    function defaultAvatar(name = "U") {

        const letter =
            String(name || "U")
                .trim()
                .charAt(0)
                .toUpperCase();

        const svg = `
            <svg xmlns="http://www.w3.org/2000/svg"
                 width="200"
                 height="200"
                 viewBox="0 0 200 200">

                <rect width="200"
                      height="200"
                      fill="#6D28D9"/>

                <text
                    x="100"
                    y="125"
                    text-anchor="middle"
                    font-size="90"
                    font-family="Arial"
                    font-weight="bold"
                    fill="white">
                    ${letter}
                </text>

            </svg>
        `;

        return "data:image/svg+xml;charset=UTF-8," +
            encodeURIComponent(svg);
    }


    /* =========================================
       HTML ESCAPE
    ========================================= */

    function escapeHTML(value) {

        if (value === null || value === undefined) {
            return "";
        }

        return String(value)
            .replaceAll("&", "&amp;")
            .replaceAll("<", "&lt;")
            .replaceAll(">", "&gt;")
            .replaceAll('"', "&quot;")
            .replaceAll("'", "&#039;");
    }


    /* =========================================
       AUTH UI
    ========================================= */

    const authButton =
        document.getElementById("auth-button");

    const switchButton =
        document.getElementById("switch-button");

    const switchText =
        document.getElementById("switch-text");

    const authMessage =
        document.getElementById("auth-message");


    switchButton.addEventListener("click", () => {

        loginMode = !loginMode;

        if (loginMode) {

            authButton.textContent = "Log In";
            switchText.textContent =
                "Don't have an account?";
            switchButton.textContent = "Sign Up";

        } else {

            authButton.textContent = "Create Account";
            switchText.textContent =
                "Already have an account?";
            switchButton.textContent = "Log In";

        }

        authMessage.textContent = "";

    });


    authButton.addEventListener("click", handleAuth);


    async function handleAuth() {

        const username =
            document.getElementById("username")
                .value
                .trim();

        const password =
            document.getElementById("password")
                .value;

        authMessage.textContent = "";

        if (!username || !password) {

            authMessage.textContent =
                "Enter a username and password.";

            return;
        }

        if (username.length < 3) {

            authMessage.textContent =
                "Username must be at least 3 characters.";

            return;
        }

        if (password.length < 6) {

            authMessage.textContent =
                "Password must be at least 6 characters.";

            return;
        }


        const email =
            usernameToInternalEmail(username);


        try {

            if (loginMode) {

                const { error } =
                    await supabaseClient.auth.signInWithPassword({
                        email,
                        password
                    });

                if (error) {
                    throw error;
                }

            } else {

                const { error } =
                    await supabaseClient.auth.signUp({

                        email,
                        password,

                        options: {
                            data: {
                                username: username,
                                display_name: username
                            }
                        }

                    });

                if (error) {
                    throw error;
                }

            }

        } catch (error) {

            console.error(error);

            authMessage.textContent =
                error.message || "Authentication failed.";

        }

    }


    /* =========================================
       INITIAL SESSION
    ========================================= */

    async function initialize() {

        const {
            data: {
                session
            }
        } = await supabaseClient.auth.getSession();


        if (session) {

            currentUser = session.user;

            await enterApp();

        } else {

            showAuth();

        }

    }


    supabaseClient.auth.onAuthStateChange(
        async (_event, session) => {

            if (session) {

                currentUser = session.user;

                await enterApp();

            } else {

                currentUser = null;
                currentProfile = null;

                showAuth();

            }

        }
    );


    async function enterApp() {

        document.getElementById("auth-screen")
            .style.display = "none";

        document.getElementById("app")
            .style.display = "block";


        await loadCurrentProfile();

        await loadFeed();

    }


    function showAuth() {

        document.getElementById("auth-screen")
            .style.display = "flex";

        document.getElementById("app")
            .style.display = "none";

    }


    /* =========================================
       PROFILE
    ========================================= */

    async function loadCurrentProfile() {

        if (!currentUser) return;


        const {
            data,
            error
        } = await supabaseClient
            .from("profiles")
            .select("*")
            .eq("id", currentUser.id)
            .single();


        if (error) {

            console.error(error);

            return;

        }


        currentProfile = data;


        const avatar =
            currentProfile.avatar_url ||
            defaultAvatar(currentProfile.display_name);


        document.getElementById("create-avatar")
            .src = avatar;

        document.getElementById("profile-avatar")
            .src = avatar;

        document.getElementById("profile-display-name")
            .textContent =
            currentProfile.display_name;

        document.getElementById("profile-username")
            .textContent =
            "@" + currentProfile.username;

        document.getElementById("profile-bio")
            .textContent =
            currentProfile.bio || "";


        document.getElementById("edit-display-name")
            .value =
            currentProfile.display_name;

        document.getElementById("edit-bio")
            .value =
            currentProfile.bio || "";

    }


    function toggleProfileEdit() {

        const box =
            document.getElementById("profile-edit");

        box.style.display =
            box.style.display === "block"
                ? "none"
                : "block";

    }


    async function saveProfile() {

        if (!currentUser) return;


        const displayName =
            document.getElementById("edit-display-name")
                .value
                .trim();

        const bio =
            document.getElementById("edit-bio")
                .value
                .trim();


        if (!displayName) {

            alert("Display name cannot be empty.");

            return;

        }


        let avatarUrl =
            currentProfile.avatar_url;


        const file =
            document.getElementById("avatar-input")
                .files[0];


        try {

            if (file) {

                const extension =
                    file.name
                        .split(".")
                        .pop()
                        .toLowerCase();

                const path =
                    currentUser.id +
                    "/avatar." +
                    extension;


                const {
                    error: uploadError
                } = await supabaseClient
                    .storage
                    .from("avatars")
                    .upload(
                        path,
                        file,
                        {
                            upsert: true,
                            contentType: file.type
                        }
                    );


                if (uploadError) {
                    throw uploadError;
                }


                const {
                    data
                } = supabaseClient
                    .storage
                    .from("avatars")
                    .getPublicUrl(path);


                avatarUrl =
                    data.publicUrl;

            }


            const {
                error
            } = await supabaseClient
                .from("profiles")
                .update({

                    display_name:
                        displayName,

                    bio:
                        bio,

                    avatar_url:
                        avatarUrl

                })
                .eq(
                    "id",
                    currentUser.id
                );


            if (error) {
                throw error;
            }


            await loadCurrentProfile();

            await loadFeed();


            document.getElementById("profile-edit")
                .style.display = "none";


        } catch (error) {

            console.error(error);

            alert(
                "Could not update profile: " +
                error.message
            );

        }

    }


    /* =========================================
       PAGE NAVIGATION
    ========================================= */

    function showPage(page) {

        document
            .querySelectorAll(".page")
            .forEach(element => {

                element.classList.remove("active");

            });


        document
            .getElementById(page + "-page")
            .classList.add("active");


        if (page === "home") {
            loadFeed();
        }

        if (page === "profile") {
            loadCurrentProfile();
        }

    }


    /* =========================================
       FILE SELECTION
    ========================================= */

    const imageInput =
        document.getElementById("image-input");

    const videoInput =
        document.getElementById("video-input");

    const selectedFile =
        document.getElementById("selected-file");


    imageInput.addEventListener("change", () => {

        if (imageInput.files.length) {

            videoInput.value = "";

            selectedFile.textContent =
                imageInput.files[0].name;

        }

    });


    videoInput.addEventListener("change", () => {

        if (videoInput.files.length) {

            imageInput.value = "";

            selectedFile.textContent =
                videoInput.files[0].name;

        }

    });


    /* =========================================
       CREATE POST
    ========================================= */

    async function createPost() {

        if (!currentUser) return;


        const content =
            document.getElementById("post-content")
                .value
                .trim();


        const image =
            imageInput.files[0];

        const video =
            videoInput.files[0];

        const file =
            image || video;


        if (!content && !file) {

            alert(
                "Write something or choose a photo/video."
            );

            return;

        }


        try {

            let mediaUrl = null;
            let mediaType = null;


            if (file) {

                mediaType =
                    image ? "image" : "video";


                const extension =
                    file.name
                        .split(".")
                        .pop()
                        .toLowerCase();


                const uniqueName =
                    Date.now() +
                    "_" +
                    Math.random()
                        .toString(36)
                        .slice(2);


                const path =
                    currentUser.id +
                    "/" +
                    uniqueName +
                    "." +
                    extension;


                const {
                    error: uploadError
                } = await supabaseClient
                    .storage
                    .from("post-media")
                    .upload(
                        path,
                        file,
                        {
                            contentType: file.type
                        }
                    );


                if (uploadError) {
                    throw uploadError;
                }


                const {
                    data
                } = supabaseClient
                    .storage
                    .from("post-media")
                    .getPublicUrl(path);


                mediaUrl =
                    data.publicUrl;

            }


            const {
                error
            } = await supabaseClient
                .from("posts")
                .insert({

                    user_id:
                        currentUser.id,

                    content:
                        content || null,

                    media_url:
                        mediaUrl,

                    media_type:
                        mediaType

                });


            if (error) {
                throw error;
            }


            document.getElementById("post-content")
                .value = "";

            imageInput.value = "";
            videoInput.value = "";

            selectedFile.textContent = "";


            await loadFeed();


        } catch (error) {

            console.error(error);

            alert(
                "Could not create post: " +
                error.message
            );

        }

    }


    /* =========================================
       LOAD FEED
    ========================================= */

    async function loadFeed() {

        const feed =
            document.getElementById("feed");


        feed.innerHTML =
            '<div class="status">Loading posts...</div>';


        try {

            const {
                data: posts,
                error: postsError
            } = await supabaseClient
                .from("posts")
                .select("*")
                .order(
                    "created_at",
                    {
                        ascending: false
                    }
                );


            if (postsError) {
                throw postsError;
            }


            if (!posts || posts.length === 0) {

                feed.innerHTML =
                    '<div class="status">No posts yet.</div>';

                return;

            }


            const userIds =
                [
                    ...new Set(
                        posts.map(
                            post => post.user_id
                        )
                    )
                ];


            const {
                data: profiles,
                error: profilesError
            } = await supabaseClient
                .from("profiles")
                .select("*")
                .in("id", userIds);


            if (profilesError) {
                throw profilesError;
            }


            const profileMap =
                new Map(
                    profiles.map(
                        profile => [
                            profile.id,
                            profile
                        ]
                    )
                );


            const postIds =
                posts.map(
                    post => post.id
                );


            const {
                data: likes
            } = await supabaseClient
                .from("likes")
                .select("*")
                .in(
                    "post_id",
                    postIds
                );


            const {
                data: comments
            } = await supabaseClient
                .from("comments")
                .select("*")
                .in(
                    "post_id",
                    postIds
                )
                .order(
                    "created_at",
                    {
                        ascending: true
                    }
                );


            const commentUserIds =
                [
                    ...new Set(
                        (comments || [])
                            .map(
                                comment =>
                                    comment.user_id
                            )
                    )
                ];


            let commentProfiles = [];


            if (commentUserIds.length) {

                const {
                    data
                } = await supabaseClient
                    .from("profiles")
                    .select("*")
