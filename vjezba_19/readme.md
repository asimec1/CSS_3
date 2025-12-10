# Vježba 19 – Responzivni redizajn LEGO kluba (samo CSS)

U ovoj vježbi radimo **redizajn postojećeg LEGO projekta** koristeći isključivo CSS.  
HTML kôd (`index.html`, `gallery.html`, `contact.html`) ostaje nepromijenjen, a cilj je:

- zadržati postojeću strukturu i logiku stranica,  
- vizualno “ispeglati” sve elemente (boje, razmaci, okviri, tipografija),  
- osigurati da je stranica **responzivna**:
  - na desktopu: horizontalni izbornik, galerija u više stupaca, forma prostrana
  - na mobitelu: “hamburger” navigacija, galerija – **slika ispod slike**, kontakt forma jednostavna, u jednom stupcu.

**smiješ uređivati samo `style.css`.**

---

## 1. Pravila vježbe

1. Ne smiješ mijenjati HTML – ne dodaješ nove elemente, ne brišeš postojeće.
2. Sve promjene rade se u datoteci `style.css`.
3. Poželjno je obrisati/izmijeniti postojeće deklaracije koje smetaju novom dizajnu.
4. Na kraju rada stranica mora:
   - biti čitljiva i pregledna na **desktopu**,
   - biti jednako čitljiva na **mobitelu** (320–480 px širine),
   - imati smislen raspored elemenata (nema “spljoštenih” elemenata, preklapanja i sl.).

---

## 2. Što želimo postići ovim redizajnom

1. **Navigacija**
   - Desktop:
     - horizontali izbornik, linkovi jedan do drugoga.
   - Mobile:
     - vidljiva “traka” s tekstom npr. “☰ Meni” (hamburger),
     - ispod nje se prikazuju linkovi **jedan ispod drugog** kada se meni “otvori”.
2. **Galerija**
   - Desktop:
     - galerija u više stupaca (2–3 stupca, ovisno o širini).
   - Mobile:
     - svaka kartica/svaka slika prikazuje se **jedna ispod druge**.
3. **Kontakt forma**
   - Desktop:
     - forma organizirana u logičniji raspored (npr. ime/prezime u istom redu, ostala polja preko cijele širine),
     - vizualno više nalik “profesionalnoj” formi.
   - Mobile:
     - jedan stupac, elementi vertikalno složeni, dovoljno unutarnjeg razmaka.

---

## 3. Upute po koracima – što upisati u koji selektor

U nastavku je kostur: koji selektori su važni i koje bi deklaracije trebale ići u svaki.  
Prvo pokušajte sami, a na kraju dokumenta se nalaze “preporučene deklaracije” (jedna moguća verzija rješenja).

### 3.1 Globalno i osnovni layout

Selektori: `*`, `body`, `.page`

- `*`  
  - obavezno: `margin`, `padding`, `box-sizing`  
  - hint: koristiš isto što već imaš (globalni reset).

- `body`  
  - obavezno: `font-family`, `background-color`, `color`, `line-height`  
  - hint: koristi neku svijetlu pozadinu i tamniji tekst; `line-height` neka bude barem `1.5`.

- `.page`  
  - obavezno: `max-width`, `margin`, `padding`  
  - hint: centriraš sadržaj (`margin: 0 auto`) i dodaš malo bočnog `padding`a.

### 3.2 Header i banner

Selektori: `header`, `.banner img`

- `header`  
  - obavezno: `background-color`, `border`, `margin`, `padding`, `border-radius`  
  - hint: dodaj `box-shadow` da izgleda kao kartica.

- `.banner img`  
  - obavezno: `width: 100%`, `display: block`, `border-radius`, `border-bottom`  
  - hint: zaobli malo rubove; zadrži LEGO žuti donji rub.

### 3.3 Navigacija – “hamburger” na mobilu

HTML koristi: `<nav class="main-nav">` s `<ul><li><a>`

Selektori koje trebaš urediti:

- `.main-nav`  
  - obavezno: `margin-top`, `background-color`, `border-radius`, `position`, `overflow`  
  - hint: ovo je “kutija” za navigaciju; neka bude tamna (tamno siva ili crna).

- `.main-nav::before`  
  - obavezno: `content`, `display`, `align-items`, `justify-content`, `padding`, `color`, `font-weight`, `cursor`  
  - hint: koristi tekst `"☰ Meni"` kao sadržaj; ovo je “gornja traka” (hamburger).

- `.main-nav ul`  
  - obavezno (mobile): `list-style-type: none`, `display: none`, `flex-direction: column`, `gap`, `padding`  
  - hint: na mobitelu linkovi trebaju ići u stupac, ali se ne vide dok se meni ne “otvori”.

- `.main-nav:hover ul` i `.main-nav:focus-within ul`  
  - obavezno: `display: flex`  
  - hint: ovo je trik da se meni otvori kada korisnik pređe mišem ili klikne na područje menija.

- `.main-nav a`  
  - obavezno: `display: block`, `padding`, `background-color`, `color`, `font-weight`, `border-radius`, `border`, `font-size`  
  - hint: napravi da linkovi izgledaju kao “pilule” (border-radius: 999px).

- Pseudo klase (`:hover`, `:focus`, `:active`, `:visited`)  
  - obavezno: promjena `background-color`, `outline`, `transform` (za active), nijansa `color` (za visited).  
  - hint: ne pretjeruj, ali jasno pokaži da je link aktivan ili posjećen.

- Selektori atributa:  
  - `.main-nav a[href="gallery.html"]` → istakni boju pozadine, npr. plavu  
  - `.main-nav a[target="_blank"]` → istakni žutom; dodaj `::after` sa strelicom.

### 3.4 Glavni sadržaj (sekcije i tekst)

Selektori: `main`, `.section`, `.section-header`, `.section-header h1`, `.section-subtitle`, `.section-title`, `main p`, `.uvod`, `#osnovan`, `.lego-link`, `.image-box`, `.lego-slika`, `.image-caption`, `.raspored` i povezano.

Upute:

- `main`  
  - obavezno: `background-color`, `border`, `margin-bottom`, `padding`, `border-radius`, `box-shadow`.  
  - hint: razmisli o “kartici” s bijelom pozadinom i blagom sjenom.

- `.section-header`  
  - obavezno: `background-color`, `border-left`, `padding`, `margin-bottom`, `border-radius`.  

- `.section-header h1`, `.section-title`  
  - obavezno: `font-size`, `color`, `font-family`, `margin-bottom`, `border-bottom`, `padding-bottom`.

- `.lego-slika`  
  - obavezno: `width: 100%`, `max-width`, `border`, `border-radius`, `padding`, `box-shadow`.  
  - hint: slika mora biti responzivna, ali ne prevelika (ograniči max-width).

- `.raspored`, `.raspored th`, `.raspored td`, `.raspored tbody tr:nth-child(even)`  
  - obavezno: `width`, `border-collapse`, `padding`, `font-size`, zebra efekt.  
  - hint: lagana podloga i tanki okviri su dovoljni.

### 3.5 Galerija – slika ispod slike na mobitelu

HTML u `gallery.html` koristi `.lego-gallery`, `.lego-gallery-grid`, `.gallery-item`, `figure`, `figcaption` i `data-set` atribut.  

Selektori:

- `.lego-gallery`  
  - obavezno: `max-width`, `margin`, `padding`, `background-color`, `border-radius`, `border`, `box-shadow`.

- `.lego-gallery-grid`  
  - mobile: `display: flex`, `flex-direction: column`, `gap`  
  - hint: ovo osigurava “slika ispod slike” na mobilnim uređajima.

- `.gallery-item`  
  - obavezno: `background-color`, `border-radius`, `border`, `overflow`, `display: flex`, `flex-direction: column`, `transition` za transform/box-shadow/border-color.

- `.gallery-item img`  
  - obavezno: `width: 100%`, `display: block`.

- `.gallery-item figcaption`  
  - obavezno: `padding`, `font-size`, `color`, `text-align`.

- Selektori atributa:  
  - `.gallery-item[data-set="city"]`  
  - `.gallery-item[data-set="technic"]`  
  - `.gallery-item[data-set="friends"]`  
  - obavezno: različite boje okvira(`border-color`) po tipu seta.

- `.gallery-item:hover`  
  - obavezno: `transform` (npr. blagi `translateY`), `box-shadow`, jača `border-color`.

### 3.6 Kontakt forma – drugačiji izgled na mobile i desktop

HTML u `contact.html` koristite `.lego-contact`, `.lego-form`, `.form-row`, `.option`, `.btn-send`, razne inpute.

Selektori:

- `.lego-contact`  
  - obavezno: `margin-top`, `padding`, `background-color`, `border-radius`, `border`, `box-shadow`.  
  - hint: neka izgleda kao istaknuta kartica s plavim rubom.

- `.lego-form` (mobile)  
  - obavezno: `max-width`, `margin: 0 auto;`  
  - hint: na mobilnoj verziji ne trebaš raditi grid, samo jedan stupac.

- `.lego-form .form-row`  
  - obavezno: `margin-bottom`.  

- `.lego-form label`  
  - obavezno: `display: block`, `font-weight`, `margin-bottom`.

- `.lego-form input[...]`, `select`, `textarea`  
  - obavezno: `width: 100%`, `padding`, `border`, `border-radius`, `font`, `background-color`.  

- `.lego-form input:focus`, `select:focus`, `textarea:focus`  
  - obavezno: promjena `border-color`, `background-color`, `box-shadow`.

- `.lego-form .btn-send`  
  - obavezno: `display`, `padding`, `border`, `border-radius`, `background-color`, `color`, `font-weight`, `cursor`.  
  - hint: gumb neka izgleda kao glavni CTA (npr. zelena boja).

Za desktop verziju koristimo **media query** (vidi dolje):

- u `@media (min-width: 768px)`  
  - `.lego-form` pretvori u grid s 2 stupca (`display: grid`, `grid-template-columns: repeat(2, ...)`),  
  - odredi koje `.form-row` idu svaki u svoj stupac, a koja polja idu preko cijele širine (`grid-column`).

- u `@media (min-width: 1024px)`  
  - `.lego-contact` možeš podijeliti u 2 stupca: s lijeve strane tekst, s desne strane forma.

---

## 4. Media queries – kada što primijeniti

Trebat će barem dvije prijelomne točke:

```css
@media (min-width: 768px) {
    /* tablet i širi ekrani:
       - navigacija prelazi u horizontalni meni
       - galerija ide u 2–3 stupca
       - kontakt forma dobiva 2 stupca
    */
}

@media (min-width: 1024px) {
    /* desktop:
       - dodatno povećanje paddinga
       - još prostranija kontakt forma
       - eventualno prilagodba font-size-a
    */
}

```

U `.main-nav` u media queryju za 768px:

 - `.main-nav::before` → `display: none;` (sakrij hamburger traku)
 - `.main-nav ul` → `display: flex`, `flex-direction: row`, `justify-content: center`, `gap:` ...

U `.lego-gallery-grid` u media queryju za 768px:

 - umjesto `flex-column` → `display: grid`, `grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));, gap:` ...

U .lego-form u media queryju za 768px:

 - `display: grid;, grid-template-columns: repeat(2, minmax(0, 1fr));, column-gap, row-gap.`

U media queryju za 1024px:

 - `.lego-contact` → `display: grid, grid-template-columns` (lijevi i desni stupac),

pažnja na raspored: h2 i uvodni tekst u prvom stupcu, .lego-form u drugom.

## 5. Preporučeno rješenje (jedna moguća verzija CSS-a)

Ako želiš provjeriti svoj rad ili usporediti rješenja, ispod je jedna kompletna verzija **style.css** koja zadovoljava sve uvjete zadatka.

Napomena: Nemoj je odmah kopirati.
Prvo pokušaj samostalno napisati deklaracije na temelju gornjih smjernica, a onda provjeri što si mogao poboljšati.

```css

/* ============================
   RESET & GLOBAL
   ============================ */

/* Reset osnovnih margina i paddinga */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Osnovni stil za cijelu stranicu */
body {
    font-family: "Roboto", Arial, sans-serif;
    background-color: #f3f4f6;
    color: #1f2933;
    line-height: 1.5;
}

/* Omotač da sadržaj ne bude preko cijelog ekrana */
.page {
    max-width: 1080px;
    margin: 0 auto;
    padding: 0 1rem 2rem;
}

/* ============================
   HEADER
   ============================ */

header {
    background-color: #ffffff;
    border: 2px solid #ffcc00;
    margin: 20px 0 10px 0;
    padding: 16px;
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.06);
}

/* Banner slika unutar headera */
.banner img {
    width: 100%;
    display: block;
    border-radius: 8px;
    border-bottom: 3px solid #ffcc00;
}

/* ============================
   NAVIGACIJA – HAMBURGER NA MOBILU
   ============================ */

.main-nav {
    margin-top: 10px;
    background-color: #111827;
    border-radius: 8px;
    position: relative;
    overflow: hidden;
}

/* Hamburger traka – mobile first */
.main-nav::before {
    content: "☰ Meni";
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0.7rem 1rem;
    color: #ffffff;
    font-weight: 600;
    font-size: 0.95rem;
    cursor: pointer;
}

/* Lista u navigaciji – skrivena dok se ne "otvori" */
.main-nav ul {
    list-style-type: none;
    display: none;
    flex-direction: column;
    gap: 0.5rem;
    padding: 0.5rem 0.9rem 0.9rem;
}

/* Kad korisnik "otvori" meni (hover/focus) */
.main-nav:hover ul,
.main-nav:focus-within ul {
    display: flex;
}

.main-nav li {
    margin: 0;
}

/* Linkovi u navigaciji */
.main-nav a {
    display: block;
    padding: 0.6rem 1rem;
    text-decoration: none;
    background-color: #1f2937;
    color: #ffffff;
    font-size: 0.95rem;
    font-weight: 600;
    border-radius: 999px;
    border: 1px solid transparent;
    font-family: "Roboto", Arial, sans-serif;
}

/* PSEUDO KLASE */
.main-nav a:hover,
.main-nav a:focus {
    background-color: #374151;
    outline: 2px solid #ffffff;
    outline-offset: 2px;
}

.main-nav a:active {
    transform: scale(0.97);
}

.main-nav a:visited {
    color: #e0e0ff;
}

/* SELEKTORI ATRIBUTA NA LINKOVIMA */
.main-nav a[href="gallery.html"] {
    background-color: #0069d9;
}

.main-nav a[target="_blank"] {
    background-color: #ffc107;
    color: #000;
}

.main-nav a[target="_blank"]::after {
    content: " ↗";
    font-size: 0.85em;
}

/* ============================
   GLAVNI SADRŽAJ
   ============================ */

main {
    background-color: #ffffff;
    border: 1px solid #e5e7eb;
    margin-bottom: 20px;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 12px 30px rgba(0, 0, 0, 0.04);
}

.section {
    margin-bottom: 24px;
}

/* Header sekcije */
.section-header {
    background-color: #fff7cc;
    border-left: 4px solid #ffcc00;
    padding: 12px 18px;
    margin-bottom: 18px;
    border-radius: 8px;
}

.section-header h1 {
    font-size: 28px;
    color: #d32f2f;
    margin-bottom: 5px;
    text-transform: uppercase;
    font-family: "Lobster", "Georgia", serif;
}

.section-subtitle {
    font-size: 16px;
    color: #444444;
}

/* Naslovi sekcija */
.section-title {
    font-size: 20px;
    color: #111827;
    margin-bottom: 8px;
    border-bottom: 1px solid #e5e7eb;
    padding-bottom: 4px;
    font-family: "Lobster", "Georgia", serif;
}

main p {
    line-height: 1.6;
    margin-bottom: 10px;
    font-size: 16px;
}

.uvod {
    font-style: italic;
    font-weight: bold;
    margin-bottom: 15px;
}

/* Kartica "osnovan" */
#osnovan {
    background-color: #ffffff;
    border: 2px solid #ffcc00;
    padding: 12px 16px;
    margin-bottom: 16px;
    border-radius: 8px;
}

/* Istaknute riječi */
.vazno {
    color: #15803d;
    font-weight: bold;
}

/* Link kartica/gumb */
.lego-link {
    display: inline-block;
    margin-top: 10px;
    margin-bottom: 10px;
    text-decoration: none;
    border: 2px solid #0069d9;
    padding: 8px 16px;
    color: #0069d9;
    background-color: #ffffff;
    border-radius: 999px;
    font-weight: 600;
}

.lego-link:hover {
    background-color: #0069d9;
    color: #ffffff;
}

/* Slika i opis */
.image-box {
    margin-top: 10px;
    margin-bottom: 10px;
    text-align: center;
}

.lego-slika {
    width: 100%;
    max-width: 320px;
    border: 2px solid #e5e7eb;
    border-radius: 12px;
    padding: 4px;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.06);
}

.image-caption {
    font-size: 14px;
    color: #555555;
    margin-top: 5px;
}

.lista-tema {
    margin-left: 20px;
    margin-bottom: 10px;
    list-style-type: square;
}

.napomena {
    color: #b91c1c;
    font-size: 14px;
    margin-top: 10px;
}

/* TABLICA RASPOREDA RADIONICA */
.raspored {
    width: 100%;
    border-collapse: collapse;
    margin-top: 10px;
}

.raspored caption {
    margin-bottom: 5px;
    font-weight: bold;
}

.raspored th,
.raspored td {
    border: 1px solid #e5e7eb;
    padding: 6px;
    text-align: center;
    font-size: 14px;
}

.raspored th {
    background-color: #fff7cc;
}

/* Zebra efekt */
.raspored tbody tr:nth-child(even) {
    background-color: #f9fafb;
}

/* ============================
   KONTAKT FORMA – LEGO SUPPORT
   ============================ */

.lego-contact {
    margin-top: 2rem;
    padding: 1.75rem 1.25rem;
    background-color: #f5f9ff;
    border-radius: 12px;
    border: 2px solid #0069d9;
    box-shadow: 0 8px 20px rgba(15, 23, 42, 0.06);
}

.lego-contact h2 {
    margin-top: 0;
    margin-bottom: 0.5rem;
    font-family: "Lobster", "Georgia", serif;
}

.lego-contact p {
    margin-bottom: 1.25rem;
}

/* Layout forme – mobile: jedan stupac */
.lego-form {
    max-width: 720px;
    margin: 0 auto;
}

.lego-form .form-row {
    margin-bottom: 1rem;
}

.lego-form label {
    display: block;
    font-weight: 600;
    margin-bottom: 0.25rem;
}

/* Osnovni stil za inpute, select i textarea */
.lego-form input[type="text"],
.lego-form input[type="email"],
.lego-form input[type="password"],
.lego-form select,
.lego-form textarea {
    width: 100%;
    padding: 0.6rem 0.75rem;
    border: 1px solid #cbd5e1;
    border-radius: 6px;
    font: inherit;
    background-color: #ffffff;
}

.lego-form textarea {
    resize: vertical;
}

/* Red za checkbox/radio + labelu */
.lego-form .option {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 0.25rem;
}

.lego-form .option input[type="checkbox"],
.lego-form .option input[type="radio"] {
    width: auto;
}

/* :FOCUS – aktivno polje */
.lego-form input:focus,
.lego-form select:focus,
.lego-form textarea:focus {
    border-color: #007bff;
    background-color: #eef6ff;
    outline: none;
    box-shadow: 0 0 0 2px rgba(0, 123, 255, 0.25);
}

/* :CHECKED – checkbox i radio */
.lego-form input[type="checkbox"]:checked + label,
.lego-form input[type="radio"]:checked + label {
    font-weight: 700;
    color: #1a7f1a;
}

/* :DISABLED i :ENABLED */
.lego-form input:disabled,
.lego-form select:disabled,
.lego-form textarea:disabled {
    background-color: #eeeeee;
    color: #666666;
    cursor: not-allowed;
}

/* GUMB – :hover */
.lego-form .btn-send {
    display: inline-block;
    padding: 0.6rem 1.7rem;
    border: none;
    border-radius: 999px;
    background-color: #22c55e;
    color: #ffffff;
    font-weight: 700;
    cursor: pointer;
    font-size: 1rem;
}

.lego-form .btn-send:hover {
    background-color: #16a34a;
}

/* ============================
   GALERIJA SLIKA
   ============================ */

.lego-gallery {
    max-width: 900px;
    margin: 2rem auto;
    padding: 1.5rem 1.5rem;
    background-color: #ffffff;
    border-radius: 12px;
    border: 1px solid #e5e7eb;
    box-shadow: 0 8px 22px rgba(0, 0, 0, 0.05);
}

.lego-gallery h2 {
    margin-top: 0;
    margin-bottom: 0.5rem;
    font-family: "Lobster", "Georgia", serif;
}

.lego-gallery p {
    margin-bottom: 1.5rem;
}

/* MOBILE FIRST – SLIKE JEDNA ISPOD DRUGE */
.lego-gallery-grid {
    display: flex;
    flex-direction: column;
    gap: 1.25rem;
}

/* Kartica za svaki LEGO set */
.gallery-item {
    background-color: #fafafa;
    border-radius: 12px;
    border: 2px solid #e0e0e0;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    transition:
        transform 0.15s ease,
        box-shadow 0.15s ease,
        border-color 0.15s ease;
}

.gallery-item img {
    width: 100%;
    display: block;
}

/* Tekst ispod slike */
.gallery-item figcaption {
    padding: 0.75rem 1rem 1rem;
    font-size: 0.9rem;
    color: #444444;
    text-align: center;
}

/* Selektori atributa – boja okvira po tipu seta */
.gallery-item[data-set="city"] {
    border-color: steelblue;
}

.gallery-item[data-set="technic"] {
    border-color: darkorange;
}

.gallery-item[data-set="friends"] {
    border-color: deeppink;
}

/* Malo zaobljeni kutovi za .jpg slike */
.gallery-item img[src$=".jpg"] {
    border-radius: 0;
}

/* Hover efekt – moderan “card” */
.gallery-item:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 18px rgba(0, 0, 0, 0.18);
    border-color: #0069d9;
    cursor: pointer;
}

/* ============================
   FOOTER
   ============================ */

footer {
    text-align: center;
    font-size: 0.8rem;
    color: #6b7280;
    margin-top: 0.75rem;
}

/* ============================
   MEDIA QUERIES – TABLET / DESKTOP
   ============================ */

/* TABLET I ŠIRE */
@media (min-width: 768px) {

    .page {
        padding: 0 1.5rem 2.25rem;
    }

    main {
        padding: 24px;
    }

    /* Navigacija – klasični horizontalni meni */
    .main-nav::before {
        display: none;
    }

    .main-nav ul {
        display: flex;
        flex-direction: row;
        justify-content: center;
        gap: 0.75rem;
        padding: 0.6rem 0.75rem;
    }

    .main-nav a {
        min-width: 7rem;
        text-align: center;
        font-size: 1rem;
    }

    /* Kontakt forma – 2 stupca za prva dva polja */
    .lego-contact {
        padding: 2rem 2rem;
    }

    .lego-form {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
        column-gap: 1.25rem;
        row-gap: 1rem;
    }

    .lego-form .form-row {
        margin-bottom: 0;
    }

    /* Ime i prezime dijele red */
    .lego-form .form-row:nth-child(1),
    .lego-form .form-row:nth-child(2) {
        grid-column: span 1;
    }

    /* Ostala polja preko cijele širine */
    .lego-form .form-row:nth-child(n + 3) {
        grid-column: 1 / -1;
    }

    .lego-form .btn-send {
        justify-self: flex-start;
    }

    /* Galerija – grid sa više stupaca */
    .lego-gallery-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 1.5rem;
    }
}

/* DESKTOP */
@media (min-width: 1024px) {

    .page {
        padding: 0 2rem 2.5rem;
    }

    main {
        padding: 26px 28px;
    }

    .section {
        margin-bottom: 28px;
    }

    .lego-contact {
        display: grid;
        grid-template-columns: minmax(0, 1.4fr) minmax(0, 2fr);
        column-gap: 2rem;
        align-items: flex-start;
    }

    .lego-contact h2,
    .lego-contact p {
        grid-column: 1;
    }

    .lego-contact .lego-form {
        grid-column: 2;
    }
}
```