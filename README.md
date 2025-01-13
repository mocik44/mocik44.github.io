<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="author" content="Maciej Hajnosz">
    <title>Funkcjonalna Lista Zakupów</title>
    <link rel="stylesheet" href="style.css">
    <style>
        body {
    font-family: Arial, sans-serif;
    background: linear-gradient(to bottom, #a8dadc, #457b9d);
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 1300px;
}
header {
    width: 100%;
    background-color: #007bff;
    color: white;
    text-align: center;
    padding: 10px 0;
    display: flex;
    align-items: center;
    justify-content: center;
}
header img {
    width: 160px;
    height: 120px;
    margin-right: 15px;
}
nav {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    margin-top: 20px;
    width: 90%;
    max-width: 1200px;
}
.panel-formularza {
    flex: 1;
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-right: 20px;
}
.panel-listy {
    flex: 2;
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
h1, h2 {
    text-align: center;
    color: #333;
}
form {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}
input[type="text"], select {
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    outline: none;
}
button {
    padding: 10px;
    background-color: #28a745;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 4px;
    transition: background-color 0.3s;
}
button:hover {
    background-color: #218838;
}
.kategoria {
    margin-bottom: 20px;
}
ul {
    list-style: none;
    padding: 0;
}
li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 10px;
    background-color: #f9f9f9;
}
li.ukonczony {
    text-decoration: line-through;
    background-color: #d4edda;
}
.usun {
    background-color: #dc3545;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
}
.usun:hover {
    background-color: #c82333;
}
footer {
    width: 100%;
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px 0;
    margin-top: auto;
}

    </style>
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
    <script>
        const formularzZakupow = document.getElementById('formularz-zakupow');
const polePrzedmiotu = document.getElementById('pole-przedmiotu');
const wyborKategorii = document.getElementById('wybor-kategorii');

const kategorie = {
    warzywa: document.getElementById('lista-warzywa'),
    owoce: document.getElementById('lista-owoce'),
    nabial: document.getElementById('lista-nabial'),
    innes: document.getElementById('lista-innes'),
    narzedzia: document.getElementById('lista-narzedzia'),
    inne: document.getElementById('lista-inne')
};

formularzZakupow.addEventListener('submit', function(zdarzenie) {
    zdarzenie.preventDefault();

    const tekstPrzedmiotu = polePrzedmiotu.value.trim();
    const kategoria = wyborKategorii.value;

    if (tekstPrzedmiotu === '' || !kategorie[kategoria]) return;

    const elementListy = document.createElement('li');
    elementListy.innerHTML = `
        <span>${tekstPrzedmiotu}</span>
        <button class="usun">Usuń</button>
    `;

    elementListy.addEventListener('click', function() {
        elementListy.classList.toggle('ukonczony');
    });

    elementListy.querySelector('.usun').addEventListener('click', function(zdarzenie) {
        zdarzenie.stopPropagation();
        elementListy.remove();
    });

    kategorie[kategoria].appendChild(elementListy);
    polePrzedmiotu.value = '';
});
    </script>
</body>
</html>
