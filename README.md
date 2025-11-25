# tw_Proiect_2025-2026_Ciutescu_Iulia_anSuplimentar

# 🚗 Administrarea locurilor de parcare folosind Google Maps


**Disciplina:** Tehnologii Web  

**AN III Suplimentar**

**Ciutescu Iulia Alexandra**

---

## 1. Descriere generală

Proiectul constă în dezvoltarea unei aplicații web de tip **Single Page Application (SPA)** pentru administrarea locurilor de parcare utilizând harta interactivă oferită de **Google Maps**.

Aplicația oferă utilizatorilor autentificați posibilitatea de a gestiona parcările proprii și locurile de parcare asociate acestora.

---

## 2. Obiectivul aplicației

Scopul principal este de a facilita:

- organizarea și administrarea parcărilor private sau de firmă;
- vizualizarea parcărilor într-o manieră grafică, direct pe hartă;
- gestionarea în timp real a statusului locurilor de parcare.


---

## 3. Cerințe funcționale

* Vizualizare pagină de login și înregistrare.

* Posibilitate de creare cont nou (email, parolă, nume).

* Autentificare cu validare și afișarea mesajelor de eroare.

---

## 4. Funcționalități

Utilizatorii pot:

✔ crea cont și se pot autentifica  
✔ adăuga parcări prin selectarea unei locații pe hartă  
✔ edita și șterge parcările proprii  
✔ gestiona locurile de parcare (adăugare, modificare, ștergere)  
✔ vizualiza statusul fiecărui loc: liber / ocupat  
✔ vizualiza parcările pe Google Maps sub formă de markeri  
✔ utilizând persistența, vor rămâne logați chiar și după refresh-ul browserului


### 4.1 Funcționalități pentru utilizatori înregistrați

* Funcționalități utilizator autentificat
   
   Dashboard cu lista parcărilor create de utilizator.

* Administrare parcări:

   creare parcare nouă prin selectarea locației pe hartă;

   specificarea detaliilor: nume parcare, adresă, coordonate (lat, lng), număr total locuri, descriere;

   modificarea informațiilor unei parcări;

   ștergerea unei parcări.

* Administrare locuri de parcare (locuri) pentru o parcare:
  
   adăugarea locurilor (ex: numerotare);

   modificarea sau ștergerea unui loc;

   schimbarea statusului (ocupat/liber).

* Afișarea pe Google Maps a tuturor parcărilor utilizatorului ca markere;
  
   la click pe marker se afișează detaliile parcării și locurile disponibile.
  
   Logout

---

## 5. Tehnologii utilizate

### Front-end
- HTML
- CSS
- JavaScript
- React.js

### Back-end
- Node.js  
- Express.js  
- SQLite  
- Sequelize ORM  

### Alte tehnologii și biblioteci
- Google Maps JavaScript API  
- JSON Web Tokens (JWT)  

---

## 6. Arhitectura aplicației

Am ales să împart aplicația în două componente principale:

### ➤ Front-end
- Implementat folosind **React.js**
- Aplicație de tip SPA  
- Comunicarea cu serverul se face prin request-uri HTTP tip REST  
- Navigația este realizată folosind React Router  

### ➤ Back-end
- API RESTful realizat în Node.js cu Express  
- Implementarea operațiilor CRUD pentru entitățile principale  
- Gestiunea autentificării prin JWT  
- Conectare la baza de date SQLite prin ORM (Sequelize)

---

## 7. Model de date

Aplicația utilizează o bază de date relațională SQLite cu următoarele entități:

### Tabele:

#### utilizatori
- id  
- nume  
- email  
- parolă  

#### parcări
- id  
- utilizator_id (FK)  
- nume  
- adresă  
- latitudine  
- longitudine  
- total_locuri  
- descriere  

#### loc_parcare
- id  
- loc_parcare_id (FK)  
- loc_număr  
- status (liber / ocupat)

### Relații:
- Un utilizator → mai multe parcări  
- O parcare → mai multe locuri  

---

## 8. Securitate și autentificare

- Autentificarea se realizează prin **JWT (JSON Web Tokens)**  
- Fiecare request protejat necesită token în header-ul:  
  `Authorization: Bearer <token>`  
- Datele sunt izolate pe utilizatori:  
  fiecare utilizator poate accesa **exclusiv** resursele proprii  
- Token-ul este salvat în `localStorage` pentru persitența sesiunii  

---

## 9. Integrarea cu Google Maps

Aplicația integrează **Google Maps JavaScript API** pentru:

- afișarea parcărilor pe hartă  
- selectarea coordonatelor prin click pe hartă  
- utilizarea markerelor și ferestrelor informative  

---

## 10. Instrucțiuni de rulare

### Pornirea serverului (Back-end)

```bash
cd server
npm install
npm start
