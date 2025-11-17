

<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Eiscafé Sanremo – Digitale Speisekarte</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        * { box-sizing: border-box; }

        body {
            margin: 0;
            padding: 0;
            background-image: url('fundo-gelado.jpg'); /* opcional */
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            font-family: Arial, sans-serif;
        }

        .overlay {
            min-height: 100vh;
            background: rgba(255,255,255,0.9);
            padding: 10px;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
        }

        h1, h2, h3 {
            margin-top: 0;
        }

        .header {
            text-align: center;
            margin-bottom: 10px;
        }

        .header-note {
            text-align: center;
            font-size: 0.85rem;
            color: #444;
            margin-bottom: 8px;
        }

        .table-info {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 10px;
            justify-content: center;
        }

        .table-info input {
            padding: 8px;
            border-radius: 6px;
            border: 1px solid #ccc;
            min-width: 140px;
        }

        .info-note {
            text-align: center;
            font-size: 0.95rem;
            color: #444;
            background: #fff;
            padding: 8px 12px;
            border-radius: 10px;
            margin-bottom: 15px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        .category-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-bottom: 15px;
        }

        .category-buttons button {
            border: none;
            padding: 10px 18px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: bold;
            background-color: #f3f3f3;
        }

        .category-buttons button.active {
            background-color: #ffcc66;
        }

        .category {
            display: none;
            border-radius: 12px;
            padding: 10px;
            background: rgba(255,255,255,0.95);
            box-shadow: 0 1px 4px rgba(0,0,0,0.1);
            margin-bottom: 15px;
            border-left: 4px solid transparent;
        }

        .category.active {
            display: block;
        }

        /* cores diferentes por categoria */
        #cat-eis {
            border-left-color: #ffb74d;
            background: rgba(255,248,225,0.95);
        }
        #cat-kinder {
            border-left-color: #64b5f6;
            background: rgba(227,242,253,0.95);
        }
        #cat-essen {
            border-left-color: #81c784;
            background: rgba(232,245,233,0.95);
        }
        #cat-getraenke {
            border-left-color: #ba68c8;
            background: rgba(243,229,245,0.95);
        }

        .items-grid {
            display: block;
            max-height: 480px;
            overflow-y: auto;
            padding-right: 4px;
        }

        .item-card {
            margin-bottom: 10px;
            border-radius: 12px;
            padding: 10px;
            background: #ffffff;
            box-shadow: 0 1px 4px rgba(0,0,0,0.1);
        }

        .item-header {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-bottom: 4px;
        }

        .item-name { font-weight: bold; }
        .item-price { font-weight: bold; }

        .item-options {
            font-size: 0.85rem;
            margin-bottom: 6px;
        }

        .item-row {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            align-items: center;
            margin-top: 6px;
        }

        .item-row input[type="number"],
        .item-row select {
            padding: 5px;
            border-radius: 6px;
            border: 1px solid #ccc;
            font-size: 0.85rem;
        }

        .item-row button {
            border: none;
            padding: 6px 10px;
            border-radius: 10px;
            cursor: pointer;
            background-color: #4caf50;
            color: #fff;
            font-size: 0.85rem;
        }

        .order-summary {
            margin-top: 20px;
            padding: 10px;
            border-radius: 12px;
            background: #fff;
            box-shadow: 0 1px 4px rgba(0,0,0,0.1);
        }

        .order-summary h2 { margin-top: 0; }
        .order-list { font-size: 0.9rem; margin-bottom: 8px; }

        .order-item {
            display: flex;
            justify-content: space-between;
            gap: 10px;
            border-bottom: 1px solid #eee;
            padding: 3px 0;
        }

        .order-total {
            font-weight: bold;
            margin-top: 5px;
        }

        .order-actions {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 10px;
        }

        .order-actions button {
            border: none;
            padding: 8px 14px;
            border-radius: 18px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .btn-clear {
            background-color: #e53935;
            color: #fff;
        }

        .btn-print {
            background-color: #1976d2;
            color: #fff;
        }

        .btn-whatsapp {
            background-color: #25D366;
            color: #fff;
        }

        .small-note {
            font-size: 0.75rem;
            color: #555;
        }
    </style>
</head>
<body>
<div class="overlay">
    <div class="container">
        <div class="header">
            <h1>Eiscafé Sanremo</h1>
            <h3>Digitale Speisekarte &amp; Tischbestellung</h3>
        </div>

        <div class="header-note">
            Dieses Bestellsystem funktioniert nur im Eiscafé San Remo und benötigt die Standortfreigabe auf Ihrem Handy.
        </div>

        <!-- FOTO NO TOPO -->
        <div style="text-align:center;">
            <img src="eis-sanremo.jpg" alt="Eisbecher" style="width:100%;max-width:380px;border-radius:12px;margin-bottom:15px;">
        </div>

        <div class="table-info">
            <input type="text" id="tableNumber" placeholder="Tischnummer">
            <input type="text" id="guestName" placeholder="Name / Familie (optional)">
        </div>

        <div class="info-note">
            <strong>Bitte zuerst die Tischnummer eingeben.</strong><br>
            Danach können Sie die gewünschten Produkte auswählen und die Bestellung abschicken.
        </div>

        <div class="category-buttons">
            <button class="cat-btn active" data-target="cat-eis">🍨 Eis &amp; Becher</button>
            <button class="cat-btn" data-target="cat-kinder">👶 Kinder</button>
            <button class="cat-btn" data-target="cat-essen">🍽️ Snacks, Waffeln &amp; Desserts</button>
            <button class="cat-btn" data-target="cat-getraenke">☕ Kaffee &amp; Getränke</button>
        </div>

        <!-- EIS & BECHER -->
        <div id="cat-eis" class="category active">
            <h2>🍨 Eis &amp; Becher</h2>
            <p>
                <strong>Eissorten (Auswahl):</strong>
                Vanille, Stracciatella, Schokolade, Amarena Kirsch, Joghurt,
                Cookies, Erdbeer, Himbeere, Banane, Schlumpfeis, Zitrone,
                Mango, Limette, Maracuja, Walnuss, Malaga, Pistazie,
                Dunkle Schokolade, After Eight.
            </p>

            <h3>🍨 Portionen </h3>
            <div class="items-grid" id="grid-portions"></div>

            <h3 style="margin-top:20px;">🍨 Eisbecher &amp; Spezial</h3>
            <div class="items-grid" id="grid-eis"></div>
        </div>

        <!-- KINDER – VERTICAL -->
        <div id="cat-kinder" class="category">
            <h2>👶 Kinderbecher</h2>
            <p>Mit oder ohne Sahne, Sorten frei wählbar.</p>
            <div class="items-grid" id="grid-kinder"></div>
        </div>

        <!-- SNACKS, WAFFELN & DESSERTS -->
        <div id="cat-essen" class="category">
            <h2>🍽️ Snacks, Waffeln &amp; Desserts</h2>
            <div class="items-grid" id="grid-essen"></div>
        </div>

        <!-- KAFFEE & GETRÄNKE -->
        <div id="cat-getraenke" class="category">
            <h2>☕ Kaffee &amp; Getränke</h2>
            <div class="items-grid" id="grid-getraenke"></div>
        </div>

        <div class="order-summary">
            <h2>🧾 Aktuelle Bestellung</h2>
            <div class="order-list" id="orderList">
                Noch keine Positionen.
            </div>
            <div class="order-total" id="orderTotal">Gesamt: 0,00 €</div>
            <div class="small-note">
                Diese Seite speichert keine Daten auf dem Server – sie dient nur als Übersicht für den Tisch.
            </div>
            <div class="order-actions">
                <button class="btn-clear" id="clearOrderBtn">Tisch leeren / neue Gäste</button>
                <button class="btn-print" id="printBtn">Bestellung drucken</button>
                <button class="btn-whatsapp" id="whatsAppBtn">Bestellung per WhatsApp senden</button>
            </div>
        </div>
    </div>
</div>

<script>
const flavours = [
    "Vanille","Stracciatella","Schokolade","Amarena Kirsch","Joghurt",
    "Cookies","Erdbeer","Himbeere","Banane","Schlumpfeis","Zitrone",
    "Mango","Limette","Maracuja","Walnuss","Malaga","Pistazie",
    "Dunkle Schokolade","After Eight"
];

// Porções 23–26 (com suplemento de Sahne +1,20 €)
const portionItems = [
    {"id": "23","name": "Kinder Portion","price": 3.5},
    {"id": "24","name": "Kleine Portion","price": 5.0},
    {"id": "25","name": "Normale Portion","price": 6.5},
    {"id": "26","name": "Große Portion","price": 9.5}
];

// Kinderbecher – só aqui
const kidsItems = [
    {"id": "1601","name": "Pinocchio","price": 5.10},
    {"id": "1602","name": "Spaghetti Bambini","price": 5.60},
    {"id": "1603","name": "Kinder Spaghetti Schoko","price": 5.70},
    {"id": "1604","name": "Kinder Spaghetti Gummibärchen","price": 5.70},
    {"id": "1605","name": "Kinder Spaghetti","price": 5.40},
    {"id": "1606","name": "Kinder Spaghetti Erdbeere","price": 6.00}
];

// Eisbecher & Spezial
const becherItems = [
    {"id": "30","name": "Amarena Becher","price": 8.5},
    {"id": "31","name": "Erdbeer Becher","price": 8.5},
    {"id": "32","name": "Banana Cup","price": 9.0},
    {"id": "33","name": "Liebes Traum","price": 13.5},
    {"id": "34","name": "Kiwi Becher","price": 8.5},
    {"id": "35","name": "Frucht Becher","price": 8.5},
    {"id": "36","name": "Großer Frucht Becher","price": 11.9},
    {"id": "37","name": "Großer Amarena Becher","price": 12.5},
    {"id": "38","name": "Großer Erdbeer Becher","price": 12.5},
    {"id": "39","name": "Erdbeer-Banane Becher","price": 10.9},
    {"id": "40","name": "Exotischer Becher","price": 12.0},
    {"id": "41","name": "Waldbecher","price": 10.5},
    {"id": "42","name": "Bella Italia","price": 11.0},
    {"id": "43","name": "Mango Becher","price": 9.0},
    {"id": "44","name": "Banana Split","price": 10.0},
    {"id": "45","name": "Sommer Becher","price": 13.0},
    {"id": "46","name": "Coppa Melone","price": 9.5},
    {"id": "47","name": "Heidelbeer Becher","price": 9.5},
    {"id": "48","name": "Himbeer Becher","price": 9.5},
    {"id": "50","name": "Spaghetti Eis","price": 6.5},
    {"id": "51","name": "Spaghetti Eis groß","price": 9.5},
    {"id": "52","name": "Spaghetti Vanille","price": 7.4},
    {"id": "53","name": "Spaghetti Erdbeere","price": 8.9},
    {"id": "54","name": "Spaghetti Kiwi","price": 8.5},
    {"id": "55","name": "Spaghetti Vanille-Schoko","price": 7.5},
    {"id": "56","name": "Spaghetti Carbonara","price": 9.5},
    {"id": "57","name": "Spaghetti Nussknacker","price": 9.5},
    {"id": "58","name": "Spaghetti Amarena","price": 8.9},
    {"id": "59","name": "Spaghetti Waldfrüchte","price": 8.9},
    {"id": "60","name": "Spaghetti Melone","price": 8.9},
    {"id": "61","name": "Spaghetti Tutti Frutti","price": 8.9},
    {"id": "62","name": "Lasagne Eis","price": 8.9},
    {"id": "63","name": "Pizza Margherita Eis","price": 9.0},
    {"id": "64","name": "Pizza Grandiosa Eis","price": 12.0},
    {"id": "70","name": "Mixgetränk Spezial","price": 6.5},
    {"id": "71","name": "Joghurrette","price": 9.5},
    {"id": "72","name": "Joghurt Cocktail","price": 9.5},
    {"id": "73","name": "Joghurt Kiwi","price": 9.0},
    {"id": "74","name": "Joghurt Erdbeere","price": 9.0},
    {"id": "75","name": "Joghurt Ananas","price": 9.0},
    {"id": "76","name": "Müsli Joghurt","price": 9.0},
    {"id": "77","name": "Joghurt Heidelbeere","price": 9.0},
    {"id": "78","name": "Joghurt Banane","price": 9.0},
    {"id": "79","name": "Joghurt Amarena","price": 9.0},
    {"id": "80","name": "Joghurt Himbeere","price": 9.0},
    {"id": "81","name": "Heiße Kirschen mit Eis","price": 8.5},
    {"id": "82","name": "Heiße Himbeeren mit Eis","price": 9.0},
    {"id": "83","name": "Zimt Becher","price": 8.5},
    {"id": "84","name": "Cup Dänemark","price": 8.5},
    {"id": "85","name": "Wiener Mokka Eisbecher","price": 8.5},
    {"id": "90","name": "Amaretto Becher","price": 8.5},
    {"id": "91","name": "Schwarzwald Becher","price": 9.0},
    {"id": "92","name": "Baileys Becher","price": 8.5},
    {"id": "93","name": "Malaga Becher","price": 9.0},
    {"id": "94","name": "San Remo Becher","price": 12.0},
    {"id": "95","name": "Kaffee Becher","price": 8.5},
    {"id": "96","name": "Eierlikör Becher","price": 8.5},
    {"id": "98","name": "Nuss Becher","price": 9.5},
    {"id": "99","name": "Rocher Becher","price": 9.5},
    {"id": "100","name": "Giotto Becher","price": 9.0},
    {"id": "101","name": "Berg Becher","price": 10.5},
    {"id": "102","name": "Walnuss Becher","price": 9.5},
    {"id": "103","name": "Coppa Delizia","price": 10.9},
    {"id": "110","name": "After Eight Becher","price": 8.9},
    {"id": "111","name": "Stracciatella Becher","price": 7.9},
    {"id": "112","name": "Tartufo Nero","price": 9.5},
    {"id": "113","name": "Tartufo Bianco","price": 9.5},
    {"id": "114","name": "Hausbecher (groß)","price": 20.0},
    {"id": "116","name": "Krokant Becher","price": 8.5},
    {"id": "117","name": "Schoko Becher","price": 8.5},
    {"id": "118","name": "Schoko Becher groß","price": 12.0},
    {"id": "122","name": "Pistazien Becher","price": 11.5},
    {"id": "130","name": "Flipper","price": 5.0},
    {"id": "131","name": "Bellini Eisdrink","price": 6.0},
    {"id": "132","name": "Mimosa Eisdrink","price": 6.0},
    {"id": "133","name": "Formula 1","price": 6.0},
    {"id": "134","name": "Formula 2","price": 6.0},
    {"id": "140","name": "Eiskaffee","price": 5.5},
    {"id": "141","name": "Eisschokolade","price": 5.5},
    {"id": "142","name": "Eis-Cappuccino","price": 5.5},
    {"id": "150","name": "Milch-Mix","price": 4.0},
    {"id": "151","name": "Milkshake","price": 4.6},
    {"id": "152","name": "Riesen Mix","price": 5.0},
    {"id": "153","name": "Riesen Shake","price": 5.5},
    {"id": "154","name": "Vulcano","price": 3.7}
];

const essenItems = [
    {"id": "160","name": "Erdbeer Donut","price": 6.9},
    {"id": "161","name": "Schoko Donut","price": 6.9},
    {"id": "162","name": "Caramel Donut","price": 6.9},
    {"id": "163","name": "Pistazien Donut","price": 7.2},
    {"id": "164","name": "Kinder Donut","price": 6.5},
    {"id": "500","name": "Flammkuchen Elsässer","price": 8.9},
    {"id": "501","name": "Flammkuchen Lachs","price": 8.9},
    {"id": "502","name": "Flammkuchen Griechisch","price": 8.9},
    {"id": "510","name": "Toast Käse","price": 3.7},
    {"id": "511","name": "Toast Schinken","price": 4.3},
    {"id": "512","name": "Toast Salami","price": 4.3},
    {"id": "513","name": "Toast Hawaii","price": 5.6},
    {"id": "520","name": "Baguette XXL","price": 6.9},
    {"id": "600","name": "Apfelstrudel","price": 3.7},
    {"id": "601","name": "Apfelstrudel mit Vanillesoße","price": 4.0},
    {"id": "602","name": "Apfelstrudel mit Sahne","price": 4.7},
    {"id": "603","name": "Apfelstrudel mit Eis","price": 6.1},
    {"id": "610","name": "Tiramisu","price": 4.2},
    {"id": "620","name": "Waffel","price": 4.0},
    {"id": "621","name": "Waffel mit Sahne","price": 5.0},
    {"id": "622","name": "Waffel mit Eis","price": 5.3},
    {"id": "623","name": "Waffel mit Eis & Sahne","price": 6.3},
    {"id": "624","name": "Waffel mit Nutella","price": 5.0},
    {"id": "6301","name": "Zimt & Banane","price": 6.8},
    {"id": "6302","name": "Obstsalat","price": 7.9},
    {"id": "6303","name": "Erdbeeren","price": 7.5},
    {"id": "6304","name": "Waldbeeren","price": 7.2},
    {"id": "6305","name": "Schoko-Banane","price": 7.9},
    {"id": "6306","name": "Heiße Kirschen Dessert","price": 7.0},
    {"id": "6307","name": "Dessert Schoko","price": 6.8},
    {"id": "6308","name": "Tutti Frutti Dessert","price": 7.5}
];

const getraenkeItems = [
    {"id": "155","name": "Orangensaft","price": 4.5},
    {"id": "156","name": "Kalte Zitrone","price": 3.5},
    {"id": "200","name": "Espresso","price": 2.0},
    {"id": "201","name": "Espresso Macchiato","price": 2.3},
    {"id": "202","name": "Espresso Corretto","price": 3.4},
    {"id": "203","name": "Doppelter Espresso","price": 3.6},
    {"id": "204","name": "Doppelter Espresso Macchiato","price": 3.8},
    {"id": "210","name": "Kaffee","price": 2.2},
    {"id": "212","name": "Kännchen Kaffee","price": 4.4},
    {"id": "220","name": "Milchkaffee","price": 3.0},
    {"id": "221","name": "Milchkaffee mit Baileys","price": 4.0},
    {"id": "230","name": "Latte Macchiato","price": 3.6},
    {"id": "231","name": "Latte Macchiato mit Sirup","price": 3.2},
    {"id": "240","name": "Cappuccino","price": 2.6},
    {"id": "241","name": "Cappuccino groß","price": 3.0},
    {"id": "244","name": "Cappuccino Amaretto","price": 4.0},
    {"id": "245","name": "Cappuccino Eierlikör","price": 4.0},
    {"id": "246","name": "Cappuccino Baileys","price": 4.0},
    {"id": "300","name": "Coca-Cola","price": 2.7},
    {"id": "301","name": "Coca-Cola Light","price": 2.7},
    {"id": "302","name": "Coca-Cola Zero","price": 2.7},
    {"id": "303","name": "Fanta","price": 2.7},
    {"id": "304","name": "Mezzo Mix","price": 2.7},
    {"id": "305","name": "Sprite","price": 2.7},
    {"id": "306","name": "Bitter Lemon","price": 2.7},
    {"id": "307","name": "Apfelschorle","price": 1.9},
    {"id": "308","name": "Eistee","price": 1.9},
    {"id": "309","name": "Wild Berry","price": 2.2},
    {"id": "310","name": "Tonic Water","price": 2.2},
    {"id": "311","name": "S.Pellegrino 0,25 l","price": 2.4},
    {"id": "312","name": "S.Pellegrino 0,75 l","price": 5.9},
    {"id": "350","name": "Krombacher Pils","price": 2.8},
    {"id": "351","name": "Krombacher Radler","price": 2.8},
    {"id": "352","name": "Erdinger Weißbier","price": 4.5},
    {"id": "353","name": "Erdinger Alkoholfrei 0,33 l","price": 2.8},
    {"id": "354","name": "Erdinger Alkoholfrei 0,50 l","price": 4.5},
    {"id": "400","name": "Rotwein","price": 4.9},
    {"id": "401","name": "Weißwein","price": 4.9},
    {"id": "402","name": "Glas Sekt","price": 3.9},
    {"id": "403","name": "Campari Sekt","price": 3.9},
    {"id": "410","name": "Aperitif des Hauses","price": 5.9},
    {"id": "430","name": "Grappa","price": 4.7},
    {"id": "431","name": "Asbach","price": 3.2},
    {"id": "432","name": "Ramazzotti","price": 3.2},
    {"id": "433","name": "Aperol Spritz","price": 6.1},
    {"id": "434","name": "Hugo","price": 6.1}
];

document.querySelectorAll('.cat-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
        document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
        document.querySelectorAll('.category').forEach(c => c.classList.remove('active'));
        btn.classList.add('active');
        const target = btn.getAttribute('data-target');
        document.getElementById(target).classList.add('active');
    });
});

function formatDisplayPrice(value) {
    return value.toFixed(2).replace('.', ',') + ' €';
}

function buildCards() {
    const portionsGrid = document.getElementById('grid-portions');
    const kidsGrid = document.getElementById('grid-kinder');
    const eisGrid = document.getElementById('grid-eis');
    const essenGrid = document.getElementById('grid-essen');
    const getraenkeGrid = document.getElementById('grid-getraenke');

    const flavourOptions = flavours.map(f => `<option value="${f}">${f}</option>`).join('');

    // Porções 23–26 (com suplemento de Sahne)
    portionItems.forEach(item => {
        const card = document.createElement('div');
        card.className = 'item-card';
        card.setAttribute('data-name', item.name);
        card.setAttribute('data-price', item.price);
        card.setAttribute('data-portion', 'true');

        card.innerHTML = `
            <div class="item-header">
                <span class="item-name">${item.id}. ${item.name}</span>
                <span class="item-price">${formatDisplayPrice(item.price)}</span>
            </div>
            <div class="item-options">
                <strong>Sahne:</strong> mit oder ohne (mit Sahne +1,20 €).<br>
                <strong>Eissorten auswählen:</strong>
            </div>
            <div class="item-row">
                <label>Menge:
                    <input type="number" min="1" value="1" class="qty-input">
                </label>
                <label>Sahne:
                    <select class="cream-select">
                        <option value="mit Sahne">mit Sahne (+1,20 €)</option>
                        <option value="ohne Sahne">ohne Sahne</option>
                    </select>
                </label>
                <select class="flavour-select" multiple size="3" style="min-width:140px;">
                    ${flavourOptions}
                </select>
                <button class="add-btn">Zur Bestellung hinzufügen</button>
            </div>
        `;
        portionsGrid.appendChild(card);
    });

    // Kinder – VERTICAL, com Sahne + Sorten (sem suplemento extra)
    kidsItems.forEach(item => {
        const card = document.createElement('div');
        card.className = 'item-card';
        card.setAttribute('data-name', item.name);
        card.setAttribute('data-price', item.price);

        card.innerHTML = `
            <div class="item-header">
                <span class="item-name">${item.id}. ${item.name}</span>
                <span class="item-price">${formatDisplayPrice(item.price)}</span>
            </div>
            <div class="item-options">
                <strong>Sahne:</strong> mit oder ohne (optional).<br>
                <strong>Eissorten auswählen:</strong>
            </div>
            <div class="item-row">
                <label>Menge:
                    <input type="number" min="1" value="1" class="qty-input">
                </label>
                <label>Sahne:
                    <select class="cream-select">
                        <option value="mit Sahne">mit Sahne</option>
                        <option value="ohne Sahne">ohne Sahne</option>
                    </select>
                </label>
                <select class="flavour-select" multiple size="3" style="min-width:140px;">
                    ${flavourOptions}
                </select>
                <button class="add-btn">Zur Bestellung hinzufügen</button>
            </div>
        `;
        kidsGrid.appendChild(card);
    });

    // Eisbecher & Spezial
    becherItems.forEach(item => {
        const card = document.createElement('div');
        card.className = 'item-card';
        card.setAttribute('data-name', item.name);
        card.setAttribute('data-price', item.price);

        card.innerHTML = `
            <div class="item-header">
                <span class="item-name">${item.id}. ${item.name}</span>
                <span class="item-price">${formatDisplayPrice(item.price)}</span>
            </div>
            <div class="item-options">
                <strong>Sahne:</strong> mit oder ohne (optional).<br>
                <strong>Eissorten auswählen:</strong>
            </div>
            <div class="item-row">
                <label>Menge:
                    <input type="number" min="1" value="1" class="qty-input">
                </label>
                <label>Sahne:
                    <select class="cream-select">
                        <option value="mit Sahne">mit Sahne</option>
                        <option value="ohne Sahne">ohne Sahne</option>
                    </select>
                </label>
                <select class="flavour-select" multiple size="3" style="min-width:140px;">
                    ${flavourOptions}
                </select>
                <button class="add-btn">Zur Bestellung hinzufügen</button>
            </div>
        `;
        eisGrid.appendChild(card);
    });

    // Snacks & Desserts
    essenItems.forEach(item => {
        const card = document.createElement('div');
        card.className = 'item-card';
        card.setAttribute('data-name', item.name);
        card.setAttribute('data-price', item.price);

        card.innerHTML = `
            <div class="item-header">
                <span class="item-name">${item.id}. ${item.name}</span>
                <span class="item-price">${formatDisplayPrice(item.price)}</span>
            </div>
            <div class="item-row">
                <label>Menge:
                    <input type="number" min="1" value="1" class="qty-input">
                </label>
                <button class="add-btn">Zur Bestellung hinzufügen</button>
            </div>
        `;
        essenGrid.appendChild(card);
    });

    // Getränke
    getraenkeItems.forEach(item => {
        const card = document.createElement('div');
        card.className = 'item-card';
        card.setAttribute('data-name', item.name);
        card.setAttribute('data-price', item.price);

        card.innerHTML = `
            <div class="item-header">
                <span class="item-name">${item.id}. ${item.name}</span>
                <span class="item-price">${formatDisplayPrice(item.price)}</span>
            </div>
            <div class="item-row">
                <label>Menge:
                    <input type="number" min="1" value="1" class="qty-input">
                </label>
                <button class="add-btn">Zur Bestellung hinzufügen</button>
            </div>
        `;
        getraenkeGrid.appendChild(card);
    });
}

const order = [];

function updateOrderDisplay() {
    const list = document.getElementById('orderList');
    const totalEl = document.getElementById('orderTotal');

    if (order.length === 0) {
        list.textContent = 'Noch keine Positionen.';
        totalEl.textContent = 'Gesamt: 0,00 €';
        return;
    }

    list.innerHTML = '';
    let total = 0;

    order.forEach(function(item) {
        total += item.total;

        const row = document.createElement('div');
        row.className = 'order-item';

        const left = document.createElement('div');
        left.innerHTML = '<strong>' + item.qty + '× ' + item.name + '</strong>' +
            (item.details ? '<br><span>' + item.details + '</span>' : '');

        const right = document.createElement('div');
        right.textContent = formatDisplayPrice(item.total);

        row.appendChild(left);
        row.appendChild(right);
        list.appendChild(row);
    });

    totalEl.textContent = 'Gesamt: ' + formatDisplayPrice(total);
}

// Tischnummer obrigatória + suplemento Sahne nas porções 23–26
function attachAddHandlers() {
    document.querySelectorAll('.item-card .add-btn').forEach(function(button) {
        button.addEventListener('click', function() {
            const tableInput = document.getElementById('tableNumber');
            const tableNumber = tableInput.value.trim();

            if (!tableNumber) {
                alert('Bitte geben Sie die Tischnummer ein.');
                tableInput.focus();
                return;
            }

            const card = button.closest('.item-card');
            const name = card.getAttribute('data-name');
            const basePrice = parseFloat(card.getAttribute('data-price'));
            let unitPrice = basePrice;

            const qtyInput = card.querySelector('.qty-input');
            const qty = qtyInput ? parseInt(qtyInput.value || '1', 10) : 1;

            let detailsArr = [];

            const creamSelect = card.querySelector('.cream-select');
            if (creamSelect) {
                const creamValue = creamSelect.value;
                detailsArr.push(creamValue);

                const isPortion = card.getAttribute('data-portion') === 'true';
                if (isPortion && creamValue === 'mit Sahne') {
                    unitPrice = basePrice + 1.20; // suplemento 1,20 € apenas nas porções
                }
            }

            const flavourSelect = card.querySelector('.flavour-select');
            if (flavourSelect) {
                const selected = Array.from(flavourSelect.selectedOptions).map(o => o.value);
                if (selected.length > 0) {
                    detailsArr.push('Sorten: ' + selected.join(', '));
                }
            }

            const guestName = document.getElementById('guestName').value.trim();
            detailsArr.push('Tisch: ' + tableNumber);
            if (guestName) {
                detailsArr.push('Gast: ' + guestName);
            }

            const details = detailsArr.join(' | ');
            const total = unitPrice * qty;

            order.push({
                name: name,
                qty: qty,
                total: total,
                details: details
            });

            updateOrderDisplay();
        });
    });
}

document.getElementById('clearOrderBtn').addEventListener('click', function() {
    order.length = 0;
    document.getElementById('tableNumber').value = '';
    document.getElementById('guestName').value = '';
    updateOrderDisplay();
    alert('Tisch wurde geleert. Neue Gäste können bestellen.');
});

document.getElementById('printBtn').addEventListener('click', function() {
    window.print();
});

document.getElementById('whatsAppBtn').addEventListener('click', function() {
    if (order.length === 0) {
        alert('Keine Bestellung vorhanden.');
        return;
    }

    const tableNumber = document.getElementById('tableNumber').value.trim();
    const guestName = document.getElementById('guestName').value.trim();

    let text = 'Bestellung Eiscafé Sanremo%0A';

    if (tableNumber) text += 'Tisch: ' + tableNumber + '%0A';
    if (guestName) text += 'Gast: ' + guestName + '%0A';
    text += '%0A';

    let total = 0;
    order.forEach(item => {
        total += item.total;
        const line = item.qty + 'x ' + item.name +
            ' - ' + formatDisplayPrice(item.total) +
            (item.details ? ' (' + item.details + ')' : '');
        text += line + '%0A';
    });

    text += '%0A Gesamt: ' + formatDisplayPrice(total);

    const whatsAppNumber = "4917672809926"; // teu número
    const url = 'https://wa.me/' + whatsAppNumber + '?text=' + text;

    window.open(url, '_blank');
});

buildCards();
attachAddHandlers();
</script>

<!-- 🔒 GPS-Schutz: System funktioniert nur im Eiscafé San Remo -->
<script>
// Exakte Koordinaten des Eiscafé San Remo
const cafeLat = 51.050898;
const cafeLon = 8.393595;

// Erlaubter Radius in Metern (erhöht für bessere Innenraum-Genauigkeit)
const maxDist = 150;

// Distanzberechnung (Haversine-Formel)
function distance(lat1, lon1, lat2, lon2) {
    const R = 6371e3;
    const toRad = (value) => value * Math.PI / 180;

    const dLat = toRad(lat2 - lat1);
    const dLon = toRad(don2 - lon1);

    const a =
        Math.sin(dLat / 2) ** 2 +
        Math.cos(toRad(lat1)) * Math.cos(toRad(lat2)) *
        Math.sin(dLon / 2) ** 2;

    const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
    return R * c;
}

window.addEventListener('load', () => {
    if (!navigator.geolocation) {
        document.body.innerHTML = `
            <div style="text-align:center; margin-top:80px; font-family:Arial;">
                <h1>⚠️ Zugriff nicht möglich</h1>
                <h2>Dieses System benötigt die Standortfreigabe.</h2>
                <p>Bitte Standort/GPS auf Ihrem Handy aktivieren und Seite neu laden.</p>
            </div>
        `;
        return;
    }

    navigator.geolocation.getCurrentPosition(
        (pos) => {
            const lat = pos.coords.latitude;
            const lon = pos.coords.longitude;
            const dist = distance(lat, lon, cafeLat, cafeLon);

            if (dist > maxDist) {
                document.body.innerHTML = `
                    <div style="text-align:center; margin-top:80px; font-family:Arial;">
                        <h1>⚠️ Zugriff gesperrt</h1>
                        <h2>Dieses Bestellsystem funktioniert nur<br>
                        im <b>Eiscafé San Remo</b><br>
                        Fürst-Richard-Str. 1, 57319 Bad Berleburg</h2>
                        <p style="margin-top:20px;">Sie befinden sich außerhalb des erlaubten Bereichs.</p>
                    </div>
                `;
            }
        },
        () => {
            document.body.innerHTML = `
                <div style="text-align:center; margin-top:80px; font-family:Arial;">
                    <h1>⚠️ Zugriff verweigert</h1>
                    <h2>Bitte Standortfreigabe erlauben,<br>
                    um das Bestellsystem zu benutzen.</h2>
                    <p>Öffnen Sie Ihre Browser-Einstellungen und aktivieren Sie die Standortfreigabe.</p>
                </div>
            `;
        }
    );
});
</script>

</body>
</html>
