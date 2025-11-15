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
        header h1 { font-size: 1.6rem; margin-bottom: .3rem; }
        header p { font-size: .9rem; }
        .mesa-info {
            background: #fff3cd;
            color: #856404;
            padding: .6rem 1rem;
            text-align: center;
            font-size: .95rem;
        }
        main {
            max-width: 1100px;
            margin: 0 auto;
            padding: 1rem;
        }
        section {
            margin-bottom: 1.8rem;
        }
        h2 {
            font-size: 1.3rem;
            margin-bottom: .5rem;
            border-bottom: 2px solid #d4232b;
            display: inline-block;
            padding-bottom: .2rem;
        }
        h3 {
            font-size: 1.1rem;
            margin: .8rem 0 .4rem;
        }
        .sabores-lista {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: .3rem .8rem;
            padding: .6rem 0;
        }
        .sabores-lista label {
            display: flex;
            align-items: center;
            gap: .3rem;
            font-size: .9rem;
        }
        .aviso-tres-bolas {
            font-size: .9rem;
            color: #d4232b;
            margin-top: .4rem;
        }
        .btn-whatsapp {
            display: inline-block;
            margin-top: .8rem;
            padding: .7rem 1.3rem;
            background: #25D366;
            color: #fff;
            border-radius: 4px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1rem;
            text-align: center;
        }
        .btn-whatsapp:active { transform: scale(0.98); }
        .extras {
            width: 100%;
            min-height: 60px;
            margin-top: .4rem;
            padding: .4rem;
            font-size: .9rem;
        }
        .grid-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1rem;
        }
        .card {
            background: #fff;
            border-radius: 6px;
            overflow: hidden;
            box-shadow: 0 2px 6px rgba(0,0,0,.08);
            display: flex;
            flex-direction: column;
        }
        .card img {
            width: 100%;
            height: 150px;
            object-fit: cover;
        }
        .card-body {
            padding: .7rem .8rem 1rem;
            font-size: .9rem;
        }
        .card-body h4 {
            margin-bottom: .3rem;
            font-size: .95rem;
        }
        .card-body p {
            font-size: .85rem;
            margin-bottom: .3rem;
        }
        .card-body .price {
            font-weight: bold;
            color: #d4232b;
        }
        footer {
            text-align: center;
            font-size: .8rem;
            padding: 1rem 0 2rem;
            color: #777;
        }
        @media (min-width: 768px) {
            header h1 { font-size: 2rem; }
        }
        .table-select-wrapper {
            margin: .6rem auto 0.2rem;
            text-align: center;
        }
        .table-select-wrapper select {
            padding: 0.3rem 0.6rem;
            font-size: 0.9rem;
            border-radius: 6px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
<header>
    <h1>Eiscafé Sanremo</h1>
    <p>Digitale Speisekarte – Bestellung direkt per WhatsApp</p>
</header>

<div class="mesa-info" id="mesaInfo">
    Bitte wählen Sie Ihre Tischnummer aus.
</div>
<div class="table-select-wrapper">
    <label for="tableSelect">Tisch:</label>
    <select id="tableSelect">
        <option value="">– Nummer wählen –</option>
        <!-- Mesas 1 a 33 -->
        <option value="1">1</option><option value="2">2</option><option value="3">3</option>
        <option value="4">4</option><option value="5">5</option><option value="6">6</option>
        <option value="7">7</option><option value="8">8</option><option value="9">9</option>
        <option value="10">10</option><option value="11">11</option><option value="12">12</option>
        <option value="13">13</option><option value="14">14</option><option value="15">15</option>
        <option value="16">16</option><option value="17">17</option><option value="18">18</option>
        <option value="19">19</option><option value="20">20">20</option><option value="21">21</option>
        <option value="22">22</option><option value="23">23</option><option value="24">24</option>
        <option value="25">25</option><option value="26">26</option><option value="27">27</option>
        <option value="28">28</option><option value="29">29</option><option value="30">30</option>
        <option value="31">31</option><option value="32">32</option><option value="33">33</option>
    </select>
</div>

<main>
    <section id="gelato-builder">
        <h2>Wähle dein Eis – 3 Kugeln</h2>
        <p style="font-size:.9rem; margin-top:.3rem;">
            Bitte wählen Sie genau <strong>3 Sorten</strong>. Danach können Sie unten Ihre Bestellung per WhatsApp senden.
        </p>

        <h3>Milcheis</h3>
        <div class="sabores-lista" id="sabores-milch">
            <label><input type="checkbox" value="Vanille"> Vanille</label>
            <label><input type="checkbox" value="Amarena"> Amarena</label>
            <label><input type="checkbox" value="Joghurt"> Joghurt</label>
            <label><input type="checkbox" value="Nuss"> Nuss</label>
            <label><input type="checkbox" value="Schokolade"> Schokolade</label>
            <label><input type="checkbox" value="Stracciatella"> Stracciatella</label>
            <label><input type="checkbox" value="After Eight"> After Eight</label>
            <label><input type="checkbox" value="Schlumpfeis"> Schlumpfeis</label>
            <label><input type="checkbox" value="Malaga"> Malaga</label>
            <label><input type="checkbox" value="Walnuss"> Walnuss</label>
            <label><input type="checkbox" value="Cookies"> Cookies</label>
        </div>

        <h3>Fruchteis</h3>
        <div class="sabores-lista" id="sabores-frucht">
            <label><input type="checkbox" value="Zitrone"> Zitrone</label>
            <label><input type="checkbox" value="Erdbeere"> Erdbeere</label>
            <label><input type="checkbox" value="Mango"> Mango</label>
            <label><input type="checkbox" value="Banane"> Banane</label>
            <label><input type="checkbox" value="Himbeere"> Himbeere</label>
        </div>

        <div class="aviso-tres-bolas" id="avisoBolas">
            0 von 3 Kugeln gewählt.
        </div>

        <h3>Weitere Wünsche / Extras</h3>
        <textarea class="extras" id="extras" placeholder="z.B. Sahne, Soße, Becher-Nummer, ohne Nüsse, usw."></textarea>

        <a href="#" class="btn-whatsapp" id="btnWhatsApp">Per WhatsApp bestellen</a>
    </section>

    <section>
        <h2>Beliebte Becher (mit Fotos)</h2>
        <p style="font-size:.9rem; margin-top:.3rem; margin-bottom:.8rem;">
            Hier können Sie Beispiel-Fotos Ihrer Becher einfügen. Ersetzen Sie einfach die Bilddateien im Ordner <code>images</code> auf Ihrem Server.
        </p>
        <div class="grid-cards">
            <article class="card">
                <img src="images/pinocchio.jpg" alt="Pinocchio Eisbecher">
                <div class="card-body">
                    <h4>Pinocchio Becher</h4>
                    <p>Beliebter Kinderbecher mit bunter Dekoration.</p>
                    <p class="price">5,10 €</p>
                </div>
            </article>
            <article class="card">
                <img src="images/spaghetti-eis.jpg" alt="Spaghetti Eis">
                <div class="card-body">
                    <h4>Spaghetti Eis</h4>
                    <p>Vanilleeis mit Erdbeersoße und weißen Schokoraspeln.</p>
                    <p class="price">ab 6,50 €</p>
                </div>
            </article>
            <article class="card">
                <img src="images/banana-split.jpg" alt="Banana Split">
                <div class="card-body">
                    <h4>Banana Split</h4>
                    <p>Eis, Bananenscheiben, Soße und Sahne.</p>
                    <p class="price">10,00 €</p>
                </div>
            </article>
            <article class="card">
                <img src="images/exotischer-becher.jpg" alt="Exotischer Becher">
                <div class="card-body">
                    <h4>Exotischer Becher</h4>
                    <p>Gemischtes Eis mit tropischen Früchten.</p>
                    <p class="price">12,00 €</p>
                </div>
            </article>
        </div>
    </section>
</main>

<footer>
    Eiscafé Sanremo – Bestellung per WhatsApp: +49 176 72809926
</footer>

<script>
    const mesaInfo = document.getElementById('mesaInfo');
    const tableSelect = document.getElementById('tableSelect');

    tableSelect.addEventListener('change', () => {
        if (tableSelect.value) {
            mesaInfo.textContent = 'Tisch ' + tableSelect.value + ' – bitte hier bestellen. Vielen Dank!';
        } else {
            mesaInfo.textContent = 'Bitte wählen Sie Ihre Tischnummer aus.';
        }
    });

    const checkboxes = document.querySelectorAll('#sabores-milch input, #sabores-frucht input');
    const aviso = document.getElementById('avisoBolas');

    function updateCount() {
        const checked = Array.from(checkboxes).filter(c => c.checked);
        if (checked.length > 3) {
            const last = checked.pop();
            last.checked = false;
            return updateCount();
        }
        aviso.textContent = checked.length + ' von 3 Kugeln gewählt.';
        if (checked.length === 3) {
            aviso.style.color = '#28a745';
        } else {
            aviso.style.color = '#d4232b';
        }
    }

    checkboxes.forEach(cb => cb.addEventListener('change', updateCount));
    updateCount();

    document.getElementById('btnWhatsApp').addEventListener('click', function(e) {
        e.preventDefault();
        const table = tableSelect.value;
        if (!table) {
            alert('Bitte wählen Sie Ihre Tischnummer.');
            return;
        }
        const checked = Array.from(checkboxes).filter(c => c.checked);
        if (checked.length !== 3) {
            alert('Bitte wählen Sie genau 3 Kugeln.');
            return;
        }
        const extras = document.getElementById('extras').value.trim();
        let msg = 'Bestellung – Eiscafé Sanremo%0A';
        msg += 'Tisch: ' + table + '%0A';
        msg += '%0AKugeln:%0A';
        checked.forEach((c, i) => {
            msg += (i+1) + '. ' + c.value + '%0A';
        });
        if (extras) {
            msg += '%0AWeitere Wünsche:%0A' + extras.replace(/(\r\n|\n|\r)/g, '%0A');
        }
        const phone = '4917672809926'; // WhatsApp número sem +
        const url = 'https://wa.me/' + phone + '?text=' + msg;
        window.location.href = url;
    });
</script>
</body>
</html>
