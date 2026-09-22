# dpsbssmw
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport"
      content="width=device-width, initial-scale=1.0, viewport-fit=cover">

<title>DPSB SSMW</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
    :root {
        --brown: #6F4E37;
        --olive: #B2AC88;
        --cream: #F5F5DC;

        --friend-green: #4F7D45;
        --white: #FFFFFF;
    }

    * {
        box-sizing: border-box;
    }

    html,
    body {
        margin: 0;
        padding: 0;
        min-height: 100%;
        font-family: Arial, Helvetica, sans-serif;
        background: var(--olive);
        color: var(--brown);
    }

    body {
        min-height: 100vh;
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
       AUTH
       ========================= */

    #authScreen {
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 24px;
        background: var(--olive);
    }

    .auth-box {
        width: min(440px, 100%);
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 28px;
        padding: 32px;
    }

    .auth-brand {
        color: var(--brown);
        font-size: 14px;
        font-weight: 800;
        letter-spacing: 2px;
        margin-bottom: 8px;
    }

    .auth-title {
        margin: 0;
        font-size: 38px;
        font-weight: 900;
        color: var(--brown);
    }

    .auth-subtitle {
        margin: 8px 0 28px;
        font-size: 15px;
        font-weight: 700;
        color: var(--brown);
    }

    .auth-box input {
        width: 100%;
        padding: 15px 16px;
        margin-bottom: 12px;
        border: 2px solid var(--brown);
        border-radius: 14px;
        background: var(--cream);
        color: var(--brown);
        outline: none;
        font-size: 17px;
        font-weight: 600;
    }

    .auth-box input:focus {
        border-width: 3px;
    }

    .primary-button {
        width: 100%;
        border: 0;
        border-radius: 14px;
        padding: 15px;
        background: var(--brown);
        color: var(--cream);
        font-weight: 900;
        font-size: 17px;
        margin-top: 4px;
    }

    .secondary-button {
        width: 100%;
        border: 2px solid var(--brown);
        border-radius: 14px;
        padding: 13px;
        background: var(--cream);
        color: var(--brown);
        font-weight: 900;
        margin-top: 10px;
    }

    .auth-message {
        margin-top: 14px;
        font-size: 14px;
        font-weight: 700;
        color: var(--brown);
        text-align: center;
        min-height: 20px;
    }

    /* =========================
       MAIN APP
       ========================= */

    #appScreen {
        display: none;
        min-height: 100vh;
        padding: 18px;
    }

    .app-container {
        width: min(900px, 100%);
        margin: 0 auto;
    }

    /* =========================
       BANNER
       ========================= */

    .top-banner {
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 30px;
        padding: 26px 28px;
        margin-bottom: 18px;
    }

    .product-name {
        color: var(--brown);
        font-size: 14px;
        font-weight: 900;
        letter-spacing: 2px;
        margin-bottom: 6px;
    }

    .site-title {
        margin: 0;
        color: var(--brown);
        font-size: clamp(36px, 8vw, 64px);
        line-height: 0.95;
        font-weight: 950;
        letter-spacing: -2px;
    }

    .site-subtitle {
        margin: 12px 0 0;
        color: var(--brown);
        font-size: 16px;
        font-weight: 800;
        line-height: 1.4;
    }

    /* =========================
       NAVIGATION
       ========================= */

    .nav-bar {
        display: flex;
        gap: 8px;
        flex-wrap: wrap;
        margin-bottom: 18px;
    }

    .nav-button {
        border: 2px solid var(--brown);
        background: var(--cream);
        color: var(--brown);
        border-radius: 12px;
        padding: 10px 15px;
        font-size: 14px;
        font-weight: 900;
    }

    .nav-button.active {
        background: var(--brown);
        color: var(--cream);
    }

    .logout-button {
        margin-left: auto;
    }

    /* =========================
       SECTIONS
       ========================= */

    .section {
        display: none;
    }

    .section.active {
        display: block;
    }

    /* =========================
       CREATE POST
       ========================= */

    .create-post {
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 24px;
        padding: 20px;
        margin-bottom: 18px;
    }

    .create-post textarea {
        width: 100%;
        min-height: 100px;
        resize: vertical;
        border: 2px solid var(--brown);
        border-radius: 16px;
        padding: 15px;
        background: var(--cream);
        color: var(--brown);
        font-size: 18px;
        font-weight: 600;
        outline: none;
    }

    .create-post textarea::placeholder {
        color: var(--brown);
        opacity: 0.75;
    }

    .post-tools {
        display: flex;
        align-items: center;
        gap: 9px;
        flex-wrap: wrap;
        margin-top: 12px;
    }

    .tool-button {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 7px;

        border: 2px solid var(--brown);
        border-radius: 11px;
        padding: 9px 12px;

        background: var(--cream);
        color: var(--brown);

        font-size: 13px;
        font-weight: 900;
    }

    .tool-icon {
        width: 19px;
        height: 19px;
        position: relative;
        display: inline-block;
    }

    /* Custom image icon */
    .image-icon {
        border: 2px solid var(--brown);
        border-radius: 4px;
    }

    .image-icon::before {
        content: "";
        position: absolute;
        width: 4px;
        height: 4px;
        border-radius: 50%;
        background: var(--brown);
        top: 3px;
        right: 3px;
    }

    .image-icon::after {
        content: "";
        position: absolute;
        width: 9px;
        height: 7px;
        border-left: 2px solid var(--brown);
        border-top: 2px solid var(--brown);
        transform: rotate(45deg);
        left: 3px;
        bottom: 1px;
    }

    /* Custom video icon */
    .video-icon {
        border: 2px solid var(--brown);
        border-radius: 4px;
    }

    .video-icon::after {
        content: "";
        position: absolute;
        right: -6px;
        top: 4px;
        width: 0;
        height: 0;
        border-top: 5px solid transparent;
        border-bottom: 5px solid transparent;
        border-left: 6px solid var(--brown);
    }

    .publish-button {
        margin-left: auto;
        border: 0;
        border-radius: 11px;
        padding: 11px 18px;
        background: var(--brown);
        color: var(--cream);
        font-weight: 900;
    }

    #mediaInput {
        display: none;
    }

    .selected-file {
        width: 100%;
        font-size: 13px;
        font-weight: 800;
        margin-top: 7px;
        color: var(--brown);
    }

    /* =========================
       SEARCH
       ========================= */

    .search-box {
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 20px;
        padding: 14px;
        margin-bottom: 18px;
    }

    .search-box input {
        width: 100%;
        border: 2px solid var(--brown);
        border-radius: 13px;
        padding: 13px 15px;
        background: var(--cream);
        color: var(--brown);
        font-size: 17px;
        font-weight: 700;
        outline: none;
    }

    /* =========================
       POST CARD
       ========================= */

    .post-card {
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 24px;
        padding: 18px;
        margin-bottom: 18px;
    }

    .post-header {
        display: flex;
        align-items: center;
        gap: 12px;
    }

    .avatar {
        width: 54px;
        height: 54px;
        min-width: 54px;
        object-fit: cover;
        border-radius: 10px;
        border: 2px solid var(--brown);
        background: var(--olive);
    }

    .post-user-info {
        min-width: 0;
        flex: 1;
    }

    /*
       Display name gets the requested brown background
       and white text.
    */
    .display-name {
        display: inline-block;
        background: var(--brown);
        color: var(--white);
        border-radius: 8px;
        padding: 5px 9px;
        font-size: 16px;
        font-weight: 900;
        line-height: 1.1;
    }

    .username {
        display: block;
        margin-top: 4px;
        color: var(--brown);
        font-size: 13px;
        font-weight: 800;
    }

    /*
       Two-circle friend button
       with green background.
    */
    .friend-button {
        position: relative;
        width: 48px;
        height: 38px;
        min-width: 48px;
        border: 0;
        border-radius: 11px;
        background: var(--friend-green);
        color: var(--white);
        overflow: hidden;
    }

    .friend-button::before,
    .friend-button::after {
        content: "";
        position: absolute;
        top: 8px;
        width: 13px;
        height: 13px;
        border: 2px solid var(--white);
        border-radius: 50%;
    }

    .friend-button::before {
        left: 9px;
    }

    .friend-button::after {
        right: 9px;
    }

    .friend-button span {
        position: absolute;
        left: 50%;
        bottom: 5px;
        transform: translateX(-50%);
        width: 28px;
        height: 9px;
        border: 2px solid var(--white);
        border-bottom: 0;
        border-radius: 12px 12px 0 0;
    }

    .friend-button.sent {
        background: var(--brown);
    }

    .friend-button.friends {
        background: var(--friend-green);
    }

    /* =========================
       POST CONTENT
       ========================= */

    .post-content {
        margin-top: 18px;
        color: var(--brown);
        font-size: 19px;
        line-height: 1.55;
        font-weight: 650;
        white-space: pre-wrap;
        overflow-wrap: anywhere;
    }

    .post-media {
        width: 100%;
        max-height: 650px;
        object-fit: contain;
        display: block;
        margin-top: 17px;
        border: 2px solid var(--brown);
        border-radius: 15px;
        background: var(--olive);
    }

    /* =========================
       POST ACTIONS
       ========================= */

    /*
       No divider line.
       No emojis.
       Compact buttons.
    */
    .post-actions {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-top: 14px;
        padding-top: 0;
        border-top: 0;
    }

    .action-button {
        border: 0;
        background: transparent;
        color: var(--brown);

        display: inline-flex;
        align-items: center;
        gap: 6px;

        padding: 5px 7px;
        border-radius: 8px;

        font-size: 13px;
        font-weight: 900;
    }

    .action-button:hover {
        background: var(--olive);
    }

    .action-icon {
        width: 18px;
        height: 18px;
        position: relative;
        display: inline-block;
    }

    /* CSS thumbs-up */
    .like-icon {
        width: 17px;
        height: 13px;
        border: 2px solid var(--brown);
        border-radius: 4px;
        margin-top: 4px;
    }

    .like-icon::before {
        content: "";
        position: absolute;
        width: 7px;
        height: 9px;
        border: 2px solid var(--brown);
        border-bottom: 0;
        border-radius: 6px 6px 0 0;
        left: 3px;
        top: -8px;
        transform: rotate(-8deg);
        background: var(--cream);
    }

    .like-icon::after {
        content: "";
        position: absolute;
        width: 4px;
        height: 6px;
        border-left: 2px solid var(--brown);
        left: -5px;
        top: 3px;
    }

    /* CSS comment bubble */
    .comment-icon {
        width: 18px;
        height: 14px;
        border: 2px solid var(--brown);
        border-radius: 5px;
    }

    .comment-icon::after {
        content: "";
        position: absolute;
        left: 3px;
        bottom: -5px;
        width: 6px;
        height: 6px;
        border-left: 2px solid var(--brown);
        border-bottom: 2px solid var(--brown);
        transform: skewY(-25deg);
        background: var(--cream);
    }

    .liked .like-icon {
        background: var(--brown);
    }

    .liked {
        background: var(--olive);
    }

    /* =========================
       COMMENTS
       ========================= */

    .comments-area {
        display: none;
        margin-top: 12px;
    }

    .comments-area.open {
        display: block;
    }

    .comment-list {
        margin-bottom: 10px;
    }

    .comment-item {
        border: 2px solid var(--brown);
        border-radius: 12px;
        padding: 9px 11px;
        margin-bottom: 7px;
        background: var(--olive);
    }

    .comment-name {
        font-size: 13px;
        font-weight: 900;
        color: var(--brown);
    }

    .comment-text {
        margin-top: 3px;
        font-size: 14px;
        font-weight: 650;
        color: var(--brown);
        overflow-wrap: anywhere;
    }

    .comment-form {
        display: flex;
        gap: 7px;
    }

    .comment-input {
        flex: 1;
        min-width: 0;
        border: 2px solid var(--brown);
        border-radius: 11px;
        padding: 10px;
        background: var(--cream);
        color: var(--brown);
        font-size: 14px;
        outline: none;
    }

    .comment-submit {
        border: 0;
        border-radius: 10px;
        padding: 9px 13px;
        background: var(--brown);
        color: var(--cream);
        font-weight: 900;
    }

    /* =========================
       PROFILE
       ========================= */

    .profile-card {
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 24px;
        padding: 22px;
    }

    .profile-top {
        display: flex;
        gap: 16px;
        align-items: center;
    }

    .profile-avatar {
        width: 96px;
        height: 96px;
        min-width: 96px;
        border-radius: 14px;
        object-fit: cover;
        border: 3px solid var(--brown);
        background: var(--olive);
    }

    .profile-name {
        display: inline-block;
        background: var(--brown);
        color: var(--white);
        border-radius: 9px;
        padding: 7px 10px;
        font-size: 23px;
        font-weight: 900;
    }

    .profile-username {
        margin-top: 5px;
        font-size: 15px;
        font-weight: 800;
    }

    .profile-bio {
        margin-top: 18px;
        font-size: 17px;
        line-height: 1.5;
        font-weight: 650;
    }

    .profile-edit {
        margin-top: 20px;
        padding-top: 18px;
        border-top: 2px solid var(--brown);
    }

    .profile-edit input,
    .profile-edit textarea {
        width: 100%;
        margin-bottom: 10px;
        padding: 12px;
        border: 2px solid var(--brown);
        border-radius: 12px;
        background: var(--cream);
        color: var(--brown);
        font-weight: 650;
        outline: none;
    }

    .profile-edit textarea {
        min-height: 90px;
        resize: vertical;
    }

    /* =========================
       SEARCH RESULTS
       ========================= */

    .search-result {
        display: flex;
        align-items: center;
        gap: 12px;
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 18px;
        padding: 13px;
        margin-bottom: 10px;
    }

    .search-result .avatar {
        width: 48px;
        height: 48px;
        min-width: 48px;
    }

    .search-info {
        flex: 1;
        min-width: 0;
    }

    .search-display {
        display: inline-block;
        background: var(--brown);
        color: var(--white);
        border-radius: 7px;
        padding: 4px 7px;
        font-size: 15px;
        font-weight: 900;
    }

    .search-username {
        margin-top: 3px;
        font-size: 12px;
        font-weight: 800;
    }

    /* =========================
       GENERAL
       ========================= */

    .loading,
    .empty {
        background: var(--cream);
        border: 3px solid var(--brown);
        border-radius: 20px;
        padding: 25px;
        text-align: center;
        font-size: 17px;
        font-weight: 800;
    }

    .status {
        margin-top: 10px;
        font-size: 13px;
        font-weight: 800;
    }

    .hidden {
        display: none !important;
    }

    /* =========================
       MOBILE
       ========================= */

    @media (max-width: 600px) {

        #appScreen {
            padding: 10px;
        }

        .top-banner {
            padding: 20px;
            border-radius: 23px;
        }

        .site-title {
            font-size: 40px;
        }

        .site-subtitle {
            font-size: 14px;
        }

        .nav-button {
            flex: 1;
            min-width: 0;
            padding: 9px 8px;
        }

        .logout-button {
            margin-left: 0;
        }

        .post-card {
            padding: 14px;
            border-radius: 19px;
        }

        .post-content {
            font-size: 18px;
        }

        .avatar {
            width: 48px;
            height: 48px;
            min-width: 48px;
        }

        .display-name {
            font-size: 14px;
        }

        .friend-button {
            width: 44px;
            min-width: 44px;
        }

        .post-tools {
            align-items: stretch;
        }

        .tool-button {
            flex: 1;
        }

        .publish-button {
            width: 100%;
            margin-left: 0;
        }

        .profile-top {
            align-items: flex-start;
        }

        .profile-avatar {
            width: 78px;
            height: 78px;
            min-width: 78px;
        }

        .profile-name {
            font-size: 19px;
        }
    }
</style>
</head>

<body>

<!-- =========================================================
     AUTH SCREEN
     ========================================================= -->

<div id="authScreen">

    <div class="auth-box">

        <div class="auth-brand">[ZaheenProduct]</div>

        <h1 class="auth-title">DPSB SSMW</h1>

        <p class="auth-subtitle">
            Delhi Public School Budgam Secret Social Media Website
        </p>

        <div id="loginForm">

            <input
                id="loginUsername"
                type="text"
                placeholder="Username"
                autocomplete="username"
            >

            <input
                id="loginPassword"
                type="password"
                placeholder="Password"
                autocomplete="current-password"
            >

            <button
                class="primary-button"
                onclick="login()"
            >
                Log In
            </button>

            <button
                class="secondary-button"
                onclick="showSignup()"
            >
                Create Account
            </button>

        </div>

        <div id="signupForm" class="hidden">

            <input
                id="signupUsername"
                type="text"
                placeholder="Username"
                autocomplete="username"
            >

            <input
                id="signupDisplayName"
                type="text"
                placeholder="Display name"
            >

            <input
                id="signupPassword"
                type="password"
                placeholder="Password"
                autocomplete="new-password"
            >

            <button
                class="primary-button"
                onclick="signup()"
            >
                Create Account
            </button>

            <button
                class="secondary-button"
                onclick="showLogin()"
            >
                Back to Login
            </button>

        </div>

        <div id="authMessage" class="auth-message"></div>

    </div>

</div>


<!-- =========================================================
     APP SCREEN
     ========================================================= -->

<div id="appScreen">

    <div class="app-container">

        <!-- BANNER -->

        <header class="top-banner">

            <div class="product-name">
                [ZaheenProduct]
            </div>

            <h1 class="site-title">
                [DPSB SSMW]
            </h1>

            <p class="site-subtitle">
                delhi public school budgam secret social media website
            </p>

        </header>


        <!-- NAV -->

        <nav class="nav-bar">

            <button
                id="homeNav"
                class="nav-button active"
                onclick="showSection('home')"
            >
                Home
            </button>

            <button
                id="searchNav"
                class="nav-button"
                onclick="showSection('search')"
            >
                Search
            </button>

            <button
                id="profileNav"
                class="nav-button"
                onclick="showSection('profile')"
            >
                Profile
            </button>

            <button
                class="nav-button logout-button"
                onclick="logout()"
            >
                Log Out
            </button>

        </nav>


        <!-- =====================================================
             HOME
             ===================================================== -->

        <section id="homeSection" class="section active">

            <!-- CREATE POST -->

            <div class="create-post">

                <textarea
                    id="postContent"
                    maxlength="1000"
                    placeholder="Write something..."
                ></textarea>

                <div class="post-tools">

                    <button
                        class="tool-button"
                        onclick="document.getElementById('mediaInput').click()"
                    >
                        <span class="tool-icon image-icon"></span>
                        Image
                    </button>

                    <button
                        class="tool-button"
                        onclick="document.getElementById('mediaInput').click()"
                    >
                        <span class="tool-icon video-icon"></span>
                        Video
                    </button>

                    <input
                        id="mediaInput"
                        type="file"
                        accept="image/*,video/*"
                        onchange="showSelectedFile()"
                    >

                    <button
                        class="publish-button"
                        onclick="createPost()"
                    >
                        Post
                    </button>

                </div>

                <div
                    id="selectedFile"
                    class="selected-file"
                ></div>

                <div
                    id="postStatus"
                    class="status"
                ></div>

            </div>


            <!-- FEED -->

            <div id="feed">

                <div class="loading">
                    Loading posts...
                </div>

            </div>

        </section>


        <!-- =====================================================
             SEARCH
             ===================================================== -->

        <section id="searchSection" class="section">

            <div class="search-box">

                <input
                    id="profileSearch"
                    type="text"
                    placeholder="Search profiles..."
                    oninput="searchProfiles()"
                >

            </div>

            <div id="searchResults"></div>

        </section>


        <!-- =====================================================
             PROFILE
             ===================================================== -->

        <section id="profileSection" class="section">

            <div class="profile-card">

                <div class="profile-top">

                    <img
                        id="profileAvatar"
                        class="profile-avatar"
                        src=""
                        alt="Profile picture"
                    >

                    <div>

                        <div
                            id="profileDisplayName"
                            class="profile-name"
                        >
                            User
                        </div>

                        <div
                            id="profileUsername"
                            class="profile-username"
                        >
                            @username
                        </div>

                    </div>

                </div>

                <div
                    id="profileBio"
                    class="profile-bio"
                >
                </div>


                <!-- EDIT PROFILE -->

                <div class="profile-edit">

                    <input
                        id="editDisplayName"
                        type="text"
                        placeholder="Display name"
                    >

                    <textarea
                        id="editBio"
                        maxlength="500"
                        placeholder="Bio"
                    ></textarea>

                    <input
                        id="avatarInput"
                        type="file"
                        accept="image/*"
                    >

                    <button
                        class="primary-button"
                        onclick="updateProfile()"
                    >
                        Save Profile
                    </button>

                    <div
                        id="profileStatus"
                        class="status"
                    ></div>

                </div>

            </div>

        </section>

    </div>

</div>


<script>
/* ============================================================
   SUPABASE
   ============================================================ */

const SUPABASE_URL =
    "https://soirkzbrsmgxydmikerx.supabase.co";

const SUPABASE_KEY =
    "sb_publishable_YfZn0IZdTs8L-EThj6lxOg_uFQCDxIp";

const supabaseClient =
    window.supabase.createClient(
        SUPABASE_URL,
        SUPABASE_KEY
    );


/* ============================================================
   GLOBAL STATE
   ============================================================ */

let currentUser = null;
let currentProfile = null;


/* ============================================================
   HELPERS
   ============================================================ */

function usernameToInternalEmail(username) {
    return username
        .toLowerCase()
        .trim()
        .replace(/\s+/g, "") +
        "@dpsbssmw.local";
}


function escapeHTML(value) {

    if (value === null || value === undefined) {
        return "";
    }

    return String(value)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&#039;");
}


function formatDate(dateString) {

    const date = new Date(dateString);

    return date.toLocaleString([], {
        dateStyle: "medium",
        timeStyle: "short"
    });
}


function defaultAvatar() {

    return "data:image/svg+xml;charset=UTF-8," +
        encodeURIComponent(`
            <svg xmlns="http://www.w3.org/2000/svg"
                 width="200"
                 height="200"
                 viewBox="0 0 200 200">

                <rect width="200"
                      height="200"
                      fill="#B2AC88"/>

                <rect x="65"
                      y="40"
                      width="70"
                      height="70"
                      rx="12"
                      fill="#6F4E37"/>

                <rect x="45"
                      y="125"
                      width="110"
                      height="45"
                      rx="15"
                      fill="#6F4E37"/>

            </svg>
        `);
}


/* ============================================================
   AUTH UI
   ============================================================ */

function showLogin() {

    document.getElementById("loginForm")
        .classList.remove("hidden");

    document.getElementById("signupForm")
        .classList.add("hidden");

    document.getElementById("authMessage")
        .textContent = "";
}


function showSignup() {

    document.getElementById("loginForm")
        .classList.add("hidden");

    document.getElementById("signupForm")
        .classList.remove("hidden");

    document.getElementById("authMessage")
        .textContent = "";
}


/* ============================================================
   SIGNUP
   ============================================================ */

async function signup() {

    const username =
        document.getElementById("signupUsername")
            .value
            .trim();

    const displayName =
        document.getElementById("signupDisplayName")
            .value
            .trim();

    const password =
        document.getElementById("signupPassword")
            .value;

    const message =
        document.getElementById("authMessage");


    if (!username || !displayName || !password) {

        message.textContent =
            "Please fill in every field.";

        return;
    }


    if (password.length < 6) {

        message.textContent =
            "Password must be at least 6 characters.";

        return;
    }


    message.textContent =
        "Creating account...";


    const email =
        usernameToInternalEmail(username);


    const { data, error } =
        await supabaseClient.auth.signUp({

            email: email,

            password: password,

            options: {
                data: {
                    username: username,
                    display_name: displayName
                }
            }

        });


    if (error) {

        console.error(error);

        message.textContent =
            error.message;

        return;
    }


    if (data.session) {

        currentUser = data.user;

        await openApp();

        return;
    }


    message.textContent =
        "Account created. Please log in.";

    showLogin();
}


/* ============================================================
   LOGIN
   ============================================================ */

async function login() {

    const username =
        document.getElementById("loginUsername")
            .value
            .trim();

    const password =
        document.getElementById("loginPassword")
            .value;

    const message =
        document.getElementById("authMessage");


    if (!username || !password) {

        message.textContent =
            "Enter your username and password.";

        return;
    }


    message.textContent =
        "Logging in...";


    const email =
        usernameToInternalEmail(username);


    const { data, error } =
        await supabaseClient.auth.signInWithPassword({

            email: email,

            password: password

        });


    if (error) {

        console.error(error);

        message.textContent =
            error.message;

        return;
    }


    currentUser = data.user;

    await openApp();
}


/* ============================================================
   OPEN APP
   ============================================================ */

async function openApp() {

    document.getElementById("authScreen")
        .style.display = "none";

    document.getElementById("appScreen")
        .style.display = "block";


    await loadCurrentProfile();

    await loadFeed();

    showSection("home");
}


/* ============================================================
   CURRENT PROFILE
   ============================================================ */

async function loadCurrentProfile() {

    if (!currentUser) {
        return;
    }


    const { data, error } =
        await supabaseClient
            .from("profiles")
            .select(`
                id,
                username,
                display_name,
                bio,
                avatar_url
            `)
            .eq("id", currentUser.id)
            .single();


    if (error) {

        console.error(
            "PROFILE ERROR:",
            error
        );

        return;
    }


    currentProfile = data;

    renderCurrentProfile();
}


function renderCurrentProfile() {

    if (!currentProfile) {
        return;
    }


    document.getElementById("profileDisplayName")
        .textContent =
            currentProfile.display_name || "User";


    document.getElementById("profileUsername")
        .textContent =
            "@" +
            (currentProfile.username || "username");


    document.getElementById("profileBio")
        .textContent =
            currentProfile.bio || "No bio yet.";


    document.getElementById("profileAvatar")
        .src =
            currentProfile.avatar_url ||
            defaultAvatar();


    document.getElementById("editDisplayName")
        .value =
            currentProfile.display_name || "";


    document.getElementById("editBio")
        .value =
            currentProfile.bio || "";
}


/* ============================================================
   NAVIGATION
   ============================================================ */

function showSection(section) {

    document
        .querySelectorAll(".section")
        .forEach(el => {
            el.classList.remove("active");
        });


    document
        .querySelectorAll(".nav-button")
        .forEach(el => {
            el.classList.remove("active");
        });


    if (section === "home") {

        document
            .getElementById("homeSection")
            .classList.add("active");

        document
            .getElementById("homeNav")
            .classList.add("active");

        loadFeed();

    }


    if (section === "search") {

        document
            .getElementById("searchSection")
            .classList.add("active");

        document
            .getElementById("searchNav")
            .classList.add("active");

    }


    if (section === "profile") {

        document
            .getElementById("profileSection")
            .classList.add("active");

        document
            .getElementById("profileNav")
            .classList.add("active");

        loadCurrentProfile();

    }
}


/* ============================================================
   CREATE POST
   ============================================================ */

function showSelectedFile() {

    const input =
        document.getElementById("mediaInput");

    const display =
        document.getElementById("selectedFile");


    if (!input.files.length) {

        display.textContent = "";

        return;
    }


    display.textContent =
        input.files[0].name;
}


async function createPost() {

    if (!currentUser) {
        return;
    }


    const content =
        document.getElementById("postContent")
            .value
            .trim();

    const mediaInput =
        document.getElementById("mediaInput");

    const status =
        document.getElementById("postStatus");


    if (!content && !mediaInput.files.length) {

        status.textContent =
            "Write something or choose a file.";

        return;
    }


    status.textContent =
        "Posting...";


    let mediaUrl = null;
    let mediaType = null;


    /* =========================
       MEDIA UPLOAD
       ========================= */

    if (mediaInput.files.length) {

        const file =
            mediaInput.files[0];


        if (file.size > 100 * 1024 * 1024) {

            status.textContent =
                "File is larger than 100 MB.";

            return;
        }


        mediaType =
            file.type.startsWith("video/")
                ? "video"
                : "image";


        const extension =
            file.name
                .split(".")
                .pop();


        const filePath =
            `${currentUser.id}/${Date.now()}.${extension}`;


        const { error: uploadError } =
            await supabaseClient
                .storage
                .from("post-media")
                .upload(
                    filePath,
                    file,
                    {
                        upsert: false,
                        contentType: file.type
                    }
                );


        if (uploadError) {

            console.error(uploadError);

            status.textContent =
                uploadError.message;

            return;
        }


        const { data } =
            supabaseClient
                .storage
                .from("post-media")
                .getPublicUrl(filePath);


        mediaUrl =
            data.publicUrl;
    }


    /* =========================
       DATABASE INSERT
       ========================= */

    const { error } =
        await supabaseClient
            .from("posts")
            .insert({

                user_id: currentUser.id,

                content:
                    content || null,

                media_url:
                    mediaUrl,

                media_type:
                    mediaType

            });


    if (error) {

        console.error(error);

        status.textContent =
            error.message;

        return;
    }


    document.getElementById("postContent")
        .value = "";

    mediaInput.value = "";

    document.getElementById("selectedFile")
        .textContent = "";

    status.textContent =
        "Posted.";


    await loadFeed();


    setTimeout(() => {
        status.textContent = "";
    }, 2000);
}


/* ============================================================
   LOAD FEED
   ============================================================ */

async function loadFeed() {

    const feed =
        document.getElementById("feed");


    feed.innerHTML =
        `<div class="loading">Loading posts...</div>`;


    const {
        data: posts,
        error: postsError
    } =
        await supabaseClient
            .from("posts")
            .select(`
                id,
                user_id,
                content,
                media_url,
                media_type,
                created_at
            `)
            .order(
                "created_at",
                {
                    ascending: false
                }
            );


    if (postsError) {

        console.error(
            "POSTS ERROR:",
            postsError
        );

        feed.innerHTML =
            `<div class="empty">
                Could not load posts.
                <br><br>
                ${escapeHTML(postsError.message)}
            </div>`;

        return;
    }


    if (!posts || posts.length === 0) {

        feed.innerHTML =
            `<div class="empty">
                No posts yet.
            </div>`;

        return;
    }


    const userIds =
        [
            ...new Set(
                posts.map(post => post.user_id)
            )
        ];


    const {
        data: profiles,
        error: profilesError
    } =
        await supabaseClient
            .from("profiles")
            .select(`
                id,
                username,
                display_name,
                avatar_url
            `)
            .in(
                "id",
                userIds
            );


    if (profilesError) {

        console.error(
            "PROFILES ERROR:",
            profilesError
        );

        feed.innerHTML =
            `<div class="empty">
                Posts were found, but profiles could not be loaded.
                <br><br>
                ${escapeHTML(profilesError.message)}
            </div>`;

        return;
    }


    const profileMap = {};


    (profiles || []).forEach(profile => {

        profileMap[profile.id] =
            profile;

    });


    feed.innerHTML = "";


    for (const post of posts) {

        const profile =
            profileMap[post.user_id] || {

                id: post.user_id,

                username: "unknown",

                display_name:
                    "Unknown User",

                avatar_url: ""

            };


        const html =
            await createPostHTML(
                post,
                profile
            );


        feed.insertAdjacentHTML(
            "beforeend",
            html
        );
    }
}


/* ============================================================
   CREATE POST HTML
   ============================================================ */

async function createPostHTML(
    post,
    profile
) {

    let liked = false;
    let likeCount = 0;


    /* =========================
       LIKE COUNT
       ========================= */

    const {
        data: likes,
        error: likesError
    } =
        await supabaseClient
            .from("likes")
            .select("user_id")
            .eq(
                "post_id",
                post.id
            );


    if (!likesError && likes) {

        likeCount =
            likes.length;

        liked =
            likes.some(
                like =>
                    like.user_id ===
                    currentUser.id
            );
    }


    /* =========================
       MEDIA
       ========================= */

    let mediaHTML = "";


    if (
        post.media_url &&
        post.media_type === "image"
    ) {

        mediaHTML =
            `<img
                class="post-media"
                src="${escapeHTML(post.media_url)}"
                alt="Post image"
                loading="lazy"
            >`;
    }


    if (
        post.media_url &&
        post.media_type === "video"
    ) {

        mediaHTML =
            `<video
                class="post-media"
                src="${escapeHTML(post.media_url)}"
                controls
                playsinline
            ></video>`;
    }


    /* =========================
       TEXT
       ========================= */

    const contentHTML =
        post.content
            ? `<div class="post-content">
                    ${escapeHTML(post.content)}
               </div>`
            : "";


    const ownPost =
        currentUser &&
        post.user_id ===
            currentUser.id;


    const deleteHTML =
        ownPost
            ? `
                <button
                    class="action-button"
                    onclick="deletePost(${post.id})"
                >
                    Delete
                </button>
              `
            : "";


    return `
        <article
            class="post-card"
            id="post-${post.id}"
        >

            <div class="post-header">

                <img
                    class="avatar"
                    src="${escapeHTML(
                        profile.avatar_url ||
                        defaultAvatar()
                    )}"
                    alt="Profile picture"
                >

                <div class="post-user-info">

                    <span class="display-name">
                        ${escapeHTML(
                            profile.display_name ||
                            "Unknown User"
                        )}
                    </span>

                    <span class="username">
                        @${escapeHTML(
                            profile.username ||
                            "unknown"
                        )}
                        ·
                        ${escapeHTML(
                            formatDate(
                                post.created_at
                            )
                        )}
                    </span>

                </div>

                ${
                    !ownPost
                    ? `
                        <button
                            class="friend-button"
                            onclick="sendFriendRequest('${post.user_id}', this)"
                            title="Add friend"
                        >
                            <span></span>
                        </button>
                    `
                    : ""
                }

            </div>


            ${contentHTML}

            ${mediaHTML}


            <div class="post-actions">

                <div>

                    <button
                        class="action-button ${liked ? "liked" : ""}"
                        onclick="toggleLike(${post.id}, this)"
                    >

                        <span
                            class="action-icon like-icon"
                        ></span>

                        <span>
                            ${likeCount}
                        </span>

                    </button>

                </div>


                <div>

                    <button
                        class="action-button"
                        onclick="toggleComments(${post.id})"
                    >

                        <span
                            class="action-icon comment-icon"
                        ></span>

                        <span>
                            Comment
                        </span>

                    </button>

                    ${deleteHTML}

                </div>

            </div>


            <div
                id="comments-${post.id}"
                class="comments-area"
            >

                <div
                    id="comment-list-${post.id}"
                    class="comment-list"
                ></div>

                <div class="comment-form">

                    <input
                        id="comment-input-${post.id}"
                        class="comment-input"
                        type="text"
                        maxlength="500"
                        placeholder="Write a comment..."
                    >

                    <button
                        class="comment-submit"
                        onclick="addComment(${post.id})"
                    >
                        Send
                    </button>

                </div>

            </div>

        </article>
    `;
}


/* ============================================================
   LIKE
   ============================================================ */

async function toggleLike(
    postId,
    button
) {

    if (!currentUser) {
        return;
    }


    const {
        data: existing,
        error: findError
    } =
        await supabaseClient
            .from("likes")
            .select("post_id")
            .eq(
                "post_id",
                postId
            )
            .eq(
                "user_id",
                currentUser.id
            )
            .maybeSingle();


    if (findError) {

        console.error(findError);

        return;
    }


    if (existing) {

        const { error } =
            await supabaseClient
                .from("likes")
                .delete()
                .eq(
                    "post_id",
                    postId
                )
                .eq(
                    "user_id",
                    currentUser.id
                );


        if (error) {

            console.error(error);

            return;
        }

    } else {

        const { error } =
            await supabaseClient
                .from("likes")
                .insert({

                    post_id:
                        postId,

                    user_id:
                        currentUser.id

                });


        if (error) {

            console.error(error);

            return;
        }
    }


    await loadFeed();
}


/* ============================================================
   COMMENTS
   ============================================================ */

async function toggleComments(
    postId
) {

    const area =
        document.getElementById(
            `comments-${postId}`
        );


    if (!area.classList.contains("open")) {

        area.classList.add("open");

        await loadComments(postId);

    } else {

        area.classList.remove("open");
    }
}


async function loadComments(
    postId
) {

    const list =
        document.getElementById(
            `comment-list-${postId}`
        );


    list.innerHTML =
        `<div class="loading">
            Loading comments...
        </div>`;


    const {
        data: comments,
        error
    } =
        await supabaseClient
            .from("comments")
            .select(`
                id,
                user_id,
                content,
                created_at
            `)
            .eq(
                "post_id",
                postId
            )
            .order(
                "created_at",
                {
                    ascending: true
                }
            );


    if (error) {

        console.error(error);

        list.innerHTML =
            `<div class="comment-item">
                ${escapeHTML(error.message)}
            </div>`;

        return;
    }


    if (!comments || comments.length === 0) {

        list.innerHTML =
            `<div class="comment-item">
                No comments yet.
            </div>`;

        return;
    }


    const userIds =
        [
            ...new Set(
                comments.map(
                    comment =>
                        comment.user_id
                )
            )
        ];


    const {
        data: profiles
    } =
        await supabaseClient
            .from("profiles")
            .select(`
                id,
                display_name,
                username
            `)
            .in(
                "id",
                userIds
            );


    const profileMap = {};


    (profiles || []).forEach(profile => {

        profileMap[profile.id] =
            profile;

    });


    list.innerHTML = "";


    comments.forEach(comment => {

        const profile =
            profileMap[comment.user_id] || {

                display_name:
                    "Unknown User",

                username:
                    "unknown"

            };


        list.insertAdjacentHTML(
            "beforeend",

            `
                <div class="comment-item">

                    <div class="comment-name">
                        ${escapeHTML(
                            profile.display_name
                        )}
                        ·
                        @${escapeHTML(
                            profile.username
                        )}
                    </div>

                    <div class="comment-text">
                        ${escapeHTML(
                            comment.content
                        )}
                    </div>

                </div>
            `
        );
    });
}


async function addComment(
    postId
) {

    const input =
        document.getElementById(
            `comment-input-${postId}`
        );


    const content =
        input.value.trim();


    if (!content) {
        return;
    }


    const { error } =
        await supabaseClient
            .from("comments")
            .insert({

                post_id:
                    postId,

                user_id:
                    currentUser.id,

                content:
                    content

            });


    if (error) {

        console.error(error);

        return;
    }


    input.value = "";

    await loadComments(postId);
}


/* ============================================================
   DELETE POST
   ============================================================ */

async function deletePost(
    postId
) {

    if (!currentUser) {
        return;
    }


    const confirmed =
        window.confirm(
            "Delete this post?"
        );


    if (!confirmed) {
        return;
    }


    const { error } =
        await supabaseClient
            .from("posts")
            .delete()
            .eq(
                "id",
                postId
            )
            .eq(
                "user_id",
                currentUser.id
            );


    if (error) {

        console.error(error);

        return;
    }


    await loadFeed();
}


/* ============================================================
   FRIEND REQUEST
   ============================================================ */

async function sendFriendRequest(
    receiverId,
    button
) {

    if (!currentUser) {
        return;
    }


    if (
        receiverId ===
        currentUser.id
    ) {
        return;
    }


    button.disabled = true;


    const {
        data: existing,
        error: existingError
    } =
        await supabaseClient
            .from("friend_requests")
            .select(`
                id,
                sender_id,
                receiver_id,
                status
            `)
            .or(
                `and(sender_id.eq.${currentUser.id},receiver_id.eq.${receiverId}),and(sender_id.eq.${receiverId},receiver_id.eq.${currentUser.id})`
            );


    if (existingError) {

        console.error(
            existingError
        );

        button.disabled = false;

        return;
    }


    const currentRequest =
        existing &&
        existing.length
            ? existing[0]
            : null;


    if (currentRequest) {

        if (
            currentRequest.status ===
            "accepted"
        ) {

            button.classList.add(
                "friends"
            );

            button.title =
                "Friends";

            button.disabled =
                true;

            return;
        }


        if (
            currentRequest.sender_id ===
            currentUser.id
        ) {

            button.classList.add(
                "sent"
            );

            button.title =
                "Request sent";

            button.disabled =
                true;

            return;
        }
    }


    const { error } =
        await supabaseClient
            .from("friend_requests")
            .insert({

                sender_id:
                    currentUser.id,

                receiver_id:
                    receiverId,

                status:
                    "pending"

            });


    if (error) {

        console.error(error);

        button.disabled = false;

        return;
    }


    button.classList.add("sent");

    button.title =
        "Request sent";

    button.disabled =
        true;
}


/* ============================================================
   SEARCH
   ============================================================ */

let searchTimeout = null;


function searchProfiles() {

    clearTimeout(searchTimeout);


    searchTimeout =
        setTimeout(
            performProfileSearch,
            250
        );
}


async function performProfileSearch() {

    const query =
        document.getElementById(
            "profileSearch"
        )
        .value
        .trim();


    const results =
        document.getElementById(
            "searchResults"
        );


    if (!query) {

        results.innerHTML = "";

        return;
    }


    const pattern =
        `%${query}%`;


    const {
        data,
        error
    } =
        await supabaseClient
            .from("profiles")
            .select(`
                id,
                username,
                display_name,
                avatar_url
            `)
            .or(
                `username.ilike.${pattern},display_name.ilike.${pattern}`
            )
            .limit(30);


    if (error) {

        console.error(error);

        results.innerHTML =
            `<div class="empty">
                ${escapeHTML(error.message)}
            </div>`;

        return;
    }


    if (!data || data.length === 0) {

        results.innerHTML =
            `<div class="empty">
                No profiles found.
            </div>`;

        return;
    }


    results.innerHTML = "";


    data.forEach(profile => {

        const isSelf =
            currentUser &&
            profile.id ===
                currentUser.id;


        results.insertAdjacentHTML(

            "beforeend",

            `
                <div class="search-result">

                    <img
                        class="avatar"
                        src="${escapeHTML(
                            profile.avatar_url ||
                            defaultAvatar()
                        )}"
                        alt="Profile picture"
                    >

                    <div class="search-info">

                        <div class="search-display">
                            ${escapeHTML(
                                profile.display_name
                            )}
                        </div>

                        <div class="search-username">
                            @${escapeHTML(
                                profile.username
                            )}
                        </div>

                    </div>

                    ${
                        !isSelf
                        ? `
                            <button
                                class="friend-button"
                                onclick="sendFriendRequest('${profile.id}', this)"
                                title="Add friend"
                            >
                                <span></span>
                            </button>
                        `
                        : ""
                    }

                </div>
            `
        );
    });
}


/* ============================================================
   UPDATE PROFILE
   ============================================================ */

async function updateProfile() {

    if (!currentUser) {
        return;
    }


    const displayName =
        document.getElementById(
            "editDisplayName"
        )
        .value
        .trim();


    const bio =
        document.getElementById(
            "editBio"
        )
        .value
        .trim();


    const avatarInput =
        document.getElementById(
            "avatarInput"
        );


    const status =
        document.getElementById(
            "profileStatus"
        );


    if (!displayName) {

        status.textContent =
            "Display name cannot be empty.";

        return;
    }


    status.textContent =
        "Saving...";


    let avatarUrl =
        currentProfile.avatar_url ||
        null;


    /* =========================
       AVATAR UPLOAD
       ========================= */

    if (avatarInput.files.length) {

        const file =
            avatarInput.files[0];


        if (!file.type.startsWith("image/")) {

            status.textContent =
                "Please select an image.";

            return;
        }


        const extension =
            file.name
                .split(".")
                .pop();


        const filePath =
            `${currentUser.id}/avatar-${Date.now()}.${extension}`;


        const {
            error: uploadError
        } =
            await supabaseClient
                .storage
                .from("avatars")
                .upload(
                    filePath,
                    file,
                    {
                        upsert: false,
                        contentType: file.type
                    }
                );


        if (uploadError) {

            console.error(
                uploadError
            );

            status.textContent =
                uploadError.message;

            return;
        }


        const { data } =
            supabaseClient
                .storage
                .from("avatars")
                .getPublicUrl(filePath);


        avatarUrl =
            data.publicUrl;
    }


    /* =========================
       UPDATE DATABASE
       ========================= */

    const {
        data,
        error
    } =
        await supabaseClient
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
            )
            .select()
            .single();


    if (error) {

        console.error(error);

        status.textContent =
            error.message;

        return;
    }


    currentProfile =
        data;


    renderCurrentProfile();


    status.textContent =
        "Profile saved.";


    await loadFeed();


    setTimeout(() => {

        status.textContent = "";

    }, 2000);
}


/* ============================================================
   LOGOUT
   ============================================================ */

async function logout() {

    await supabaseClient.auth.signOut();

    currentUser = null;
    currentProfile = null;


    document.getElementById("appScreen")
        .style.display = "none";


    document.getElementById("authScreen")
        .style.display = "flex";


    document.getElementById("loginPassword")
        .value = "";


    document.getElementById("authMessage")
        .textContent = "";
}


/* ============================================================
   SESSION CHECK
   ============================================================ */

async function checkSession() {

    const {
        data
    } =
        await supabaseClient
            .auth
            .getSession();


    if (
        data &&
        data.session &&
        data.session.user
    ) {

        currentUser =
            data.session.user;

        await openApp();

    } else {

        document.getElementById(
            "authScreen"
        ).style.display = "flex";

        document.getElementById(
            "appScreen"
        ).style.display = "none";
    }
}


/* ============================================================
   AUTH STATE LISTENER
   ============================================================ */

supabaseClient
    .auth
    .onAuthStateChange(
        async (event, session) => {

            if (
                session &&
                session.user
            ) {

                currentUser =
                    session.user;

            } else {

                currentUser =
                    null;

            }
        }
    );


/* ============================================================
   START
   ============================================================ */

checkSession();

</script>

</body>
</html>
