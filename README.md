<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Fresh Grocery & Vegetable Store</title>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap">
  <style>
    /* Global Styles */
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      color: #333;
      background: url('https://img.freepik.com/premium-photo/vegetables-still-life_290431-7192.jpg?w=740') no-repeat center center/cover;
      background-attachment: fixed;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 50px;
      background-color: rgba(0, 0, 0, 0.6);
      color: white;
    }

    .logo {
      font-size: 2rem;
      font-weight: 600;
      display: flex;
      align-items: center;
    }

    .logo img {
      width: 50px;
      height: 50px;
      margin-right: 10px;
    }

    .action-buttons button {
      background-color: #4CAF50;
      color: white;
      padding: 10px 20px;
      margin-left: 15px;
      border: none;
      border-radius: 5px;
      font-size: 1rem;
      cursor: pointer;
    }

    .action-buttons button:hover {
      background-color: #45a049;
    }

    .hero-section {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      height: 80vh;
      background-color: rgba(0, 0, 0, 0.5);
      color: white;
      padding: 20px;
    }

    .hero-section h1 {
      font-size: 3rem;
      margin: 0;
    }

    .hero-section p {
      font-size: 1.5rem;
      margin: 20px 0;
    }

    .cta-btn {
      background-color: #4CAF50;
      color: white;
      padding: 15px 30px;
      border: none;
      border-radius: 5px;
      font-size: 1.2rem;
      cursor: pointer;
    }

    .cta-btn:hover {
      background-color: #45a049;
    }

    footer {
      background-color: #333;
      color: white;
      text-align: center;
      padding: 20px;
      margin-top: 50px;
    }

    /* Modal Styles */
    .modal {
      display: none;
      position: fixed;
      z-index: 10;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0, 0, 0, 0.5);
    }

    .modal-content {
      background-color: #fff;
      margin: 10% auto;
      padding: 20px;
      border-radius: 10px;
      width: 400px;
      max-width: 90%;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    .modal-content h2 {
      text-align: center;
      margin-bottom: 20px;
      font-size: 1.8rem;
    }

    .form-group {
      margin-bottom: 15px;
    }

    .form-group label {
      display: block;
      font-size: 0.9rem;
      font-weight: bold;
      margin-bottom: 5px;
    }

    .form-group input {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 1rem;
    }

    .form-group button {
      width: 100%;
      padding: 12px;
      background-color: #4CAF50;
      color: white;
      font-size: 1rem;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .form-group button:hover {
      background-color: #45a049;
    }

    .close-btn {
      position: absolute;
      top: 15px;
      right: 20px;
      font-size: 1.5rem;
      cursor: pointer;
      color: #333;
    }

    .toggle-link {
      margin-top: 15px;
      text-align: center;
      display: block;
      font-size: 0.9rem;
      color: #4CAF50;
      cursor: pointer;
    }
  </style>
</head>

<body>
  <!-- Header Section -->
  <header>
    <div class="logo">
      <img src="https://img.freepik.com/premium-vector/logo-fresh-grocery-with-basket-vegetables_763064-309.jpg?w=740" alt="Logo">
      Fresh Grocery Store
    </div>
    <div class="action-buttons">
      <button id="loginSignupBtn">Login / Sign Up</button>
    </div>
  </header>

  <!-- Hero Section -->
  <section class="hero-section">
    <h1>Welcome to Fresh Grocery Store</h1>
    <p>Get fresh vegetables, fruits, and groceries delivered at your doorstep!</p>
    <button class="cta-btn">Shop Now</button>
  </section>

  <!-- Footer Section -->
  <footer>
    <p>&copy; 2024 Fresh Grocery Store. All rights reserved.</p>
  </footer>

  <!-- Modal -->
  <div class="modal" id="loginSignupModal">
    <div class="modal-content">
      <span class="close-btn" id="closeModal">&times;</span>
      <h2 id="modalTitle">Login</h2>
      <div id="modalForm">
        <div class="form-group">
          <label for="email">Email</label>
          <input type="email" id="email" placeholder="Enter your email">
        </div>
        <div class="form-group" id="passwordField">
          <label for="password">Password</label>
          <input type="password" id="password" placeholder="Enter your password">
        </div>
        <button onclick="submitForm()">Login</button>
        <span class="toggle-link" onclick="toggleForm()">Switch to Sign Up</span>
      </div>
    </div>
  </div>

  <script>
    const modal = document.getElementById("loginSignupModal");
    const loginSignupBtn = document.getElementById("loginSignupBtn");
    const closeModal = document.getElementById("closeModal");
    const modalTitle = document.getElementById("modalTitle");
    const modalForm = document.getElementById("modalForm");
    let isLogin = true;

    loginSignupBtn.onclick = () => modal.style.display = "block";
    closeModal.onclick = () => modal.style.display = "none";
    window.onclick = event => { if (event.target === modal) modal.style.display = "none"; };

    function toggleForm() {
      isLogin = !isLogin;
      modalTitle.innerText = isLogin ? "Login" : "Sign Up";
      modalForm.innerHTML = isLogin
        ? `<div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" placeholder="Enter your email">
          </div>
          <div class="form-group" id="passwordField">
            <label for="password">Password</label>
            <input type="password" id="password" placeholder="Enter your password">
          </div>
          <button onclick="submitForm()">Login</button>
          <span class="toggle-link" onclick="toggleForm()">Switch to Sign Up</span>`
        : `<div class="form-group">
            <label for="name">Full Name</label>
            <input type="text" id="name" placeholder="Enter your full name">
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" placeholder="Enter your email">
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input type="password" id="password" placeholder="Choose a password">
          </div>
          <button onclick="submitForm()">Sign Up</button>
          <span class="toggle-link" onclick="toggleForm()">Switch to Login</span>`;
    }

    function submitForm() {
      alert(isLogin ? "Logging in..." : "Signing up...");
    }
  </script>
</body>

</html>
