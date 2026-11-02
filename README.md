# Komunala Hrastnik — demonstracijski full-stack portal

Spletna aplikacija React + Vite, REST API Express in podatkovna baza SQLite (Node.js 22+ `node:sqlite`). **Ni uradna spletna stran podjetja.**

## Zagon

```bash
npm install
ADMIN_EMAIL=admin@localhost ADMIN_PASSWORD='uporabite-dolgo-nakljucno-geslo' npm run dev
```

Javni portal: http://localhost:5173 — administracija: klik **Admin**. Node 22 ali novejši je obvezen.

## Produkcijski build

```bash
npm run build
ADMIN_EMAIL=admin@localhost ADMIN_PASSWORD='...' NODE_ENV=production npm start
```

Strežnik posluša na portu 3001. Namestite ga za HTTPS reverse-proxy. Podatkovna baza se shrani v `data/portal.sqlite` in NI vključena v repozitorij. Spremenljivke okolja nastavite v upravljalniku gostovanja (datoteka `.env` se ne nalaga samodejno). Ob prvem zagonu nastane admin račun; kasnejša sprememba okoljske spremenljivke gesla **ne spremeni** obstoječega uporabnika.

## Funkcije

- Večstranski prilagodljiv portal: domov, dejavnosti, podstrani storitev, odpadki, obvestila, dokumenti, kontakti, demo obrazci.
- Admin: prijava s scrypt hash geslom in HttpOnly sejnim piškotkom; CRUD vsebin, objavljeno/osnutek, pregled in status zahtevkov, dodajanje/brisanje terminov odvoza, dnevnik sprememb vsebin.
- REST API, lokalno shranjevanje vsebin in zahtevkov v SQLite.
- Demopodatki povzeti s **ksphrastnik.si** (preverjeno 2. 11. 2026), ne predstavljajo vsebinske 1:1 migracije.

## Predvidene pravice skrbnikov (za polno verzijo)

Superadmin: upravljanje uporabnikov/pravic, globalnih nastavitev in revizije; urednik: vsebine, obvestila, dokumenti; operativa: urniki, motnje, dežurstva; referent: zahtevki, statusi in odgovori; javni obiskovalec: pregled in oddaja obrazcev. **V prototipu je dejansko realiziran samo en administratorski profil.**

## Vsebinska vrzel / migracija

Zajete dejavnosti: pitna voda, odpadna voda, odpadki, javne površine, tržnica, plakatiranje, pogrebna služba, upravljanje objektov in zimska služba. Dodatne kategorije so oblikovane v dokumentnem centru (ceniki, letna poročila, programi, informacije javnega značaja, obrazci, javna naročila, SMS-obveščanje, e-računi, fotogalerija, iskalnik pokojnikov, Komunala.info, arhiv novic, sožalnica). **Vsebine vseh posameznih PDF-jev, albumov, arhivskih novic, vseh urnikov in integracij še NISO prenesene**. Dokumentne povezave so zato označene »V pripravi«.

## Pred produkcijo OBVEZNO

- Varnostni pregled (CSRF, uporaba HTTPS, močnejše omejevanje zahtev, varnostne glave, geselska politika/MFA, administracija sej, audit za vse operacije, ločevanje vlog).
- GDPR: pravne podlage, pravilnik zasebnosti, politika hrambe in brisanja, minimizacija podatkov. Trenutni demo obrazci ne smejo zbirati resničnih osebnih podatkov.
- Popolna revizija izvirnih dokumentov, urnikov, pravic za objavo slik, uskladitev informacij in formalna potrditev podjetja.
- Integracija z dejanskim sistemom za vodomere/e-račune, SMS, Komunala.info, iskalnikom pokojnikov.
- Varnostne kopije SQLite, nadzorovanje, dostopnost WCAG, e2e testi, nastavitve domene, SPF/DMARC za e-pošto če se implementira.

## Viri

https://www.ksphrastnik.si/ , https://www.ksphrastnik.si/dejavnosti/ , https://ksphrastnik.si/obrazci.html , https://ksphrastnik.si/ceniki.html , https://www.ksphrastnik.si/dejavnosti/odpadki.html
