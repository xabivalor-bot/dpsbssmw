# dpsbssmw
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>DPSB SSMW</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

:root {
    --blue: #2563eb;
    --blue-dark: #1d4ed8;
    --background: #f3f4f6;
    --card: #ffffff;
    --text: #111827;
    --muted: #6b7280;
    --border: #e5e7eb;
    --danger: #dc2626;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family:
        -apple-system,
        BlinkMacSystemFont,
        "Segoe UI",
        Arial,
        sans-serif;

    background: var(--background);
    color: var(--text);
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

button:disabled {
    cursor: not-allowed;
    opacity: .6;
}


/* =========================================
   AUTH
========================================= */

#authPage {
    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 20px;

    background:
        radial-gradient(
            circle at top,
            #3b82f6,
            #111827 65%
        );
}

.auth-card {
    width: 100%;
    max-width: 430px;

    background: rgba(255,255,255,.97);

    padding: 36px;

    border-radius: 24px;

    box-shadow:
        0 25px 70px rgba(0,0,0,.3);
}

.logo {
    text-align: center;
    margin-bottom: 28px;
}

.logo-icon {
    width: 70px;
    height: 70px;

    margin: 0 auto 15px;

    border-radius: 20px;

    display: flex;
    justify-content: center;
    align-items: center;

    background: var(--blue);

    color: white;

    font-size: 28px;
    font-weight: 800;

    box-shadow:
        0 10px 25px rgba(37,99,235,.3);
}

.logo h1 {
    font-size: 29px;
    color: var(--blue);
}

.logo p {
    margin-top: 7px;

    color: var(--muted);

    font-size: 14px;
    line-height: 1.5;
}

.auth-title {
    font-size: 21px;
    margin-bottom: 15px;
}

.input-group {
    margin-bottom: 13px;
}

.input-group input {
    width: 100%;

    padding: 14px 15px;

    border: 1px solid var(--border);

    border-radius: 11px;

    outline: none;

    background: white;

    transition: .2s;
}

.input-group input:focus {
    border-color: var(--blue);

    box-shadow:
        0 0 0 3px rgba(37,99,235,.1);
}

.primary-button {
    width: 100%;

    border: none;

    padding: 14px;

    border-radius: 11px;

    background: var(--blue);

    color: white;

    font-weight: 700;

    transition: .2s;
}

.primary-button:hover {
    background: var(--blue-dark);
    transform: translateY(-1px);
}

.switch-button {
    width: 100%;

    margin-top: 15px;

    border: none;

    background: transparent;

    color: var(--blue);

    font-size: 14px;
}

.auth-message {
    display: none;

    margin: 12px 0;

    padding: 11px 12px;

    border-radius: 9px;

    font-size: 14px;

    line-height: 1.4;
}

.auth-message.error {
    display: block;

    background: #fee2e2;
    color: #991b1b;
}

.auth-message.success {
    display: block;

    background: #dcfce7;
    color: #166534;
}


/* =========================================
   APP
========================================= */

#appPage {
    display: none;
    min-height: 100vh;
}

.navbar {
    position: sticky;

    top: 0;

    z-index: 100;

    height: 64px;

    display: flex;

    justify-content: space-between;
    align-items: center;

    padding: 0 20px;

    background: rgba(255,255,255,.94);

    backdrop-filter: blur(12px);

    border-bottom: 1px solid var(--border);
}

.nav-logo {
    color: var(--blue);

    font-size: 20px;

    font-weight: 800;
}

.nav-actions {
    display: flex;
    gap: 8px;
}

.nav-button {
    border: none;

    padding: 9px 13px;

    border-radius: 9px;

    background: #eff6ff;

    color: #1d4ed8;

    font-weight: 600;
}

.nav-button:hover {
    background: #dbeafe;
}

.nav-button.logout {
    background: #fee2e2;
    color: #991b1b;
}


/* =========================================
   MAIN
========================================= */

.main {
    width: 100%;

    max-width: 760px;

    margin: auto;

    padding: 25px 15px 60px;
}


/* =========================================
   PROFILE
========================================= */

.profile-card {
    background: var(--card);

    border: 1px solid var(--border);

    border-radius: 18px;

    padding: 20px;

    margin-bottom: 18px;

    box-shadow:
        0 3px 15px rgba(0,0,0,.04);
}

.profile {
    display: flex;

    align-items: center;

    gap: 14px;
}

.avatar {
    width: 60px;
    height: 60px;

    flex-shrink: 0;

    border-radius: 50%;

    display: flex;

    align-items: center;
    justify-content: center;

    background: var(--blue);

    color: white;

    font-size: 20px;

    font-weight: 800;
}

.profile-name {
    font-size: 19px;

    font-weight: 750;
}

.profile-username {
    color: var(--muted);

    font-size: 14px;

    margin-top: 3px;
}


/* =========================================
   CREATE POST
========================================= */

.create-card {
    background: var(--card);

    border: 1px solid var(--border);

    border-radius: 18px;

    padding: 18px;

    margin-bottom: 18px;

    box-shadow:
        0 3px 15px rgba(0,0,0,.04);
}

.create-card textarea {
    width: 100%;

    min-height: 105px;

    resize: vertical;

    border: 1px solid var(--border);

    border-radius: 12px;

    padding: 13px;

    outline: none;

    line-height: 1.5;
}

.create-card textarea:focus {
    border-color: var(--blue);

    box-shadow:
        0 0 0 3px rgba(37,99,235,.08);
}

.create-footer {
    display: flex;

    justify-content: flex-end;

    margin-top: 10px;
}

.post-button {
    border: none;

    padding: 10px 18px;

    border-radius: 10px;

    background: var(--blue);

    color: white;

    font-weight: 700;
}


/* =========================================
   POST
========================================= */

.post {
    background: var(--card);

    border: 1px solid var(--border);

    border-radius: 18px;

    padding: 19px;

    margin-bottom: 15px;

    box-shadow:
        0 3px 15px rgba(0,0,0,.04);
}

.post-header {
    display: flex;

    align-items: center;

    gap: 11px;

    margin-bottom: 14px;
}

.post-avatar {
    width: 44px;
    height: 44px;

    flex-shrink: 0;

    border-radius: 50%;

    display: flex;

    align-items: center;
    justify-content: center;

    background: #dbeafe;

    color: #1d4ed8;

    font-weight: 800;
}

.post-name {
    font-weight: 700;
}

.post-username {
    color: var(--muted);

    font-size: 13px;

    margin-top: 2px;
}

.post-time {
    color: #9ca3af;

    font-size: 11px;

    margin-top: 2px;
}

.post-content {
    line-height: 1.6;

    font-size: 15px;

    white-space: pre-wrap;

    overflow-wrap: anywhere;

    margin-bottom: 14px;
}

.post-actions {
    display: flex;

    gap: 8px;

    padding-top: 12px;

    border-top: 1px solid var(--border);
}

.action-button {
    border: none;

    background: #f3f4f6;

    color: #374151;

    padding: 8px 12px;

    border-radius: 9px;

    font-size: 13px;
}

.action-button:hover {
    background: #e5e7eb;
}

.action-button.liked {
    background: #dbeafe;

    color: #1d4ed8;
}

.action-button.delete {
    margin-left: auto;

    color: var(--danger);

    background: #fef2f2;
}


/* =========================================
   COMMENTS
========================================= */

.comments {
    margin-top: 13px;

    padding-top: 13px;

    border-top: 1px solid var(--border);
}

.comment {
    background: #f9fafb;

    border-radius: 9px;

    padding: 9px 11px;

    margin-bottom: 7px;

    font-size: 13px;

    line-height: 1.4;
}

.comment-author {
    font-weight: 700;

    color: #374151;

    margin-right: 5px;
}

.comment-input-row {
    display: flex;

    gap: 7px;

    margin-top: 9px;
}

.comment-input {
    flex: 1;

    min-width: 0;

    border: 1px solid var(--border);

    border-radius: 9px;

    padding: 9px 10px;

    outline: none;
}

.comment-input:focus {
    border-color: var(--blue);
}

.comment-send {
    border: none;

    border-radius: 9px;

    padding: 9px 13px;

    background: var(--blue);

    color: white;

    font-weight: 600;
}


/* =========================================
   STATES
========================================= */

.loading,
.empty,
.error-box {
    text-align: center;

    background: var(--card);

    border: 1px solid var(--border);

    border-radius: 18px;

    padding: 30px 20px;

    color: var(--muted);
}

.error-box {
    color: #991b1b;

    background: #fef2f2;
}


/* =========================================
   MOBILE
========================================= */

@media(max-width:600px) {

    .navbar {
        padding: 0 12px;
    }

    .nav-logo {
        font-size: 17px;
    }

    .nav-button {
        padding: 8px 9px;

        font-size: 12px;
    }

    .main {
        padding: 15px 10px 45px;
    }

    .auth-card {
        padding: 25px 20px;
    }

    .post {
        padding: 15px;
    }

    .action-button {
        padding: 8px 9px;
    }

    .comment-input-row {
        flex-direction: row;
    }
}
</style>
</head>


<body>


<!-- =========================================
     AUTH PAGE
========================================= -->

<div id="authPage">

    <div class="auth-card">

        <div class="logo">

            <div class="logo-icon">
                D
            </div>

            <h1>DPSB SSMW</h1>

            <p>
                Delhi Public School Budgam<br>
                Social Media Website
            </p>

        </div>


        <!-- LOGIN -->

        <div id="loginForm">

            <h2 class="auth-title">
                Login
            </h2>

            <div class="input-group">

                <input
                    id="loginUsername"
                    type="text"
                    placeholder="Username"
                    autocomplete="username"
                    maxlength="20"
                >

            </div>


            <div class="input-group">

                <input
                    id="loginPassword"
                    type="password"
                    placeholder="Password"
                    autocomplete="current-password"
                >

            </div>


            <div
                id="loginMessage"
                class="auth-message"
            ></div>


            <button
                id="loginButton"
                class="primary-button"
                onclick="login()"
            >
                Login
            </button>


            <button
                class="switch-button"
                onclick="showSignup()"
            >
                Don't have an account? Sign up
            </button>

        </div>


        <!-- SIGNUP -->

        <div
            id="signupForm"
            style="display:none;"
        >

            <h2 class="auth-title">
                Create Account
            </h2>


            <div class="input-group">

                <input
                    id="signupUsername"
                    type="text"
                    placeholder="Username"
                    autocomplete="username"
                    maxlength="20"
                >

            </div>


            <div class="input-group">

                <input
                    id="signupDisplayName"
                    type="text"
                    placeholder="Display name"
                    maxlength="50"
                >

            </div>


            <div class="input-group">

                <input
                    id="signupPassword"
                    type="password"
                    placeholder="Password"
                    autocomplete="new-password"
                >

            </div>


            <div
                id="signupMessage"
                class="auth-message"
            ></div>


            <button
                id="signupButton"
                class="primary-button"
                onclick="signup()"
            >
                Create Account
            </button>


            <button
                class="switch-button"
                onclick="showLogin()"
            >
                Already have an account? Login
            </button>

        </div>

    </div>

</div>


<!-- =========================================
     MAIN APP
========================================= -->

<div id="appPage">


    <nav class="navbar">

        <div class="nav-logo">
            DPSB SSMW
        </div>


        <div class="nav-actions">

            <button
                class="nav-button"
                onclick="refreshFeed()"
            >
                Home
            </button>

            <button
                class="nav-button logout"
                onclick="logout()"
            >
                Logout
            </button>

        </div>

    </nav>


    <main class="main">


        <!-- PROFILE -->

        <section class="profile-card">

            <div class="profile">

                <div
                    id="profileAvatar"
                    class="avatar"
                >
                    ?
                </div>


                <div>

                    <div
                        id="profileName"
                        class="profile-name"
                    >
                        Loading...
                    </div>

                    <div
                        id="profileUsername"
                        class="profile-username"
                    >
                        @loading
                    </div>

                </div>

            </div>

        </section>


        <!-- CREATE POST -->

        <section class="create-card">

            <textarea
                id="postContent"
                maxlength="1000"
                placeholder="What's happening?"
            ></textarea>


            <div class="create-footer">

                <button
                    id="postButton"
                    class="post-button"
                    onclick="createPost()"
                >
                    Post
                </button>

            </div>

        </section>


        <!-- FEED -->

        <section id="feed">

            <div class="loading">
                Loading posts...
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

const SUPABASE_PUBLISHABLE_KEY =
    "sb_publishable_YfZn0IZdTs8L-EThj6lxOg_uFQCDxIp";


const supabaseClient =
    window.supabase.createClient(
        SUPABASE_URL,
        SUPABASE_PUBLISHABLE_KEY
    );


/* =========================================
   STATE
========================================= */

let currentUser = null;
let currentProfile = null;


/*
    Supabase Auth normally expects an email.

    We hide that implementation detail
    from the user and derive an internal
    identifier from the username.

    Users only see:
    username
    password
*/

function usernameToInternalEmail(username) {

    return (
        username.toLowerCase() +
        "@dpsbssmw.local"
    );
}


/* =========================================
   AUTH UI
========================================= */

function showSignup() {

    document.getElementById("loginForm")
        .style.display = "none";

    document.getElementById("signupForm")
        .style.display = "block";

    clearMessages();
}


function showLogin() {

    document.getElementById("signupForm")
        .style.display = "none";

    document.getElementById("loginForm")
        .style.display = "block";

    clearMessages();
}


function clearMessages() {

    document.getElementById("loginMessage")
        .className = "auth-message";

    document.getElementById("signupMessage")
        .className = "auth-message";
}


function showMessage(
    elementId,
    message,
    type
) {

    const element =
        document.getElementById(elementId);

    element.textContent = message;

    element.className =
        "auth-message " + type;
}


/* =========================================
   VALIDATE USERNAME
========================================= */

function validUsername(username) {

    return /^[a-z0-9_]{3,20}$/.test(
        username
    );
}


/* =========================================
   SIGN UP
========================================= */

async function signup() {

    clearMessages();


    const username =
        document.getElementById(
            "signupUsername"
        )
        .value
        .trim()
        .toLowerCase();


    const displayName =
        document.getElementById(
            "signupDisplayName"
        )
        .value
        .trim();


    const password =
        document.getElementById(
            "signupPassword"
        )
        .value;


    if (
        !username ||
        !displayName ||
        !password
    ) {

        showMessage(
            "signupMessage",
            "Please fill in every field.",
            "error"
        );

        return;
    }


    if (!validUsername(username)) {

        showMessage(
            "signupMessage",
            "Username must be 3-20 characters and contain only letters, numbers, or underscores.",
            "error"
        );

        return;
    }


    if (password.length < 6) {

        showMessage(
            "signupMessage",
            "Password must be at least 6 characters.",
            "error"
        );

        return;
    }


    const button =
        document.getElementById(
            "signupButton"
        );

    button.disabled = true;

    button.textContent =
        "Creating...";


    const internalEmail =
        usernameToInternalEmail(
            username
        );


    const {
        data,
        error
    } =
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


    button.disabled = false;

    button.textContent =
        "Create Account";


    if (error) {

        let message =
            error.message;


        if (
            message
                .toLowerCase()
                .includes("already registered")
        ) {

            message =
                "That username is already taken.";

        }


        showMessage(
            "signupMessage",
            message,
            "error"
        );

        return;
    }


    if (!data.session) {

        showMessage(
            "signupMessage",
            "Account created, but Supabase is still requiring confirmation. Turn off Confirm email in Authentication → Providers → Email.",
            "error"
        );

        return;
    }


    currentUser =
        data.user;


    await openApp();
}


/* =========================================
   LOGIN
========================================= */

async function login() {

    clearMessages();


    const username =
        document.getElementById(
            "loginUsername"
        )
        .value
        .trim()
        .toLowerCase();


    const password =
        document.getElementById(
            "loginPassword"
        )
        .value;


    if (!username || !password) {

        showMessage(
            "loginMessage",
            "Enter your username and password.",
            "error"
        );

        return;
    }


    if (!validUsername(username)) {

        showMessage(
            "loginMessage",
            "Enter a valid username.",
            "error"
        );

        return;
    }


    const button =
        document.getElementById(
            "loginButton"
        );

    button.disabled = true;

    button.textContent =
        "Logging in...";


    const internalEmail =
        usernameToInternalEmail(
            username
        );


    const {
        data,
        error
    } =
        await supabaseClient.auth
        .signInWithPassword({

            email: internalEmail,

            password: password

        });


    button.disabled = false;

    button.textContent =
        "Login";


    if (error) {

        showMessage(
            "loginMessage",
            "Incorrect username or password.",
            "error"
        );

        return;
    }


    currentUser =
        data.user;


    await openApp();
}


/* =========================================
   OPEN APP
========================================= */

async function openApp() {

    document.getElementById(
        "authPage"
    ).style.display = "none";


    document.getElementById(
        "appPage"
    ).style.display = "block";


    await loadProfile();

    await loadFeed();


    window.scrollTo({
        top: 0,
        behavior: "instant"
    });
}


/* =========================================
   LOAD PROFILE
========================================= */

async function loadProfile() {

    if (!currentUser)
        return;


    const {
        data,
        error
    } =
        await supabaseClient
        .from("profiles")
        .select("*")
        .eq("id", currentUser.id)
        .single();


    if (error) {

        console.error(
            "Profile error:",
            error
        );

        document.getElementById(
            "profileName"
        ).textContent =
            "Profile unavailable";

        return;
    }


    currentProfile =
        data;


    document.getElementById(
        "profileName"
    ).textContent =
        data.display_name;


    document.getElementById(
        "profileUsername"
    ).textContent =
        "@" + data.username;


    document.getElementById(
        "profileAvatar"
    ).textContent =
        getInitials(
            data.display_name
        );
}


/* =========================================
   CREATE POST
========================================= */

async function createPost() {

    if (!currentUser)
        return;


    const textarea =
        document.getElementById(
            "postContent"
        );


    const content =
        textarea.value.trim();


    if (!content) {

        return;
    }


    const button =
        document.getElementById(
            "postButton"
        );


    button.disabled = true;

    button.textContent =
        "Posting...";


    const {
        error
    } =
        await supabaseClient
        .from("posts")
        .insert({

            user_id:
                currentUser.id,

            content:
                content

        });


    button.disabled = false;

    button.textContent =
        "Post";


    if (error) {

        console.error(error);

        alert(
            "Could not create post:\n\n" +
            error.message
        );

        return;
    }


    textarea.value = "";


    await loadFeed();
}


/* =========================================
   LOAD FEED
========================================= */

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


    const {
        data: posts,
        error
    } =
        await supabaseClient
        .from("posts")
        .select(`
            id,
            user_id,
            content,
            created_at,
            profiles (
                username,
                display_name
            )
        `)
        .order(
            "created_at",
            {
                ascending: false
            }
        );


    if (error) {

        console.error(error);

        feed.innerHTML = `
            <div class="error-box">
                Could not load the feed.<br><br>
                ${escapeHTML(error.message)}
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
                No posts yet.<br><br>
                Be the first person to post.
            </div>
        `;

        return;
    }


    feed.innerHTML = "";


    for (
        const post of posts
    ) {

        const element =
            await buildPost(
                post
            );

        feed.appendChild(
            element
        );
    }
}


/* =========================================
   BUILD POST
========================================= */

async function buildPost(post) {

    const element =
        document.createElement(
            "article"
        );


    element.className =
        "post";


    const profile =
        post.profiles;


    const displayName =
        profile?.display_name ||
        "Unknown User";


    const username =
        profile?.username ||
        "unknown";


    const initials =
        getInitials(
            displayName
        );


    /* LIKES */

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


    if (likesError) {

        console.error(
            likesError
        );
    }


    const likeCount =
        likes?.length || 0;


    const userLiked =
        likes?.some(
            like =>
                like.user_id ===
                currentUser.id
        ) || false;


    /* COMMENTS */

    const {
        data: comments,
        error: commentsError
    } =
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


    if (commentsError) {

        console.error(
            commentsError
        );
    }


    let commentsHTML =
        "";


    for (
        const comment
        of comments || []
    ) {

        const commentName =
            comment.profiles
                ?.display_name ||
            "Unknown User";


        commentsHTML += `

            <div class="comment">

                <span class="comment-author">
                    ${escapeHTML(
                        commentName
                    )}
                </span>

                ${escapeHTML(
                    comment.content
                )}

            </div>

        `;
    }


    const deleteButton =
        post.user_id ===
        currentUser.id
        ? `
            <button
                class="action-button delete"
                onclick="deletePost(${post.id})"
            >
                Delete
            </button>
        `
        : "";


    element.innerHTML = `

        <div class="post-header">

            <div class="post-avatar">
                ${escapeHTML(
                    initials
                )}
            </div>


            <div>

                <div class="post-name">
                    ${escapeHTML(
                        displayName
                    )}
                </div>

                <div class="post-username">
                    @${escapeHTML(
                        username
                    )}
                </div>

                <div class="post-time">
                    ${escapeHTML(
                        formatDate(
                            post.created_at
                        )
                    )}
                </div>

            </div>

        </div>


        <div class="post-content">
            ${escapeHTML(
                post.content
            )}
        </div>


        <div class="post-actions">

            <button
                class="action-button ${
                    userLiked
                    ? "liked"
                    : ""
                }"
                onclick="toggleLike(${post.id})"
            >
                ❤️ ${likeCount}
            </button>


            <button
                class="action-button"
                onclick="focusComment(${post.id})"
            >
                💬 ${comments?.length || 0}
            </button>


            ${deleteButton}

        </div>


        <div class="comments">

            ${commentsHTML}


            <div class="comment-input-row">

                <input
                    id="comment-${post.id}"
                    class="comment-input"
                    type="text"
                    maxlength="500"
                    placeholder="Write a comment..."
                >


                <button
                    class="comment-send"
                    onclick="addComment(${post.id})"
                >
                    Send
                </button>

            </div>

        </div>

    `;


    return element;
}


/* =========================================
   LIKE
========================================= */

async function toggleLike(postId) {

    if (!currentUser)
        return;


    const {
        data: existing,
        error: checkError
    } =
        await supabaseClient
        .from("likes")
        .select("*")
        .eq(
            "post_id",
            postId
        )
        .eq(
            "user_id",
            currentUser.id
        )
        .maybeSingle();


    if (checkError) {

        console.error(
            checkError
        );

        return;
    }


    if (existing) {

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

            console.error(
                error
            );

            return;
        }
    }


    await loadFeed();
}


/* =========================================
   COMMENT
========================================= */

async function addComment(postId) {

    if (!currentUser)
        return;


    const input =
        document.getElementById(
            "comment-" + postId
        );


    const content =
        input.value.trim();


    if (!content)
        return;


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

        alert(
            "Could not add comment:\n\n" +
            error.message
        );

        return;
    }


    input.value = "";


    await loadFeed();
}


/* =========================================
   DELETE POST
========================================= */

async function deletePost(postId) {

    const confirmed =
        confirm(
            "Delete this post?"
        );


    if (!confirmed)
        return;


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

        alert(
            "Could not delete post:\n\n" +
            error.message
        );

        return;
    }


    await loadFeed();
}


/* =========================================
   COMMENT FOCUS
========================================= */

function focusComment(postId) {

    const input =
        document.getElementById(
            "comment-" + postId
        );


    if (!input)
        return;


    input.focus();


    input.scrollIntoView({
        behavior: "smooth",
        block: "center"
    });
}


/* =========================================
   REFRESH
========================================= */

async function refreshFeed() {

    await loadProfile();

    await loadFeed();

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


/* =========================================
   LOGOUT
========================================= */

async function logout() {

    await supabaseClient
        .auth
        .signOut();


    currentUser = null;

    currentProfile = null;


    document.getElementById(
        "appPage"
    ).style.display = "none";


    document.getElementById(
        "authPage"
    ).style.display = "flex";


    document.getElementById(
        "loginUsername"
    ).value = "";


    document.getElementById(
        "loginPassword"
    ).value = "";


    showLogin();
}


/* =========================================
   HELPERS
========================================= */

function getInitials(name) {

    if (!name)
        return "?";


    const words =
        name
            .trim()
            .split(/\s+/);


    if (
        words.length === 1
    ) {

        return words[0]
            .substring(0,2)
            .toUpperCase();
    }


    return (
        words[0][0] +
        words[1][0]
    ).toUpperCase();
}


function formatDate(dateString) {

    const date =
        new Date(
            dateString
        );


    return date.toLocaleString(
        undefined,
        {
            dateStyle:
                "medium",

            timeStyle:
                "short"
        }
    );
}


/*
    Never insert user-generated
    text directly into HTML.
*/

function escapeHTML(value) {

    const div =
        document.createElement(
            "div"
        );


    div.textContent =
        value ?? "";


    return div.innerHTML;
}


/* =========================================
   SESSION
========================================= */

async function checkSession() {

    const {
        data,
        error
    } =
        await supabaseClient
        .auth
        .getSession();


    if (error) {

        console.error(
            error
        );

        return;
    }


    if (data.session) {

        currentUser =
            data.session.user;


        await openApp();

    } else {

        document.getElementById(
            "authPage"
        ).style.display =
            "flex";


        document.getElementById(
            "appPage"
        ).style.display =
            "none";
    }
}


/* =========================================
   AUTH LISTENER
========================================= */

supabaseClient
    .auth
    .onAuthStateChange(
        (event, session) => {

            if (session) {

                currentUser =
                    session.user;

            } else {

                currentUser =
                    null;
            }
        }
    );


/* =========================================
   START
========================================= */

checkSession();

</script>

</body>
</html>
