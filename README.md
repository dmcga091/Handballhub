# Handballhub
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Handball Hub</title>
<link rel="stylesheet" href="styles.css" />
</head>
<body>
<header>
  <h1>Handball Hub</h1>
  <nav>
    <a href="login.html">Login</a> |
    <a href="groups.html">Groups</a> |
    <a href="fixtures.html">Fixtures</a> |
    <a href="booking.html">Court Booking</a>
  </nav>
</header>
<main>
  <h2>Welcome to Handball Hub</h2>
  <p>Manage your handball club’s groups, fixtures, and court bookings.</p>
</main>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Fixtures - Handball Hub</title>
<link rel="stylesheet" href="styles.css" />
</head>
<body>
<header>
  <h1>Fixtures</h1>
  <nav>
    <a href="index.html">Home</a> |
    <a href="login.html">Login</a> |
    <a href="groups.html">Groups</a> |
    <a href="booking.html">Court Booking</a>
  </nav>
</header>
<main>
  <h2>Fixtures List</h2>
  <p>This is a placeholder for your fixture list.</p>
</main>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Court Booking - Handball Hub</title>
<link rel="stylesheet" href="styles.css" />
</head>
<body>
<header>
  <h1>Court Booking</h1>
  <nav>
    <a href="index.html">Home</a> |
    <a href="login.html">Login</a> |
    <a href="groups.html">Groups</a> |
    <a href="fixtures.html">Fixtures</a>
  </nav>
</header>
<main>
  <h2>Court Booking Placeholder</h2>
  <p>This section will be developed soon.</p>
</main>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  max-width: 700px;
  margin: auto;
  padding: 1rem;
  background: #f9f9f9;
}

header {
  background: #004080;
  color: white;
  padding: 1rem;
  margin-bottom: 1rem;
}

header h1 {
  margin: 0;
}

nav a {
  color: white;
  margin-right: 1rem;
  text-decoration: none;
}

nav a:hover {
  text-decoration: underline;
}

main h2 {
  color: #004080;
}

form label {
  display: block;
  margin: 0.5rem 0;
}

button {
  background: #004080;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  cursor: pointer;
  margin-top: 1rem;
}

button:hover {
  background: #00264d;
}

ul {
  list-style: none;
  padding-left: 0;
}

ul li {
  background: white;
  margin: 0.3rem 0;
  padding: 0.5rem;
  border-radius: 4px;
}
// Basic navigation & login simulation for demo only

document.addEventListener("DOMContentLoaded", () => {
  // Login form handling
  const loginForm = document.getElementById("loginForm");
  if (loginForm) {
    loginForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const email = document.getElementById("email").value.trim();
      const password = document.getElementById("password").value.trim();
      const loginMessage = document.getElementById("loginMessage");

      // Dummy check: accept any email/password for demo
      if (email && password) {
        loginMessage.textContent = "Login successful! (Demo only)";
        setTimeout(() => {
          window.location.href = "index.html";
        }, 1000);
      } else {
        loginMessage.textContent = "Please enter email and password.";
      }
    });
  }

  // Group management - store groups in localStorage
  const groupForm = document.getElementById("groupForm");
  const groupsList = document.getElementById("groupsList");

  if (groupForm && groupsList) {
    function renderGroups() {
      const groups = JSON.parse(localStorage.getItem("groups") || "[]");
      groupsList.innerHTML = "";
      groups.forEach((group, idx) => {
        const li = document.createElement("li");
        li.textContent = group;
        groupsList.appendChild(li);
      });
    }

    groupForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const groupName = document.getElementById("groupName").value.trim();
      if (!groupName) return alert("Please enter a group name.");
      let groups = JSON.parse(localStorage.getItem("groups") || "[]");
      groups.push(groupName);
      localStorage.setItem("groups", JSON.stringify(groups));
      renderGroups();
      groupForm.reset();
    });

    renderGroups();
  }
});
