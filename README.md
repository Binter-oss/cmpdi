# cmpdi
This is a prototype website regarding the information of projects handle by cmpdi
author : Binter
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>CMPDI Dashboard</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #fafafa;
            margin: 0;
            padding: 0;
            color: #333;
            scroll-behavior: smooth;
        }

        .navbar {
            background-color: #004d40;
            padding: 10px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: white;
        }

        .navbar-logo {
            display: flex;
            align-items: center;
        }

        .navbar-logo img {
            height: 50px;
            margin-right: 15px;
        }

        .navbar-links {
            display: flex;
            gap: 15px;
        }

        .navbar a {
            color: white;
            text-decoration: none;
            padding: 8px 16px;
            font-size: 16px;
            transition: background-color 0.3s, color 0.3s;
        }

        .navbar a:hover {
            background-color: #00796b;
            color: #ffffff;
            border-radius: 5px;
        }

        .landing {
            text-align: center;
            padding: 80px 20px;
            background: url('https://www.ga.gov.au/__data/assets/image/0006/109383/iStock-937183680.jpg') no-repeat center center/cover;
            background-color: black;
            color: #2cad6c;
            min-height: 60vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            animation: fadeIn 1.5s ease-in-out;
        }

        .landing h2 {
            font-size: 28px;
            margin-bottom: 20px;
            color: #ffccbc;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
        }

        .landing p {
            font-size: 18px;
            margin-bottom: 30px;
            max-width: 500px;
            line-height: 1.5;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
        }

        .login-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .login-buttons a {
            padding: 12px 24px;
            font-size: 16px;
            background-color: #02ced1;
            color: white;
            border-radius: 5px;
            text-decoration: none;
            transition: background-color 0.3s, transform 0.3s;
        }

        .login-buttons a:hover {
            background-color: #0277bd;
            transform: scale(1.02);
        }

        .about-us {
            padding: 40px 20px;
            background-color: #e0f2f1;
            color: #004d40;
            animation: slideIn 1s ease-out;
        }

        .about-us h3 {
            text-align: center;
            font-size: 28px;
            margin-bottom: 30px;
            color: #004d40;
        }

        .about-us p {
            font-size: 16px;
            margin-bottom: 20px;
            line-height: 1.6;
            color: #004d40;
            animation: fadeIn 1s ease-out;
        }

        .columns {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            max-width: 1000px;
            margin: 0 auto;
        }

        .column-item {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 8px;
            border: 1px solid #eeeeee;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.7s forwards;
        }

        .column-item:nth-child(odd) {
            animation-delay: 0.2s;
        }

        .column-item:nth-child(even) {
            animation-delay: 0.4s;
        }

        .column-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .column-item h4 {
            font-size: 20px;
            margin-bottom: 10px;
            color: #004d40;
        }

        .column-item p {
            display: none;
            font-size: 14px;
            line-height: 1.6;
            color: #004d40;
        }

        .column-item.active p {
            display: block;
            animation: fadeIn 1s ease-out;
        }

        .add-pdf {
            position: absolute;
            bottom: 10px;
            right: 10px;
            background-color: #02ced1;
            color: white;
            padding: 8px 12px;
            border-radius: 5px;
            font-size: 14px;
            cursor: pointer;
            text-decoration: none;
        }

        .add-pdf:hover {
            background-color: #0277bd;
        }

        .footer {
            background-color: #004d40;
            color: white;
            text-align: center;
            padding: 15px;
            font-size: 14px;
        }

        /* Animation Keyframes */
        @keyframes fadeIn {
            0% {
                opacity: 0;
            }

            100% {
                opacity: 1;
            }
        }

        @keyframes slideIn {
            0% {
                opacity: 0;
                transform: translateY(50px);
            }

            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            0% {
                opacity: 0;
                transform: translateY(20px);
            }

            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Media Queries for Mobile View */
        @media (max-width: 768px) {
            .navbar-links {
                flex-direction: column;
                gap: 10px;
            }

            .columns {
                grid-template-columns: 1fr;
            }

            .landing h2 {
                font-size: 24px;
            }

            .landing p {
                font-size: 16px;
            }

            .login-buttons a {
                font-size: 14px;
            }
        }

        /* Admin and Investigator Login Styles */
        .login-section {
            padding: 40px 20px;
            background-color: #004d40;
            color: white;
            text-align: center;
        }

        .login-section h2 {
            font-size: 28px;
            margin-bottom: 20px;
        }

        .login-buttons-container {
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .login-buttons-container a {
            padding: 15px 30px;
            font-size: 18px;
            background-color: #02ced1;
            color: white;
            border-radius: 5px;
            text-decoration: none;
            transition: background-color 0.3s, transform 0.3s;
        }

        .login-buttons-container a:hover {
            background-color: #0277bd;
            transform: scale(1.05);
        }

        /* CMPDI Connect Styles */
        .cmpdi-connect {
            padding: 40px 20px;
            background-color: #e0f2f1;
            color: #004d40;
            animation: slideIn 1s ease-out;
        }

        .cmpdi-connect h3 {
            text-align: center;
            font-size: 28px;
            margin-bottom: 20px;
        }

        .cmpdi-connect form {
            max-width: 600px;
            margin: 0 auto;
        }

        .cmpdi-connect label {
            display: block;
            margin-bottom: 10px;
            font-size: 16px;
        }

        .cmpdi-connect input, .cmpdi-connect textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        .cmpdi-connect button {
            background-color: #02ced1;
            color: white;
            padding: 12px 24px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .cmpdi-connect button:hover {
            background-color: #0277bd;
        }
    </style>
</head>

<body>
    <div class="navbar">
        <div class="navbar-logo">
            <img src="data:image/png;base64,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" alt="CMPDI Logo">
            <span>CMPDI Dashboard</span>
        </div>
        <div class="navbar-links">
            <a href="#landing">Home</a>
            <a href="#about-us">About Us</a>
            <a href="#login">Login</a>
            <a href="#connect">CMPDI Connect</a>
        </div>
    </div>

    <div class="landing" id="landing">
        <h1>Welcome to CMPDI Dashboard</h1>
        <h3>Your one-stop solution for managing research projects efficiently.</h3>
        <div class="login-buttons">
            <a href="#admin-login">Admin Login</a>
            <a href="#investigator-login">Project Investigator Login</a>
        </div>
    </div>

    <div class="about-us" id="about-us">
        <h3>About Us</h3>
        <div class="columns">
            <div class="column-item" onclick="this.classList.toggle('active')">
                <h4>Mission</h4>
                <p>The Mission of CMPDIL is to provide total consultancy in coal and mineral exploration, mining, engineering, and allied fields as premier consultants in India and a leading one in the International arena.</p>
            </div>
            <div class="column-item" onclick="this.classList.toggle('active')">
                <h4>Vision</h4>
                <p>To be the market leader in an expanding earth resource sector and allied professional activities.</p>
            </div>
            <div class="column-item" onclick="this.classList.toggle('active')">
                <h4>Management Policy</h4>
                <p>Our management policy focuses on enhancing operational efficiency, fostering innovation, and ensuring client satisfaction through quality services and ethical practices.</p>
            </div>
            <div class="column-item" onclick="this.classList.toggle('active')">
                <h4>Achievements</h4>
                <p>CMPDIL has achieved significant milestones in coal and mineral exploration, including successful projects, technological advancements, and recognition in the industry.</p>
            </div>
        </div>
    </div>

    <div class="login-section" id="login">
        <h2>Login</h2>
        <div class="login-buttons-container">
            <a href="#admin-login">Admin Login</a>
            <a href="#investigator-login">Project Investigator Login</a>
        </div>
    </div>

    <div class="cmpdi-connect" id="connect">
        <h3>CMPDI Connect</h3>
        <form>
            <label for="name">Name</label>
            <input type="text" id="name" name="name" required>

            <label for="email">Email</label>
            <input type="email" id="email" name="email" required>

            <label for="message">Message</label>
            <textarea id="message" name="message" rows="4" required></textarea>

            <button type="submit">Send</button>
        </form>
    </div>

    <footer class="footer">
        &copy; 2024 CMPDI. All rights reserved.
    </footer>
</body>

</html>
