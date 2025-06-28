
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BIGZSHOPX - Custom & Premade Outfits</title>
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
      background: url('logo.jpeg') no-repeat center center fixed;
      background-size: cover;
      color: #fff;
      line-height: 1.6;
    }

    header {
      background-color: rgba(0, 0, 0, 0.85);
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

    nav img {
      height: 50px;
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

    nav a:hover {
      color: #ddd;
    }

    .section {
      padding: 80px 20px;
      max-width: 1100px;
      margin: auto;
      background-color: rgba(0, 0, 0, 0.85);
      border-radius: 12px;
    }

    .hero {
      background: rgba(0, 0, 0, 0.7);
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
      color: black;
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
      background: #111;
      padding: 2rem;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(255,255,255,0.05);
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
      border: 1px solid #444;
      background-color: #000;
      color: #fff;
      border-radius: 8px;
    }

    button {
      background-color: white;
      color: black;
      padding: 0.75rem;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
    }

    footer {
      background: #111;
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
      <img src="logo.jpeg" alt="BIGZSHOPX Logo">
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#services">Outfits</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section id="home" class="hero">
    <h2>Style That Fits You</h2>
    <p>BIGZSHOPX offers trendy premade outfits and fully customizable clothing that makes you stand out.</p>
    <a href="#contact" class="btn">Order Now</a>
  </section>

  <section id="services" class="section">
    <h2>Our Outfits</h2>
    <div class="grid">
      <div class="card">
        <h3>Premade Outfits</h3>
        <p>Handpicked stylish fits, ready to wear and ship immediately.</p>
      </div>
      <div class="card">
        <h3>Custom Designs</h3>
        <p>Create your dream outfit with our design team. You choose, we make it happen.</p>
      </div>
      <div class="card">
        <h3>Group Orders</h3>
        <p>Perfect for teams, events, and crews. Bulk options available with personalized touches.</p>
      </div>
    </div>
  </section>

  <section id="about" class="section">
    <h2>About BIGZSHOPX</h2>
    <p>Founded in 2025, BIGZSHOPX was built to bring creativity and identity to fashion. Whether you're after convenience or a fully custom look, we're here to deliver high-quality style at an affordable price.</p>
  </section>

  <section id="contact" class="section">
    <h2>Contact Us</h2>
    <p>Have questions or ready to order? Reach out directly at <strong>bigzshopx@gmail.com</strong> or use the form below.</p>
    <form>
      <input type="text" placeholder="Your Name" required />
      <input type="email" placeholder="Your Email" required />
      <textarea placeholder="Your Message" rows="5" required></textarea>
      <button type="submit">Send Message</button>
    </form>
  </section>

  <footer>
    <p>&copy; 2025 BIGZSHOPX. All rights reserved.</p>
  </footer>
</body>
</html>
