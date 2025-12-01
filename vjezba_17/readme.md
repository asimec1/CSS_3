# Vježba – Box model, border, padding, margin, boje i fontovi (LEGO klub)

U ovoj vježbi nastavljamo raditi na postojećem projektu **LEGO klub**.

Radite na datotekama:

- `index.html`
- `contact.html`
- `gallery.html`
- `style.css`

(Profesor će vam dati link na GitHub repozitorij.)

Cilj je:

- razumjeti kako **border, padding i margin** utječu na izgled elemenata  
- urediti okvire (kartice) na stranici tako da budu pregledniji i vizualno privlačniji  
- primijeniti **Google font** za cijelu stranicu i odabrati odgovarajući font za naslove  
- dosljedno koristiti **paletu boja** na svim stranicama

---

## 1. Priprema – Google Fonts

1. Otvorite stranicu **[Google Fonts](https://fonts.google.com/)**.  
2. Odaberite jedan **glavni font za tekst** (npr. `Roboto`, `Open Sans`, `Poppins`…)  
3. Odaberite jedan **font za naslove** (može biti isti, ali s debljim rezom ili dekorativniji font, npr. `Lobster`, `Fredoka`, `Montserrat` bold, itd.)  
4. U svakom HTML dokumentu (`index.html`, `contact.html`, `gallery.html`) u `<head>` dio dodajte `<link>` za odabrane fontove, npr.:

```html
   <link rel="stylesheet"
         href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Lobster&display=swap">
```

5. U datoteci **style.css** 
    - postavite glavni font za cijelo tijelo dokumenta:

```css
body {
    font-family: "Roboto", Arial, sans-serif;
    background-color: #f0f0f0;
}
```
    - za naslove (npr. .section-header h1, .section-title, h2 u kontakt i galeriji) postavite drugi font:

        ```css
        .section-header h1,
        .section-title,
        .lego-contact h2,
        .lego-gallery h2 {
            font-family: "Lobster", "Georgia", serif;
        }

        ```

**Cilj: svi tekstovi koriste isti osnovni font, a naslovi imaju poseban, prepoznatljiv stil.**


## 2. Dorada okvira – border, padding, margin

### 2.1. Kartice na početnoj stranici (index.html)

Radite u style.css.

1. Pronađite stilove za sekcije i posebne elemente: 
    - .section-header
    - #osnovan
    - .lego-link
    - .image-box / .lego-slika
    - .raspored (tablica)

2. Doradite ih tako da:

    - dodate ili prilagodite border
        - debljina (border-width), stil (border-style – solid, dashed, dotted) i boja (border-color)
    - podesite unutarnji razmak (padding) da sadržaj “diše”
    - podesite vanjski razmak (margin) između blokova (sekcija)

Primjeri smjernica (ne morate ih kopirati doslovno):

    - #osnovan neka izgleda kao “kartica” (card):

        ```css     
        #osnovan {
            background-color: #ffffff;
            border: 2px solid #ffcc00;
            padding: 12px 16px;
            margin-bottom: 16px;
            border-radius: 6px;
        }
        ```
    - .lego-link neka izgleda kao gumb:

        ```css  
        .lego-link {
            display: inline-block;
            padding: 8px 16px;
            margin: 10px 0;
            border: 2px solid #0069d9;
            border-radius: 4px;
        }
        ```

### 2.2. Kontakt forma (contact.html)

U style.css već postoji dio za kontakt formu (.lego-contact, .lego-form, .form-row…).

**Zadatak:**

1. Neka cijela sekcija .lego-contact izgleda kao istaknuta kartica:
    
    - prilagodite border, padding, margin, background-color
    - dodajte blagi border-radius (npr. 8px)

2. Neka pojedina polja forme budu jasnije odvojena:

    - povećajte margin-bottom u .lego-form .form-row
    - pojačajte border na poljima (input, select, textarea) ili promijenite boju ruba

3. Gumb .btn-send:
    
    - neka ima konzistentnu boju iz palete (primarna boja stranice)
    - dodajte :hover efekt (npr. tamnija nijansa, mala promjena sjene)

### 2.3. Galerija slika (gallery.html)

U style.css postoji dio:
    
    - .lego-gallery
    - .lego-gallery .gallery-row
    - .lego-gallery img
    - selektori atributa za data-set="city", data-set="technic", data-set="friends"


1. Uredite okvire oko slika:

    - prilagodite border-width, border-style i border-color
    - zadržite razliku po data-set atributu (različite boje okvira za city/technic/friends)

2. Podesite padding i margin oko galerije:

    - neka .lego-gallery ima dovoljno unutarnjeg razmaka (padding)
    - neka se odvoji od ostatka sadržaja (margin-top, margin-bottom)

3. Dodajte/pojačajte hover efekt na slikama:

    - blagi transform: scale(...)
    - box-shadow
    - cursor: pointer;

## 3. Boje i tipografija

1. Definirajte jednostavnu paletu boja za cijeli projekt (npr.):

    - primarna: plava (linkovi, gumbi)
    - sekundarna: žuta (naglasci, okviri)
    - neutralne: bijela pozadina, tamnosivi tekst

2. Provjerite da:
    
    - header, main, .section-header, .lego-contact, .lego-gallery, gumbi, linkovi koriste boje iz iste palete
    - nema “slučajnih” boja koje ne pripadaju paleti

3. Provjerite fontove:

    - body → glavni Google font
    - naslovi (h1, h2, .section-title, .section-header h1) → naslovni font
    - izbjegavajte previše različitih fontova