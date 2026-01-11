<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Kingdos Cake | Official</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Montserrat:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        :root { 
            --maroon: #421131; --pink: #F89CD2; --yellow: #FFD43B; 
            --lavender: #F3E5F5; --gold: #D4AF37; --white: #ffffff;
            --accent-blue: #E1F5FE;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
        
        html, body { 
            width: 100%; 
            overflow-x: hidden; 
            background: var(--yellow); 
            font-family: 'Montserrat', sans-serif;
        }

        /* FULL WIDTH HEADER */
        header { 
            background: var(--maroon); 
            width: 100%;
            padding: 30px 20px; 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            border-bottom: 6px solid var(--gold); 
            position: sticky; 
            top: 0; 
            z-index: 1000; 
        }
        
        .header-left { flex: 1; }
        .luxury-icon { width: 60px; height: 60px; fill: var(--gold); }
        
        .header-title { 
            color: var(--gold); 
            font-family: 'Playfair Display'; 
            font-weight: 900; 
            font-size: 26px;
            text-align: center;
            flex: 2;
        }
        
        .header-right { flex: 1; display: flex; justify-content: flex-end; }
        .cart-pill { background: var(--gold); color: var(--maroon); padding: 10px 18px; border-radius: 30px; font-weight: 900; }

        /* FULL WIDTH HERO */
        .hero { 
            width: 100%;
            height: 70vh; 
            position: relative; 
            overflow: hidden; 
            border-bottom: 6px solid var(--gold); 
        }
        
        .slide { position: absolute; width: 100%; height: 100%; opacity: 0; transition: 1s ease; background-size: cover; background-position: center; }
        .active { opacity: 1; }
        
        .slide-overlay { 
            width: 100%; height: 100%; 
            background: rgba(0,0,0,0.4); 
            display: flex; flex-direction: column; align-items: center; justify-content: center; 
            color: white; text-align: center; 
        }

        .slide-overlay h1 { font-family: 'Playfair Display'; font-size: 50px; }

        /* MENU GRID */
        .section-title { text-align: center; padding: 40px 0 20px; font-family: 'Playfair Display'; font-size: 32px; }
        .container { width: 100%; padding: 20px 5% 60px; }
        .grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; }

        .card { background: white; border-radius: 20px; overflow: hidden; box-shadow: 0 8px 20px rgba(0,0,0,0.15); position: relative; }
        .card img { width: 100%; height: 200px; object-fit: cover; }
        .card-name { padding: 15px; text-align: center; font-weight: 800; font-size: 13px; text-transform: uppercase; }
        .bogo-badge { position: absolute; top: 12px; left: 12px; background: #ff0000; color: white; padding: 5px 12px; font-size: 10px; font-weight: 900; border-radius: 8px; z-index: 10; }

        /* PRODUCT DETAILS WITH BASE & SERVINGS */
        #details-page { display: none; background: #fff; position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 2000; overflow-y: auto; }
        .back-nav { padding: 20px; background: var(--maroon); color: var(--gold); font-weight: 900; border: none; width: 100%; text-align: left; font-size: 16px; }
        .p-image { width: 100%; height: 400px; object-fit: cover; border-bottom: 8px solid var(--pink); }
        .p-body { padding: 30px; max-width: 600px; margin: auto; padding-bottom: 150px; }
        .p-price { font-size: 38px; font-weight: 900; color: #ff0066; margin-bottom: 20px; }

        /* REPAIRED INFO TILES */
        .info-row { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-bottom: 25px; }
        .info-box { background: var(--lavender); padding: 15px; border-radius: 12px; border-left: 5px solid var(--maroon); }
        .info-label { font-size: 10px; font-weight: 800; color: #666; text-transform: uppercase; }
        .info-value { font-size: 15px; font-weight: 700; color: var(--maroon); }

        .btn-greeting { background: linear-gradient(135deg, #421131, #F89CD2); color: white; padding: 20px; border-radius: 15px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; margin-top: 10px; }

        .floating-footer { position: fixed; bottom: 0; left: 0; width: 100%; background: white; padding: 20px; border-top: 1px solid #ddd; z-index: 2001; }
        .add-btn { background: var(--maroon); color: white; width: 100%; padding: 20px; border: none; border-radius: 15px; font-weight: 900; font-size: 20px; }
        
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 3000; align-items: center; justify-content: center; padding: 20px; }
        .modal-content { background: white; border-radius: 20px; padding: 30px; width: 100%; max-width: 400px; text-align: center; }
        input { width: 100%; padding: 15px; margin: 20px 0; border: 1px solid #ddd; border-radius: 10px; }
    </style>
</head>
<body>

<header>
    <div class="header-left">
        <svg class="luxury-icon" viewBox="0 0 24 24"><path d="M5,16L3,5L8.5,10L12,4L15.5,10L21,5L19,16H5M19,19A1,1 0 0,1 18,20H6A1,1 0 0,1 5,19V18H19V19Z" /></svg>
    </div>
    <div class="header-title">KINGDOS CAKE</div>
    <div class="header-right"><div class="cart-pill">🛒 <span id="cartCount">0</span></div></div>
</header>

<div id="home-page">
    <div class="hero">
        <div class="slide active" style="background-image: url('https://images.unsplash.com/photo-1578985545062-69928b1d9587')"><div class="slide-overlay"><h1>KINGDOS ROYAL</h1></div></div>
        <div class="slide" style="background-image: url('https://images.unsplash.com/photo-1535254973040-607b474cb8c2')"><div class="slide-overlay"><h1>PURE LUXURY</h1></div></div>
    </div>
    <h2 class="section-title">Signature Menu</h2>
    <div class="container" style="background: var(--accent-blue);"><div class="grid" id="sigGrid"></div></div>
    <h2 class="section-title">Luxury Masterpieces</h2>
    <div class="container" style="background: var(--yellow);"><div class="grid" id="premGrid"></div></div>
</div>

<div id="details-page">
    <button class="back-nav" onclick="closeDetails()">← BACK TO MENU</button>
    <img id="pImg" class="p-image">
    <div class="p-body">
        <h1 id="pTitle" style="font-family:'Playfair Display'; font-size: 32px; margin-bottom: 10px;"></h1>
        <div id="pPrice" class="p-price"></div>

        <div class="info-row">
            <div class="info-box"><div class="info-label">Cake Base</div><div class="info-value" id="pBase"></div></div>
            <div class="info-box"><div class="info-label">People can eat</div><div class="info-value" id="pServes"></div></div>
        </div>

        <div class="btn-greeting" onclick="showModal()">
            <div><div style="font-weight:900;">✍️ ICING MESSAGE</div><div id="greetingDisplay" style="font-size:11px;">Add your message for free</div></div>
            <div style="font-weight:900;">FREE</div>
        </div>
    </div>
    <div class="floating-footer"><button class="add-btn" onclick="addToCart()">ADD TO CART</button></div>
</div>

<div id="modalOverlay" class="modal">
    <div class="modal-content">
        <h3>Icing Message</h3>
        <input type="text" id="msgI" placeholder="Happy Birthday...">
        <button class="add-btn" onclick="saveM()">SAVE MESSAGE</button>
    </div>
</div>

<script>
    let cart = 0;
    const signature = [
        {name: "Ribbon Classic", base: "Butter Sponge", serves: "12 People", price: "Rs. 3,850", img: "https://images.unsplash.com/photo-1535141192574-5d4897c12636", bogo: true},
        {name: "Chocolate Dream", base: "Dutch Cocoa", serves: "10 People", price: "Rs. 4,500", img: "https://images.unsplash.com/photo-1578985545062-69928b1d9587", bogo: true},
        {name: "Red Velvet Royale", base: "Velvet Mix", serves: "8 People", price: "Rs. 5,200", img: "https://images.unsplash.com/photo-1616541823729-00fe0aacd32c", bogo: true},
        {name: "Berry Bliss", base: "Strawberry", serves: "10 People", price: "Rs. 4,900", img: "https://images.unsplash.com/photo-1464347744102-11db6282f854", bogo: true},
        {name: "Coffee Gala", base: "Espresso", serves: "10 People", price: "Rs. 3,950", img: "https://images.unsplash.com/photo-1559620192-032c4bc4674e", bogo: true},
        {name: "Vanilla Dream", base: "Vanilla", serves: "12 People", price: "Rs. 3,200", img: "https://images.unsplash.com/photo-1488477181946-6428a0291777", bogo: true},
        {name: "Oreo Gala", base: "Cookie Cream", serves: "12 People", price: "Rs. 5,100", img: "https://images.unsplash.com/photo-1542826438-bd32f43d626f", bogo: true},
        {name: "Salted Caramel", base: "Toffee", serves: "10 People", price: "Rs. 4,800", img: "https://images.unsplash.com/photo-1550617931-e17a7b70dce2", bogo: true},
    ];

    const luxury = [
        {name: "24K Gold Cake", base: "Gold Leaf", serves: "20 People", price: "Rs. 18,500", img: "https://images.unsplash.com/photo-1588195538326-c5b1e9f80a1b", bogo: false},
        {name: "Midnight Forest", base: "Black Cherry", serves: "15 People", price: "Rs. 11,000", img: "https://images.unsplash.com/photo-1606313564200-e75d5e30476c", bogo: false},
        {name: "Tiffany Blue", base: "Ganache", serves: "12 People", price: "Rs. 14,500", img: "https://images.unsplash.com/photo-1557925923-33b27f891f88", bogo: false},
        {name: "Nutty Nutella", base: "Hazelnut", serves: "10 People", price: "Rs. 9,400", img: "https://images.unsplash.com/photo-1506459225024-1428097a7e18", bogo: false},
        {name: "Blueberry Hill", base: "Wild Berry", serves: "10 People", price: "Rs. 7,800", img: "https://images.unsplash.com/photo-1559620192-032c4bc4674e", bogo: false},
    ];

    function load(data, id) {
        const g = document.getElementById(id);
        data.forEach(c => {
            const d = document.createElement('div');
            d.className = 'card';
            d.onclick = () => {
                document.getElementById('pTitle').innerText = c.name;
                document.getElementById('pPrice').innerText = c.price;
                document.getElementById('pBase').innerText = c.base;
                document.getElementById('pServes').innerText = c.serves;
                document.getElementById('pImg').src = c.img;
                document.getElementById('home-page').style.display = 'none';
                document.getElementById('details-page').style.display = 'block';
                window.scrollTo(0,0);
            };
            d.innerHTML = `${c.bogo ? '<div class="bogo-badge">BUY 1 GET 1 FREE</div>' : ''}<img src="${c.img}"><div class="card-name">${c.name}</div>`;
            g.appendChild(d);
        });
    }

    function showModal() { document.getElementById('modalOverlay').style.display = 'flex'; }
    function saveM() {
        const v = document.getElementById('msgI').value;
        if(v) document.getElementById('greetingDisplay').innerText = "Message: " + v;
        document.getElementById('modalOverlay').style.display = 'none';
    }
    function closeDetails() { document.getElementById('home-page').style.display = 'block'; document.getElementById('details-page').style.display = 'none'; }
    function addToCart() { cart++; document.getElementById('cartCount').innerText = cart; alert("Added to cart!"); closeDetails(); }

    load(signature, 'sigGrid'); load(luxury, 'premGrid');
    let idx = 0; const slides = document.querySelectorAll('.slide');
    setInterval(() => { slides[idx].classList.remove('active'); idx = (idx + 1) % slides.length; slides[idx].classList.add('active'); }, 4000);
</script>
</body>
</html>
