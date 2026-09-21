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
}

body {
    background: var(--olive);
    color: var(--brown);
    font-family: Arial, Helvetica, sans-serif;
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
    align-items: center;
    justify-content: center;
    padding: 20px;
}

.auth-card {
    width: 100%;
    max-width: 430px;
    background: var(--cream);
    border: 4px solid var(--brown);
    border-radius: 24px;
    padding: 28px;
    box-shadow: 0 12px 30px rgba(0,0,0,.15);
}

.auth-logo {
    text-align: center;
    font-size: 14px;
    font-weight: 900;
}

.auth-title {
    text-align: center;
    font-size: 38px;
    margin: 8px 0 0;
    font-weight: 1000;
}

.auth-subtitle {
    text-align: center;
    font-size: 11px;
    font-weight: 900;
    margin: 8px 0 25px;
}

.auth-card input {
    width: 100%;
    padding: 14px;
    margin-bottom: 12px;
    border: 2px solid var(--brown);
    border-radius: 12px;
    background: var(--cream);
    color: var(--brown);
    outline: none;
}

.main-button,
.secondary-button {
    width: 100%;
    padding: 13px;
    border-radius: 12px;
    font-weight: 900;
}

.main-button {
    border: 3px solid var(--brown);
    background: var(--brown);
    color: var(--cream);
}

.secondary-button {
    margin-top: 10px;
    border: 3px solid var(--brown);
    background: var(--olive);
    color: var(--brown);
}

.auth-message {
    min-height: 20px;
    margin-top: 12px;
    text-align: center;
    font-size: 13px;
    font-weight: 900;
}

/* =========================
   HEADER
========================= */

.top-banner {
    background: var(--brown);
    color: var(--cream);
    padding: 18px 16px 20px;
    border-bottom: 5px solid var(--cream);
}

.product-name {
    font-size: 12px;
    font-weight: 900;
}

.site-title {
    margin-top: 7px;
    font-size: clamp(30px, 9vw, 58px);
    line-height: .95;
    font-weight: 1000;
}

.site-subtitle {
    margin-top: 9px;
    font-size: 11px;
    font-weight: 900;
}

/* =========================
   NAV
========================= */

.nav {
    position: sticky;
    top: 0;
    z-index: 50;

    display: flex;
    gap: 8px;
    flex-wrap: wrap;

    padding: 10px;

    background: var(--cream);
    border-bottom: 3px solid var(--brown);
}

.nav button {
    padding: 9px 13px;
    border: 2px solid var(--brown);
    border-radius: 10px;
    background: var(--olive);
    color: var(--brown);
    font-weight: 900;
}

.nav button:hover {
    background: var(--brown);
    color: var(--cream);
}

/* =========================
   MAIN
========================= */

.container {
    width: 100%;
    max-width: 850px;
    margin: auto;
    padding: 18px 10px 50px;
}

/* =========================
   CREATE POST
========================= */

.create-post {
    background: var(--cream);
    border: 3px solid var(--brown);
    border-radius: 18px;
    padding: 14px;
    margin-bottom: 18px;
}

.create-post textarea {
    width: 100%;
    min-height: 90px;
    resize: vertical;
    padding: 12px;
    border: 2px solid var(--brown);
    border-radius: 12px;
    background: var(--cream);
    color: var(--brown);
    outline: none;
}

.post-tools {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-top: 10px;
}

.file-label {
    display: inline-flex;
    align-items: center;
    justify-content: center;

    padding: 10px 13px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--olive);
    color: var(--brown);

    font-weight: 900;
    cursor: pointer;
}

.file-label input {
    display: none;
}

.post-button {
    margin-left: auto;
    padding: 10px 18px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--brown);
    color: var(--cream);

    font-weight: 900;
}

.selected-file {
    margin-top: 8px;
    font-size: 12px;
    font-weight: 900;
}

/* =========================
   POSTS
========================= */

.post {
    background: var(--cream);
    border: 3px solid var(--brown);
    border-radius: 18px;
    padding: 14px;
    margin-bottom: 18px;
}

.post-header {
    display: flex;
    align-items: center;
    gap: 10px;
}

.avatar {
    width: 48px;
    height: 48px;
    min-width: 48px;

    border-radius: 50%;
    border: 3px solid var(--brown);

    object-fit: cover;

    background: var(--olive);
}

.avatar-placeholder {
    display: flex;
    align-items: center;
    justify-content: center;

    font-size: 18px;
    font-weight: 1000;
}

.user-info {
    min-width: 0;
    flex: 1;
}

.display-name {
    font-size: 15px;
    font-weight: 1000;
}

.username {
    font-size: 11px;
    font-weight: 900;
}

.post-time {
    margin-top: 3px;
    font-size: 10px;
    font-weight: 900;
}

.post-content {
    margin: 16px 2px;
    text-align: center;
    white-space: pre-wrap;
    overflow-wrap: anywhere;

    font-size: 16px;
    line-height: 1.45;
}

.post-media {
    display: block;
    width: 100%;
    max-height: 650px;

    object-fit: contain;

    border: 3px solid var(--brown);
    border-radius: 14px;

    background: var(--olive);
    margin: 12px auto;
}

.post-actions {
    display: flex;
    justify-content: space-between;

    margin-top: 12px;
    padding-top: 10px;

    border-top: 2px solid var(--brown);
}

.action-button {
    padding: 8px 12px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--olive);
    color: var(--brown);

    font-weight: 900;
}

.action-button.liked {
    background: var(--brown);
    color: var(--cream);
}

.delete-button {
    border: 0;
    background: transparent;
    color: var(--brown);
    font-size: 11px;
    font-weight: 900;
}

/* =========================
   FRIEND BUTTON
========================= */

.friend-button {
    position: relative;

    width: 43px;
    height: 43px;
    min-width: 43px;

    border: 3px solid var(--brown);
    border-radius: 50%;

    background: var(--olive);
}

.friend-button::before,
.friend-button::after {
    content: "";

    position: absolute;

    width: 15px;
    height: 15px;

    top: 11px;

    border: 2px solid var(--brown);
    border-radius: 50%;
}

.friend-button::before {
    left: 6px;
}

.friend-button::after {
    right: 6px;
}

/* =========================
   COMMENTS
========================= */

.comments {
    margin-top: 12px;
    padding-top: 10px;
    border-top: 2px solid var(--brown);
}

.comment {
    padding: 8px 0;
    border-bottom: 1px solid var(--brown);
    font-size: 13px;
}

.comment strong {
    font-weight: 1000;
}

.comment-form {
    display: flex;
    gap: 7px;
    margin-top: 10px;
}

.comment-form input {
    flex: 1;
    min-width: 0;

    padding: 10px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--cream);
    color: var(--brown);
}

.comment-form button {
    padding: 0 13px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--brown);
    color: var(--cream);

    font-weight: 900;
}

/* =========================
   SEARCH
========================= */

.search-box {
    display: flex;
    gap: 8px;
    margin-bottom: 15px;
}

.search-box input {
    flex: 1;
    min-width: 0;

    padding: 13px;

    border: 3px solid var(--brown);
    border-radius: 12px;

    background: var(--cream);
    color: var(--brown);
}

.search-box button {
    padding: 0 16px;

    border: 3px solid var(--brown);
    border-radius: 12px;

    background: var(--brown);
    color: var(--cream);

    font-weight: 900;
}

.search-result {
    display: flex;
    align-items: center;
    gap: 10px;

    padding: 12px;
    margin-bottom: 10px;

    background: var(--cream);
    border: 3px solid var(--brown);
    border-radius: 15px;
}

.open-profile {
    flex: 1;

    text-align: left;

    background: transparent;
    border: 0;

    color: var(--brown);
}

.open-profile strong {
    display: block;
    font-weight: 1000;
}

.open-profile span {
    font-size: 11px;
    font-weight: 900;
}

.send-friend {
    padding: 9px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--olive);
    color: var(--brown);

    font-weight: 900;
}

/* =========================
   PROFILE
========================= */

.profile-card {
    background: var(--cream);
    border: 3px solid var(--brown);
    border-radius: 18px;
    padding: 18px;
}

.profile-top {
    display: flex;
    align-items: center;
    gap: 15px;
}

.profile-avatar {
    width: 100px;
    height: 100px;

    border-radius: 50%;
    border: 4px solid var(--brown);

    object-fit: cover;

    background: var(--olive);
}

.profile-name {
    font-size: 25px;
    font-weight: 1000;
}

.profile-username {
    font-size: 13px;
    font-weight: 900;
}

.profile-bio {
    margin-top: 15px;
    white-space: pre-wrap;
    line-height: 1.4;
}

.profile-edit {
    margin-top: 18px;
    padding-top: 15px;

    border-top: 3px solid var(--brown);
}

.profile-edit input,
.profile-edit textarea {
    width: 100%;
    padding: 11px;
    margin-bottom: 10px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--cream);
    color: var(--brown);
}

.profile-edit textarea {
    min-height: 80px;
    resize: vertical;
}

.profile-edit button {
    padding: 10px 15px;

    border: 2px solid var(--brown);
    border-radius: 10px;

    background: var(--brown);
    color: var(--cream);

    font-weight: 900;
}

/* =========================
   UTILITY
========================= */

.empty,
.loading {
    text-align: center;
    padding: 25px;

    background: var(--cream);

    border: 3px solid var(--brown);
    border-radius: 18px;

    font-weight: 900;
}

.section-title {
    margin-bottom: 14px;
    font-size: 24px;
    font-weight: 1000;
}

@media (max-width: 600px) {

    .site-title {
        font-size: 32px;
    }

    .container {
        padding-left: 7px;
        padding-right: 7px;
    }

    .post-tools {
        flex-direction: column;
    }

    .post-button {
        width: 100%;
        margin-left: 0;
    }

    .profile-avatar {
        width: 82px;
        height: 82px;
    }
}
</style>
</head>

<body>

<!-- =========================================================
     AUTH
========================================================= -->

<section id="authScreen">

    <div class="auth-card">

        <div class="auth-logo">
            [ZaheenProduct]
        </div>

        <h1 class="auth-title">
            [DPSB SSMW]
        </h1>

        <div class="auth-subtitle">
            delhi public school budgam secret social media website
        </div>

        <!-- LOGIN -->

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
                class="main-button"
                onclick="login()"
            >
                LOGIN
            </button>

            <button
                class="secondary-button"
                onclick="showSignup()"
            >
                CREATE ACCOUNT
            </button>

        </div>


        <!-- SIGNUP -->

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
                class="main-button"
                onclick="signup()"
            >
                SIGN UP
            </button>

            <button
                class="secondary-button"
                onclick="showLogin()"
            >
                BACK TO LOGIN
            </button>

        </div>

        <div id="authMessage" class="auth-message"></div>

    </div>

</section>


<!-- =========================================================
     APP
========================================================= -->

<section id="app" class="hidden">

    <header class="top-banner">

        <div class="product-name">
            [ZaheenProduct]
        </div>

        <div class="site-title">
            [DPSB SSMW]
        </div>

        <div class="site-subtitle">
            delhi public school budgam secret social media website
        </div>

    </header>


    <nav class="nav">

        <button onclick="showHome()">
            HOME
        </button>

        <button onclick="showMyProfile()">
            PROFILE
        </button>

        <button onclick="showSearch()">
            SEARCH
        </button>

        <button onclick="logout()">
            LOG OUT
        </button>

    </nav>


    <main class="container">

        <!-- HOME -->

        <section id="homeSection">

            <div class="create-post">

                <textarea
                    id="postText"
                    maxlength="1000"
                    placeholder="Write something..."
                ></textarea>

                <div class="post-tools">

                    <label class="file-label">

                        PHOTO / VIDEO

                        <input
                            id="postMedia"
                            type="file"
                            accept="image/*,video/*"
                            onchange="showSelectedFile()"
                        >

                    </label>

                    <button
                        class="post-button"
                        onclick="createPost()"
                    >
                        POST
                    </button>

                </div>

                <div
                    id="selectedFile"
                    class="selected-file"
                ></div>

            </div>


            <div id="feed">

                <div class="loading">
                    Loading posts...
                </div>

            </div>

        </section>


        <!-- PROFILE -->

        <section
            id="profileSection"
            class="hidden"
        >

            <div class="section-title">
                PROFILE
            </div>

            <div id="profileContent"></div>

        </section>


        <!-- SEARCH -->

        <section
            id="searchSection"
            class="hidden"
        >

            <div class="section-title">
                SEARCH PROFILES
            </div>

            <div class="search-box">

                <input
                    id="profileSearchInput"
                    type="text"
                    placeholder="Search username or name..."
                    onkeydown="if(event.key==='Enter') searchProfiles()"
                >

                <button onclick="searchProfiles()">
                    SEARCH
                </button>

            </div>

            <div id="searchResults"></div>

        </section>

    </main>

</section>


<script>

/* =========================================================
   SUPABASE
========================================================= */

const SUPABASE_URL =
    "https://soirkzbrsmgxydmikerx.supabase.co";

const SUPABASE_KEY =
    "sb_publishable_YfZn0IZdTs8L-EThj6lxOg_uFQCDxIp";

const supabaseClient =
    window.supabase.createClient(
        SUPABASE_URL,
        SUPABASE_KEY
    );


/* =========================================================
   STATE
========================================================= */

let currentUser = null;
let currentProfile = null;


/* =========================================================
   AUTH
========================================================= */

function usernameToInternalEmail(username) {

    return (
        username
            .toLowerCase()
            .trim()
            .replace(/\s+/g, "")
        + "@dpsbssmw.local"
    );

}


function setAuthMessage(message) {

    document.getElementById(
        "authMessage"
    ).textContent = message || "";

}


function showLogin() {

    document
        .getElementById("loginForm")
        .classList.remove("hidden");

    document
        .getElementById("signupForm")
        .classList.add("hidden");

    setAuthMessage("");

}


function showSignup() {

    document
        .getElementById("loginForm")
        .classList.add("hidden");

    document
        .getElementById("signupForm")
        .classList.remove("hidden");

    setAuthMessage("");

}


/* =========================================================
   SIGN UP
========================================================= */

async function signup() {

    const username =
        document
            .getElementById("signupUsername")
            .value
            .trim();

    const displayName =
        document
            .getElementById("signupDisplayName")
            .value
            .trim();

    const password =
        document
            .getElementById("signupPassword")
            .value;


    if (!username || !displayName || !password) {

        setAuthMessage(
            "Please fill in every field."
        );

        return;
    }


    if (username.length < 3) {

        setAuthMessage(
            "Username must be at least 3 characters."
        );

        return;
    }


    if (password.length < 6) {

        setAuthMessage(
            "Password must be at least 6 characters."
        );

        return;
    }


    setAuthMessage(
        "Creating account..."
    );


    const email =
        usernameToInternalEmail(
            username
        );


    const {
        data,
        error
    } =
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

        setAuthMessage(
            error.message
        );

        return;
    }


    if (!data.user) {

        setAuthMessage(
            "Account could not be created."
        );

        return;
    }


    setAuthMessage(
        "Account created."
    );


    currentUser =
        data.user;


    await openApp();

}


/* =========================================================
   LOGIN
========================================================= */

async function login() {

    const username =
        document
            .getElementById("loginUsername")
            .value
            .trim();

    const password =
        document
            .getElementById("loginPassword")
            .value;


    if (!username || !password) {

        setAuthMessage(
            "Enter your username and password."
        );

        return;
    }


    setAuthMessage(
        "Logging in..."
    );


    const email =
        usernameToInternalEmail(
            username
        );


    const {
        data,
        error
    } =
        await supabaseClient.auth
            .signInWithPassword({

                email: email,

                password: password

            });


    if (error) {

        console.error(error);

        setAuthMessage(
            "Login failed: " +
            error.message
        );

        return;
    }


    currentUser =
        data.user;


    await openApp();

}


/* =========================================================
   SESSION
========================================================= */

async function loadCurrentUser() {

    const {
        data: {
            session
        }
    } =
        await supabaseClient.auth
            .getSession();


    if (
        session &&
        session.user
    ) {

        currentUser =
            session.user;

        await openApp();

    }

}


supabaseClient.auth.onAuthStateChange(
    (event, session) => {

        currentUser =
            session?.user || null;

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

    await showHome();

}


/* =========================================================
   CURRENT PROFILE
========================================================= */

async function loadCurrentProfile() {

    if (!currentUser) return;


    const {
        data,
        error
    } =
        await supabaseClient
            .from("profiles")
            .select("*")
            .eq(
                "id",
                currentUser.id
            )
            .maybeSingle();


    if (error) {

        console.error(
            "Profile error:",
            error
        );

        return;
    }


    currentProfile =
        data;

}


/* =========================================================
   NAVIGATION
========================================================= */

function hideAllSections() {

    document
        .getElementById("homeSection")
        .classList.add("hidden");

    document
        .getElementById("profileSection")
        .classList.add("hidden");

    document
        .getElementById("searchSection")
        .classList.add("hidden");

}


async function showHome() {

    hideAllSections();

    document
        .getElementById("homeSection")
        .classList.remove("hidden");

    await loadFeed();

}


async function showMyProfile() {

    await loadProfilePage(
        currentUser.id
    );

}


function showSearch() {

    hideAllSections();

    document
        .getElementById("searchSection")
        .classList.remove("hidden");

    document
        .getElementById("profileSearchInput")
        .focus();

}


/* =========================================================
   LOGOUT
========================================================= */

async function logout() {

    await supabaseClient.auth.signOut();

    currentUser = null;
    currentProfile = null;


    document
        .getElementById("app")
        .classList.add("hidden");

    document
        .getElementById("authScreen")
        .classList.remove("hidden");

    showLogin();

}


/* =========================================================
   LOAD FEED
========================================================= */

async function loadFeed() {

    const feed =
        document.getElementById(
            "feed"
        );


    feed.innerHTML = `
        <div class="loading">
            Loading posts...
        </div>
    `;


    /*
       IMPORTANT:
       Posts and profiles are intentionally
       fetched separately.
    */

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


        feed.innerHTML = `
            <div class="empty">

                Could not load posts.

                <br><br>

                ${escapeHTML(
                    postsError.message
                )}

            </div>
        `;

        return;
    }


    if (
        !posts ||
        posts.length === 0
    ) {

        feed.innerHTML = `
            <div class="empty">
                No posts yet.
            </div>
        `;

        return;
    }


    const userIds =
        [
            ...new Set(
                posts.map(
                    post =>
                        post.user_id
                )
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


        feed.innerHTML = `
            <div class="empty">

                Posts were found,
                but profiles could not be loaded.

                <br><br>

                ${escapeHTML(
                    profilesError.message
                )}

            </div>
        `;

        return;
    }


    const profileMap = {};


    (profiles || [])
        .forEach(profile => {

            profileMap[
                profile.id
            ] = profile;

        });


    feed.innerHTML = "";


    for (
        const post of posts
    ) {

        const profile =
            profileMap[
                post.user_id
            ] || {

                id: post.user_id,

                username:
                    "unknown",

                display_name:
                    "Unknown User",

                avatar_url:
                    ""

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


/* =========================================================
   POST HTML
========================================================= */

async function createPostHTML(
    post,
    profile
) {

    let likeCount = 0;
    let userLiked = false;


    const {
        count
    } =
        await supabaseClient
            .from("likes")
            .select(
                "*",
                {
                    count: "exact",
                    head: true
                }
            )
            .eq(
                "post_id",
                post.id
            );


    likeCount =
        count || 0;


    if (currentUser) {

        const {
            data
        } =
            await supabaseClient
                .from("likes")
                .select("post_id")
                .eq(
                    "post_id",
                    post.id
                )
                .eq(
                    "user_id",
                    currentUser.id
                )
                .maybeSingle();


        userLiked =
            !!data;

    }


    const {
        data: comments
    } =
        await supabaseClient
            .from("comments")
            .select(`
                id,
                content,
                user_id,
                created_at
            `)
            .eq(
                "post_id",
                post.id
            )
            .order(
                "created_at",
                {
                    ascending: true
                }
            );


    let commentHTML = "";


    if (
        comments &&
        comments.length
    ) {

        const ids =
            [
                ...new Set(
                    comments.map(
                        c => c.user_id
                    )
                )
            ];


        const {
            data: commentProfiles
        } =
            await supabaseClient
                .from("profiles")
                .select(`
                    id,
                    username,
                    display_name
                `)
                .in(
                    "id",
                    ids
                );


        const map = {};


        (commentProfiles || [])
            .forEach(profile => {

                map[
                    profile.id
                ] = profile;

            });


        commentHTML =
            comments
                .map(comment => {

                    const p =
                        map[
                            comment.user_id
                        ] || {

                            display_name:
                                "Unknown User"

                        };


                    return `
                        <div class="comment">

                            <strong>
                                ${escapeHTML(
                                    p.display_name
                                )}
                            </strong>

                            ${escapeHTML(
                                comment.content
                            )}

                        </div>
                    `;

                })
                .join("");

    }


    let avatarHTML;


    if (profile.avatar_url) {

        avatarHTML = `
            <img
                class="avatar"
                src="${escapeAttribute(
                    profile.avatar_url
                )}"
                alt="Profile picture"
            >
        `;

    } else {

        avatarHTML = `
            <div class="avatar avatar-placeholder">
                ${escapeHTML(
                    getInitial(
                        profile.display_name
                    )
                )}
            </div>
        `;

    }


    let mediaHTML = "";


    if (
        post.media_url &&
        post.media_type === "image"
    ) {

        mediaHTML = `
            <img
                class="post-media"
                src="${escapeAttribute(
                    post.media_url
                )}"
                alt="Post image"
                loading="lazy"
            >
        `;

    }


    if (
        post.media_url &&
        post.media_type === "video"
    ) {

        mediaHTML = `
            <video
                class="post-media"
                src="${escapeAttribute(
                    post.media_url
                )}"
                controls
                playsinline
            ></video>
        `;

    }


    const ownPost =
        currentUser &&
        currentUser.id === post.user_id;


    return `

        <article
            class="post"
            id="post-${post.id}"
        >

            <div class="post-header">

                ${avatarHTML}

                <div class="user-info">

                    <div class="display-name">
                        ${escapeHTML(
                            profile.display_name ||
                            profile.username ||
                            "Unknown User"
                        )}
                    </div>

                    <div class="username">
                        @${escapeHTML(
                            profile.username ||
                            "unknown"
                        )}
                    </div>

                    <div class="post-time">
                        ${formatDate(
                            post.created_at
                        )}
                    </div>

                </div>


                ${
                    ownPost
                    ? ""
                    : `
                        <button
                            class="friend-button"
                            title="Send friend request"
                            onclick="sendFriendRequest('${post.user_id}')"
                        ></button>
                    `
                }

            </div>


            ${
                post.content
                ? `
                    <div class="post-content">
                        ${escapeHTML(
                            post.content
                        )}
                    </div>
                `
                : ""
            }


            ${mediaHTML}


            <div class="post-actions">

                <button
                    class="action-button ${
                        userLiked
                            ? "liked"
                            : ""
                    }"
                    onclick="toggleLike(${post.id})"
                >
                    👍 ${likeCount}
                </button>


                <button
                    class="action-button"
                    onclick="toggleComments(${post.id})"
                >
                    💬 ${
                        comments
                            ? comments.length
                            : 0
                    }
                </button>

            </div>


            ${
                ownPost
                ? `
                    <div style="text-align:right;margin-top:8px;">

                        <button
                            class="delete-button"
                            onclick="deletePost(${post.id})"
                        >
                            DELETE POST
                        </button>

                    </div>
                `
                : ""
            }


            <div
                id="comments-${post.id}"
                class="comments hidden"
            >

                <div>
                    ${commentHTML}
                </div>


                <div class="comment-form">

                    <input
                        id="comment-input-${post.id}"
                        maxlength="500"
                        placeholder="Write a comment..."
                    >

                    <button
                        onclick="addComment(${post.id})"
                    >
                        SEND
                    </button>

                </div>

            </div>

        </article>

    `;

}


/* =========================================================
   CREATE POST
========================================================= */

function showSelectedFile() {

    const file =
        document
            .getElementById("postMedia")
            .files[0];


    document
        .getElementById("selectedFile")
        .textContent =
        file
            ? "Selected: " + file.name
            : "";

}


async function uploadPostMedia(file) {

    const extension =
        file.name
            .split(".")
            .pop()
            .toLowerCase();


    const path =
        currentUser.id +
        "/" +
        Date.now() +
        "_" +
        Math.random()
            .toString(36)
            .slice(2) +
        "." +
        extension;


    const {
        error
    } =
        await supabaseClient.storage
            .from("post-media")
            .upload(
                path,
                file,
                {
                    cacheControl:
                        "3600",

                    upsert:
                        false
                }
            );


    if (error) {

        throw error;

    }


    const {
        data
    } =
        supabaseClient.storage
            .from("post-media")
            .getPublicUrl(
                path
            );


    return data.publicUrl;

}


async function createPost() {

    if (!currentUser) {

        alert(
            "Please log in first."
        );

        return;
    }


    const text =
        document
            .getElementById("postText")
            .value
            .trim();


    const file =
        document
            .getElementById("postMedia")
            .files[0];


    if (!text && !file) {

        alert(
            "Write something or select a photo/video."
        );

        return;
    }


    try {

        let mediaURL = null;
        let mediaType = null;


        if (file) {

            if (
                file.size >
                100 * 1024 * 1024
            ) {

                alert(
                    "Keep files under 100 MB."
                );

                return;
            }


            mediaURL =
                await uploadPostMedia(
                    file
                );


            if (
                file.type.startsWith(
                    "image/"
                )
            ) {

                mediaType =
                    "image";

            } else if (
                file.type.startsWith(
                    "video/"
                )
            ) {

                mediaType =
                    "video";

            }

        }


        const {
            error
        } =
            await supabaseClient
                .from("posts")
                .insert({

                    user_id:
                        currentUser.id,

                    content:
                        text || null,

                    media_url:
                        mediaURL,

                    media_type:
                        mediaType

                });


        if (error) {

            console.error(error);

            alert(
                "Could not create post:\n\n" +
                error.message
            );

            return;
        }


        document
            .getElementById("postText")
            .value = "";


        document
            .getElementById("postMedia")
            .value = "";


        document
            .getElementById("selectedFile")
            .textContent = "";


        await loadFeed();

    } catch (error) {

        console.error(error);

        alert(
            "Something went wrong:\n\n" +
            error.message
        );

    }

}


/* =========================================================
   LIKE
========================================================= */

async function toggleLike(postId) {

    const {
        data: existing
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


    if (existing) {

        const {
            error
        } =
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

            alert(error.message);

            return;
        }

    } else {

        const {
            error
        } =
            await supabaseClient
                .from("likes")
                .insert({

                    post_id:
                        postId,

                    user_id:
                        currentUser.id

                });


        if (error) {

            alert(error.message);

            return;
        }

    }


    await loadFeed();

}


/* =========================================================
   COMMENTS
========================================================= */

function toggleComments(postId) {

    document
        .getElementById(
            "comments-" + postId
        )
        .classList.toggle(
            "hidden"
        );

}


async function addComment(postId) {

    const input =
        document
            .getElementById(
                "comment-input-" + postId
            );


    const content =
        input.value.trim();


    if (!content) return;


    const {
        error
    } =
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

        alert(error.message);

        return;
    }


    await loadFeed();


    setTimeout(() => {

        const comments =
            document.getElementById(
                "comments-" + postId
            );

        if (comments) {

            comments.classList.remove(
                "hidden"
            );

        }

    }, 100);

}


/* =========================================================
   DELETE POST
========================================================= */

async function deletePost(postId) {

    if (
        !confirm(
            "Delete this post?"
        )
    ) return;


    const {
        error
    } =
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

        alert(error.message);

        return;
    }


    await loadFeed();

}


/* =========================================================
   FRIEND REQUEST
========================================================= */

async function sendFriendRequest(
    receiverId
) {

    if (
        !currentUser ||
        receiverId === currentUser.id
    ) return;


    const {
        data: existing
    } =
        await supabaseClient
            .from("friend_requests")
            .select("id,status")
            .or(
                `and(sender_id.eq.${currentUser.id},receiver_id.eq.${receiverId}),and(sender_id.eq.${receiverId},receiver_id.eq.${currentUser.id})`
            );


    if (
        existing &&
        existing.length
    ) {

        alert(
            "A friend request already exists."
        );

        return;
    }


    const {
        error
    } =
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

        alert(
            "Could not send friend request:\n\n" +
            error.message
        );

        return;
    }


    alert(
        "Friend request sent."
    );

}


/* =========================================================
   SEARCH
========================================================= */

async function searchProfiles() {

    const query =
        document
            .getElementById(
                "profileSearchInput"
            )
            .value
            .trim();


    const results =
        document
            .getElementById(
                "searchResults"
            );


    if (!query) {

        results.innerHTML = `
            <div class="empty">
                Enter a username or name.
            </div>
        `;

        return;
    }


    results.innerHTML = `
        <div class="loading">
            Searching...
        </div>
    `;


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
                `username.ilike.%${escapeFilter(query)}%,display_name.ilike.%${escapeFilter(query)}%`
            )
            .limit(30);


    if (error) {

        results.innerHTML = `
            <div class="empty">
                ${escapeHTML(
                    error.message
                )}
            </div>
        `;

        return;
    }


    if (
        !data ||
        data.length === 0
    ) {

        results.innerHTML = `
            <div class="empty">
                No users found.
            </div>
        `;

        return;
    }


    results.innerHTML =
        data.map(profile => {

            const avatar =
                profile.avatar_url
                ? `
                    <img
                        class="avatar"
                        src="${escapeAttribute(
                            profile.avatar_url
                        )}"
                        alt=""
                    >
                `
                : `
                    <div class="avatar avatar-placeholder">
                        ${escapeHTML(
                            getInitial(
                                profile.display_name
                            )
                        )}
                    </div>
                `;


            const own =
                profile.id ===
                currentUser.id;


            return `

                <div class="search-result">

                    ${avatar}

                    <button
                        class="open-profile"
                        onclick="loadProfilePage('${profile.id}')"
                    >

                        <strong>
                            ${escapeHTML(
                                profile.display_name
                            )}
                        </strong>

                        <span>
                            @${escapeHTML(
                                profile.username
                            )}
                        </span>

                    </button>


                    ${
                        own
                        ? ""
                        : `
                            <button
                                class="send-friend"
                                onclick="sendFriendRequest('${profile.id}')"
                            >
                                + FRIEND
                            </button>
                        `
                    }

                </div>

            `;

        }).join("");

}


/* =========================================================
   PROFILE
========================================================= */

async function loadProfilePage(
    userId
) {

    hideAllSections();


    document
        .getElementById(
            "profileSection"
        )
        .classList.remove(
            "hidden"
        );


    const container =
        document.getElementById(
            "profileContent"
        );


    container.innerHTML = `
        <div class="loading">
            Loading profile...
        </div>
    `;


    const {
        data: profile,
        error
    } =
        await supabaseClient
            .from("profiles")
            .select("*")
            .eq(
                "id",
                userId
            )
            .maybeSingle();


    if (
        error ||
        !profile
    ) {

        container.innerHTML = `
            <div class="empty">
                Could not load profile.
            </div>
        `;

        return;
    }


    const own =
        currentUser.id ===
        userId;


    const avatar =
        profile.avatar_url
        ? `
            <img
                class="profile-avatar"
                src="${escapeAttribute(
                    profile.avatar_url
                )}"
                alt="Profile picture"
            >
        `
        : `
            <div class="profile-avatar avatar-placeholder">
                ${escapeHTML(
                    getInitial(
                        profile.display_name
                    )
                )}
            </div>
        `;


    container.innerHTML = `

        <div class="profile-card">

            <div class="profile-top">

                ${avatar}

                <div>

                    <div class="profile-name">
                        ${escapeHTML(
                            profile.display_name
                        )}
                    </div>

                    <div class="profile-username">
                        @${escapeHTML(
                            profile.username
                        )}
                    </div>

                </div>

            </div>


            <div class="profile-bio">

                ${
                    profile.bio
                    ? escapeHTML(
                        profile.bio
                    )
                    : "No bio yet."
                }

            </div>


            ${
                own
                ? `

                    <div class="profile-edit">

                        <input
                            id="editDisplayName"
                            maxlength="80"
                            value="${escapeAttribute(
                                profile.display_name || ""
                            )}"
                            placeholder="Display name"
                        >

                        <textarea
                            id="editBio"
                            maxlength="300"
                            placeholder="Bio"
                        >${escapeHTML(
                            profile.bio || ""
                        )}</textarea>


                        <label class="file-label">

                            CHANGE PROFILE PICTURE

                            <input
                                id="avatarFile"
                                type="file"
                                accept="image/*"
                            >

                        </label>


                        <br><br>


                        <button
                            onclick="saveProfile()"
                        >
                            SAVE PROFILE
                        </button>

                    </div>

                `
                : `

                    <button
                        class="main-button"
                        style="margin-top:18px;"
                        onclick="sendFriendRequest('${profile.id}')"
                    >
                        ADD FRIEND
                    </button>

                `
            }

        </div>

    `;

}


/* =========================================================
   AVATAR UPLOAD
========================================================= */

async function uploadAvatar(file) {

    const extension =
        file.name
            .split(".")
            .pop()
            .toLowerCase();


    const path =
        currentUser.id +
        "/avatar_" +
        Date.now() +
        "." +
        extension;


    const {
        error
    } =
        await supabaseClient.storage
            .from("avatars")
            .upload(
                path,
                file,
                {
                    cacheControl:
                        "3600",

                    upsert:
                        false
                }
            );


    if (error) {

        throw error;

    }


    const {
        data
    } =
        supabaseClient.storage
            .from("avatars")
            .getPublicUrl(
                path
            );


    return data.publicUrl;

}


/* =========================================================
   SAVE PROFILE
========================================================= */

async function saveProfile() {

    const displayName =
        document
            .getElementById(
                "editDisplayName"
            )
            .value
            .trim();


    const bio =
        document
            .getElementById(
                "editBio"
            )
            .value
            .trim();


    const file =
        document
            .getElementById(
                "avatarFile"
            )
            .files[0];


    if (!displayName) {

        alert(
            "Display name cannot be empty."
        );

        return;
    }


    try {

        let avatarURL =
            currentProfile?.avatar_url ||
            null;


        if (file) {

            avatarURL =
                await uploadAvatar(
                    file
                );

        }


        const {
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
                        avatarURL

                })
                .eq(
                    "id",
                    currentUser.id
                );


        if (error) {

            alert(
                error.message
            );

            return;
        }


        await loadCurrentProfile();

        await loadProfilePage(
            currentUser.id
        );

    } catch (error) {

        alert(
            "Profile update failed:\n\n" +
            error.message
        );

    }

}


/* =========================================================
   HELPERS
========================================================= */

function getInitial(name) {

    if (!name) return "?";

    return name
        .trim()
        .charAt(0)
        .toUpperCase();

}


function formatDate(dateString) {

    if (!dateString) return "";

    return new Date(
        dateString
    ).toLocaleString(
        undefined,
        {
            dateStyle: "medium",
            timeStyle: "short"
        }
    );

}


function escapeHTML(value) {

    if (
        value === null ||
        value === undefined
    ) return "";


    return String(value)
        .replace(
            /&/g,
            "&amp;"
        )
        .replace(
            /</g,
            "&lt;"
        )
        .replace(
            />/g,
            "&gt;"
        )
        .replace(
            /"/g,
            "&quot;"
        )
        .replace(
            /'/g,
            "&#039;"
        );

}


function escapeAttribute(value) {

    return escapeHTML(value);

}


function escapeFilter(value) {

    return String(value)
        .replace(
            /\\/g,
            "\\\\"
        )
        .replace(
            /%/g,
            "\\%"
        )
        .replace(
            /_/g,
            "\\_"
        )
        .replace(
            /,/g,
            "\\,"
        )
        .replace(
            /\./g,
            "\\."
        );

}


/* =========================================================
   START
========================================================= */

loadCurrentUser();

</script>

</body>
</html>
