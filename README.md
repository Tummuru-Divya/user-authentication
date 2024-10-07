# user-authentication

Html


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Authentication</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="form-container">
        <form id="registerForm">
            <h2>Register</h2>
            <input type="text" id="regUsername" placeholder="Username" required>
            <input type="password" id="regPassword" placeholder="Password" required>
            <button type="submit">Register</button>
        </form>

        <form id="loginForm">
            <h2>Login</h2>
            <input type="text" id="loginUsername" placeholder="Username" required>
            <input type="password" id="loginPassword" placeholder="Password" required>
            <button type="submit">Login</button>
        </form>
    </div>
    <script src="script.js"></script>
</body>
</html>


CSS

/* styles.css */
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
}

.form-container {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    max-width: 300px;
    width: 100%;
}

form {
    display: flex;
    flex-direction: column;
}

input {
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}


JavaScript


/* script.js */
// Simple in-memory storage for demonstration purposes
const users = [];

document.getElementById('registerForm').addEventListener('submit', function (e) {
    e.preventDefault();
    const username = document.getElementById('regUsername').value;
    const password = document.getElementById('regPassword').value;

    // Hash the password using a simple method (in practice, use a library like bcrypt)
    const hashedPassword = btoa(password);

    users.push({ username, password: hashedPassword });
    alert('Registered successfully!');
});

document.getElementById('loginForm').addEventListener('submit', function (e) {
    e.preventDefault();
    const username = document.getElementById('loginUsername').value;
    const password = document.getElementById('loginPassword').value;

    // Hash the entered password for comparison
    const hashedPassword = btoa(password);

    const user = users.find(user => user.username === username && user.password === hashedPassword);

    if (user) {
        alert('Login successful!');
        // Redirect to a protected route or page
        window.location.href = 'protected.html';
    } else {
        alert('Invalid username or password!');
    }
});
// Example using localStorage for session management
if (user) {
    localStorage.setItem('loggedInUser', JSON.stringify(user));
} 

const loggedInUser = JSON.parse(localStorage.getItem('loggedInUser'));
if (loggedInUser) {
    // User is logged in, allow access to protected routes
}
const users = [
    { username: 'admin', password: 'adminHashedPassword', role: 'admin' },
    { username: 'user1', password: 'user1HashedPassword', role: 'user' }
];

// Check user role during login
if (user && user.role === 'admin') {
    window.location.href = 'admin.html';
} else if (user) {
    window.location.href = 'user.html';
}
