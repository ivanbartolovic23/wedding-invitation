# Digitalna Pozivnica za Vjenčanje - Iva i Ivan 💍

Minimalistička digitalna pozivnica za vjenčanje sa RSVP formularom i Google Sheets integracijom.

## 📋 Sadržaj

- **Stranica 1**: Naslovna pozivnica "Two Less Fish in the Sea"
- **Stranica 2**: RSVP formular za potvrdu dolaska
- **Stranica 3**: Detalji vjenčanja (datum, vrijeme, lokacija)

## 🚀 Postavljanje

### Korak 1: Kreiranje GitHub računa i repozitorija

1. Idite na [github.com](https://github.com) i kreirajte besplatan račun
2. Kliknite na "+" u gornjem desnom kutu → "New repository"
3. Nazovite repozitorij: `wedding-invitation` (ili bilo koje ime)
4. Označite "Public"
5. Kliknite "Create repository"

### Korak 2: Upload datoteka

1. U vašem novom repozitoriju, kliknite "uploading an existing file"
2. Povucite `index.html` datoteku ili kliknite "choose your files"
3. Kliknite "Commit changes"

### Korak 3: Aktiviranje GitHub Pages

1. U repozitoriju idite na **Settings** → **Pages**
2. Pod "Source" odaberite **main** branch
3. Kliknite **Save**
4. Nakon nekoliko minuta, vaša stranica će biti dostupna na:
   ```
   https://VASE-KORISNICKO-IME.github.io/wedding-invitation/
   ```

### Korak 4: Postavljanje Google Sheets za RSVP odgovore

#### 4.1 Kreiranje Google Sheet-a

1. Idite na [sheets.google.com](https://sheets.google.com)
2. Kreirajte novi spreadsheet: "Vjenčanje - RSVP Odgovori"
3. U prvom redu dodajte zaglavlja:
   ```
   Vrijeme | Dolazak | Gosti | Broj gostiju | Napomene
   ```

#### 4.2 Kreiranje Google Apps Script

1. U Google Sheet-u, idite na **Extensions** → **Apps Script**
2. Obrišite postojeći kod
3. Kopirajte kod iz `google-script.js` datoteke
4. Kliknite **Save** (ikona diskete)
5. Kliknite **Deploy** → **New deployment**
6. Kliknite na ikonu zupčanika → odaberite **Web app**
7. Postavke:
   - **Description**: Wedding RSVP
   - **Execute as**: Me
   - **Who has access**: Anyone
8. Kliknite **Deploy**
9. **Kopirajte Web app URL** (izgleda kao: `https://script.google.com/macros/s/...../exec`)

#### 4.3 Povezivanje sa HTML stranicom

1. Otvorite `index.html` datoteku
2. Pronađite liniju (oko linije 330):
   ```javascript
   const GOOGLE_SCRIPT_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL_HERE';
   ```
3. Zamijenite sa vašim URL-om:
   ```javascript
   const GOOGLE_SCRIPT_URL = 'https://script.google.com/macros/s/...../exec';
   ```
4. Spremite i ponovno uploadajte na GitHub

## 📱 Kako koristiti

### Slanje pozivnice gostima

Pošaljite link gostima:
```
https://VASE-KORISNICKO-IME.github.io/wedding-invitation/
```

### Praćenje odgovora

Svi odgovori će se automatski spremati u vaš Google Sheet sa sljedećim informacijama:
- Vrijeme odgovora
- Dolazak (Da/Ne)
- Imena gostiju
- Broj gostiju
- Dodatne napomene (alergije, komentari)

## 🎨 Prilagodba

### Promjena teksta

Otvorite `index.html` i promijenite:

**Naslovna stranica** (linija ~310):
```html
<div class="couple-names">Iva i Ivan</div>
<div class="wedding-date">are getting married on 27.6.2026</div>
```

**Detalji** (linija ~450):
```html
<div class="details-section">
    <h3>📅 Datum</h3>
    <p>27.6.2026.</p>
</div>
```

### Promjena boja

U `<style>` sekciji promijenite:
```css
background-color: #f5f0eb;  /* Bež pozadina */
color: #2c2c2c;             /* Crna boja teksta */
```

## 📊 Pregled statistike

U Google Sheet-u možete dodati formule za automatsko brojanje:

**Ukupan broj gostiju koji dolaze:**
```
=SUMIF(B:B,"Da",D:D)
```

**Ukupan broj gostiju koji ne dolaze:**
```
=SUMIF(B:B,"Ne",D:D)
```

**Postotak potvrđenih:**
```
=COUNTIF(B:B,"Da")/COUNTA(B:B)*100
```

## 🔧 Testiranje

Prije slanja gostima:
1. Otvorite stranicu u browseru
2. Ispunite RSVP formular
3. Provjerite da li se podaci pojavljuju u Google Sheet-u
4. Testirajte na mobitelu i računalu

## 💡 Savjeti

- **Backup**: Redovno kopirajte Google Sheet
- **Rok za odgovor**: Postavite jasan rok u pozivnici
- **Podsjetnik**: Pošaljite podsjetnik gostima koji nisu odgovorili
- **Privatnost**: Link možete zaštititi tako da ga dijelite samo pozvanim gostima

## 🆘 Rješavanje problema

### Forma ne šalje podatke
- Provjerite da li ste zamijenili `GOOGLE_SCRIPT_URL` sa pravim URL-om
- Provjerite da li je Google Apps Script deployment postavljen na "Anyone"

### Stranica se ne učitava
- Pričekajte 5-10 minuta nakon aktiviranja GitHub Pages
- Provjerite da li je repozitorij "Public"

### Podaci ne stižu u Google Sheet
- Provjerite da li ste kopirali cijeli kod iz `google-script.js`
- Provjerite da li ste kliknuli "Deploy" u Apps Script-u

## 📞 Podrška

Za dodatna pitanja ili pomoć, kontaktirajte developera.

---

**Sretno vjenčanje! 🎉💒**
