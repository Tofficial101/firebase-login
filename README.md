# firebase-login
<!DOCTYPE html>
<html>
  <head>
    <title>Login Page</title>
    <script src="https://www.gstatic.com/firebasejs/11.3.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/11.3.1/firebase-auth.js"></script>
    <script src="script.js"></script>
  </head>
  <body>
    <h2>Login Page</h2>
    <input type="email" id="email" placeholder="Email"><br>
    <input type="password" id="password" placeholder="Password"><br>
    <button onclick="login()">Login</button>
    <p id="status"></p>
  </body>
</html>
// Firebase Config (Replace with your Firebase details)
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

firebase.initializeApp(firebaseConfig);

function login() {
  var email = document.getElementById("email").value;
  var password = document.getElementById("password").value;

  firebase.auth().signInWithEmailAndPassword(email, password)
    .then((userCredential) => {
      document.getElementById("status").innerText = "Login Successful!";
    })
    .catch((error) => {
      document.getElementById("status").innerText = "Login Failed: " + error.message;
    });
}
