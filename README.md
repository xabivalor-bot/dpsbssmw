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
    --brown: #6F4E37;
    --olive: #B2AC88;
    --cream: #F5F5DC;
}

* {
    box-sizing: border-box;
}

html, body {
    margin: 0;
    padding: 0;
    min-height: 100%;
    background: var(--olive);
    color: var(--brown);
    font-family: Arial, Helvetica, sans-serif;
}

body {
    overflow-x: hidden;
}

button,
input,
textarea {
    font: inherit;
}

button {
    cursor: pointer;
}

.hidden {
    display: none !important;
}

/* =========================
   AUTH
========================= */

#authScreen {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 25px;
    background: var(--olive);
}

.authCard {
    width: min(440px, 100%);
    background: var(--cream);
    border: 4px solid var(--brown);
    border-radius: 24px;
    padding: 30px;
    box-shadow: 10px 10px 0 var(--brown);
}

.authBrand {
    text-align: center;
    margin-bottom: 25px;
}

.authBrand small {
    font-weight: bold;
    letter-spacing: 2px;
}

.authBrand h1 {
    margin: 8px 0;
    font-size: 38px;
}

.authBrand p {
    margin: 0;
    font-size: 13px;
    font-weight: bold;
}

.authTabs {
    display: flex;
    gap: 8px;
    margin-bottom: 20px;
}

.authTabs button {
    flex: 1;
    padding: 12px;
    border: 3px solid var(--brown);
    border-radius: 12px;
    background: var(--olive);
    color: var(--brown);
    font-weight: bold;
}

.authTabs button.active {
    background: var(--brown);
    color: var(--cream);
}

.inputGroup {
    margin-bottom: 14px;
}

.inputGroup label {
    display: block;
    font-weight: bold;
    margin-bottom: 6px;
}

.inputGroup input,
.inputGroup textarea,
.searchInput,
.postTextarea {
    width: 100%;
    border: 3px solid var(--brown);
    border-radius: 12px;
    padding: 12px;
    background: var(--cream);
    color: var(--brown);
    outline: none;
}

.inputGroup input:focus,
.inputGroup textarea:focus,
.searchInput:focus,
.postTextarea:focus {
    box-shadow: 0 0 0 3px var(--olive);
}

.primaryButton {
    width: 100%;
    border: 3px solid var(--brown);
    border-radius: 12px;
    padding: 13px;
    background: var(--brown);
    color: var(--cream);
    font-weight: bold;
}

.primaryButton:hover {
    background: var(--olive);
    color: var(--brown);
}

.statusMessage {
    margin-top: 14px;
    padding: 10px;
    border: 2px solid var(--brown);
    border-radius: 10px;
    font-weight: bold;
    text-align: center;
}

/* =========================
   APP
========================= */

#app {
    min-height: 100vh;
}

/* =========================
   TOP BANNER
========================= */

.topBanner {
    background: var(--brown);
    color: var(--cream);
    padding: 18px 20px 22px;
    border-bottom: 8px solid var(--olive);
}

.bannerInner {
    width: min(1050px, 100%);
    margin: auto;
}

.productName {
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 2px;
}

.siteTitle {
    font-size: clamp(38px, 8vw, 72px);
    font-weight: 900;
    line-height: 0.95;
    margin: 8px 0;
}

.siteSubtitle {
    font-size: clamp(12px, 2vw, 16px);
    font-weight: bold;
    text-transform: lowercase;
}

/* =========================
   NAVIGATION
========================= */

.navBar {
    background: var(--olive);
    border-bottom: 4px solid var(--brown);
    padding: 10px 15px;
}

.navInner {
    width: min(1050px, 100%);
    margin: auto;
    display: flex;
    gap: 8px;
    align-items: center;
    flex-wrap: wrap;
}

.navButton {
    border: 3px solid var(--brown);
    border-radius: 12px;
    padding: 9px 13px;
    background: var(--cream);
    color: var(--brown);
    font-weight: bold;
}

.navButton:hover,
.navButton.active {
    background: var(--brown);
    color: var(--cream);
}

.navSpacer {
    flex: 1;
}

/* =========================
   MAIN
========================= */

.mainContainer {
    width: min(1050px, 100%);
    margin: auto;
    padding: 20px 15px 50px;
}

.searchArea {
    margin-bottom: 18px;
}

.searchInput {
    background: var(--cream);
}

/* =========================
   CREATE POST
========================= */

.createPost {
    background: var(--cream);
    border: 4px solid var(--brown);
    border-radius: 18px;
    padding: 16px;
    margin-bottom: 20px;
}

.createPost h2 {
    margin-top: 0;
}

.mediaRow {
    display: flex;
    gap: 10px;
    align-items: center;
    flex-wrap: wrap;
    margin-top: 10px;
}

.fileLabel {
    display: inline-block;
    border: 3px solid var(--brown);
    border-radius: 12px;
    padding: 10px 13px;
    background: var(--olive);
    color: var(--brown);
    font-weight: bold;
    cursor: pointer;
}

.fileLabel input {
    display: none;
}

.selectedFile {
    font-size: 13px;
    font-weight: bold;
}

.postButton {
    border: 3px solid var(--brown);
    border-radius: 12px;
    padding: 11px 18px;
    background: var(--brown);
    color: var(--cream);
    font-weight: bold;
}

.postButton:hover {
    background: var(--olive);
    color: var(--brown);
}

/* =========================
   POST CARD
========================= */

.postCard {
    background: var(--cream);
    border: 4px solid var(--brown);
    border-radius: 18px;
    padding: 15px;
    margin-bottom: 18px;
    overflow: hidden;
}

.postTop {
    display: flex;
    align-items: center;
    gap: 10px;
}

.userInfo {
    flex: 1;
    min-width: 0;
}

.userName {
    font-size: 17px;
    font-weight: 900;
}

.userHandle {
    font-size: 12px;
    font-weight: bold;
}

.postDate {
    font-size: 11px;
    margin-top: 3px;
}

.avatar {
    width: 48px;
    height: 48px;
    min-width: 48px;
    border: 3px solid var(--brown);
    border-radius: 6px;
    object-fit: cover;
    background: var(--olive);
}

.friendButton {
    width: 45px;
    height: 45px;
    min-width: 45px;
    border: 3px solid var(--brown);
    border-radius: 50%;
    background: var(--olive);
    position: relative;
    padding: 0;
}

/* Two overlapping circles = friend request icon */
.friendButton::before,
.friendButton::after {
    content: "";
    position: absolute;
    width: 19px;
    height: 19px;
    border: 3px solid var(--brown);
    border-radius: 50%;
    top: 10px;
}

.friendButton::before {
    left: 7px;
}

.friendButton::after {
    right: 7px;
}

.friendButton.sent {
    background: var(--brown);
}

.friendButton.sent::before,
.friendButton.sent::after {
    border-color: var(--cream);
}

.postContent {
    margin: 18px 5px;
    text-align: center;
    word-wrap: break-word;
}

.postText {
    font-size: 17px;
    line-height: 1.5;
    white-space: pre-wrap;
    margin-bottom: 12px;
}

.postMedia {
    max-width: 100%;
    max-height: 650px;
    display: block;
    margin: 0 auto;
    border: 3px solid var(--brown);
    border-radius: 12px;
    object-fit: contain;
    background: var(--olive);
}

.postBottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 12px;
}

.actionButton {
    border: 3px solid var(--brown);
    border-radius: 12px;
    background: var(--olive);
    color: var(--brown);
    padding: 8px 13px;
    font-weight: bold;
    display: flex;
    align-items: center;
    gap: 7px;
}

.actionButton:hover,
.actionButton.active {
    background: var(--brown);
    color: var(--cream);
}

.likeIcon {
    font-size: 20px;
}

.commentIcon {
    width: 19px;
    height: 15px;
    border: 3px solid currentColor;
    border-radius: 5px;
    position: relative;
    display: inline-block;
}

.commentIcon::after {
    content: "";
    position: absolute;
    bottom: -6px;
    left: 3px;
    width: 7px;
    height: 7px;
    border-left: 3px solid currentColor;
    transform: skew(-25deg);
}

.deleteButton {
    border: 3px solid var(--brown);
    background: var(--cream);
    color: var(--brown);
    border-radius: 10px;
    padding: 7px 10px;
    font-weight: bold;
}

/* =========================
   COMMENTS
========================= */

.commentsArea {
    margin-top: 12px;
    border-top: 3px solid var(--brown);
    padding-top: 12px;
}

.comment {
    border: 2px solid var(--brown);
    border-radius: 10px;
    padding: 8px;
    margin-bottom: 8px;
    background: var(--olive);
}

.commentName {
    font-weight: 900;
    font-size: 13px;
}

.commentText {
    margin-top: 3px;
    white-space: pre-wrap;
}

.commentForm {
    display: flex;
    gap: 7px;
}

.commentForm input {
    flex: 1;
    min-width: 0;
    border: 3px solid var(--brown);
    border-radius: 10px;
    padding: 9px;
    background: var(--cream);
    color: var(--brown);
}

.commentForm button {
    border: 3px solid var(--brown);
    border-radius: 10px;
    background: var(--brown);
    color: var(--cream);
    font-weight: bold;
    padding: 8px 12px;
}

/* =========================
   PROFILE
========================= */

.profileCard {
    background: var(--cream);
    border: 4px solid var(--brown);
    border-radius: 20px;
    padding: 20px;
}

.profileHeader {
    display: flex;
    align-items: center;
    gap: 20px;
    flex-wrap: wrap;
}

.profileAvatar {
    width: 130px;
    height: 130px;
    border: 5px solid var(--brown);
    border-radius: 6px;
    object-fit: cover;
    background: var(--olive);
}

.profileDetails {
    flex: 1;
}

.profileDetails h2 {
    margin: 0;
    font-size: 30px;
}

.profileDetails p {
    margin: 7px 0;
}

.profileActions {
    margin-top: 15px;
}

.profileEdit {
    margin-top: 25px;
    border-top: 3px solid var(--brown);
    padding-top: 20px;
}

/* =========================
   SEARCH RESULTS
========================= */

.searchResults {
    margin-top: 10px;
}

.searchUser {
    display: flex;
    align-items: center;
    gap: 12px;
    background: var(--cream);
    border: 3px solid var(--brown);
    border-radius: 13px;
    padding: 10px;
    margin-bottom: 8px;
    cursor: pointer;
}

.searchUser:hover {
    background: var(--brown);
    color: var(--cream);
}

/* =========================
   EMPTY / LOADING
========================= */

.emptyMessage {
    text-align: center;
    background: var(--cream);
    border: 4px solid var(--brown);
    border-radius: 18px;
    padding: 30px;
    font-weight: bold;
}

.loading {
    text-align: center;
    padding: 30px;
    font-weight: bold;
}

/* =========================
   RESPONSIVE
========================= */

@media (max-width: 650px) {

    .authCard {
        padding: 20px;
        box-shadow: 6px 6px 0 var(--brown);
    }

    .siteTitle {
        font-size: 42px;
    }

    .mainContainer {
        padding-left: 10px;
        padding-right: 10px;
    }

    .postCard {
        border-width: 3px;
    }

    .profileAvatar {
        width: 100px;
        height: 100px;
    }

    .profileHeader {
        gap: 13px;
    }

    .actionButton {
        padding: 7px 9px;
    }

    .postBottom {
        gap: 8px;
    }
}
</style>
</head>

<body>

<!-- =========================
     AUTH SCREEN
========================= -->

<section id="authScreen">

    <div class="authCard">

        <div class="authBrand">
            <small>ZaheenProduct</small>
            <h1>DPSB SSMW</h1>
            <p>delhi public school budgam secret social media website</p>
        </div>

        <div class="authTabs">
            <button id="loginTab" class="active" onclick="showLogin()">
                Login
            </button>

            <button id="signupTab" onclick="showSignup()">
                Sign Up
            </button>
        </div>

        <div id="loginForm">

            <div class="inputGroup">
                <label>Username</label>
                <input id="loginUsername"
                       type="text"
                       maxlength="20"
                       autocomplete="username">
            </div>

            <div class="inputGroup">
                <label>Password</label>
                <input id="loginPassword"
                       type="password"
                       autocomplete="current-password">
            </div>

            <button class="primaryButton" onclick="login()">
                Login
            </button>

        </div>

        <div id="signupForm" class="hidden">

            <div class="inputGroup">
                <label>Username</label>
                <input id="signupUsername"
                       type="text"
                       maxlength="20"
                       placeholder="letters, numbers and _ only">
            </div>

            <div class="inputGroup">
                <label>Display name</label>
                <input id="signupDisplayName"
                       type="text"
                       maxlength="40">
            </div>

            <div class="inputGroup">
                <label>Password</label>
                <input id="signupPassword"
                       type="password"
                       autocomplete="new-password">
            </div>

            <button class="primaryButton" onclick="signup()">
                Create Account
            </button>

        </div>

        <div id="authMessage" class="statusMessage hidden"></div>

    </div>

</section>


<!-- =========================
     MAIN APP
========================= -->

<section id="app" class="hidden">

    <header class="topBanner">

        <div class="bannerInner">

            <div class="productName">
                ZaheenProduct
            </div>

            <div class="siteTitle">
                DPSB SSMW
            </div>

            <div class="siteSubtitle">
                delhi public school budgam secret social media website
            </div>

        </div>

    </header>


    <nav class="navBar">

        <div class="navInner">

            <button class="navButton active"
                    onclick="showHome()">
                Home
            </button>

            <button class="navButton"
                    onclick="showMyProfile()">
                Profile
            </button>

            <button class="navButton"
                    onclick="logout()">
                Logout
            </button>

            <div class="navSpacer"></div>

            <span id="navUsername"></span>

        </div>

    </nav>


    <main class="mainContainer">

        <!-- SEARCH -->

        <div class="searchArea">

            <input
                id="profileSearch"
                class="searchInput"
                type="text"
                placeholder="Search profiles..."
                oninput="searchProfiles()"
            >

            <div id="searchResults"
                 class="searchResults">
            </div>

        </div>


        <!-- HOME -->

        <section id="homeView">

            <div class="createPost">

                <h2>Create a post</h2>

                <textarea
                    id="postText"
                    class="postTextarea"
                    rows="4"
                    maxlength="1000"
                    placeholder="What's happening?"
                ></textarea>

                <div class="mediaRow">

                    <label class="fileLabel">
                        📷 Add photo/video
                        <input
                            id="postMediaInput"
                            type="file"
                            accept="image/*,video/*"
                            onchange="showSelectedFile()"
                        >
                    </label>

                    <span id="selectedFile"
                          class="selectedFile">
                    </span>

                    <button
                        class="postButton"
                        onclick="createPost()">
                        Post
                    </button>

                </div>

            </div>


            <div id="feed">
                <div class="loading">
                    Loading posts...
                </div>
            </div>

        </section>


        <!-- PROFILE -->

        <section id="profileView" class="hidden">

            <div id="profileContainer">
                <div class="loading">
                    Loading profile...
                </div>
            </div>

        </section>

    </main>

</section>


<script>
/* =========================================================
   SUPABASE
========================================================= */

const SUPABASE_URL =
    "https://soirkzbrsmgxydmikerx.supabase.co";

const SUPABASE_PUBLISHABLE_KEY =
    "sb_publishable_YfZn0IZdTs8L-EThj6lxOg_uFQCDxIp";

const supabaseClient =
    window.supabase.createClient(
        SUPABASE_URL,
        SUPABASE_PUBLISHABLE_KEY
    );


/* =========================================================
   GLOBAL STATE
========================================================= */

let currentUser = null;
let currentProfile = null;
let currentViewedProfile = null;


/* =========================================================
   HELPERS
========================================================= */

function usernameToInternalEmail(username) {
    return username.toLowerCase().trim() + "@dpsbssmw.local";
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

function avatarHTML(profile, extraClass = "avatar") {

    if (profile && profile.avatar_url) {

        return `
            <img
                class="${extraClass}"
                src="${escapeHTML(profile.avatar_url)}"
                alt="Profile picture"
            >
        `;
    }

    return `
        <div class="${extraClass}"
             style="
                display:flex;
                align-items:center;
                justify-content:center;
                font-weight:900;
             ">
            ${escapeHTML(
                profile?.display_name?.charAt(0)?.toUpperCase() || "?"
            )}
        </div>
    `;
}

function showMessage(message) {

    const box = document.getElementById("authMessage");

    box.textContent = message;
    box.classList.remove("hidden");
}


/* =========================================================
   AUTH TABS
========================================================= */

function showLogin() {

    document.getElementById("loginForm")
        .classList.remove("hidden");

    document.getElementById("signupForm")
        .classList.add("hidden");

    document.getElementById("loginTab")
        .classList.add("active");

    document.getElementById("signupTab")
        .classList.remove("active");

    document.getElementById("authMessage")
        .classList.add("hidden");
}

function showSignup() {

    document.getElementById("loginForm")
        .classList.add("hidden");

    document.getElementById("signupForm")
        .classList.remove("hidden");

    document.getElementById("loginTab")
        .classList.remove("active");

    document.getElementById("signupTab")
        .classList.add("active");

    document.getElementById("authMessage")
        .classList.add("hidden");
}


/* =========================================================
   SIGNUP
========================================================= */

async function signup() {

    const username =
        document.getElementById("signupUsername")
        .value
        .trim()
        .toLowerCase();

    const displayName =
        document.getElementById("signupDisplayName")
        .value
        .trim();

    const password =
        document.getElementById("signupPassword")
        .value;

    if (!/^[a-z0-9_]{3,20}$/.test(username)) {

        showMessage(
            "Username must be 3-20 characters and use only letters, numbers or _."
        );

        return;
    }

    if (!displayName) {

        showMessage("Enter a display name.");

        return;
    }

    if (password.length < 6) {

        showMessage("Password must contain at least 6 characters.");

        return;
    }

    showMessage("Creating account...");

    const internalEmail =
        usernameToInternalEmail(username);

    const { data, error } =
        await supabaseClient.auth.signUp({

            email: internalEmail,

            password: password,

            options: {
                data: {
                    username: username,
                    display_name: displayName
                }
            }

        });

    if (error) {

        showMessage(error.message);

        return;
    }

    if (!data.session) {

        showMessage(
            "Account created. Make sure Supabase Email Confirmation is OFF."
        );

        return;
    }

    await openApp();
}


/* =========================================================
   LOGIN
========================================================= */

async function login() {

    const username =
        document.getElementById("loginUsername")
        .value
        .trim()
        .toLowerCase();

    const password =
        document.getElementById("loginPassword")
        .value;

    if (!username || !password) {

        showMessage(
            "Enter your username and password."
        );

        return;
    }

    showMessage("Logging in...");

    const internalEmail =
        usernameToInternalEmail(username);

    const { data, error } =
        await supabaseClient.auth.signInWithPassword({

            email: internalEmail,
            password: password

        });

    if (error) {

        showMessage(error.message);

        return;
    }

    currentUser = data.user;

    await openApp();
}


/* =========================================================
   SESSION
========================================================= */

async function checkSession() {

    const {
        data: {
            session
        }
    } = await supabaseClient.auth.getSession();

    if (session) {

        currentUser = session.user;

        await openApp();

    } else {

        showAuth();
    }
}

supabaseClient.auth.onAuthStateChange(
    async (event, session) => {

        if (session) {

            currentUser = session.user;

        } else {

            currentUser = null;
        }
    }
);


/* =========================================================
   OPEN APP
========================================================= */

async function openApp() {

    document
        .getElementById("authScreen")
        .classList.add("hidden");

    document
        .getElementById("app")
        .classList.remove("hidden");

    await loadCurrentProfile();

    document.getElementById("navUsername")
        .textContent =
        currentProfile?.username || "";

    await loadFeed();
}

function showAuth() {

    document
        .getElementById("authScreen")
        .classList.remove("hidden");

    document
        .getElementById("app")
        .classList.add("hidden");
}


/* =========================================================
   PROFILE
========================================================= */

async function loadCurrentProfile() {

    if (!currentUser) return;

    const { data, error } =
        await supabaseClient
            .from("profiles")
            .select("*")
            .eq("id", currentUser.id)
            .single();

    if (!error) {

        currentProfile = data;
    }
}


/* =========================================================
   NAVIGATION
========================================================= */

function showHome() {

    document
        .getElementById("homeView")
        .classList.remove("hidden");

    document
        .getElementById("profileView")
        .classList.add("hidden");

    document
        .getElementById("profileSearch")
        .value = "";

    document
        .getElementById("searchResults")
        .innerHTML = "";

    loadFeed();
}

async function showMyProfile() {

    await showProfile(currentUser.id);
}


/* =========================================================
   PROFILE DISPLAY
========================================================= */

async function showProfile(userId) {

    document
        .getElementById("homeView")
        .classList.add("hidden");

    document
        .getElementById("profileView")
        .classList.remove("hidden");

    const container =
        document.getElementById("profileContainer");

    container.innerHTML =
        `<div class="loading">Loading profile...</div>`;

    const { data: profile, error } =
        await supabaseClient
            .from("profiles")
            .select("*")
            .eq("id", userId)
            .single();

    if (error) {

        container.innerHTML =
            `<div class="emptyMessage">Profile not found.</div>`;

        return;
    }

    currentViewedProfile = profile;

    const isOwnProfile =
        currentUser &&
        currentUser.id === profile.id;

    container.innerHTML = `

        <div class="profileCard">

            <div class="profileHeader">

                ${avatarHTML(profile, "profileAvatar")}

                <div class="profileDetails">

                    <h2>
                        ${escapeHTML(profile.display_name)}
                    </h2>

                    <p>
                        @${escapeHTML(profile.username)}
                    </p>

                    <p>
                        ${escapeHTML(profile.bio || "No bio yet.")}
                    </p>

                    <div class="profileActions">

                        ${
                            isOwnProfile

                            ? ""

                            : `
                            <button
                                class="friendButton"
                                title="Send friend request"
                                onclick="sendFriendRequest('${profile.id}')">
                            </button>
                            `
                        }

                    </div>

                </div>

            </div>


            ${
                isOwnProfile
                ? `

                <div class="profileEdit">

                    <h3>Edit Profile</h3>

                    <div class="inputGroup">

                        <label>Display name</label>

                        <input
                            id="editDisplayName"
                            value="${escapeHTML(profile.display_name)}"
                            maxlength="40"
                        >

                    </div>


                    <div class="inputGroup">

                        <label>Bio</label>

                        <textarea
                            id="editBio"
                            rows="4"
                            maxlength="300"
                        >${escapeHTML(profile.bio || "")}</textarea>

                    </div>


                    <div class="mediaRow">

                        <label class="fileLabel">

                            Change profile picture

                            <input
                                id="avatarInput"
                                type="file"
                                accept="image/*"
                                onchange="showAvatarFile()"
                            >

                        </label>

                        <span id="avatarFileName">
                        </span>

                    </div>

                    <br>

                    <button
                        class="postButton"
                        onclick="saveProfile()">
                        Save Profile
                    </button>

                </div>

                `
                : ""
            }

        </div>
    `;
}


/* =========================================================
   SAVE PROFILE
========================================================= */

async function saveProfile() {

    if (!currentUser) return;

    const displayName =
        document.getElementById("editDisplayName")
        .value
        .trim();

    const bio =
        document.getElementById("editBio")
        .value
        .trim();

    if (!displayName) {

        alert("Display name cannot be empty.");

        return;
    }

    let avatarUrl =
        currentProfile?.avatar_url || null;

    const avatarInput =
        document.getElementById("avatarInput");

    if (
        avatarInput &&
        avatarInput.files &&
        avatarInput.files.length > 0
    ) {

        const file = avatarInput.files[0];

        if (!file.type.startsWith("image/")) {

            alert("Profile picture must be an image.");

            return;
        }

        if (file.size > 5 * 1024 * 1024) {

            alert("Profile picture must be smaller than 5 MB.");

            return;
        }

        const extension =
            file.name.split(".").pop().toLowerCase();

        const path =
            `${currentUser.id}/avatar-${Date.now()}.${extension}`;

        const { error: uploadError } =
            await supabaseClient.storage
                .from("avatars")
                .upload(path, file, {
                    upsert: true
                });

        if (uploadError) {

            alert(uploadError.message);

            return;
        }

        const {
            data: publicData
        } =
            supabaseClient.storage
                .from("avatars")
                .getPublicUrl(path);

        avatarUrl =
            publicData.publicUrl;
    }

    const { error } =
        await supabaseClient
            .from("profiles")
            .update({
                display_name: displayName,
                bio: bio,
                avatar_url: avatarUrl
            })
            .eq("id", currentUser.id);

    if (error) {

        alert(error.message);

        return;
    }

    await loadCurrentProfile();

    alert("Profile updated.");

    await showProfile(currentUser.id);
}

function showAvatarFile() {

    const input =
        document.getElementById("avatarInput");

    const output =
        document.getElementById("avatarFileName");

    if (input.files.length) {

        output.textContent =
            input.files[0].name;
    }
}


/* =========================================================
   POST FILE
========================================================= */

function showSelectedFile() {

    const input =
        document.getElementById("postMediaInput");

    const output =
        document.getElementById("selectedFile");

    if (input.files.length) {

        const file = input.files[0];

        output.textContent =
            file.name;
    } else {

        output.textContent = "";
    }
}


/* =========================================================
   CREATE POST
========================================================= */

async function createPost() {

    if (!currentUser) return;

    const text =
        document.getElementById("postText")
        .value
        .trim();

    const input =
        document.getElementById("postMediaInput");

    let mediaUrl = null;
    let mediaType = null;

    if (!text && !input.files.length) {

        alert("Write something or choose a photo/video.");

        return;
    }

    if (input.files.length) {

        const file = input.files[0];

        const isImage =
            file.type.startsWith("image/");

        const isVideo =
            file.type.startsWith("video/");

        if (!isImage && !isVideo) {

            alert("Only images and videos are allowed.");

            return;
        }

        const maxSize =
            isVideo
            ? 50 * 1024 * 1024
            : 10 * 1024 * 1024;

        if (file.size > maxSize) {

            alert(
                isVideo
                ? "Video must be smaller than 50 MB."
                : "Image must be smaller than 10 MB."
            );

            return;
        }

        mediaType =
            isImage
            ? "image"
            : "video";

        const extension =
            file.name.split(".").pop().toLowerCase();

        const path =
            `${currentUser.id}/${Date.now()}-${Math.random()
                .toString(36)
                .substring(2)}.${extension}`;

        const { error: uploadError } =
            await supabaseClient.storage
                .from("post-media")
                .upload(path, file);

        if (uploadError) {

            alert(uploadError.message);

            return;
        }

        const {
            data: publicData
        } =
            supabaseClient.storage
                .from("post-media")
                .getPublicUrl(path);

        mediaUrl =
            publicData.publicUrl;
    }

    const { error } =
        await supabaseClient
            .from("posts")
            .insert({
                user_id: currentUser.id,
                content: text || null,
                media_url: mediaUrl,
                media_type: mediaType
            });

    if (error) {

        alert(error.message);

        return;
    }

    document.getElementById("postText")
        .value = "";

    document.getElementById("postMediaInput")
        .value = "";

    document.getElementById("selectedFile")
        .textContent = "";

    await loadFeed();
}


/* =========================================================
   LOAD FEED
========================================================= */

async function loadFeed() {

    const feed =
        document.getElementById("feed");

    feed.innerHTML =
        `<div class="loading">Loading posts...</div>`;

    const { data: posts, error } =
        await supabaseClient
            .from("posts")
            .select(`
                id,
                user_id,
                content,
                media_url,
                media_type,
                created_at,
                profiles (
                    id,
                    username,
                    display_name,
                    avatar_url
                )
            `)
            .order("created_at", {
                ascending: false
            });

    if (error) {

        feed.innerHTML = `
            <div class="emptyMessage">
                Could not load posts.<br><br>
                ${escapeHTML(error.message)}
            </div>
        `;

        return;
    }

    if (!posts || posts.length === 0) {

        feed.innerHTML = `
            <div class="emptyMessage">
                No posts yet. Be the first one.
            </div>
        `;

        return;
    }

    feed.innerHTML = "";

    for (const post of posts) {

        feed.insertAdjacentHTML(
            "beforeend",
            await createPostHTML(post)
        );
    }
}


/* =========================================================
   POST HTML
========================================================= */

async function createPostHTML(post) {

    const profile =
        post.profiles || {};

    const { data: myLike } =
        await supabaseClient
            .from("likes")
            .select("post_id")
            .eq("post_id", post.id)
            .eq("user_id", currentUser.id)
            .maybeSingle();

    const { count: likeCount } =
        await supabaseClient
            .from("likes")
            .select("*", {
                count: "exact",
                head: true
            })
            .eq("post_id", post.id);

    const { count: commentCount } =
        await supabaseClient
            .from("comments")
            .select("*", {
                count: "exact",
                head: true
            })
            .eq("post_id", post.id);

    let mediaHTML = "";

    if (post.media_url && post.media_type === "image") {

        mediaHTML = `
            <img
                class="postMedia"
                src="${escapeHTML(post.media_url)}"
                alt="Post image"
                loading="lazy"
            >
        `;

    } else if (
        post.media_url &&
        post.media_type === "video"
    ) {

        mediaHTML = `
            <video
                class="postMedia"
                src="${escapeHTML(post.media_url)}"
                controls
                playsinline
            ></video>
        `;
    }

    return `

        <article class="postCard"
                 id="post-${post.id}">

            <div class="postTop">

                ${avatarHTML(profile)}

                <div class="userInfo">

                    <div class="userName">
                        ${escapeHTML(profile.display_name)}
                    </div>

                    <div class="userHandle">
                        @${escapeHTML(profile.username)}
                    </div>

                    <div class="postDate">
                        ${formatDate(post.created_at)}
                    </div>

                </div>


                ${
                    post.user_id !== currentUser.id

                    ? `
                    <button
                        class="friendButton"
                        title="Send friend request"
                        onclick="sendFriendRequest('${post.user_id}')">
                    </button>
                    `

                    : `
                    <button
                        class="deleteButton"
                        onclick="deletePost('${post.id}')">
                        Delete
                    </button>
                    `
                }

            </div>


            <div class="postContent">

                ${
                    post.content
                    ? `
                    <div class="postText">
                        ${escapeHTML(post.content)}
                    </div>
                    `
                    : ""
                }

                ${mediaHTML}

            </div>


            <div class="postBottom">

                <button
                    class="actionButton ${myLike ? "active" : ""}"
                    onclick="toggleLike(${post.id})">

                    <span class="likeIcon">👍</span>

                    <span>
                        ${likeCount || 0}
                    </span>

                </button>


                <button
                    class="actionButton"
                    onclick="toggleComments(${post.id})">

                    <span class="commentIcon"></span>

                    <span>
                        ${commentCount || 0}
                    </span>

                </button>

            </div>


            <div
                id="comments-${post.id}"
                class="commentsArea hidden">
            </div>

        </article>
    `;
}


/* =========================================================
   LIKE
========================================================= */

async function toggleLike(postId) {

    const { data: existing } =
        await supabaseClient
            .from("likes")
            .select("post_id")
            .eq("post_id", postId)
            .eq("user_id", currentUser.id)
            .maybeSingle();

    if (existing) {

        await supabaseClient
            .from("likes")
            .delete()
            .eq("post_id", postId)
            .eq("user_id", currentUser.id);

    } else {

        await supabaseClient
            .from("likes")
            .insert({
                post_id: postId,
                user_id: currentUser.id
            });
    }

    await loadFeed();
}


/* =========================================================
   COMMENTS
========================================================= */

async function toggleComments(postId) {

    const area =
        document.getElementById(
            `comments-${postId}`
        );

    if (!area.classList.contains("hidden")) {

        area.classList.add("hidden");

        return;
    }

    area.classList.remove("hidden");

    await loadComments(postId);
}

async function loadComments(postId) {

    const area =
        document.getElementById(
            `comments-${postId}`
        );

    area.innerHTML =
        `<div class="loading">Loading comments...</div>`;

    const { data: comments, error } =
        await supabaseClient
            .from("comments")
            .select(`
                id,
                content,
                created_at,
                profiles (
                    username,
                    display_name
                )
            `)
            .eq("post_id", postId)
            .order("created_at", {
                ascending: true
            });

    if (error) {

        area.innerHTML =
            `<div>${escapeHTML(error.message)}</div>`;

        return;
    }

    let html = "";

    for (const comment of comments || []) {

        html += `
            <div class="comment">

                <div class="commentName">
                    ${escapeHTML(
                        comment.profiles?.display_name || "User"
                    )}
                    ·
                    @${escapeHTML(
                        comment.profiles?.username || ""
                    )}
                </div>

                <div class="commentText">
                    ${escapeHTML(comment.content)}
                </div>

            </div>
        `;
    }

    html += `

        <div class="commentForm">

            <input
                id="commentInput-${postId}"
                maxlength="500"
                placeholder="Write a comment..."
            >

            <button
                onclick="addComment(${postId})">
                Post
            </button>

        </div>

    `;

    area.innerHTML = html;
}

async function addComment(postId) {

    const input =
        document.getElementById(
            `commentInput-${postId}`
        );

    const content =
        input.value.trim();

    if (!content) return;

    const { error } =
        await supabaseClient
            .from("comments")
            .insert({
                post_id: postId,
                user_id: currentUser.id,
                content: content
            });

    if (error) {

        alert(error.message);

        return;
    }

    await loadComments(postId);
}


/* =========================================================
   DELETE POST
========================================================= */

async function deletePost(postId) {

    if (!confirm("Delete this post?")) {
        return;
    }

    const { error } =
        await supabaseClient
            .from("posts")
            .delete()
            .eq("id", postId)
            .eq("user_id", currentUser.id);

    if (error) {

        alert(error.message);

        return;
    }

    await loadFeed();
}


/* =========================================================
   PROFILE SEARCH
========================================================= */

let searchTimer = null;

function searchProfiles() {

    clearTimeout(searchTimer);

    searchTimer =
        setTimeout(
            performProfileSearch,
            300
        );
}

async function performProfileSearch() {

    const query =
        document.getElementById("profileSearch")
        .value
        .trim();

    const results =
        document.getElementById("searchResults");

    if (query.length < 2) {

        results.innerHTML = "";

        return;
    }

    const { data, error } =
        await supabaseClient
            .from("profiles")
            .select(`
                id,
                username,
                display_name,
                avatar_url
            `)
            .or(
                `username.ilike.%${query}%,display_name.ilike.%${query}%`
            )
            .limit(10);

    if (error) {

        results.innerHTML =
            `<div>${escapeHTML(error.message)}</div>`;

        return;
    }

    if (!data.length) {

        results.innerHTML = `
            <div class="emptyMessage">
                No users found.
            </div>
        `;

        return;
    }

    results.innerHTML = data.map(profile => `

        <div
            class="searchUser"
            onclick="showProfile('${profile.id}')">

            ${avatarHTML(profile)}

            <div>

                <strong>
                    ${escapeHTML(profile.display_name)}
                </strong>

                <br>

                @${escapeHTML(profile.username)}

            </div>

        </div>

    `).join("");
}


/* =========================================================
   FRIEND REQUESTS
========================================================= */

async function sendFriendRequest(targetUserId) {

    if (!currentUser) return;

    if (targetUserId === currentUser.id) {
        return;
    }

    const { data: existing, error: checkError } =
        await supabaseClient
            .from("friend_requests")
            .select("id,status")
            .eq("sender_id", currentUser.id)
            .eq("receiver_id", targetUserId)
            .maybeSingle();

    if (checkError) {

        alert(
            "Friend requests are not set up yet. Run the friend-request SQL below."
        );

        return;
    }

    if (existing) {

        alert(
            existing.status === "accepted"
            ? "You are already friends."
            : "Friend request already sent."
        );

        return;
    }

    const { error } =
        await supabaseClient
            .from("friend_requests")
            .insert({
                sender_id: currentUser.id,
                receiver_id: targetUserId,
                status: "pending"
            });

    if (error) {

        alert(error.message);

        return;
    }

    alert("Friend request sent.");
}


/* =========================================================
   LOGOUT
========================================================= */

async function logout() {

    await supabaseClient.auth.signOut();

    currentUser = null;
    currentProfile = null;

    showAuth();
}


/* =========================================================
   START
========================================================= */

checkSession();

</script>

</body>
</html>
