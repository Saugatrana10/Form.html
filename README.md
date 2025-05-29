<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background: #f0f8ff;
            min-height: 100vh;
            padding-top: 70px; 
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #333;
            padding: 15px 20px;
        }

        .logo {
            color: white;
            font-size: 24px;
            font-weight: bold;
        }

        .nav-links {
            list-style: none;
            display: flex;
        }

        .nav-links li {
            margin: 0 15px;
        }

        .nav-links a {
            text-decoration: none;
            color: white;
            font-size: 18px;
        }

        .nav-links a:hover {
            color: red
        }

        .container {
            border: 2px solid black;
            padding: 20px;
            width: 300px;
            background-color: lightblue;
            border-radius: 10px;
            box-shadow: 0 2px 8px green;
            text-align: center;
        }
        .container h1 {
            text-align: center;
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="logo">FORM</div>
        <ul class="nav-links">
            <li><a href="#">Home</a></li>
            <li><a href="#">About</a></li>
            <li><a href="#">Services</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
    <div class="container">
        <h1>Form</h1>
        <form>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required><br><br>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required><br><br>
            <label for="password"> Password:</label>
            <input type="password" id="password" name="password" required/><br><br>
            <label for="number">Ph-No.:</label>
            <input type="number" id="number" name="Ph-No." required><br><br>
            <input type="File" value="File" required><br><br>
            <input type="submit" value="Submit" onclick="alert('Form Submitted')"><br><br>
        </form>
    </div>
    <script>
        const form = document.querySelector('form');
        form.addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            const number = document.getElementById('number').value;
            const file = document.querySelector('input[type="file"]').files[0];
            document.write("<h1>Form Data</h1>");
            document.write("Name: " + name + "<br>");
            document.write("Email: " + email + "<br>");
            document.write("Password: " + password + "<br>");
            document.write("Phone Number: " + number + "<br>");
            document.write("File: " + (file ? file.name : "No file selected") + "<br>");

            function validatePassword(password) {
                const regex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d]{8,}$/;
                return regex.test(password);
            }
            function validateEmail(email) {
                const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/; 
                return regex.test(email);
            }
            try {
                if (!validatePassword(password)) {
                    alert("Password must be at least 8 characters long and contain at least one uppercase letter, one lowercase letter, and one number.");
                }
                if (!validateEmail(email)) {
                    alert("Invalid email format.");
                }
                if (name === "" || email === "" || number === "") {
                    alert("All fields are required.");
                }
            } catch (error) {
                document.write(error.message);
            }
        });
    </script>
</body>
</html>
