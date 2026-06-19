
<!DOCTYPE html>
<html>
<head>
    <title>User Authentication System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f4f4;
            display: flex;
            justify-content: center;
            margin-top: 50px;
        }

        .container {
            background: white;
            padding: 20px;
            width: 350px;
            border-radius: 10px;
            box-shadow: 0 0 10px gray;
        }

        h2 {
            text-align: center;
        }

        input {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
        }

        button {
            width: 100%;
            padding: 10px;
            background: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background: #0056b3;
        }

        #message {
            margin-top: 10px;
            text-align: center;
            color: green;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Register</h2>

    <input type="text" id="regName" placeholder="Enter Name">
    <input type="email" id="regEmail" placeholder="Enter Email">
    <input type="password" id="regPassword" placeholder="Enter Password">

    <button onclick="register()">Register</button>

    <hr>

    <h2>Login</h2>

    <input type="email" id="loginEmail" placeholder="Enter Email">
    <input type="password" id="loginPassword" placeholder="Enter Password">

    <button onclick="login()">Login</button>

    <hr>

    <button onclick="logout()">Logout</button>

    <p id="message"></p>
</div>

<script>
function register() {
    const name = document.getElementById("regName").value;
    const email = document.getElementById("regEmail").value;
    const password = document.getElementById("regPassword").value;

    const user = {
        name,
        email,
        password
    };

    localStorage.setItem(email, JSON.stringify(user));

    document.getElementById("message").innerText =
        "Registration Successful!";
}

function login() {
    const email = document.getElementById("loginEmail").value;
    const password = document.getElementById("loginPassword").value;

    const storedUser = JSON.parse(localStorage.getItem(email));

    if (storedUser && storedUser.password === password) {
        localStorage.setItem("loggedInUser", email);

        document.getElementById("message").innerText =
            "Login Successful!";
    } else {
        document.getElementById("message").innerText =
            "Invalid Email or Password!";
    }
}

function logout() {
    localStorage.removeItem("loggedInUser");

    document.getElementById("message").innerText =
        "Logged Out Successfully!";
}
</script>

</body>
</html>

