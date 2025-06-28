<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>My Website</title>
  <link rel="stylesheet" href="style.css"/>
</head>
<body>
  <header>
    <h1>Welcome to My Website BIGZSHOP</h1>
    <nav>
      <ul>
        <li><a href="#about">About Me</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section id="about">
    <h2>About Me</h2>
    <p>Hello! I'm [Your Name], and this is my personal website. I love building things with code.</p>
  </section>

  <section id="projects">
    <h2>Projects</h2>
    <ul>
      <li>Project 1 – Description</li>
      <li>Project 2 – Description</li>
    </ul>
  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p>You can reach me at <a href="mailto:you@example.com">you@example.com</a>.</p>
  </section>

  <footer>
    <p>&copy; 2025 Your Name</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  line-height: 1.6;
  background-color: #f4f4f4;
}

header {
  background: #333;
  color: white;
  padding: 1rem 0;
  text-align: center;
}

nav ul {
  list-style: none;
  padding: 0;
}

nav ul li {
  display: inline;
  margin: 0 15px;
}

nav a {
  color: #fff;
  text-decoration: none;
}

section {
  padding: 20px;
  margin: 10px;
  background: white;
  border-radius: 5px;
}

footer {
  text-align: center;
  padding: 1rem;
  background: #333;
  color: white;
}
// Example: Show an alert when the page loads
window.onload = function () {
  console.log("Welcome to your website!");
};
