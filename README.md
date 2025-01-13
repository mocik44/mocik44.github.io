<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="author" content="Maciej Hajnosz">
    <title>Funkcjonalna Lista Zakupów</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <img src="zakupy.jpeg" alt="zakupy">
        <div>
        <h1>Witamy na Funkcjonalnej Liście Zakupów!</h1>
        <p>Zorganizuj swoje zakupy szybko i łatwo.</p>
    </div>
    </header>
    <nav>
        <section class="panel-formularza">
            <h2>Dodaj Przedmioty</h2>
            <form id="formularz-zakupow">
                <input type="text" id="pole-przedmiotu" placeholder="Dodaj przedmiot..." required>
                <select id="wybor-kategorii">
                    <option value="warzywa">Warzywa</option>
                    <option value="owoce">Owoce</option>
                    <option value="nabial">Nabiał</option>
                    <option value="innes">Inne produkty spożywcze</option>
                    <option value="narzedzia">Narzędzia</option>
                    <option value="inne">Inne</option>
                </select>
                <button type="submit">Dodaj</button>
            </form>
        </section>
        <section class="panel-listy">
            <h2>Lista Zakupów</h2>
            <div class="kategoria">
                <h3>Warzywa</h3>
                <ul id="lista-warzywa"></ul>
            </div>
            <div class="kategoria">
                <h3>Owoce</h3>
                <ul id="lista-owoce"></ul>
            </div>
            <div class="kategoria">
                <h3>Nabiał</h3>
                <ul id="lista-nabial"></ul>
            </div>
            <div class="kategoria">
                <h3>Inne produkty spożywcze</h3>
                <ul id="lista-innes"></ul>
            </div>
            <div class="kategoria">
                <h3>Narzędzia</h3>
                <ul id="lista-narzedzia"></ul>
            </div>
            <div class="kategoria">
                <h3>Inne</h3>
                <ul id="lista-inne"></ul>
            </div>
        </section>
    </nav>
    <footer>
        <p>Dziękujemy za skorzystanie z naszej usługi</p>
        <p>Numer albumu: 132533</p>
    </footer>
    <script src="zakupy.js">
    </script>
</body>
</html>
