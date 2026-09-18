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
}

body {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
    background: #f3f4f6;
    color: #111827;
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
   LOGIN
========================= */

#authPage {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
    background:
        linear-gradient(135deg, #111827, #1f2937);
}

.authBox {
    width: 100%;
    max-width: 420px;
    background: white;
    padding: 35px;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.25);
}

.logo {
    text-align: center;
    margin-bottom: 25px;
}

.logo h1 {
    margin: 0;
    font-size: 30px;
}

.logo p {
    margin: 8px 0 0;
    color: #6b7280;
    font-size: 14px;
}

.authBox input {
    width: 100%;
    padding: 13px;
    margin-bottom: 12px;
    border: 1px solid #d1d5db;
    border-radius: 10px;
    outline: none;
}

.authBox input:focus {
    border-color: #111827;
}

.primary {
    width: 100%;
    padding: 13px;
    border: none;
    border-radius: 10px;
    background: #111827;
    color: white;
    font-weight: bold;
}

.switch {
    text-align: center;
    margin-top: 18px;
    color: #6b7280;
    font-size: 14px;
}

.switch span {
    color: #111827;
    font-weight: bold;
    cursor: pointer;
}

#authMessage {
    margin-top: 15px;
    text-align: center;
    font-size: 14px;
}


/* =========================
   APP
========================= */

#appPage {
    min-height: 100vh;
}

.navbar {
    height: 65px;
    background: white;
    border-bottom: 1px solid #e5e7eb;

    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 0 20px;

    position: sticky;
    top: 0;
    z-index: 10;
}

.navLogo {
    font-weight: 900;
    font-size: 20px;
}

.logout {
    border: none;
    background: #f3f4f6;
    padding: 8px 13px;
    border-radius: 8px;
}

.container {
    width: 100%;
    max-width: 700px;
    margin: auto;
    padding: 20px 15px 50px;
}


/* =========================
   PROFILE
========================= */

.profileCard {
    background: white;
    border-radius: 15px;
    padding: 20px;
    margin-bottom: 15px;
    border: 1px solid #e5e7eb;
}

.profileName {
    font-size: 22px;
    font-weight: bold;
}

.profileUsername {
    color: #6b7280;
    margin-top: 4px;
}


/* =========================
   CREATE POST
========================= */

.createPost {
    background: white;
    padding: 18px;
    border-radius: 15px;
    border: 1px solid #e5e7eb;
    margin-bottom: 15px;
}

.createPost textarea {
    width: 100%;
    min-height: 90px;
    resize: vertical;

    padding: 12px;

    border: 1px solid #d1d5db;
    border-radius: 10px;

    outline: none;
}

.postButton {
    margin-top: 10px;
    padding: 10px 18px;

    background: #111827;
    color: white;

    border: none;
    border-radius: 9px;

    font-weight: bold;
}


/* =========================
   POSTS
========================= */

.post {
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 15px;
    margin-bottom: 15px;
    overflow: hidden;
}

.postHeader {
    padding: 15px 15px 5px;
}

.postAuthor {
    font-weight: bold;
}

.postTime {
    font-size: 12px;
    color: #9ca3af;
    margin-top: 3px;
}

.postContent {
    padding: 10px 15px 15px;
    white-space: pre-wrap;
    word-break: break-word;
}

.postActions {
    display: flex;
    border-top: 1px solid #f0f0f0;
}

.actionButton {
    flex: 1;
    border: none;
    background: white;
    padding: 12px;
}

.actionButton:hover {
    background: #f9fafb;
}

.comments {
    padding: 0 15px 15px;
}

.comment {
    background: #f3f4f6;
    border-radius: 10px;
    padding: 8px 10px;
    margin-top: 8px;
    font-size: 14px;
}

.comment strong {
    display: block;
    margin-bottom: 3px;
}

.commentBox {
    display: flex;
    gap: 7px;
    margin-top: 10px;
}

.commentBox input {
    flex: 1;
    border: 1px solid #d1d5db;
    border-radius: 8px;
    padding: 8px;
}

.commentBox button {
    border: none;
    border-radius: 8px;
    padding: 8px 12px;
    background: #111827;
    color: white;
}


/* =========================
   MOBILE
========================= */

@media (max-width: 600px) {

    .navbar {
        padding: 0 12px;
    }

    .navLogo {
        font-size: 16px;
    }

    .authBox {
        padding: 25px;
    }

}

</style>
</head>


<body>


<!-- =========================
     LOGIN / SIGNUP
========================= -->

<section id="authPage">

    <div class="authBox">

        <div class="logo">
            <h1>DPSB SSMW</h1>
            <p>Private Social Media Website</p>
        </div>


        <!-- LOGIN -->

        <div id="loginForm">

            <input
                id="loginEmail"
                type="email"
                placeholder="Email"
            >

            <input
                id="loginPassword"
                type="password"
                placeholder="Password"
            >

            <button
                class="primary"
                onclick="login()"
            >
                Login
            </button>

            <div class="switch">
                Don't have an account?
                <span onclick="showSignup()">Create one</span>
            </div>

        </div>


        <!-- SIGNUP -->

        <div id="signupForm" class="hidden">

            <input
                id="signupUsername"
                type="text"
                placeholder="Username"
            >

            <input
                id="signupName"
                type="text"
                placeholder="Display name"
            >

            <input
                id="signupEmail"
                type="email"
                placeholder="Email"
            >

            <input
                id="signupPassword"
                type="password"
                placeholder="Password"
            >

            <button
                class="primary"
                onclick="signup()"
            >
                Create Account
            </button>

            <div class="switch">
                Already have an account?
                <span onclick="showLogin()">Login</span>
            </div>

        </div>


        <div id="authMessage"></div>

    </div>

</section>



<!-- =========================
     MAIN APP
========================= -->

<section id="appPage" class="hidden">

    <nav class="navbar">

        <div class="navLogo">
            DPSB SSMW
        </div>

        <button
            class="logout"
            onclick="logout()"
        >
            Logout
        </button>

    </nav>


    <main class="container">


        <!-- PROFILE -->

        <div
            id="profileCard"
            class="profileCard"
        >
            Loading profile...
        </div>


        <!-- CREATE POST -->

        <div class="createPost">

            <textarea
                id="postContent"
                maxlength="1000"
                placeholder="What's happening?"
            ></textarea>

            <button
                class="postButton"
                onclick="createPost()"
            >
                Post
            </button>

        </div>


        <!-- FEED -->

        <div id="feed">
            Loading posts...
        </div>


    </main>

</section>



<script>

/* ==================================================
   SUPABASE CONFIGURATION
================================================== */

/*
   PUT YOUR SUPABASE INFORMATION HERE.

   Supabase Dashboard:
   Project Settings → API
*/

const SUPABASE_URL = "YOUR_SUPABASE_PROJECT_URL";

const SUPABASE_PUBLISHABLE_KEY =
    "YOUR_SUPABASE_PUBLISHABLE_KEY";


const supabaseClient =
    window.supabase.createClient(
        SUPABASE_URL,
        SUPABASE_PUBLISHABLE_KEY
    );


/* ==================================================
   GLOBAL VARIABLES
================================================== */

let currentUser = null;
let currentProfile = null;


/* ==================================================
   AUTH UI
================================================== */

function showSignup() {

    document
        .getElementById("loginForm")
        .classList.add("hidden");

    document
        .getElementById("signupForm")
        .classList.remove("hidden");

    clearMessage();
}


function showLogin() {

    document
        .getElementById("signupForm")
        .classList.add("hidden");

    document
        .getElementById("loginForm")
        .classList.remove("hidden");

    clearMessage();
}


function showMessage(message, error = false) {

    const box =
        document.getElementById("authMessage");

    box.textContent = message;

    box.style.color =
        error ? "#dc2626" : "#16a34a";
}


function clearMessage() {

    document
        .getElementById("authMessage")
        .textContent = "";

}


/* ==================================================
   SIGN UP
================================================== */

async function signup() {

    const username =
        document
        .getElementById("signupUsername")
        .value
        .trim()
        .toLowerCase();

    const displayName =
        document
        .getElementById("signupName")
        .value
        .trim();

    const email =
        document
        .getElementById("signupEmail")
        .value
        .trim();

    const password =
        document
        .getElementById("signupPassword")
        .value;


    if (!username || !displayName || !email || !password) {

        showMessage(
            "Please fill in everything.",
            true
        );

        return;
    }


    if (username.length < 3) {

        showMessage(
            "Username must be at least 3 characters.",
            true
        );

        return;
    }


    if (password.length < 6) {

        showMessage(
            "Password must be at least 6 characters.",
            true
        );

        return;
    }


    showMessage("Creating account...");


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

        showMessage(
            error.message,
            true
        );

        return;
    }


    /*
       Depending on your Supabase Auth settings,
       the user may need to confirm their email.
    */

    if (!data.session) {

        showMessage(
            "Account created. Check your email to confirm it."
        );

    } else {

        showMessage(
            "Account created!"
        );

    }

}


/* ==================================================
   LOGIN
================================================== */

async function login() {

    const email =
        document
        .getElementById("loginEmail")
        .value
        .trim();

    const password =
        document
        .getElementById("loginPassword")
        .value;


    if (!email || !password) {

        showMessage(
            "Enter your email and password.",
            true
        );

        return;
    }


    showMessage("Logging in...");


    const { data, error } =
        await supabaseClient.auth.signInWithPassword({

            email: email,

            password: password

        });


    if (error) {

        showMessage(
            error.message,
            true
        );

        return;
    }


    currentUser = data.user;

    await openApp();

}


/* ==================================================
   LOGOUT
================================================== */

async function logout() {

    await supabaseClient.auth.signOut();

    currentUser = null;
    currentProfile = null;

    document
        .getElementById("appPage")
        .classList.add("hidden");

    document
        .getElementById("authPage")
        .classList.remove("hidden");

}


/* ==================================================
   OPEN APP
================================================== */

async function openApp() {

    document
        .getElementById("authPage")
        .classList.add("hidden");

    document
        .getElementById("appPage")
        .classList.remove("hidden");


    await loadProfile();

    await loadFeed();

}


/* ==================================================
   LOAD PROFILE
================================================== */

async function loadProfile() {

    const { data, error } =
        await supabaseClient
        .from("profiles")
        .select("*")
        .eq("id", currentUser.id)
        .single();


    if (error) {

        console.error(error);

        return;
    }


    currentProfile = data;


    document
        .getElementById("profileCard")
        .innerHTML = `

            <div class="profileName">
                ${escapeHTML(data.display_name)}
            </div>

            <div class="profileUsername">
                @${escapeHTML(data.username)}
            </div>

        `;

}


/* ==================================================
   CREATE POST
================================================== */

async function createPost() {

    const textarea =
        document.getElementById("postContent");

    const content =
        textarea.value.trim();


    if (!content) return;


    const { error } =
        await supabaseClient
        .from("posts")
        .insert({

            user_id: currentUser.id,

            content: content

        });


    if (error) {

        alert(error.message);

        return;
    }


    textarea.value = "";

    await loadFeed();

}


/* ==================================================
   LOAD FEED
================================================== */

async function loadFeed() {

    const feed =
        document.getElementById("feed");

    feed.innerHTML =
        "Loading posts...";


    const { data, error } =
        await supabaseClient
        .from("posts")
        .select(`
            id,
            content,
            created_at,
            user_id,
            profiles (
                username,
                display_name
            )
        `)
        .order("created_at", {
            ascending: false
        });


    if (error) {

        console.error(error);

        feed.innerHTML =
            "Could not load posts.";

        return;
    }


    if (!data || data.length === 0) {

        feed.innerHTML = `
            <div class="post">
                <div class="postContent">
                    No posts yet. Be the first.
                </div>
            </div>
        `;

        return;
    }


    feed.innerHTML = "";


    for (const post of data) {

        const postElement =
            await createPostElement(post);

        feed.appendChild(postElement);

    }

}


/* ==================================================
   CREATE POST ELEMENT
================================================== */

async function createPostElement(post) {

    const article =
        document.createElement("article");

    article.className = "post";


    const profile =
        post.profiles;


    const authorName =
        profile
        ? profile.display_name
        : "Unknown User";


    const username =
        profile
        ? profile.username
        : "unknown";


    const time =
        new Date(post.created_at)
        .toLocaleString();


    /* Get likes */

    const { data: likes } =
        await supabaseClient
        .from("likes")
        .select("user_id")
        .eq("post_id", post.id);


    const likeCount =
        likes ? likes.length : 0;


    const userLiked =
        likes
        ? likes.some(
            like => like.user_id === currentUser.id
          )
        : false;


    /* Get comments */

    const { data: comments } =
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
        .eq("post_id", post.id)
        .order("created_at", {
            ascending: true
        });


    let commentsHTML = "";


    if (comments) {

        commentsHTML =
            comments.map(comment => {

                const name =
                    comment.profiles
                    ? comment.profiles.display_name
                    : "Unknown User";


                return `

                    <div class="comment">

                        <strong>
                            ${escapeHTML(name)}
                        </strong>

                        ${escapeHTML(comment.content)}

                    </div>

                `;

            }).join("");

    }


    article.innerHTML = `

        <div class="postHeader">

            <div class="postAuthor">
                ${escapeHTML(authorName)}
            </div>

            <div class="postTime">
                @${escapeHTML(username)}
                ·
                ${escapeHTML(time)}
            </div>

        </div>


        <div class="postContent">
            ${escapeHTML(post.content)}
        </div>


        <div class="postActions">

            <button
                class="actionButton"
                onclick="toggleLike(${post.id})"
            >

                ${userLiked ? "❤️" : "♡"}
                ${likeCount}

            </button>

        </div>


        <div class="comments">

            ${commentsHTML}


            <div class="commentBox">

                <input
                    id="comment-${post.id}"
                    placeholder="Write a comment..."
                    maxlength="500"
                >

                <button
                    onclick="addComment(${post.id})"
                >
                    Send
                </button>

            </div>

        </div>

    `;


    return article;

}


/* ==================================================
   LIKE / UNLIKE
================================================== */

async function toggleLike(postId) {

    const { data: existing } =
        await supabaseClient
        .from("likes")
        .select("*")
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


/* ==================================================
   ADD COMMENT
================================================== */

async function addComment(postId) {

    const input =
        document.getElementById(
            `comment-${postId}`
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


    input.value = "";

    await loadFeed();

}


/* ==================================================
   SECURITY HELPER
================================================== */

function escapeHTML(value) {

    const div =
        document.createElement("div");

    div.textContent =
        value ?? "";

    return div.innerHTML;

}


/* ==================================================
   CHECK EXISTING SESSION
================================================== */

async function checkSession() {

    const {
        data: {
            session
        }
    } = await supabaseClient.auth.getSession();


    if (session) {

        currentUser =
            session.user;

        await openApp();

    }

}


/* ==================================================
   AUTH STATE
================================================== */

supabaseClient.auth
    .onAuthStateChange(
        async (event, session) => {

            if (session) {

                currentUser =
                    session.user;

            }

        }
    );


/* START */

checkSession();

</script>

</body>
</html>
