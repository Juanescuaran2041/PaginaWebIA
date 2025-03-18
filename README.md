<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ShoeMaster | Premium Brand Shoes</title>
    <style>
        :root {
            --primary: #3a86ff;
            --secondary: #ff006e;
            --light: #f8f9fa;
            --dark: #212529;
            --success: #38b000;
            --warning: #ffbe0b;
            --danger: #d90429;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: var(--dark);
            line-height: 1.6;
        }
        
        header {
            background-color: white;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .logo span {
            color: var(--secondary);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 20px;
        }
        
        nav ul li a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: var(--primary);
        }
        
        .cart-icon {
            position: relative;
            cursor: pointer;
        }
        
        .cart-count {
            position: absolute;
            top: -10px;
            right: -10px;
            background-color: var(--secondary);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 12px;
            font-weight: bold;
        }
        
        .hero {
            background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('/api/placeholder/1200/400');
            background-size: cover;
            background-position: center;
            color: white;
            text-align: center;
            padding: 60px 0;
            margin-bottom: 40px;
        }
        
        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
        }
        
        .hero p {
            font-size: 18px;
            max-width: 600px;
            margin: 0 auto 30px;
        }
        
        .btn {
            display: inline-block;
            padding: 12px 24px;
            background-color: var(--primary);
            color: white;
            text-decoration: none;
            border-radius: 4px;
            font-weight: bold;
            transition: background-color 0.3s;
            border: none;
            cursor: pointer;
        }
        
        .btn:hover {
            background-color: #2a75e6;
        }
        
        .btn-secondary {
            background-color: var(--secondary);
        }
        
        .btn-secondary:hover {
            background-color: #e0005d;
        }
        
        .section-title {
            text-align: center;
            font-size: 32px;
            margin-bottom: 30px;
        }
        
        .brand-section {
            margin-bottom: 40px;
        }
        
        .brand-title {
            font-size: 24px;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--primary);
        }
        
        .products {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
        }
        
        .product-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }
        
        .product-card:hover {
            transform: translateY(-5px);
        }
        
        .product-image {
            height: 200px;
            width: 100%;
            object-fit: cover;
        }
        
        .product-info {
            padding: 15px;
        }
        
        .product-name {
            font-size: 18px;
            margin-bottom: 10px;
        }
        
        .product-price {
            font-size: 20px;
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .stock {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .in-stock {
            color: var(--success);
            font-weight: 500;
        }
        
        .low-stock {
            color: var(--warning);
            font-weight: 500;
        }
        
        .out-stock {
            color: var(--danger);
            font-weight: 500;
        }
        
        .add-to-cart {
            width: 100%;
            padding: 10px;
            font-size: 16px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .add-to-cart i {
            margin-right: 8px;
        }
        
        footer {
            background-color: var(--dark);
            color: white;
            padding: 40px 0;
            margin-top: 60px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
        }
        
        .footer-column h3 {
            margin-bottom: 20px;
            font-size: 18px;
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column ul li {
            margin-bottom: 10px;
        }
        
        .footer-column ul li a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-column ul li a:hover {
            color: white;
        }
        
        .copyright {
            text-align: center;
            padding-top: 20px;
            margin-top: 20px;
            border-top: 1px solid #444;
        }
        
        /* Cart Modal */
        .modal {
            display: none;
            position: fixed;
            z-index: 200;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
        }
        
        .modal-content {
            background-color: white;
            margin: 10% auto;
            padding: 20px;
            width: 80%;
            max-width: 600px;
            border-radius: 8px;
            position: relative;
        }
        
        .close {
            position: absolute;
            right: 15px;
            top: 10px;
            font-size: 24px;
            cursor: pointer;
        }
        
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }
        
        .cart-item-details {
            display: flex;
            align-items: center;
        }
        
        .cart-item img {
            width: 60px;
            height: 60px;
            object-fit: cover;
            margin-right: 15px;
        }
        
        .cart-item-actions {
            display: flex;
            align-items: center;
        }
        
        .quantity-btn {
            background-color: #eee;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            font-weight: bold;
        }
        
        .item-quantity {
            margin: 0 10px;
        }
        
        .remove-item {
            color: var(--danger);
            cursor: pointer;
            margin-left: 20px;
        }
        
        .cart-total {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #eee;
            font-weight: bold;
            font-size: 18px;
        }
        
        .cart-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        /* Responsive Styles */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
            }
            
            nav ul {
                margin-top: 15px;
            }
            
            nav ul li {
                margin: 0 10px;
            }
            
            .hero h1 {
                font-size: 36px;
            }
            
            .modal-content {
                width: 95%;
                margin: 5% auto;
            }
            
            .cart-item {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .cart-item-actions {
                margin-top: 10px;
            }
        }
        
        @media (max-width: 480px) {
            .products {
                grid-template-columns: 1fr;
            }
        }
        
        /* Author info */
        .author-info {
            text-align: center;
            background-color: #f8f9fa;
            padding: 20px;
            margin-top: 40px;
            border-top: 1px solid #ddd;
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <a href="#" class="logo">Shoe<span>Master</span> 👟</a>
                <nav>
                    <ul>
                        <li><a href="#">Home</a></li>
                        <li><a href="#nike">Nike</a></li>
                        <li><a href="#puma">Puma</a></li>
                        <li><a href="#polo">Polo</a></li>
                        <li>
                            <div class="cart-icon" onclick="openCart()">
                                🛒
                                <div class="cart-count">0</div>
                            </div>
                        </li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    
    <section class="hero">
        <div class="container">
            <h1>Step Up Your Style Game</h1>
            <p>Shop the latest collection of premium brand shoes from Nike, Puma, and Polo at unbeatable prices.</p>
            <a href="#featured" class="btn">Shop Now</a>
        </div>
    </section>
    
    <section id="featured" class="container">
        <h2 class="section-title">Featured Collections</h2>
        
        <div id="nike" class="brand-section">
            <h3 class="brand-title">Nike</h3>
            <div class="products">
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Nike Air Max" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Nike Air Max 90</h4>
                        <div class="product-price">$129.99</div>
                        <div class="stock">
                            <span class="in-stock">✓ In Stock (15)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Nike Air Max 90', 129.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
                
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Nike Revolution" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Nike Revolution 6</h4>
                        <div class="product-price">$89.99</div>
                        <div class="stock">
                            <span class="low-stock">⚠ Low Stock (3)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Nike Revolution 6', 89.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
                
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Nike Court Vision" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Nike Court Vision Low</h4>
                        <div class="product-price">$74.99</div>
                        <div class="stock">
                            <span class="in-stock">✓ In Stock (8)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Nike Court Vision Low', 74.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="puma" class="brand-section">
            <h3 class="brand-title">Puma</h3>
            <div class="products">
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Puma Softride" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Puma Softride Vital</h4>
                        <div class="product-price">$69.99</div>
                        <div class="stock">
                            <span class="in-stock">✓ In Stock (12)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Puma Softride Vital', 69.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
                
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Puma Smash" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Puma Smash v2</h4>
                        <div class="product-price">$54.99</div>
                        <div class="stock">
                            <span class="out-stock">✕ Out of Stock</span>
                        </div>
                        <button class="btn add-to-cart" disabled>
                            Out of Stock
                        </button>
                    </div>
                </div>
                
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Puma RS-X" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Puma RS-X³ Puzzle</h4>
                        <div class="product-price">$109.99</div>
                        <div class="stock">
                            <span class="in-stock">✓ In Stock (5)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Puma RS-X³ Puzzle', 109.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="polo" class="brand-section">
            <h3 class="brand-title">Polo</h3>
            <div class="products">
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Polo Ranger" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Polo Ranger Boot</h4>
                        <div class="product-price">$119.99</div>
                        <div class="stock">
                            <span class="in-stock">✓ In Stock (7)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Polo Ranger Boot', 119.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
                
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Polo Thorton" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Polo Thorton Sneaker</h4>
                        <div class="product-price">$89.99</div>
                        <div class="stock">
                            <span class="low-stock">⚠ Low Stock (2)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Polo Thorton Sneaker', 89.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
                
                <div class="product-card">
                    <img src="/api/placeholder/300/200" alt="Polo Court" class="product-image">
                    <div class="product-info">
                        <h4 class="product-name">Polo Court Side Sneaker</h4>
                        <div class="product-price">$79.99</div>
                        <div class="stock">
                            <span class="in-stock">✓ In Stock (10)</span>
                        </div>
                        <button class="btn add-to-cart" onclick="addToCart('Polo Court Side Sneaker', 79.99, '/api/placeholder/300/200')">
                            Add to Cart
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Cart Modal -->
    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCart()">&times;</span>
            <h2>Your Shopping Cart</h2>
            <div id="cartItems">
                <!-- Cart items will be displayed here -->
                <div class="empty-cart">Your cart is empty. Start shopping now!</div>
            </div>
            <div class="cart-total">
                <span>Total:</span>
                <span id="cartTotal">$0.00</span>
            </div>
            <div class="cart-buttons">
                <button class="btn" onclick="closeCart()">Continue Shopping</button>
                <button class="btn btn-secondary" onclick="checkout()">Checkout</button>
            </div>
        </div>
    </div>
    
    <div class="author-info">
        <p>Juan Esteban Cuaran Santander</p>
        <p>Semestre 1B 2025</p>
    </div>
    
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>Shop</h3>
                    <ul>
                        <li><a href="#">New Arrivals</a></li>
                        <li><a href="#">Best Sellers</a></li>
                        <li><a href="#">Sales & Offers</a></li>
                        <li><a href="#">Gift Cards</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Support</h3>
                    <ul>
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">FAQs</a></li>
                        <li><a href="#">Shipping & Returns</a></li>
                        <li><a href="#">Size Guide</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>About</h3>
                    <ul>
                        <li><a href="#">Our Story</a></li>
                        <li><a href="#">Careers</a></li>
                        <li><a href="#">Corporate Responsibility</a></li>
                        <li><a href="#">Terms & Conditions</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Connect</h3>
                    <ul>
                        <li><a href="#">Instagram</a></li>
                        <li><a href="#">Facebook</a></li>
                        <li><a href="#">Twitter</a></li>
                        <li><a href="#">YouTube</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2025 ShoeMaster. All rights reserved.</p>
            </div>
        </div>
    </footer>
    
    <script>
        // Cart functionality
        let cart = [];
        let cartCount = 0;
        
        function updateCartCount() {
            document.querySelector('.cart-count').textContent = cartCount;
        }
        
        function addToCart(name, price, image) {
            // Check if item already exists in cart
            const existingItem = cart.find(item => item.name === name);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    name: name,
                    price: price,
                    image: image,
                    quantity: 1
                });
            }
            
            cartCount++;
            updateCartCount();
            showNotification(`${name} added to cart!`);
        }
        
        function removeFromCart(index) {
            cartCount -= cart[index].quantity;
            cart.splice(index, 1);
            updateCartCount();
            renderCart();
        }
        
        function increaseQuantity(index) {
            cart[index].quantity += 1;
            cartCount++;
            updateCartCount();
            renderCart();
        }
        
        function decreaseQuantity(index) {
            if (cart[index].quantity > 1) {
                cart[index].quantity -= 1;
                cartCount--;
            } else {
                removeFromCart(index);
            }
            updateCartCount();
            renderCart();
        }
        
        function renderCart() {
            const cartItemsElement = document.getElementById('cartItems');
            const cartTotalElement = document.getElementById('cartTotal');
            
            if (cart.length === 0) {
                cartItemsElement.innerHTML = '<div class="empty-cart">Your cart is empty. Start shopping now!</div>';
                cartTotalElement.textContent = '$0.00';
                return;
            }
            
            let cartHTML = '';
            let total = 0;
            
            cart.forEach((item, index) => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                
                cartHTML += `
                    <div class="cart-item">
                        <div class="cart-item-details">
                            <img src="${item.image}" alt="${item.name}">
                            <div>
                                <h4>${item.name}</h4>
                                <p>$${item.price.toFixed(2)}</p>
                            </div>
                        </div>
                        <div class="cart-item-actions">
                            <button class="quantity-btn" onclick="decreaseQuantity(${index})">-</button>
                            <span class="item-quantity">${item.quantity}</span>
                            <button class="quantity-btn" onclick="increaseQuantity(${index})">+</button>
                            <span class="remove-item" onclick="removeFromCart(${index})">🗑️</span>
                        </div>
                    </div>
                `;
            });
            
            cartItemsElement.innerHTML = cartHTML;
            cartTotalElement.textContent = `$${total.toFixed(2)}`;
        }
        
        function openCart() {
            renderCart();
            document.getElementById('cartModal').style.display = 'block';
        }
        
        function closeCart() {
            document.getElementById('cartModal').style.display = 'none';
        }
        
        function checkout() {
            if (cart.length === 0) {
                alert('Your cart is empty!');
                return;
            }
            
            alert('Thank you for your purchase! Redirecting to payment...');
            cart = [];
            cartCount = 0;
            updateCartCount();
            closeCart();
        }
        
        function showNotification(message) {
            // Create notification element
            const notification = document.createElement('div');
            notification.textContent = message;
            notification.style.position = 'fixed';
            notification.style.bottom = '20px';
            notification.style.right = '20px';
            notification.style.backgroundColor = '#38b000';
            notification.style.color = 'white';
            notification.style.padding = '10px 20px';
            notification.style.borderRadius = '4px';
            notification.style.zIndex = '300';
            notification.style.boxShadow = '0 2px 5px rgba(0,0,0,0.2)';
            
            // Add to body
            document.body.appendChild(notification);
            
            // Remove after 3 seconds
            setTimeout(() => {
                notification.style.opacity = '0';
                notification.style.transition = 'opacity 0.5s';
                
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 500);
            }, 2000);
        }
        
        // Close modal when clicking outside of it
        window.onclick = function(event) {
            const modal = document.getElementById('cartModal');
            if (event.target == modal) {
                closeCart();
            }
        }
    </script>
</body>
</html>
