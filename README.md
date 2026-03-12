<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EliteGrip Webshop</title>
<style>
body{font-family:Arial,Helvetica,sans-serif;margin:0;background:#0f172a;color:white}
header{display:flex;justify-content:space-between;align-items:center;padding:20px 40px;background:#020617;position:sticky;top:0}
.logo{font-size:28px;font-weight:700}
nav a{color:white;margin-left:20px;text-decoration:none}
.hero{display:flex;flex-direction:column;align-items:center;text-align:center;padding:80px 20px}
.hero h1{font-size:48px;margin-bottom:20px}
.hero p{max-width:700px;margin-bottom:30px;font-size:18px}
.price{font-size:36px;font-weight:700;margin-bottom:20px}
button{background:#ef4444;border:none;padding:15px 30px;color:white;font-size:18px;border-radius:10px;cursor:pointer}
section{padding:60px 20px;text-align:center}
.products{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:30px;max-width:1000px;margin:auto}
.product{background:#1e293b;padding:25px;border-radius:15px}
.product img{width:100%;border-radius:10px}
.features{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px;max-width:900px;margin:auto}
.card{background:#1e293b;padding:25px;border-radius:15px}
.cart{position:fixed;right:20px;bottom:20px;background:#ef4444;padding:15px 20px;border-radius:10px;font-weight:bold}
footer{padding:30px;text-align:center;background:#020617;color:#94a3b8}
</style>
</head>
<body>

<header>
<div class="logo">EliteGrip</div>
<nav>
<a href="#product">Product</a>
<a href="#features">Voordelen</a>
<a href="#buy">Bestellen</a>
<a href=¨#shoppingcart¨>winkelmand</a>
</nav>
</header>

<section class="hero">
<h1>EliteGrip Antislip Sok</h1>
<p>De eerste sportsok met ingebouwde scheenbescherming en professionele grip onder de voet. Perfect voor voetballers die meer controle, comfort en bescherming willen.</p>
<div class="price">€19,99 voor 2 paar</div>
<a href="#buy"><button>Koop Nu</button></a>
</section>

<section id="product">
<h2>Ons Product</h2>
<div class="products">

<div class="product">
<img src="https://themedicaptain.com/cdn/shop/files/MedSoccerSocksListingswhite-09.jpg?v=1724793620" alt="grip socks">
<h3>EliteGrip Sok</h3>
<p>2 paar antislip sokken met ingebouwde scheenbeschermers.</p>
<p><strong>€19,99</strong></p>
<button onclick="addToCart(2 paar antislip gripsokken met ingebouwdescheenbeschermers)">Toevoegen aan winkelwagen</button>
</div>

</div>
</section>

<section id="features">
<h2>Waarom EliteGrip?</h2>
<div class="features">
<div class="card">
<h3>Antislip Grip</h3>
<p>Siliconen grip onder de sok voorkomt schuiven in je schoen.</p>
</div>
<div class="card">
<h3>Ingebouwde Scheenbeschermers</h3>
<p>Bescherming direct in de sok verwerkt voor extra gemak.</p>
</div>
<div class="card">
<h3>Comfort & Compressie</h3>
<p>Strakke pasvorm zodat de sok perfect blijft zitten tijdens het sporten.</p>
</div>
</div>
</section>

<section id="buy">
<h2>Bestellen</h2>
<p>Klik op de knop om het product toe te voegen aan je winkelwagen.</p>
<button onclick="addToCart()">Bestel 2 Paar voor €19,99</button>
</section>

<div class="cart" id="cart">🛒 Winkelwagen: 0</div>


<section id=¨shoppingcart¨>
<h2>winkelwagen</h2>
</section>
<script>
let cartCount = 0;
function addToCart(){
cartCount++;
document.getElementById("cart").innerText = "🛒 Winkelwagen: " + cartCount;
}
</script>

</body>
</html>

<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<title>Winkelmand</title>
<style>
    body { font-family: Arial, sans-serif; margin: 30px; }
    h1 { color: #f9f3f3; }
    select, button { margin: 5px; padding: 5px; }
    table { width: 60%; border-collapse: collapse; margin-top: 20px; }
    th, td { border: 1px solid #ccc; padding: 10px; text-align: left; }
    th { background-color: #000000; }
    button { cursor: pointer; }
</style>
</head>
<body>

<h1>Winkelmand</h1>

<label for="producten">Kies een product:</label>
<select id="producten">
<option value=¨gripsokken met ingebouwde scheenbeschermers¨ data-prijs=¨19.99¨>gripsokken met ingebouwde scheenbeschermers - €19.99</option>  
</select>
<button onclick="toevoegen()">Toevoegen</button>

<table id="winkelmand">
    <thead>
        <tr>
            <th>Product</th>
            <th>Aantal</th>
            <th>Prijs per stuk</th>
            <th>Subtotaal</th>
            <th>Verwijderen</th>
        </tr>
    </thead>
    <tbody>
    </tbody>
</table>

<h2>Totaal: €<span id="totaal">0.00</span></h2>

<script>
let mand = {};

function toevoegen() {
    const select = document.getElementById('producten');
    const product = select.value;
    const prijs = parseFloat(select.selectedOptions[0].dataset.prijs);

    // Voeg toe of verhoog aantal
    if (mand[product]) {
        mand[product].aantal += 1;
    } else {
        mand[product] = { prijs: prijs, aantal: 1 };
    }

    updateWinkelmand();
}

function verwijder(product) {
    delete mand[product];
    updateWinkelmand();
}

function updateWinkelmand() {
    const tableBody = document.getElementById('winkelmand').getElementsByTagName('tbody')[0];
    tableBody.innerHTML = "";

    let totaal = 0;

    for (const [product, info] of Object.entries(mand)) {
        const row = tableBody.insertRow();
        const celProduct = row.insertCell(0);
        const celAantal = row.insertCell(1);
        const celPrijs = row.insertCell(2);
        const celSubtotaal = row.insertCell(3);
        const celVerwijder = row.insertCell(4);

        celProduct.textContent = product;
        celAantal.textContent = info.aantal;
        celPrijs.textContent = "€" + info.prijs.toFixed(2);
        const subtotal = info.aantal * info.prijs;
        celSubtotaal.textContent = "€" + subtotal.toFixed(2);

        const btnVerwijder = document.createElement('button');
        btnVerwijder.textContent = "Verwijderen";
        btnVerwijder.onclick = () => verwijder(product);
        celVerwijder.appendChild(btnVerwijder);

        totaal += subtotal;
    }

    document.getElementById('totaal').textContent = totaal.toFixed(2);
}
</script>

</body>
</html>

<footer>
<p>© 2026 EliteGrip Webshop</p>
</footer>
