  </div>
</div>

<!-- Footer -->
<footer class="mt-auto py-8 border-t border-gray-800 text-center text-gray-400">
  <div>
    &copy; 2025 BIGZSHOPX. All rights reserved. | <a href="#contact" class="text-purple-400 hover:underline">Contact Us</a>
  </div>
</footer>

<script>
/** ----- 3D Floating Logo with Three.js ----- **/
function run3DLogo() {
  const canvasContainer = document.getElementById('logo3d');
  canvasContainer.innerHTML = ""; // Clear in case of re-entry

  const width = 120, height = 120;
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(45, width/height, 0.1, 1000);
  const renderer = new THREE.WebGLRenderer({ alpha:true, antialias:true });
  renderer.setClearColor(0x000000, 0);
  renderer.setSize(width, height);
  canvasContainer.appendChild(renderer.domElement);

  // 3D geometry: replace this with your logo model if available
  const geometry = new THREE.TorusKnotGeometry(32, 7, 100, 16);
  const material = new THREE.MeshStandardMaterial({ color: 0x8b5cf6, metalness: 0.7, roughness: 0.2 });
  const mesh = new THREE.Mesh(geometry, material);
  scene.add(mesh);

  // Add floating text "BZ"
  const loader = new THREE.FontLoader();
  loader.load('https://threejs.org/examples/fonts/helvetiker_bold.typeface.json', function(font) {
    const textGeo = new THREE.TextGeometry('BZ', {
      font: font,
      size: 24,
      height: 4,
      curveSegments: 12,
      bevelEnabled: true,
      bevelThickness: 1,
      bevelSize: 1.5,
      bevelSegments: 6
    });
    const textMat = new THREE.MeshStandardMaterial({ color: 0xffffff });
    const textMesh = new THREE.Mesh(textGeo, textMat);
    textMesh.position.set(-21, -10, 25);
    scene.add(textMesh);
  });

  // Lighting
  const ambientLight = new THREE.AmbientLight(0xffffff, 0.6);
  scene.add(ambientLight);
  const spotLight = new THREE.SpotLight(0xffffff, 0.7);
  spotLight.position.set(60, 80, 100);
  scene.add(spotLight);

  camera.position.z = 120;
  let start = null;
  function animateLogo(now) {
    if (!start) start = now;
    const elapsed = (now - start)/1000;
    // Animate for 5s at ~50fps
    if (elapsed < 5) {
      mesh.rotation.x += 0.023;
      mesh.rotation.y += 0.041;
      renderer.render(scene, camera);
      requestAnimationFrame(animateLogo);
    } else {
      // Stop animation, show static
      renderer.render(scene, camera);
    }
  }
  animateLogo();
}
run3DLogo();

/** ----- Product List & Cart Functionality ----- **/
let products = [
  {name:'Premium Hoodie', price:89},
  {name:'Designer Jeans', price:129},
  {name:'Elegant Dress', price:159}
];
let cart = [];

function renderProducts() {
  const grid = document.getElementById('productGrid');
  grid.innerHTML = products.map((p, i) => `
    <div class="glass rounded-lg p-6 flex flex-col items-center">
      <img src="https://placehold.co/200x200/8b5cf6/fff?text=Product" alt="${p.name}" class="mb-4 rounded shadow">
      <h4 class="text-xl font-semibold mb-2">${p.name}</h4>
      <div class="text-purple-400 text-lg mb-4 font-bold">$${p.price}</div>
      <button onclick="addToCart(${i})" class="px-4 py-2 bg-purple-600 rounded hover:bg-purple-700">Add to Cart</button>
    </div>
  `).join('');
  renderAdminProductList();
}
function addToCart(i) {
  const prod = products[i];
  const existing = cart.find(item => item.name === prod.name);
  if (existing) { existing.qty++; }
  else { cart.push({...prod, qty:1}); }
  alert(prod.name + " added to cart.");
}
function renderAdminProductList() {
  const ul = document.getElementById('adminProdList');
  if (!ul) return;
  ul.innerHTML = products.map((p,i) => `
    <li class="mb-2 flex items-center">
      <span class="flex-1">${p.name} - $${p.price}</span>
      <button class="px-2 py-1 rounded bg-red-600 hover:bg-red-700 ml-2" onclick="removeProduct(${i})">Delete</button>
    </li>
  `).join('');
}
function addProduct() {
  const name = document.getElementById('prodName').value;
  const price = Number(document.getElementById('prodPrice').value);
  if (name && price > 0) {
    products.push({name, price});
    document.getElementById('prodName').value = '';
    document.getElementById('prodPrice').value = '';
    renderProducts();
  }
}
function removeProduct(i) {
  products.splice(i, 1);
  renderProducts();
}

/** ----- Cart Modal ----- **/
document.getElementById('cartBtn').onclick = function() {
  const modal = document.getElementById('cartModal');
  modal.classList.remove('hidden');
  renderCart();
};
function renderCart() {
  const list = document.getElementById('cartList');
  if (!list) return;
  list.innerHTML = cart.length ? cart.map((item, i) => `
    <li class="flex justify-between mb-2">
      <span>${item.name} x${item.qty}</span>
      <span>$${(item.qty * item.price).toFixed(2)}</span>
      <button class="ml-2 px-2 bg-red-600 rounded" onclick="removeFromCart(${i})">Remove</button>
    </li>
  `).join('') : '<li>Your cart is empty.</li>';
  document.getElementById('cartTotal').innerText = '$' + cart.reduce((a, c) => a + c.qty * c.price, 0).toFixed(2);
}
function closeCart() {
  document.getElementById('cartModal').classList.add('hidden');
}
function removeFromCart(i) {
  cart.splice(i, 1);
  renderCart();
}
function checkout() {
  closeCart();
  document.getElementById('payModal').classList.remove('hidden');
}
function closePay() {
  document.getElementById('payModal').classList.add('hidden');
}
function finishPayment() {
  alert("Thank you for your payment! (Demo, not real payment.)");
  closePay();
  cart = [];
}

/** ----- Customizer ----- **/
document.getElementById('topSelect').onchange = function() {
  document.getElementById('prevTop').innerText = this.value;
};
document.getElementById('bottomSelect').onchange = function() {
  document.getElementById('prevBottom').innerText = this.value;
};
document.getElementById('accSelect').onchange = function() {
  document.getElementById('prevAcc').innerText = this.value;
};
function addCustomToCart() {
  cart.push({
    name: `Custom Outfit (${document.getElementById('topSelect').value}, ${document.getElementById('bottomSelect').value}, ${document.getElementById('accSelect').value})`,
    price: 99,
    qty: 1
  });
  alert("Custom outfit added to cart!");
}

/** ----- Login & Admin Panel ----- **/
let isAdmin = false;
document.getElementById('loginBtn').onclick = function() {
  document.getElementById('loginModal').classList.remove('hidden');
};
function closeLogin() {
  document.getElementById('loginModal').classList.add('hidden');
}
function login() {
  const u = document.getElementById('loginUser').value;
  const p = document.getElementById('loginPass').value;
  if (u === "admin" && p === "admin123") {
    isAdmin = true;
    document.body.classList.add('admin-active');
    document.getElementById('loginModal').classList.add('hidden');
    alert("Admin logged in!");
    renderAdminProductList();
  } else {
    document.getElementById('loginMsg').innerText = "Invalid credentials.";
  }
}
document.getElementById('adminBtn').onclick = function() {
  if (!isAdmin) {
    alert("Admin login required.");
    document.getElementById('loginModal').classList.remove('hidden');
  } else {
    document.body.classList.toggle('admin-active');
  }
};
function logoutAdmin() {
  isAdmin = false;
  document.body.classList.remove('admin-active');
  alert("Admin logged out.");
}

/** ----- Admin Panel Content Editing ----- **/
function editSiteContent() {
  const text = document.getElementById('siteContent').value;
  document.querySelector('section#home h1').innerText = text;
}
renderProducts();
</script>
</body>
</html>
