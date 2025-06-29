
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BIGZSHOPX - Customazible & Premade Outfits</title>
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
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: #fff;
      line-height: 1.6;
      min-height: 100vh;
    }

    header {
      background-color: rgba(0, 0, 0, 0.9);
      color: white;
      padding: 1rem 0;
      position: sticky;
      top: 0;
      z-index: 999;
      box-shadow: 0 4px 20px rgba(0,0,0,0.3);
      backdrop-filter: blur(10px);
    }

    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      max-width: 1200px;
      margin: auto;
      padding: 0 1rem;
    }

    .logo {
      font-size: 1.5rem;
      font-weight: 800;
      color: #fff;
      text-decoration: none;
    }

    nav ul {
      list-style: none;
      display: flex;
      gap: 2rem;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: 600;
      transition: color 0.3s, transform 0.3s;
    }

    nav a:hover {
      color: #667eea;
      transform: translateY(-2px);
    }

    .section {
      padding: 80px 20px;
      max-width: 1200px;
      margin: auto;
      background-color: rgba(255, 255, 255, 0.1);
      border-radius: 20px;
      margin-bottom: 2rem;
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .hero {
      background: linear-gradient(135deg, rgba(0, 0, 0, 0.8), rgba(102, 126, 234, 0.3));
      color: white;
      text-align: center;
      padding: 120px 20px;
      border-radius: 20px;
      margin: 2rem auto;
      max-width: 1200px;
    }

    .hero h2 {
      font-size: 4rem;
      margin-bottom: 1rem;
      font-weight: 800;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
      animation: fadeInUp 1s ease-out;
    }

    .hero p {
      font-size: 1.3rem;
      max-width: 600px;
      margin: auto;
      opacity: 0.9;
      animation: fadeInUp 1s ease-out 0.3s both;
    }

    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .btn {
      display: inline-block;
      margin-top: 30px;
      background: linear-gradient(135deg, #667eea, #764ba2);
      color: white;
      padding: 15px 30px;
      border-radius: 50px;
      text-decoration: none;
      font-weight: bold;
      transition: all 0.3s;
      box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
      animation: fadeInUp 1s ease-out 0.6s both;
    }

    .btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
    }

    .grid {
      display: grid;
      gap: 2rem;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    }

    .card {
      background: rgba(255, 255, 255, 0.1);
      padding: 2rem;
      border-radius: 20px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.2);
      transition: all 0.3s;
      text-align: center;
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .card:hover {
      transform: translateY(-10px);
      box-shadow: 0 15px 40px rgba(0,0,0,0.3);
    }

    .outfit-gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 1.5rem;
      margin-top: 2rem;
    }

    .outfit-item {
      background: rgba(255, 255, 255, 0.1);
      border-radius: 15px;
      overflow: hidden;
      transition: all 0.3s;
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .outfit-item:hover {
      transform: scale(1.05);
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }

    .outfit-image {
      width: 100%;
      height: 300px;
      background: linear-gradient(45deg, #667eea, #764ba2);
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.2rem;
      font-weight: 600;
      position: relative;
      overflow: hidden;
    }

    .outfit-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.3s;
    }

    .outfit-image:hover img {
      transform: scale(1.1);
    }

    .outfit-image::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="30" r="8" fill="white" opacity="0.3"/><rect x="40" y="40" width="20" height="25" fill="white" opacity="0.3"/><rect x="35" y="65" width="10" height="20" fill="white" opacity="0.3"/><rect x="55" y="65" width="10" height="20" fill="white" opacity="0.3"/></svg>') center/60px no-repeat;
      z-index: 1;
    }

    .outfit-image img + .placeholder-text {
      display: none;
    }

    .outfit-image .placeholder-text {
      z-index: 2;
      position: relative;
    }

    .outfit-info {
      padding: 1rem;
    }

    .outfit-info h4 {
      margin-bottom: 0.5rem;
      font-size: 1.1rem;
    }

    .outfit-info p {
      opacity: 0.8;
      font-size: 0.9rem;
    }

    .price {
      color: #667eea;
      font-weight: 600;
      font-size: 1.1rem;
      margin-top: 0.5rem;
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      margin-top: 2rem;
    }

    input, textarea {
      padding: 1rem;
      font-size: 1rem;
      border: 1px solid rgba(255, 255, 255, 0.3);
      background-color: rgba(255, 255, 255, 0.1);
      color: #fff;
      border-radius: 10px;
      backdrop-filter: blur(10px);
    }

    input::placeholder, textarea::placeholder {
      color: rgba(255, 255, 255, 0.7);
    }

    button {
      background: linear-gradient(135deg, #667eea, #764ba2);
      color: white;
      padding: 1rem;
      border: none;
      border-radius: 10px;
      font-size: 1rem;
      cursor: pointer;
      transition: all 0.3s;
      font-weight: 600;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
    }

    footer {
      background: rgba(0, 0, 0, 0.9);
      color: #fff;
      text-align: center;
      padding: 3rem 1rem;
      margin-top: 4rem;
    }

    .section h2 {
      font-size: 2.5rem;
      margin-bottom: 2rem;
      text-align: center;
      font-weight: 800;
    }

    .github-notice {
      background: rgba(102, 126, 234, 0.2);
      border: 1px solid rgba(102, 126, 234, 0.5);
      padding: 1rem;
      border-radius: 10px;
      margin-bottom: 2rem;
      text-align: center;
    }

    @media (max-width: 768px) {
      .hero h2 {
        font-size: 2.5rem;
      }
      
      nav ul {
        gap: 1rem;
      }
      
      .grid {
        grid-template-columns: 1fr;
      }
      
      nav {
        flex-direction: column;
        gap: 1rem;
      }
    }
  </style>
</head>
<body>
  <header>
    <nav>
      <a href="#home" class="logo">BIGZSHOPX</a>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#mens">Men's</a></li>
        <li><a href="#womens">Women's</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section id="home" class="hero">
    <h2>BIGZSHOPX</h2>
    <p>BIGZSHOPX offers trendy premade outfits and fully customizable clothing that makes you stand out from the crowd.</p>
    <a href="#contact" class="btn">Order Now</a>
  </section>

  <div class="github-notice">
    <p><strong>📸 Ready to add your outfit pictures?</strong> Upload your images to your GitHub repository and update the file names in the code!</p>
  </div>

  <section id="mens" class="section">
    <h2>Men's Collection</h2>
    <div class="grid">
      <div class="card">
        <h3>Streetwear</h3>
        <p>Urban-inspired looks with hoodies, joggers, and fresh sneakers. Perfect for the streets and casual hangouts.</p>
      </div>
      <div class="card">
        <h3>Smart Casual</h3>
        <p>Versatile pieces that work for both work and play. Elevated basics that never go out of style.</p>
      </div>
      <div class="card">
        <h3>Athletic</h3>
        <p>Performance meets style with our activewear collection. Stay comfortable while looking fresh.</p>
      </div>
    </div>

    <div class="outfit-gallery">
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/mens-outfit-1.jpg" alt="Men's Streetwear Set" onerror="this.style.display='none';">
          <span class="placeholder-text">Men's Streetwear #1</span>
        </div>
        <div class="outfit-info">
          <h4>Urban Classic</h4>
          <p>Comfortable hoodie and joggers combo</p>
          <div class="price">$89.99</div>
        </div>
      </div>
      
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/mens-outfit-2.jpg" alt="Men's Casual Fit" onerror="this.style.display='none';">
          <span class="placeholder-text">Men's Casual #2</span>
        </div>
        <div class="outfit-info">
          <h4>Daily Essentials</h4>
          <p>Perfect for everyday wear</p>
          <div class="price">$69.99</div>
        </div>
      </div>
      
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/mens-outfit-3.jpg" alt="Men's Premium Set" onerror="this.style.display='none';">
          <span class="placeholder-text">Men's Premium #3</span>
        </div>
        <div class="outfit-info">
          <h4>Luxury Collection</h4>
          <p>High-end materials and design</p>
          <div class="price">$129.99</div>
        </div>
      </div>
      
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/mens-outfit-4.jpg" alt="Men's Sport Look" onerror="this.style.display='none';">
          <span class="placeholder-text">Men's Athletic #4</span>
        </div>
        <div class="outfit-info">
          <h4>Active Wear</h4>
          <p>Performance meets style</p>
          <div class="price">$79.99</div>
        </div>
      </div>
    </div>
  </section>

  <section id="womens" class="section">
    <h2>Women's Collection</h2>
    <div class="grid">
      <div class="card">
        <h3>Trendy Sets</h3>
        <p>Fashion-forward outfits that keep you ahead of the trends. Perfect for making a statement wherever you go.</p>
      </div>
      <div class="card">
        <h3>Elegant Wear</h3>
        <p>Sophisticated and classy pieces for special occasions and professional settings that command attention.</p>
      </div>
      <div class="card">
        <h3>Casual Chic</h3>
        <p>Comfortable yet stylish everyday wear that transitions from day to night effortlessly.</p>
      </div>
    </div>

    <div class="outfit-gallery">
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/womens-outfit-1.jpg" alt="Women's Trendy Set" onerror="this.style.display='none';">
          <span class="placeholder-text">Women's Trendy #1</span>
        </div>
        <div class="outfit-info">
          <h4>Fashion Forward</h4>
          <p>Latest trends in one complete look</p>
          <div class="price">$95.99</div>
        </div>
      </div>
      
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/womens-outfit-2.jpg" alt="Women's Elegant Wear" onerror="this.style.display='none';">
          <span class="placeholder-text">Women's Elegant #2</span>
        </div>
        <div class="outfit-info">
          <h4>Sophisticated Style</h4>
          <p>Perfect for professional settings</p>
          <div class="price">$119.99</div>
        </div>
      </div>
      
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/womens-outfit-3.jpg" alt="Women's Casual Chic" onerror="this.style.display='none';">
          <span class="placeholder-text">Women's Casual #3</span>
        </div>
        <div class="outfit-info">
          <h4>Everyday Elegance</h4>
          <p>Comfortable meets stylish</p>
          <div class="price">$99.99</div>
        </div>
      </div>
      
      <div class="outfit-item">
        <div class="outfit-image">
          <img src="images/womens-outfit-4.jpg" alt="Women's Summer Collection" onerror="this.style.display='none';">
          <span class="placeholder-text">Women's Summer #4</span>
        </div>
        <div class="outfit-info">
          <h4>Summer Collection</h4>
          <p>Light and breezy for warm days</p>
          <div class="price">$85.99</div>
        </div>
      </div>
    </div>
  </section>

  <section id="about" class="section">
    <h2>About BIGZSHOPX</h2>
    <p>Founded in 2025, BIGZSHOPX was built to bring creativity and identity to fashion. Whether you're after convenience with our premade collections or want something uniquely yours with our custom designs, we're here to deliver high-quality style at an affordable price. Our team of experienced designers works closely with customers to create outfits that truly represent their personality and lifestyle.</p>
  </section>

  <section id="contact" class="section">
    <h2>Contact Us</h2>
    <p>Have questions or ready to order? Reach out directly at <strong>stephanmarlyp@gmail.com</strong> or use the form below.</p>
    <form action="mailto:stephanmarlyp@gmail.com" method="post" enctype="text/plain">
      <input type="text" name="name" placeholder="Your Name" required />
      <input type="email" name="email" placeholder="Your Email" required />
      <textarea name="message" placeholder="Your Message (describe your outfit needs, preferred style, size, etc.)" rows="5" required></textarea>
      <button type="submit">Send Message</button>
    </form>
  </section>

  <footer>
    <p>&copy; 2025 BIGZSHOPX. All rights reserved.</p>
    <p>Contact: stephanmarlyp@gmail.com</p>
  </footer>
</body>
</html><!-- Floating Admin Button -->
<button id="admin-btn" style="
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: #2c3e50;
  color: black;
  border: none;
  font-size: 20px;
  cursor: pointer;
  box-shadow: 0 2px 10px rgba(0,0,0,0.2);
  z-index: 9999;
">⚙️</button>

<script>
  document.getElementById("admin-btn").addEventListener("click", function() {
    // Create admin panel if it doesn't exist
    if (!document.getElementById("admin-panel")) {
      const panel = document.createElement("div");
      panel.id = "admin-panel";
      panel.innerHTML = `
        <div style="
          position: fixed;
          bottom: 80px;
          right: 20px;
          width: 300px;
          background: white;
          border-radius: 8px;
          padding: 15px;
          box-shadow: 0 0 20px rgba(0,0,0,0.2);
          z-index: 9998;
        ">
          <!-- Paste the FULL admin panel code from earlier here -->
        </div>
      `;
      document.body.appendChild(panel);
    }
    
    // Toggle visibility
    const panel = document.getElementById("admin-panel");
    panel.style.display = panel.style.display === "block" ? "none" : "block";
  });
</script>
<!-- Add this right before </body> in index.html -->
<div id="admin-panel" style="display: none;">
  <div class="admin-header" onclick="toggleAdmin()">
    <span>🔒 BIGZSHOPX ADMIN</span>
    <span id="admin-toggle-icon">▼</span>
  </div>
  
  <div class="admin-content" id="admin-content">
    <div id="login-form">
      <h3>Admin Login</h3>
      <input type="password" id="admin-password" placeholder="Enter password">
      <button onclick="verifyAdmin()">Unlock</button>
      <p id="password-hint" style="color: #ff6b6b; display: none;">
        Hint: Try "0000000000"
      </p>
    </div>
    
    <div id="admin-tools" style="display: none;">
      <!-- ... (keep existing admin tools content) ... -->
    </div>
  </div>
</div>

<script>
  // Password Configuration
  const ADMIN_PASSWORD = "zshop.x9y56";
  let failedAttempts = 0;

  function verifyAdmin() {
    const password = document.getElementById("admin-password").value;
    const hintElement = document.getElementById("password-hint");
    
    if (password === ADMIN_PASSWORD) {
      // Successful login
      document.getElementById("login-form").style.display = "none";
      document.getElementById("admin-tools").style.display = "block";
      loadProducts();
      failedAttempts = 0;
      hintElement.style.display = "none";
    } else {
      // Failed attempt
      failedAttempts++;
      hintElement.style.display = "block";
      
      if (failedAttempts >= 2) {
        hintElement.textContent = `Hint: The password is "${ADMIN_PASSWORD}"`;
      }
      
      // Shake animation for wrong password
      document.getElementById("admin-password").style.animation = "shake 0.5s";
      setTimeout(() => {
        document.getElementById("admin-password").style.animation = "";
      }, 500);
    }
  }

  // Add this to your CSS
  const style = document.createElement('style');
  style.textContent = `
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      20%, 60% { transform: translateX(-5px); }
      40%, 80% { transform: translateX(5px); }
    }
  `;
  document.head.appendChild(style);
</script>
<style>
  #admin-panel {
    max-width: 90vw; /* Limits width on mobile */
    left: 20px; /* Centers panel */
    right: 20px;
    margin: 0 auto;
  }
</style>
