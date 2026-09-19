# dpsbssmw
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>DPSB SSMW</title>

    <!-- Supabase -->
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, sans-serif;
            background: #f2f4f7;
            color: #222;
        }

        button {
            cursor: pointer;
        }

        /* =========================
           AUTH PAGE
        ========================= */

        #authPage {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            background: linear-gradient(
                135deg,
                #111827,
                #2563eb
            );
        }

        .auth-box {
            width: 100%;
            max-width: 430px;
            background: white;
            border-radius: 20px;
            padding: 35px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.25);
        }

        .logo {
            text-align: center;
            margin-bottom: 25px;
        }

        .logo h1 {
            font-size: 30px;
            color: #2563eb;
        }

        .logo p {
            color: #666;
            margin-top: 8px;
            font-size: 14px;
        }

        .auth-box input {
            width: 100%;
            padding: 13px;
            margin-bottom: 12px;
            border: 1px solid #d1d5db;
            border-radius: 10px;
            font-size: 15px;
            outline: none;
        }

        .auth-box input:focus {
            border-color: #2563eb;
        }

        .primary-btn {
            width: 100%;
            border: none;
            padding: 13px;
            border-radius: 10px;
            background: #2563eb;
            color: white;
            font-size: 16px;
            font-weight: bold;
            margin-top: 5px;
        }

        .primary-btn:hover {
            background: #1d4ed8;
        }

        .secondary-btn {
            width: 100%;
            border: none;
            background: transparent;
            color: #2563eb;
            margin-top: 15px;
            font-size: 14px;
        }

        .message {
            margin: 12px 0;
            padding: 10px;
            border-radius: 8px;
            font-size: 14px;
            display: none;
        }

        .error {
            background: #fee2e2;
            color: #991b1b;
        }

        .success {
            background: #dcfce7;
            color: #166534;
        }

        /* =========================
           APP
        ========================= */

        #appPage {
            display: none;
            min-height: 100vh;
        }

        .navbar {
            position: sticky;
            top: 0;
            z-index: 100;
            background: white;
            border-bottom: 1px solid #ddd;
            height: 65px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 25px;
        }

        .nav-logo {
            color: #2563eb;
            font-size: 22px;
            font-weight: bold;
        }

        .nav-buttons {
            display: flex;
            gap: 10px;
        }

        .nav-btn {
            border: none;
            padding: 9px 14px;
            border-radius: 8px;
            background: #eef2ff;
            color: #1d4ed8;
            font-weight: bold;
        }

        .logout-btn {
            background: #fee2e2;
            color: #991b1b;
        }

        .main-container {
            width: 100%;
            max-width: 850px;
            margin: auto;
            padding: 25px 15px;
        }

        /* =========================
           PROFILE
        ========================= */

        .profile-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .profile-header {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: #2563eb;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            font-weight: bold;
        }

        .profile-info h2 {
            font-size: 20px;
        }

        .profile-info p {
            color: #777;
            font-size: 14px;
            margin-top: 4px;
        }

        /* =========================
           CREATE POST
        ========================= */

        .create-post {
            background: white;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .create-post textarea {
            width: 100%;
            min-height: 100px;
            resize: vertical;
            border: 1px solid #ddd;
            border-radius: 10px;
            padding: 12px;
            font-family: inherit;
            font-size: 15px;
            outline: none;
        }

        .create-post textarea:focus {
            border-color: #2563eb;
        }

        .post-btn {
            margin-top: 10px;
            background: #2563eb;
            color: white;
            border: none;
            padding: 11px 18px;
            border-radius: 9px;
            font-weight: bold;
        }

        /* =========================
           POSTS
        ========================= */

        .post {
            background: white;
            border-radius: 15px;
            margin-bottom: 18px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .post-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 15px;
        }

        .small-avatar {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            background: #2563eb;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        .post-user-name {
            font-weight: bold;
        }

        .post-username {
            color: #777;
            font-size: 13px;
        }

        .post-time {
            color: #999;
            font-size: 12px;
            margin-top: 3px;
        }

        .post-content {
            font-size: 16px;
            line-height: 1.5;
            white-space: pre-wrap;
            word-wrap: break-word;
            margin-bottom: 15px;
        }

        .post-actions {
            display: flex;
            gap: 10px;
            border-top: 1px solid #eee;
            padding-top: 12px;
        }

        .action-btn {
            border: none;
            background: #f3f4f6;
            padding: 8px 12px;
            border-radius: 8px;
            font-size: 14px;
        }

        .action-btn:hover {
            background: #e5e7eb;
        }

        .liked {
            background: #dbeafe;
            color: #1d4ed8;
        }

        /* =========================
           COMMENTS
        ========================= */

        .comments {
            margin-top: 15px;
            border-top: 1px solid #eee;
            padding-top: 12px;
        }

        .comment {
            background: #f7f7f7;
            padding: 9px;
            border-radius: 8px;
            margin-bottom: 7px;
            font-size: 14px;
        }

        .comment strong {
            margin-right: 5px;
        }

        .comment-box {
            display: flex;
            gap: 8px;
            margin-top: 10px;
        }

        .comment-box input {
            flex: 1;
            padding: 9px;
            border: 1px solid #ddd;
            border-radius: 8px;
        }

        .comment-box button {
            border: none;
            background: #2563eb;
            color: white;
            padding: 9px 13px;
            border-radius: 8px;
        }

        .loading {
            text-align: center;
            color: #777;
            padding: 30px;
        }

        .empty {
            background: white;
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            color: #777;
        }

        /* =========================
           MOBILE
        ========================= */

        @media (max-width: 600px) {

            .navbar {
                padding: 0 12px;
            }

            .nav-logo {
                font-size: 17px;
            }

            .nav-btn {
                padding: 7px 9px;
                font-size: 12px;
            }

            .auth-box {
                padding: 25px;
            }

            .main-container {
                padding: 15px 10px;
            }

            .post {
                padding: 15px;
            }
        }
    </style>
</head>

<body>

<!-- =========================================
     LOGIN / SIGNUP
========================================= -->

<div id="authPage">

    <div class="auth-box">

        <div class="logo">
            <h1>DPSB SSMW</h1>
            <p>
                Delhi Public School Budgam<br>
                Secret Social Media Website
            </p>
        </div>

        <!-- LOGIN -->

        <div id="loginForm">

            <input
                type="email"
                id="loginEmail"
                placeholder="Email"
            >

            <input
                type="password"
                id="loginPassword"
                placeholder="Password"
            >

            <div id="loginMessage" class="message"></div>

            <button
                class="primary-btn"
                onclick="login()"
            >
                Login
            </button>

            <button
                class="secondary-btn"
                onclick="showSignup()"
            >
                Don't have an account? Sign up
            </button>

        </div>


        <!-- SIGNUP -->

        <div id="signupForm" style="display:none;">

            <input
                type="text"
                id="signupUsername"
                placeholder="Username"
            >

            <input
                type="text"
                id="signupDisplayName"
                placeholder="Display name"
            >

            <input
                type="email"
                id="signupEmail"
                placeholder="Email"
            >

            <input
                type="password"
                id="signupPassword"
                placeholder="Password"
            >

            <div id="signupMessage" class="message"></div>

            <button
                class="primary-btn"
                onclick="signup()"
            >
                Create Account
            </button>

            <button
                class="secondary-btn"
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

        <div class="nav-buttons">

            <button
                class="nav-btn"
                onclick="scrollToTop()"
            >
                Home
            </button>

            <button
                class="nav-btn logout-btn"
                onclick="logout()"
            >
                Logout
            </button>

        </div>

    </nav>


    <main class="main-container">

        <!-- PROFILE -->

        <div class="profile-card">

            <div class="profile-header">

                <div
                    class="avatar"
                    id="profileAvatar"
                >
                    ?
                </div>

                <div class="profile-info">

                    <h2 id="profileName">
                        Loading...
                    </h2>

                    <p id="profileUsername">
                        @loading
                    </p>

                </div>

            </div>

        </div>


        <!-- CREATE POST -->

        <div class="create-post">

            <textarea
                id="postContent"
                maxlength="1000"
                placeholder="What's happening?"
            ></textarea>

            <button
                class="post-btn"
                onclick="createPost()"
            >
                Post
            </button>

        </div>


        <!-- FEED -->

        <div id="feed">

            <div class="loading">
                Loading posts...
            </div>

        </div>

    </main>

</div>


<script>

/* =========================================
   SUPABASE CONFIGURATION
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
   GLOBAL VARIABLES
========================================= */

let currentUser = null;
let currentProfile = null;


/* =========================================
   AUTH PAGE
========================================= */

function showSignup() {

    document.getElementById("loginForm").style.display =
        "none";

    document.getElementById("signupForm").style.display =
        "block";

    clearMessages();
}


function showLogin() {

    document.getElementById("signupForm").style.display =
        "none";

    document.getElementById("loginForm").style.display =
        "block";

    clearMessages();
}


function clearMessages() {

    document.getElementById("loginMessage").style.display =
        "none";

    document.getElementById("signupMessage").style.display =
        "none";
}


function showMessage(elementId, message, type) {

    const element =
        document.getElementById(elementId);

    element.textContent = message;

    element.className =
        "message " + type;

    element.style.display = "block";
}


/* =========================================
   SIGN UP
========================================= */

async function signup() {

    clearMessages();

    const username =
        document.getElementById("signupUsername")
        .value
        .trim();

    const displayName =
        document.getElementById("signupDisplayName")
        .value
        .trim();

    const email =
        document.getElementById("signupEmail")
        .value
        .trim();

    const password =
        document.getElementById("signupPassword")
        .value;


    if (!username || !displayName || !email || !password) {

        showMessage(
            "signupMessage",
            "Please fill in every field.",
            "error"
        );

        return;
    }


    if (username.length < 3) {

        showMessage(
            "signupMessage",
            "Username must be at least 3 characters.",
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


    showMessage(
        "signupMessage",
        "Creating your account...",
        "success"
    );


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
            "signupMessage",
            error.message,
            "error"
        );

        return;
    }


    /*
       If email confirmation is enabled,
       Supabase will require the user
       to confirm their email.
    */

    if (!data.session) {

        showMessage(
            "signupMessage",
            "Account created! Check your email to confirm your account, then log in.",
            "success"
        );

        return;
    }


    currentUser = data.user;

    await openApp();
}


/* =========================================
   LOGIN
========================================= */

async function login() {

    clearMessages();

    const email =
        document.getElementById("loginEmail")
        .value
        .trim();

    const password =
        document.getElementById("loginPassword")
        .value;


    if (!email || !password) {

        showMessage(
            "loginMessage",
            "Enter your email and password.",
            "error"
        );

        return;
    }


    showMessage(
        "loginMessage",
        "Logging in...",
        "success"
    );


    const { data, error } =
        await supabaseClient.auth
        .signInWithPassword({

            email: email,

            password: password

        });


    if (error) {

        showMessage(
            "loginMessage",
            error.message,
            "error"
        );

        return;
    }


    currentUser = data.user;

    await openApp();
}


/* =========================================
   LOGOUT
========================================= */

async function logout() {

    await supabaseClient.auth.signOut();

    currentUser = null;
    currentProfile = null;

    document.getElementById("appPage").style.display =
        "none";

    document.getElementById("authPage").style.display =
        "flex";

    showLogin();
}


/* =========================================
   OPEN APP
========================================= */

async function openApp() {

    document.getElementById("authPage").style.display =
        "none";

    document.getElementById("appPage").style.display =
        "block";

    await loadProfile();

    await loadFeed();

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


/* =========================================
   LOAD PROFILE
========================================= */

async function loadProfile() {

    if (!currentUser) return;


    const { data, error } =
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

        return;
    }


    currentProfile = data;


    document.getElementById("profileName")
        .textContent =
        data.display_name;


    document.getElementById("profileUsername")
        .textContent =
        "@" + data.username;


    document.getElementById("profileAvatar")
        .textContent =
        getInitials(data.display_name);
}


/* =========================================
   CREATE POST
========================================= */

async function createPost() {

    if (!currentUser) return;


    const textarea =
        document.getElementById("postContent");

    const content =
        textarea.value.trim();


    if (!content) {

        alert("Write something first.");

        return;
    }


    if (content.length > 1000) {

        alert(
            "Your post is too long. Maximum is 1000 characters."
        );

        return;
    }


    const button =
        document.querySelector(".post-btn");

    button.disabled = true;

    button.textContent = "Posting...";


    const { error } =
        await supabaseClient
        .from("posts")
        .insert({

            user_id: currentUser.id,

            content: content

        });


    button.disabled = false;

    button.textContent = "Post";


    if (error) {

        console.error(error);

        alert(
            "Could not create post: " +
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
        document.getElementById("feed");


    feed.innerHTML =
        '<div class="loading">Loading posts...</div>';


    const { data: posts, error } =
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
            { ascending: false }
        );


    if (error) {

        console.error(error);

        feed.innerHTML = `
            <div class="empty">
                Could not load posts.<br><br>
                ${escapeHTML(error.message)}
            </div>
        `;

        return;
    }


    if (!posts || posts.length === 0) {

        feed.innerHTML = `
            <div class="empty">
                No posts yet.<br>
                Be the first person to post!
            </div>
        `;

        return;
    }


    feed.innerHTML = "";


    for (const post of posts) {

        const postElement =
            await createPostElement(post);

        feed.appendChild(postElement);
    }
}


/* =========================================
   CREATE POST ELEMENT
========================================= */

async function createPostElement(post) {

    const div =
        document.createElement("div");

    div.className = "post";


    const profile =
        post.profiles;


    const displayName =
        profile?.display_name ||
        "Unknown User";


    const username =
        profile?.username ||
        "unknown";


    const initials =
        getInitials(displayName);


    const time =
        formatDate(post.created_at);


    /* GET LIKES */

    const { data: likes } =
        await supabaseClient
        .from("likes")
        .select("user_id")
        .eq("post_id", post.id);


    const likeCount =
        likes ? likes.length : 0;


    const userLiked =
        likes &&
        likes.some(
            like =>
                like.user_id === currentUser.id
        );


    /* GET COMMENTS */

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
        .order(
            "created_at",
            { ascending: true }
        );


    const commentHTML =
        comments && comments.length
            ? comments.map(comment => {

                const commenter =
                    comment.profiles?.display_name ||
                    "Unknown User";

                const commentUsername =
                    comment.profiles?.username ||
                    "unknown";

                return `
                    <div class="comment">
                        <strong>
                            ${escapeHTML(commenter)}
                        </strong>

                        <span>
                            @${escapeHTML(commentUsername)}
                        </span>

                        <br>

                        ${escapeHTML(comment.content)}
                    </div>
                `;

            }).join("")
            : "";


    div.innerHTML = `

        <div class="post-header">

            <div class="small-avatar">
                ${escapeHTML(initials)}
            </div>

            <div>

                <div class="post-user-name">
                    ${escapeHTML(displayName)}
                </div>

                <div class="post-username">
                    @${escapeHTML(username)}
                </div>

                <div class="post-time">
                    ${escapeHTML(time)}
                </div>

            </div>

        </div>


        <div class="post-content">
            ${escapeHTML(post.content)}
        </div>


        <div class="post-actions">

            <button
                class="action-btn ${userLiked ? "liked" : ""}"
                onclick="toggleLike(${post.id})"
            >
                ❤️ ${likeCount}
            </button>

            <button
                class="action-btn"
                onclick="focusComment(${post.id})"
            >
                💬 ${comments ? comments.length : 0}
            </button>

            ${
                post.user_id === currentUser.id
                ? `
                    <button
                        class="action-btn"
                        onclick="deletePost(${post.id})"
                    >
                        🗑️ Delete
                    </button>
                `
                : ""
            }

        </div>


        <div
            class="comments"
            id="comments-${post.id}"
        >

            ${commentHTML}

            <div class="comment-box">

                <input
                    id="comment-input-${post.id}"
                    type="text"
                    maxlength="500"
                    placeholder="Write a comment..."
                >

                <button
                    onclick="addComment(${post.id})"
                >
                    Send
                </button>

            </div>

        </div>

    `;


    return div;
}


/* =========================================
   LIKE / UNLIKE
========================================= */

async function toggleLike(postId) {

    if (!currentUser) return;


    const { data: existingLike } =
        await supabaseClient
        .from("likes")
        .select("*")
        .eq("post_id", postId)
        .eq("user_id", currentUser.id)
        .maybeSingle();


    if (existingLike) {

        const { error } =
            await supabaseClient
            .from("likes")
            .delete()
            .eq("post_id", postId)
            .eq("user_id", currentUser.id);


        if (error) {

            console.error(error);

            alert(
                "Could not remove like: " +
                error.message
            );

            return;
        }

    } else {

        const { error } =
            await supabaseClient
            .from("likes")
            .insert({

                post_id: postId,

                user_id: currentUser.id

            });


        if (error) {

            console.error(error);

            alert(
                "Could not like post: " +
                error.message
            );

            return;
        }
    }


    await loadFeed();
}


/* =========================================
   ADD COMMENT
========================================= */

async function addComment(postId) {

    if (!currentUser) return;


    const input =
        document.getElementById(
            "comment-input-" + postId
        );


    const content =
        input.value.trim();


    if (!content) return;


    if (content.length > 500) {

        alert(
            "Comment is too long. Maximum is 500 characters."
        );

        return;
    }


    const { error } =
        await supabaseClient
        .from("comments")
        .insert({

            post_id: postId,

            user_id: currentUser.id,

            content: content

        });


    if (error) {

        console.error(error);

        alert(
            "Could not add comment: " +
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

    if (!currentUser) return;


    const confirmed =
        confirm(
            "Delete this post?"
        );


    if (!confirmed) return;


    const { error } =
        await supabaseClient
        .from("posts")
        .delete()
        .eq("id", postId)
        .eq("user_id", currentUser.id);


    if (error) {

        console.error(error);

        alert(
            "Could not delete post: " +
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
            "comment-input-" + postId
        );


    if (input) {

        input.focus();

        input.scrollIntoView({
            behavior: "smooth",
            block: "center"
        });
    }
}


/* =========================================
   DATE FORMAT
========================================= */

function formatDate(dateString) {

    const date =
        new Date(dateString);


    return date.toLocaleString(
        undefined,
        {
            dateStyle: "medium",
            timeStyle: "short"
        }
    );
}


/* =========================================
   INITIALS
========================================= */

function getInitials(name) {

    if (!name) return "?";


    const words =
        name.trim().split(/\s+/);


    if (words.length === 1) {

        return words[0]
            .substring(0, 2)
            .toUpperCase();
    }


    return (
        words[0][0] +
        words[1][0]
    ).toUpperCase();
}


/* =========================================
   SECURITY
========================================= */

function escapeHTML(value) {

    const div =
        document.createElement("div");

    div.textContent =
        value ?? "";

    return div.innerHTML;
}


/* =========================================
   HOME
========================================= */

function scrollToTop() {

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


/* =========================================
   CHECK EXISTING SESSION
========================================= */

async function checkSession() {

    const { data, error } =
        await supabaseClient.auth.getSession();


    if (error) {

        console.error(error);

        return;
    }


    if (data.session) {

        currentUser =
            data.session.user;

        await openApp();

    } else {

        document.getElementById(
            "authPage"
        ).style.display = "flex";

        document.getElementById(
            "appPage"
        ).style.display = "none";
    }
}


/* =========================================
   AUTH STATE CHANGES
========================================= */

supabaseClient.auth.onAuthStateChange(
    async (event, session) => {

        if (session) {

            currentUser =
                session.user;

        } else {

            currentUser = null;
            currentProfile = null;
        }
    }
);


/* =========================================
   START WEBSITE
========================================= */

checkSession();

</script>

</body>
</html>
