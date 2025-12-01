# Vježba 18 – Nova galerija (CSS Grid, figure/figcaption, border, tekst ispod slike)

U ovoj vježbi mijenjamo postojeću LEGO galeriju i radimo **novi layout** koji koristi:

- novu HTML strukturu (`figure` + `figcaption`)  
- **CSS Grid** umjesto starog flex layouta  
- modernije okvire (border, zaobljeni rubovi, hover efekt)  
- tekst ispod svake slike (naziv LEGO seta)

Radite u datotekama:

- `gallery.html`
- `style.css`

---

## 1. Zamjena HTML strukture galerije

1. Otvorite `gallery.html`.
2. Pronađite postojeću sekciju:

   ```html
   <section class="lego-gallery">
       ...
   </section>
3. Obrišite samo unutrašnji sadržaj te sekcije (stare div.gallery-row i <img> elemente).
4. Unutar <section class="lego-gallery"> zalijepite sljedeći novi HTML kod:

<h2>Galerija LEGO setova</h2>
<p>Ovdje možete vidjeti nekoliko LEGO setova iz naše kolekcije.</p>

```html
<div class="lego-gallery-grid">
    <figure class="gallery-item" data-set="city">
        <img src="img/lego_city_1.jpg" alt="LEGO City policijska postaja">
        <figcaption>LEGO City policijska postaja</figcaption>
    </figure>

    <figure class="gallery-item" data-set="technic">
        <img src="img/lego_technic_1.jpg" alt="LEGO Technic trkaći auto">
        <figcaption>LEGO Technic trkaći auto</figcaption>
    </figure>

    <figure class="gallery-item" data-set="friends">
        <img src="img/lego_friends_1.jpg" alt="LEGO Friends kafić">
        <figcaption>LEGO Friends kafić</figcaption>
    </figure>

    <figure class="gallery-item" data-set="city">
        <img src="img/lego_city_2.jpg" alt="LEGO City vatrogasci">
        <figcaption>LEGO City vatrogasci</figcaption>
    </figure>

    <figure class="gallery-item" data-set="technic">
        <img src="img/lego_technic_2.jpg" alt="LEGO Technic helikopter">
        <figcaption>LEGO Technic helikopter</figcaption>
    </figure>

    <figure class="gallery-item" data-set="friends">
        <img src="img/lego_friends_2.jpg" alt="LEGO Friends kuća">
        <figcaption>LEGO Friends kuća</figcaption>
    </figure>
</div>
```

## 2. Uklanjanje starog CSS-a za galeriju

1. Otvorite style.css.
2. Pronađite dio:

```css
        /* ============================
        GALERIJA SLIKA
        ============================ */

        .lego-gallery {
            ...
        }

        .lego-gallery h2 {
            ...
        }

...

```

3. Obrišite cijeli stari blok za galeriju (od komentara GALERIJA SLIKA do zadnjeg pravila koje se odnosi na .lego-gallery).

## 3. Dodavanje novog CSS kostura (studenti popunjavaju deklaracije)

U style.css dodajte novi blok za galeriju.
Ne pišite deklaracije odmah – prvo zalijepite kostur ispod:

```css
/* ============================
   GALERIJA SLIKA – VJEŽBA 18
   ============================ */

/* 1) Kontejner galerije – širina, margine, padding, pozadina, border, shadow */
.lego-gallery {
    /* TODO */
}

.lego-gallery h2 {
    /* TODO */
}

.lego-gallery p {
    /* TODO */
}

/* 2) GRID raspored – display: grid, broj stupaca, razmak (gap) */
.lego-gallery-grid {
    /* TODO */
}

/* 3) Svaki LEGO set kao "kartica" – pozadina, border, radius, flex kolona, transition */
.gallery-item {
    /* TODO */
}

/* Slika – širina 100%, block element */
.gallery-item img {
    /* TODO */
}

/* Tekst ispod slike – padding, veličina fonta, centriranje */
.gallery-item figcaption {
    /* TODO */
}

/* 4) Selektori atributa – različita boja okvira za tip seta (city, technic, friends) */
.gallery-item[data-set="city"] {
    /* TODO */
}

.gallery-item[data-set="technic"] {
    /* TODO */
}

.gallery-item[data-set="friends"] {
    /* TODO */
}

/* 5) Hover efekt – blagi pomak, sjena, promjena boje ruba */
.gallery-item:hover {
    /* TODO */
}

```

## 4. Smjernice (što biste trebali postaviti u CSS-u)


Nemate gotove deklaracije – sami trebate odabrati vrijednosti.
Ovo su smjernice što bi pojedini selektor trebao otprilike raditi:

.lego-gallery

- ograničiti širinu (npr. max-width)
- centrirati na stranici (margin)
- dodati unutarnji razmak (padding)
- postaviti svijetlu pozadinu
- dodati border-radius i suptilan box-shadow

.lego-gallery-grid

- uključiti CSS Grid → display: grid
- definirati 2–3 stupca (npr. grid-template-columns: repeat(...);)
- postaviti razmak između elemenata (gap)

.gallery-item

- postaviti pozadinsku boju kartice
- definirati border (boja, debljina, zaobljeni rubovi)
- koristiti display: flex + flex-direction: column (slika + tekst)
- dodati transition za transform, box-shadow ili border-color

.gallery-item img

- širina 100% kartice
- display: block

.gallery-item figcaption

- padding oko teksta
- manji font
- tekst centriran

.gallery-item[data-set="..."]

- drugačija boja okvira za:
- city (npr. plava)
- technic (npr. narančasta)
- friends (npr. ružičasta)

.gallery-item:hover

- blagi pomak kartice prema gore (transform: translateY(...))
- jača sjena (box-shadow)
- promjena boje okvira (npr. primarna boja projekta)