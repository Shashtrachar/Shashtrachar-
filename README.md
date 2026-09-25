<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shashtrachar - Admin Security</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #0f0c1b;
            color: #ffd700;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        .login-box, .admin-content {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid #ffd700;
            padding: 30px;
            border-radius: 12px;
            width: 90%;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.2);
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 15px 0;
            border-radius: 6px;
            border: 1px solid #ffd700;
            background: #1a1528;
            color: white;
            box-sizing: border-box;
        }
        button {
            width: 100%;
            padding: 10px;
            background: #8b0000;
            color: white;
            border: 1px solid #ffd700;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
        }
        .hidden { display: none; }
    </style>
</head>
<body>

    <!-- Security Login Screen -->
    <div id="loginBox" class="login-box">
        <h2>🔒 Admin Security</h2>
        <p style="color: #ccc; font-size: 14px;">Shashtrachar Panel unlock karne ke liye password dalein:</p>
        <input type="password" id="passInput" placeholder="Password yahan likhein">
        <button onclick="verifyPassword()">Unlock Panel</button>
        <p id="error" style="color: #ff4d4d; display: none; margin-top: 10px;">Galat Password!</p>
    </div>

    <!-- Protected Admin Panel -->
    <div id="adminPanel" class="admin-content hidden">
        <h2>⚙️ Shashtrachar Admin Dashboard</h2>
        <p style="color: #4caf50;">✓ Security Verified</p>
        
        <!-- Yahan aapka baki admin form ya buttons aayenge -->
        <p style="color: #fff;">Aap yahan se Nitishatak, Vastu aur Sanskrit notes update kar sakte hain.</p>
        
        <button onclick="logout()" style="background: #4a0000; margin-top: 20px;">Logout</button>
    </div>

    <script>
        // Apna custom password yahan set karein
        const ADMIN_KEY = "Shashtrachar2026"; 

        function verifyPassword() {
            const userPass = document.getElementById("passInput").value;
            if (userPass === ADMIN_KEY) {
                document.getElementById("loginBox").classList.add("hidden");
                document.getElementById("adminPanel").classList.remove("hidden");
                sessionStorage.setItem("isAdminLoggedIn", "true");
            } else {
                document.getElementById("error").style.display = "block";
            }
        }

        // Auto-check on refresh
        if (sessionStorage.getItem("isAdminLoggedIn") === "true") {
            document.getElementById("loginBox").classList.add("hidden");
            document.getElementById("adminPanel").classList.remove("hidden");
        }

        function logout() {
            sessionStorage.removeItem("isAdminLoggedIn");
            location.reload();
        }
    </script>
</body>
</html>
# Shashtrachar-
