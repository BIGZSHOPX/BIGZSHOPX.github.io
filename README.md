<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Modern Business</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Inter', sans-serif;
      background-color: #f8f9fa;
      color: #212529;
      line-height: 1.6;
    }

    header {
      background-color: #0d6efd;
      color: white;
      padding: 1rem 0;
      position: sticky;
      top: 0;
      z-index: 999;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      max-width: 1200px;
      margin: auto;
      padding: 0 1rem;
    }

    nav h1 {
      font-size: 1.5rem;
    }

    nav ul {
      list-style: none;
      display: flex;
      gap: 1rem;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: 600;
    }

    .section {
      padding: 80px 20px;
      max-width: 1100px;
      margin: auto;
    }

    .hero {
      background: linear-gradient(120deg, #0d6efd, #6610f2);
      color: white;
      text-align: center;
      padding: 100px 20px;
    }

    .hero h2 {
      font-size: 3rem;
      margin-bottom: 1rem;
    }

    .hero p {
      font-size: 1.2rem;
      max-width: 600px;
      margin: auto;
    }

    .btn {
      display: inline-block;
      margin-top: 20px;
      background: white;
      color: #0d6efd;
      padding: 12px 24px;
      border-radius: 8px;
      text-decoration: none;
      font-weight: bold;
      transition: background 0.3s;
    }

    .btn:hover {
      background: #e2e6ea;
    }

    .grid {
      display: grid;
      gap: 2rem;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    }

    .card {
      background: white;
      padding: 2rem;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.05);
      transition: transform 0.2s;
    }

    .card:hover {
      transform: translateY(-5px);
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      margin-top: 1rem;
    }

    input, textarea {
      padding: 0.75rem;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 8px;
    }

    button {
      background-color: #0d6efd;
      color: white;
      padding: 0.75rem;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
    }

    footer {
      background: #212529;
      color: #fff;
      text-align: center;
      padding: 2rem 1rem;
      margin-top: 4rem;
    }
  </style>
</head>
<body>
  <header>
    <nav>
      <h1>ModernBiz</h1>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section id="home" class="hero">
    <h2>Grow Your Business with Modern Solutions</h2>
    <p>We offer smart strategies and digital tools that drive success and make your business future-ready.</p>
    <a href="#contact" class="btn">Get Started</a>
  </section>

  <section id="services" class="section">
    <h2>Our Services</h2>
    <div class="grid">
      <div class="card">
        <h3>Business Consulting</h3>
        <p>Professional guidance to navigate your market and optimize operations.</p>
      </div>
      <div class="card">
        <h3>Digital Marketing</h3>
        <p>Social media, email, SEO and more to boost your brand visibility and engagement.</p>
      </div>
      <div class="card">
        <h3>Web & App Development</h3>
        <p>Custom, responsive websites and apps tailored to your business goals.</p>
      </div>
    </div>
  </section>

  <section id="about" class="section">
    <h2>About Us</h2>
    <p>ModernBiz is a forward-thinking agency founded in 2025. We partner with clients to deliver cutting-edge strategies that drive measurable growth. Our mission is to make business smarter, faster, and more customer-focused.</p>
  </section>

  <section id="contact" class="section">
    <h2>Contact Us</h2>
    <p>Let’s build something amazing together. Reach out via email or the form below.</p>
    <form>
      <input type="text" placeholder="Your Name" required />
      <input type="email" placeholder="Your Email" required />
      <textarea placeholder="Your Message" rows="5" required></textarea>
      <button type="submit">Send Message</button>
    </form>
  </section>

  <footer>
    <p>&copy; 2025 ModernBiz. All rights reserved.</p>
  </footer>
</body>
</html>
