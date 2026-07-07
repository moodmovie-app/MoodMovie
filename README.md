# MoodMovie

App PWA di scoperta film/serie TV per mood, basata su TMDB. Non riproduce
contenuti: mostra dove guardare legalmente un titolo (piattaforme in
abbonamento, noleggio/acquisto) e genera entrate tramite link di
affiliazione e pubblicità.

## Struttura

```text
├── index.html        # app principale (telefono/desktop, PWA)
├── tv.html / tv-app.js  # variante per Smart TV (senza consenso cookie/monetizzazione, vedi sotto)
├── sw.js              # service worker (funzionamento offline/installabile)
├── manifest.json      # manifest PWA
├── privacy.html        # Privacy Policy, cookie, disclosure affiliazione
```

## Attivare la monetizzazione reale

Tutti i placeholder sono raccolti in un solo punto, in cima allo script di
`index.html`, nell'oggetto `MONETIZATION`:

```js
const MONETIZATION = {
    vpnUrl: 'https://nordvpn.com/',       // sostituisci col tuo link di affiliazione VPN
    amazonAssociateTag: 'INSERISCI-TAG-21' // sostituisci col tuo tracking ID Amazon Associates
};
```

Per la pubblicità, cerca `function loadAds()` nello stesso file: contiene le
istruzioni commentate per collegare il tuo publisher ID Google AdSense.

## Deploy

1. Crea un account GitHub (gratis) e carica questa cartella come repository.
2. Crea un account Vercel o Netlify (gratis) e collegalo al repository:
   essendo un sito statico, non serve alcuna build — pubblica i file così
   come sono.
3. Ogni `git push` dopo il primo deploy aggiorna automaticamente il sito.

## Account da aprire prima di guadagnare davvero

- **Programma di affiliazione VPN** (es. NordVPN, ExpressVPN, Surfshark) — di solito tramite il loro sito "Affiliati/Partner".
- **Amazon Associates** (amazon.it) — richiede dati fiscali per essere pagato.
- **Google AdSense** — richiede verifica del sito e dell'identità.

## Nota sulla versione TV

`tv.html`/`tv-app.js` hanno la stessa rimozione del player pirata e lo stesso
pannello "Dove guardarlo", ma **non** hanno banner cookie né link di
affiliazione (la navigazione a telecomando rende scomodo un banner
cliccabile). Da aggiungere in un secondo momento se l'app TV viene
pubblicata seriamente.
