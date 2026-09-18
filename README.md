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


    <style>

        * {
            box-sizing: border-box;
        }


        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #f2f3f5;
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
           LOGIN PAGE
        ========================= */

        #authPage {

            min-height: 100vh;

            display: flex;

            align-items: center;

            justify-content: center;

            padding: 20px;

            background:
                linear-gradient(
                    135deg,
                    #111827,
                    #374151
                );

        }


        .authBox {

            width: 100%;

            max-width: 420px;

            background: white;

            padding: 35px;

            border-radius: 20px;

            box-shadow:
                0 20px 50px
                rgba(0, 0, 0, 0.25);

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

            margin-top: 8px;

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


        .primaryButton {

            width: 100%;

            padding: 13px;

            border: none;

            border-radius: 10px;

            background: #111827;

            color: white;

            font-weight: bold;

        }


        .switchText {

            text-align: center;

            margin-top: 18px;

            color: #6b7280;

            font-size: 14px;

        }


        .switchText span {

            color: #111827;

            font-weight: bold;

            cursor: pointer;

        }


        /* =========================
           MAIN APP
        ========================= */

        #appPage {

            min-height: 100vh;

        }


        .navbar {

            height: 65px;

            background: white;

            border-bottom:
                1px solid #e5e7eb;

            display: flex;

            align-items: center;

            justify-content: space-between;

            padding: 0 20px;

        }


        .navLogo {

            font-size: 20px;

            font-weight: 900;

        }


        .logoutButton {

            border: none;

            background: #f3f4f6;

            padding: 9px 14px;

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

            padding: 20px;

            border-radius: 15px;

            border:
                1px solid #e5e7eb;

            margin-bottom: 15px;

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

            border:
                1px solid #e5e7eb;

            margin-bottom: 15px;

        }


        .createPost textarea {

            width: 100%;

            min-height: 90px;

            resize: vertical;

            padding: 12px;

            border:
                1px solid #d1d5db;

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

            border:
                1px solid #e5e7eb;

            border-radius: 15px;

            margin-bottom: 15px;

            overflow: hidden;

        }


        .postHeader {

            padding:
                15px 15px 5px;

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

            padding:
                10px 15px 15px;

            white-space: pre-wrap;

        }


        .postActions {

            display: flex;

            border-top:
                1px solid #f0f0f0;

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

                <p>
                    Private Social Media Website
                </p>

            </div>


            <!-- LOGIN -->

            <div id="loginForm">

                <input
                    type="email"
                    placeholder="Email"
                    id="loginEmail"
                >


                <input
                    type="password"
                    placeholder="Password"
                    id="loginPassword"
                >


                <button
                    class="primaryButton"
                    onclick="login()"
                >
                    Login
                </button>


                <div class="switchText">

                    Don't have an account?

                    <span onclick="showSignup()">
                        Create one
                    </span>

                </div>

            </div>


            <!-- SIGNUP -->

            <div
                id="signupForm"
                class="hidden"
            >

                <input
                    type="text"
                    placeholder="Username"
                    id="signupUsername"
                >


                <input
                    type="text"
                    placeholder="Display name"
                    id="signupName"
                >


                <input
                    type="email"
                    placeholder="Email"
                    id="signupEmail"
                >


                <input
                    type="password"
                    placeholder="Password"
                    id="signupPassword"
                >


                <button
                    class="primaryButton"
                    onclick="signup()"
                >
                    Create Account
                </button>


                <div class="switchText">

                    Already have an account?

                    <span onclick="showLogin()">
                        Login
                    </span>

                </div>

            </div>


        </div>

    </section>



    <!-- =========================
         MAIN APP
    ========================= -->

    <section
        id="appPage"
        class="hidden"
    >


        <nav class="navbar">

            <div class="navLogo">
                DPSB SSMW
            </div>


            <button
                class="logoutButton"
                onclick="logout()"
            >
                Logout
            </button>

        </nav>


        <main class="container">


            <!-- PROFILE -->

            <div class="profileCard">

                <div class="profileName">
                    Your Name
                </div>

                <div class="profileUsername">
                    @username
                </div>

            </div>


            <!-- CREATE POST -->

            <div class="createPost">

                <textarea
                    placeholder="What's happening?"
                ></textarea>


                <button
                    class="postButton"
                >
                    Post
                </button>

            </div>


            <!-- EXAMPLE POST -->

            <article class="post">

                <div class="postHeader">

                    <div class="postAuthor">
                        Example User
                    </div>

                    <div class="postTime">
                        Just now
                    </div>

                </div>


                <div class="postContent">

                    Welcome to DPSB SSMW!

                </div>


                <div class="postActions">

                    <button
                        class="actionButton"
                    >
                        ♡ Like
                    </button>


                    <button
                        class="actionButton"
                    >
                        💬 Comment
                    </button>

                </div>

            </article>


        </main>

    </section>



    <!-- =========================
         JAVASCRIPT
    ========================= -->

    <script>

        function showSignup() {

            document
                .getElementById("loginForm")
                .classList
                .add("hidden");


            document
                .getElementById("signupForm")
                .classList
                .remove("hidden");

        }


        function showLogin() {

            document
                .getElementById("signupForm")
                .classList
                .add("hidden");


            document
                .getElementById("loginForm")
                .classList
                .remove("hidden");

        }


        function login() {

            alert(
                "Supabase login will be connected in the next step."
            );

        }


        function signup() {

            alert(
                "Supabase signup will be connected in the next step."
            );

        }


        function logout() {

            document
                .getElementById("appPage")
                .classList
                .add("hidden");


            document
                .getElementById("authPage")
                .classList
                .remove("hidden");

        }

    </script>


</body>

</html>
