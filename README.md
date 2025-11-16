<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Eiscafé Sanremo – Digitale Speisekarte</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: Arial, sans-serif;
            background: #f4f4f4;
            color: #333;
            line-height: 1.5;
        }
        header {
            background: #d4232b;
            color: #fff;
            padding: 1rem;
            text-align: center;
        }
        header h1 { font-size: 1.7rem; margin-bottom: .3rem; }
        header p { font-size: .9rem; }

        .mesa-info {
            background: #fff3cd;
            color: #856404;
            padding: .6rem 1rem;
            text-align: center;
            font-size: .95rem;
        }
        .table-select-wrapper {
            margin: .6rem auto 0.8rem;
            text-align: center;
        }
        .table-select-wrapper select {
            padding: 0.3rem 0.6rem;
            font-size: 0.9rem;
            border-radius: 6px;
            border: 1px solid #ccc;
        }

        main {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 1rem 2rem;
        }
        section {
            margin-bottom: 2rem;
        }
        h2 {
            font-size: 1.3rem;
            margin-bottom: .6rem;
            border-bottom: 2px solid #d4232b;
            display: inline-block;
            padding-bottom: .2rem;
        }
        .hint {
            font-size: .85rem;
            color: #555;
            margin-bottom: .6rem;
        }

        /* Grelha das PÁGINAS do menu */
        .menu-photos-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
            gap: .8rem;
        }
        .menu-photos-grid img {
            width: 100%;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,.2);
        }

        /* Foto única do wafflebecher */
        .menu-photos {
            display: flex;
            justify-content: center;
            margin-bottom: 1.2rem;
        }
        .menu-photos img {
            max-width: 100%;
            width: 360px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,.15);
        }

        .order-box {
            background: #fff;
            border-radius: 8px;
            padding: 1rem .9rem 1.2rem;
            box-shadow: 0 2px 8px rgba(0,0,0,.12);
        }
        .order-row {
            margin-bottom: .7rem;
        }
        label {
            display: block;
            font-size: .9rem;
            margin-bottom: .2rem;
            font-weight: 600;
        }
        select, input[type="number"], textarea {
            width: 100%;
            padding: .45rem .55rem;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: .9rem;
        }
        textarea {
            min-height: 70px;
            resize: vertical;
        }
        .flavor-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: .4rem;
        }
        .total-line {
            font-size: .95rem;
            font-weight: 700;
            color: #d4232b;
            margin-top: .4rem;
        }
        .btn-main {
            margin-top: .9rem;
            width: 100%;
            padding: .7rem;
            border-radius: 999px;
            border: none;
            background: #25D366;
            color: #fff;
            font-size: 1rem;
            font-weight: 700;
            cursor: pointer;
        }
        .btn-main:hover {
            background: #1fb357;
        }
        footer {
            text-align: center;
            font-size: .8rem;
            padding: 1rem 0 2rem;
            color: #777;
        }
    </style>
</head>
<body>
<header>
    <h1>Eiscafé Sanremo</h1>
    <p>Digitale Speisekarte – Tisch wählen, Eisbecher aussuchen, 3 Kugeln wählen &amp; per WhatsApp bestellen</p>
</header>

<div class="mesa-info" id="mesaInfo">
    Bitte wählen Sie Ihre Tischnummer aus.
</div>
<div class="table-select-wrapper">
    <label for="tableSelect">Tisch:</label>
    <select id="tableSelect">
        <option value="">– Nummer wählen –</option>
        <!-- Tische 1–33 -->
        <option value="1">1</option><option value="2">2</option><option value="3">3</option>
        <option value="4">4</option><option value="5">5</option><option value="6">6</option>
        <option value="7">7</option><option value="8">8</option><option value="9">9</option>
        <option value="10">10</option><option value="11">11</option><option value="12">12</option>
        <option value="13">13</option><option value="14">14</option><option value="15">15</option>
        <option value="16">16</option><option value="17">17</option><option value="18">18</option>
        <option value="19">19</option><option value="20">20</option><option value="21">21</option>
        <option value="22">22</option><option value="23">23</option><option value="24">24</option>
        <option value="25">25</option><option value="26">26</option><option value="27">27</option>
        <option value="28">28</option><option value="29">29</option><option value="30">30</option>
        <option value="31">31</option><option value="32">32</option><option value="33">33</option>
    </select>
</div>

<main>

    <!-- 1) MENU COMPLETO EM FOTOS -->
    <section>
        <h2>Gesamte Speisekarte (Fotomenü)</h2>
        <p class="hint">
            Hier sehen Sie die komplette Eiskarte, Getränke, Waffeln, Snacks usw.
            Tipp: Bild anklicken und vergrößern, um alle Details und Preise zu lesen.
        </p>

        <div class="menu-photos-grid">
            <!-- Usa aqui as tuas fotos das páginas do menu -->
            <!-- Só precisas subir esses ficheiros para a pasta "images" -->
            <img src="images/menu1.jpg" alt="Speisekarte Seite 1">
            <img src="images/menu2.jpg" alt="Speisekarte Seite 2">
            <img src="images/menu3.jpg" alt="Speisekarte Seite 3">
            <img src="images/menu4.jpg" alt="Speisekarte Seite 4">
            <img src="images/menu5.jpg" alt="Speisekarte Seite 5">
            <img src="images/menu6.jpg" alt="Speisekarte Seite 6">
            <img src="images/menu7.jpg" alt="Speisekarte Seite 7">
            <img src="images/menu8.jpg" alt="Speisekarte Seite 8">
            <img src="images/menu9.jpg" alt="Speisekarte Seite 9">
            <img src="images/menu10.jpg" alt="Speisekarte Seite 10">
            <img src="images/menu11.jpg" alt="Speisekarte Seite 11">
            <img src="images/menu12.jpg" alt="Speisekarte Seite 12">
        </div>
    </section>

    <!-- 2) EISBECHER EM WAFFELBECHER + FORM DE PEDIDO -->
    <section>
        <h2>Eisbecher – Online-Bestellung</h2>
        <p class="hint">
            Alle Eisbecher werden im Waffelbecher serviert. (Foto dient nur zur Veranschaulichung.)<br>
            Wählen Sie unten Ihren Eisbecher, die Menge und 3 Kugeln Eis. Andere Produkte (Getränke, Waffeln,
            Snacks usw.) können Sie im Feld „Weitere Wünsche“ dazuschreiben.
        </p>

        <div class="menu-photos">
            <img src="images/waffelbecher.jpg" alt="Eiscafé Sanremo Waffelbecher">
        </div>

        <div class="order-box">
            <div class="order-row">
                <label for="itemSelect">Eisbecher (Nummer &amp; Name)</label>
                <select id="itemSelect">
                    <option value="">Becher auswählen…</option>

                    <!-- 40er / Früchtebecher -->
                    <option value="40" data-name="Exotischer Becher" data-price="12.00">40 – Exotischer Becher – 12,00 €</option>
                    <option value="41" data-name="Wald Becher" data-price="10.50">41 – Wald Becher – 10,50 €</option>
                    <option value="42" data-name="Bella Italia" data-price="11.00">42 – Bella Italia – 11,00 €</option>
                    <option value="43" data-name="Mango Becher" data-price="9.00">43 – Mango Becher – 9,00 €</option>
                    <option value="44" data-name="Banana Split" data-price="10.00">44 – Banana Split – 10,00 €</option>
                    <option value="45" data-name="Sommer Becher" data-price="13.00">45 – Sommer Becher – 13,00 €</option>
                    <option value="46" data-name="Coppa Melone" data-price="9.50">46 – Coppa Melone – 9,50 €</option>
                    <option value="47" data-name="Heidelbeer Becher" data-price="9.50">47 – Heidelbeer Becher – 9,50 €</option>
                    <option value="48" data-name="Himbeer Becher" data-price="9.50">48 – Himbeer Becher – 9,50 €</option>

                    <!-- Italienische Spezialitäten -->
                    <option value="30" data-name="Amarena Becher" data-price="8.50">30 – Amarena Becher – 8,50 €</option>
                    <option value="31" data-name="Erdbeer Becher" data-price="8.50">31 – Erdbeer Becher – 8,50 €</option>
                    <option value="34" data-name="Kiwi Becher" data-price="8.50">34 – Kiwi Becher – 8,50 €</option>
                    <option value="35" data-name="Frucht Becher" data-price="8.50">35 – Frucht Becher – 8,50 €</option>
                    <option value="36" data-name="Großer Frucht Becher" data-price="11.90">36 – Großer Frucht Becher – 11,90 €</option>
                    <option value="37" data-name="Großer Amarena Becher" data-price="12.50">37 – Großer Amarena Becher – 12,50 €</option>
                    <option value="38" data-name="Großer Erdbeer Becher" data-price="12.50">38 – Großer Erdbeer Becher – 12,50 €</option>
                    <option value="39" data-name="Erdbeer-Banane Becher" data-price="10.90">39 – Erdbeer-Banane Becher – 10,90 €</option>
                    <option value="49" data-name="Hawaii Becher" data-price="8.90">49 – Hawaii Becher – 8,90 €</option>

                    <!-- Spaghetti Eis -->
                    <option value="50" data-name="Spaghetti Eis normal" data-price="6.50">50 – Spaghetti Eis normal – 6,50 €</option>
                    <option value="51" data-name="Spaghetti Eis groß" data-price="9.50">51 – Spaghetti Eis groß – 9,50 €</option>
                    <option value="52" data-name="Spaghetti Vanille" data-price="7.40">52 – Spaghetti Vanille – 7,40 €</option>
                    <option value="53" data-name="Spaghetti Erdbeere" data-price="8.90">53 – Spaghetti Erdbeere – 8,90 €</option>
                    <option value="54" data-name="Spaghetti Kiwi" data-price="8.50">54 – Spaghetti Kiwi – 8,50 €</option>

                    <!-- Schoko / Nuss / Klassiker -->
                    <option value="90" data-name="Amaretto Becher" data-price="8.50">90 – Amaretto Becher – 8,50 €</option>
                    <option value="91" data-name="Schwarzwald Becher" data-price="9.00">91 – Schwarzwald Becher – 9,00 €</option>
                    <option value="92" data-name="Malaga Becher" data-price="9.00">92 – Malaga Becher – 9,00 €</option>
                    <option value="93" data-name="Mon Chéri Becher" data-price="9.50">93 – Mon Chéri Becher – 9,50 €</option>
                    <option value="94" data-name="Raffaello Becher" data-price="9.50">94 – Raffaello Becher – 9,50 €</option>
                    <option value="96" data-name="Eierlikör Becher" data-price="8.50">96 – Eierlikör Becher – 8,50 €</option>
                    <option value="98" data-name="Nuss Becher" data-price="9.50">98 – Nuss Becher – 9,50 €</option>
                    <option value="99" data-name="Rocher Becher" data-price="9.50">99 – Rocher Becher – 9,50 €</option>
                    <option value="100" data-name="Giotto Becher" data-price="9.00">100 – Giotto Becher – 9,00 €</option>
                    <option value="101" data-name="Berg Becher" data-price="10.50">101 – Berg Becher – 10,50 €</option>
                    <option value="102" data-name="Walnuss Becher" data-price="9.50">102 – Walnuss Becher – 9,50 €</option>
                    <option value="103" data-name="Coppa Delizia" data-price="10.90">103 – Coppa Delizia – 10,90 €</option>

                    <!-- Klassische Spezialitäten -->
                    <option value="110" data-name="After-Eight Becher" data-price="8.90">110 – After-Eight Becher – 8,90 €</option>
                    <option value="111" data-name="Stracciatella Becher" data-price="7.90">111 – Stracciatella Becher – 7,90 €</option>
                    <option value="112" data-name="Tartufo Nero" data-price="9.50">112 – Tartufo Nero – 9,50 €</option>
                    <option value="113" data-name="Tartufo Bianco" data-price="9.50">113 – Tartufo Bianco – 9,50 €</option>
                    <option value="114" data-name="Hausbecher" data-price="20.00">114 – Hausbecher – 20,00 €</option>
                    <option value="116" data-name="Krokant Becher" data-price="8.50">116 – Krokant Becher – 8,50 €</option>
                    <option value="117" data-name="Schoko Becher" data-price="8.50">117 – Schoko Becher – 8,50 €</option>
                    <option value="118" data-name="Schoko Becher groß" data-price="12.00">118 – Schoko Becher groß – 12,00 €</option>
                    <option value="122" data-name="Pistazien Becher" data-price="11.50">122 – Pistazien Becher – 11,50 €</option>
                </select>
            </div>

            <div class="order-row">
                <label for="qty">Menge (Portionen)</label>
                <input type="number" id="qty" min="1" value="1">
            </div>

            <div class="order-row">
                <label>3 Kugeln Eis</label>
                <div class="flavor-row">
                    <select id="flavor1"></select>
                    <select id="flavor2"></select>
                    <select id="flavor3"></select>
                </div>
            </div>

            <div class="order-row">
                <label for="extras">Weitere Wünsche / andere Produkte</label>
                <textarea id="extras" placeholder="z.B. ohne Sahne, extra Soße, Getränke, Waffeln, Snacks usw."></textarea>
            </div>

            <div class="total-line" id="totalLine">
                Gesamt: ––
            </div>

            <button class="btn-main" id="btnSend">
                Bestellung per WhatsApp senden
            </button>
        </div>
    </section>
</main>

<footer>
    Eiscafé Sanremo – WhatsApp-Bestellungen: +49 176 72809926
</footer>

<script>
    // WhatsApp da cozinha (sem +, sem espaços)
    const PHONE_NUMBER = "4917672809926";

    // Sabores disponíveis
    const FLAVORS = [
        "Vanille", "Amarena", "Joghurt", "Nuss", "Schokolade",
        "Stracciatella", "After Eight", "Schlumpfeis", "Malaga",
        "Walnuss", "Cookies", "Zitrone", "Erdbeere", "Mango",
        "Banane", "Himbeere"
    ];

    const tableSelect = document.getElementById("tableSelect");
    const mesaInfo = document.getElementById("mesaInfo");
    const itemSelect = document.getElementById("itemSelect");
    const qtyInput   = document.getElementById("qty");
    const totalLine  = document.getElementById("totalLine");
    const extrasField= document.getElementById("extras");
    const btnSend    = document.getElementById("btnSend");

    const f1 = document.getElementById("flavor1");
    const f2 = document.getElementById("flavor2");
    const f3 = document.getElementById("flavor3");

    function fillFlavorSelect(sel){
        sel.innerHTML = '<option value="">Bitte wählen…</option>';
        FLAVORS.forEach(fl => {
            const opt = document.createElement("option");
            opt.value = fl;
            opt.textContent = fl;
            sel.appendChild(opt);
        });
    }
    [f1, f2, f3].forEach(fillFlavorSelect);

    tableSelect.addEventListener("change", () => {
        if(tableSelect.value){
            mesaInfo.textContent = "Tisch " + tableSelect.value + " – bitte hier bestellen. Vielen Dank!";
        } else {
            mesaInfo.textContent = "Bitte wählen Sie Ihre Tischnummer aus.";
        }
    });

    function getSelectedItem(){
        const opt = itemSelect.options[itemSelect.selectedIndex];
        if(!opt || !opt.value) return null;
        const price = parseFloat(opt.getAttribute("data-price") || "0");
        return {
            number: opt.value,
            name: opt.getAttribute("data-name") || "",
            price: price
        };
    }

    function formatEuro(value){
        return value.toFixed(2).replace(".", ",") + " €";
    }

    function updateTotal(){
        const item = getSelectedItem();
        let qty = parseInt(qtyInput.value, 10);
        if(isNaN(qty) || qty < 1){
            qty = 1;
            qtyInput.value = 1;
        }
        if(!item){
            totalLine.textContent = "Gesamt: ––";
            return;
        }
        const total = item.price * qty;
        totalLine.textContent = "Gesamt: " + formatEuro(total);
    }

    itemSelect.addEventListener("change", updateTotal);
    qtyInput.addEventListener("input", updateTotal);

    btnSend.addEventListener("click", function(e){
        e.preventDefault();

        const table = tableSelect.value;
        if(!table){
            alert("Bitte wählen Sie Ihre Tischnummer.");
            return;
        }
        const item = getSelectedItem();
        if(!item){
            alert("Bitte wählen Sie Ihren Eisbecher.");
            return;
        }
        let qty = parseInt(qtyInput.value, 10);
        if(isNaN(qty) || qty < 1){
            qty = 1;
            qtyInput.value = 1;
        }

        const flv1 = f1.value;
        const flv2 = f2.value;
        const flv3 = f3.value;
        if(!flv1 || !flv2 || !flv3){
            alert("Bitte wählen Sie 3 Kugeln.");
            return;
        }

        const total = item.price * qty;
        const extras = extrasField.value.trim();

        let msg = "Bestellung – Eiscafé Sanremo\n";
        msg += "Tisch: " + table + "\n\n";
        msg += "Eisbecher: " + item.number + " – " + item.name +
               " (" + formatEuro(item.price) + ")\n";
        msg += "Menge: " + qty + "\n";
        msg += "Gesamt: " + formatEuro(total) + "\n\n";
        msg += "Kugeln:\n";
        msg += "1. " + flv1 + "\n";
        msg += "2. " + flv2 + "\n";
        msg += "3. " + flv3 + "\n";
        if(extras){
            msg += "\nWeitere Wünsche / andere Produkte:\n" + extras;
        }

        const url = "https://wa.me/" + PHONE_NUMBER +
                    "?text=" + encodeURIComponent(msg);
        window.location.href = url;
    });

    // iniciar total
    updateTotal();
</script>
</body>
</html>
