# Kolay Landing Page — Handoff
_Creato: 2026-07-02 (sessione 36)_

---

## Cos'è
Sito marketing separato dall'app Kolay. Progetto Vercel indipendente in `PROJECTS/Kolay/landing/`.
HTML/CSS puro. Dal 17/07 struttura multilingua: pagine italiane in `it/` (index, lingue, pricing, faq, privacy, termini), `en/` creata ma vuota (in attesa di traduzione), root serve solo un redirect verso `/it/` + il `404.html` condiviso. `css/nav.css` è il componente nav condiviso da tutte le pagine. L'app è raggiungibile su `app.learnkolay.com` (non più `kolay-ochre.vercel.app` nei link della landing, anche se il progetto Vercel sottostante è lo stesso).

**Spec:** `docs/superpowers/specs/2026-07-02-kolay-landing-design.md`
**Piano:** `docs/superpowers/plans/2026-07-02-kolay-landing.md`

---

## Stato attuale

### Sessione 2026-07-02 — Brainstorming + spec + piano

#### Completato ✅
- Brainstorming completo con visual companion (browser-based)
- Decisioni design prese:
  - **Struttura:** ibrido — home one-pager + pagine dedicate (lingue, pricing, faq, registrati)
  - **Hero:** split layout — testo cream sx, blocco rosso dx con iPhone 3D
  - **iPhone:** CSS realistico con Dynamic Island, tasti laterali, perspective forte (`rotateY(-28deg) rotateX(12deg)`)
  - **Sfondo hero:** blocco rosso `#E8431A` a destra, curva morbida sul bordo sinistro
  - **Features:** card in evidenza larghezza piena + griglia 2×2
  - **Copy:** "Kolay. Facile." (gioco bilingue: kolay=facile in turco) + sottotitolo
  - **Target:** italiani che imparano lingue (non solo turco)
  - **Registrazione:** form beta tester (Formspree) → Pietro invita manualmente su Supabase
  - **Pricing:** Free (U1 A1 + 3 msg AI/giorno) vs Pro ("Presto", badge elegante)
  - **Colori:** identici all'app (`#FFF8F2` bg, `#E8431A` accent, ecc.)
- Spec scritta e approvata: `docs/superpowers/specs/2026-07-02-kolay-landing-design.md`
- Piano implementazione scritto: `docs/superpowers/plans/2026-07-02-kolay-landing.md` (10 task, codice completo)
- Cartella progetto creata: `PROJECTS/Kolay/landing/` con sottocartelle `css/` e `assets/`

---

## Sessione 2026-07-02 (sessione 37) — Build completo

#### Completato ✅
- Tutti i 10 task del piano eseguiti con subagent-driven-development (Sonnet)
- `assets/screenshot.png` copiato da `homepage_kolay.PNG`
- `css/base.css` — variabili, reset, nav sticky, hamburger, footer (+ fix: rimosso commento orphan `/* GOOGLE FONTS */`, fix `transition: transform 0.3s` invece di `all`)
- `css/home.css` — hero split, iPhone CSS 3D, features grid, CTA band
- `css/pages.css` — lingue, pricing, FAQ accordion, form registrati
- `index.html` — hero con iPhone 3D + screenshot, features 2×2, CTA band
- `lingue.html` — card Turco (disponibile) + card Inglese (coming soon)
- `pricing.html` — banner beta + Free vs Pro con badge "Presto" arancio
- `faq.html` — 8 domande accordion (toggle JS, icona + → ×)
- `registrati.html` — form Formspree 4 campi + success message inline (+ fix: `style="display:none"` su `#formSuccess`)
- `vercel.json` — `cleanUrls: true`, `trailingSlash: false`
- Git repo inizializzato con 6 commit (uno per pagina)

#### Pendente 📋 — azioni manuali Pietro
1. **Dominio** — acquistare `kolay.it` (~€8-10/anno) quando pronto per lancio

---

## Sessione 2026-07-02 (sessione 38) — Deploy live

#### Completato ✅
- Formspree endpoint configurato: `https://formspree.io/f/xzdlkeqb` → sostituito in `registrati.html` → commit
- Push su GitHub: `github.com/PietroMacorig/kolay-landing` (7 commit totali su master)
- Deploy su Vercel: progetto `kolay-landing` esistente collegato al repo → **landing LIVE**
- **La landing page è pubblica e funzionante**

#### Pendente 📋 — prossimi step pre-lancio
1. **⚠️ Fix Groq deprecato** — `api/chat.js` usa `llama-3.3-70b-versatile` (deprecato dal 17 giugno) → da aggiornare con modello attivo
2. **Dominio** — acquistare `kolay.it` (~€8-10/anno) e collegare (landing su root, app su `app.kolay.it`)
3. **Sicurezza + legale** — Privacy Policy, rate limiting form, revisione auth
4. **Aprire registrazione** — passare da invito manuale a flow automatico

---

## Sessione 2026-07-03 (sessione 39) — Privacy Policy + Termini di Servizio

#### Completato ✅
- `privacy.html` creata — Privacy Policy GDPR-compliant (9 sezioni: titolare, dati/finalità con tabella, sub-processori USA + SCC, conservazione, diritti Art.15-22, Garante, cookie, età 14 anni, modifiche)
- `termini.html` creata — Termini di Servizio italiano (10 sezioni: servizio, account, età 14 anni, uso accettabile, proprietà intellettuale, disclaimer, fornitori terzi, modifiche 15gg, cancellazione, foro Padova)
- CSS `.legal-content` aggiunto in fondo a `css/pages.css`
- Footer aggiornato in tutte e 5 le pagine (index, lingue, pricing, faq, registrati): `href="#"` → `href="privacy.html"` e `href="termini.html"`
- FAQ risposta privacy aggiornata con link reale a `privacy.html`
- Commit `9f7aa56` pushato su `github.com/PietroMacorig/kolay-landing` (branch `master`)

#### ⚠️ DEPLOY INCOMPLETO — azione richiesta a Pietro

Il Vercel CLI non era autenticato, quindi il deploy **non è stato eseguito**. Il commit `9f7aa56` esiste su GitHub ma Vercel non è collegato all'auto-deploy per questo repo. Le pagine Privacy Policy e Termini di Servizio **non sono ancora live**.

**Per completare il deploy (5 minuti):**

1. Assicurati di essere nella directory landing. Nella prossima chat digita:
   ```
   ! cd "C:\Users\pimac\Desktop\Claude\PROJECTS\Kolay\landing" && vercel login
   ```
   → si apre il browser, fai login con l'account Vercel di Pietro.

2. Dopo il login:
   ```
   ! vercel --prod
   ```
   → seleziona il progetto `kolay-landing` esistente (non crearne uno nuovo).
   → il deploy avviene in 30-60 secondi.

3. Verifica aprendo la landing e cliccando "Privacy Policy" in fondo.

#### Pendente 📋 — dopo il deploy
1. **Sostituire `[EMAIL]`** — nelle pagine `privacy.html` e `termini.html` ci sono 4 placeholder `[EMAIL]` (2 per file) da sostituire con la mail dedicata Kolay non appena Pietro la crea
2. **Dominio** — acquistare `kolay.it` (~€8-10/anno) e collegare
3. **Aprire registrazione** — flow automatico invece di inviti manuali

#### Decisioni prese
- Conformità: GDPR Art.13/15-22/46, D.Lgs. 196/2003, ePrivacy Directive
- Titolare: Pietro Macorig (non P.IVA — ancora non aperta)
- Età minima: 14 anni (norma italiana, abbassa il default GDPR di 16)
- Foro competente: Tribunale di Padova
- `[EMAIL]` è un `<strong>` non cliccabile (non un mailto rotto) — da sostituire con email reale
- Vercel CLI installato globalmente (`npm i -g vercel`) ma richiede `vercel login` interattivo

#### Decisioni prese
- Vercel: usato il progetto `kolay-landing` già esistente nell'account (creato per errore in precedenza) invece di crearne uno nuovo

#### Decisioni prese
- Architettura dominio: **un solo dominio** (`kolay.it`) copre sia landing che app (`app.kolay.it` = subdomain gratuito). NON servono due domini.
- Stack landing: HTML/CSS puro (no framework) — più semplice, deploy immediato
- Form: Formspree gratuito (non Google Forms, non Netlify) per controllo sul markup
- Pricing Pro: badge "Presto" con design elegante (non N/A né TBD)
- Claim copy: valutare "prima" invece di "unica" per "unica app italiana" — più difendibile legalmente
- Futuro: quando Pietro avrà render Blender dell'iPhone, sostituire il blocco CSS con `<img>`

---

## Sessione 2026-07-04 (sessione 45) — Signup pubblico + restyling landing

#### Completato ✅
- **Supabase**: abilitato "Allow new users to sign up" (era invite-only). "Confirm email" lasciato ON.
- **App.jsx — LoginScreen signup**: aggiunto toggle login/signup, form con Nome+Email+Password+Conferma, `doSignup` chiama `supabase.auth.signUp` con `display_name` in `user_metadata`. Commit `a58454e`.
- **App.jsx — `?signup=true`**: URL param letto al render, passato come `initialMode` a LoginScreen → app si apre direttamente in modalità signup. Utenti già loggati non sono affetti. Commit `edd5839`.
- **Landing — `?signup=true` su tutti i CTA**: tutti i link `kolay-ochre.vercel.app` aggiornati in 5 file. Sezione feedback Formspree aggiunta in `index.html`. Commit `3333394`.
- **Landing — registrati.html rewrite**: rimosso form Formspree beta, sostituito con pagina early adopter (lista feature, box ochre, CTA → app, punto notifiche email). Commit `0147864` + `d596511`.
- **Landing — beta → early adopter**: faq.html (3 risposte aggiornate), pricing.html (banner + tabella), lingue.html (em-dashes). Em-dashes rimossi dal contenuto di tutti i file. Commit `939ed0f`.
- **Landing — tabella pricing**: sostituiti i due card con tabella 3 colonne (Funzionalità / Free / Pro). Colonna Pro evidenziata in giallo ocra (#C8960C, gradient, angoli smussati). 5 righe: Lezioni, Flashcard, Testi, AI Speaking, Grammatica. Commits `14192b4`.

#### Pendente 📋 — PRIORITÀ PROSSIMA SESSIONE
1. **⚠️ Nav "Registrati" in index.html**: il link nav "Registrati" punta a `kolay-ochre.vercel.app?signup=true` (modifica non richiesta), dovrebbe puntare a `registrati.html`. Controllare anche gli altri file HTML.
2. **⚠️ lingue.html — box feedback lingua**: Pietro ha chiesto un box in fondo a lingue.html "Che lingua vorresti poter imparare su Kolay?" con form Formspree — NON implementato questa sessione.
3. **Dominio `kolay.it`**: Pietro lo compra (OVH account padre o proprio). Dopo: DNS → Vercel, Resend SMTP, `[EMAIL]` placeholder.
4. **`[EMAIL]` placeholder**: 4 in privacy.html + termini.html, da sostituire con email reale dopo dominio.
5. **Fix localhost app**: copiare `VITE_SUPABASE_URL` e `VITE_SUPABASE_ANON_KEY` da Vercel/Supabase dashboard in `.env.local` righe 24-25.

#### Decisioni prese
- Signup pubblico aperto: no invite-only, "Confirm email" ON (2 email/ora Supabase OK per lancio soft).
- `plan: 'beta'` in `user_metadata` pianificato per future tier — non ancora implementato nel codice.
- Free tier futuro: solo A1 U1, 3 msg AI/giorno. Pro: tutto il contenuto, 50 msg AI/settimana, grammatica.
- Nav "Registrati" deve portare a `registrati.html` (non app diretta) — da correggere.
- Duolingo nella FAQ: lasciato, rischio legale basso.
- "Accesso prioritario nuove lingue": rimosso dal piano Pro (Pietro non vuole impegnarsi).
- Dominio: OVH padre va bene se Pietro ha accesso diretto al pannello DNS.

---

## Sessione 2026-07-09 (sessione 60) — Deploy v2 homepage in produzione

#### Completato ✅
- **`v2/index.html` deployata come nuova `index.html`**: homepage v2 merge in root, `v2/` resta su disco ma non in git.
- **`css/style.css`** aggiunto (CSS della v2, design tokens crema+rosso+Inter).
- **7 screenshot** aggiunti in `assets/`: screen_desktop, screen_desktop_2, screen_flashcard, screen_grammatica, screen_lettura, screen_lezione, screen_scrittura.
- **Path aggiustati**: `../assets/` → `assets/`, `../lingue.html` → `lingue.html`, ecc. (tutti i path relativi del v2 corretti per il root).
- **3 accenti corretti**: "perché" (Tutor AI), "è gratuita" (CTA band h2), "aspetti è un giorno" (CTA band p).
- Commit `dbc9acf` pushato su `kolay-landing` → Vercel auto-deploy in corso.

#### Pendente 📋
1. **Dominio `kolay.it`** — ancora da acquistare
2. **Altre pagine in v2** — lingue, pricing, faq, registrati ancora in stile v1 (redesign completo, chat futura)
3. **`[EMAIL]` placeholder** — 4 occorrenze in privacy.html e termini.html
4. **Resend SMTP** — dopo dominio

---

## Sessione 2026-07-09 (sessione 61) — Allineamento contenuti pagine secondarie

#### Completato ✅
- **lingue.html**: inglese da "In arrivo — 2026" (badge arancio) a "Disponibile ora" (badge verde), testo e CTA aggiornati ("Inizia con l'inglese →").
- **faq.html**: risposta "Quando arriveranno altre lingue?" aggiornata — turco e inglese già disponibili, link a lingue.html per suggerire lingue future.
- **pricing.html**: fix accenti "Unita" → "Unità" (3 occorrenze nella tabella).
- **registrati.html**: hero subtitle aggiornato ("scegli se imparare il turco o l'inglese"), fix "Hai gia" → "Hai già".
- Commit `5cb72e7` pushato su `kolay-landing`.

#### Pendente 📋
1. **Dominio `kolay.it`** — ancora da acquistare
2. **Redesign completo pagine secondarie** (lingue, pricing, faq, registrati) in stile v2 — chat dedicata futura
3. **`[EMAIL]` placeholder** — 4 occorrenze in privacy.html e termini.html
4. **Resend SMTP** — dopo dominio

---

## Sessione 2026-07-09 (sessione 59) — Hero fix: split layout + telefoni frontali sovrapposti

#### Completato ✅
- **Layout hero split**: da centrato a grid `5fr / 6fr` — testo allineato a sinistra nella colonna sx, cluster dispositivi nella colonna dx. Aggiunto `.hero-inner` wrapper.
- **Nuova immagine desktop**: `kolay_desktop_2.png` → copiata come `assets/screen_desktop_2.png`, inserita nella cornice MacBook esistente.
- **Telefoni frontali (zero rotazione 3D)**: rimossi tutti i `perspective()` e `rotateY()` dai telefoni laterali. Tutti i telefoni guardano in avanti.
- **Sovrapposizione 70/30**: ogni telefono laterale ha 70% visibile e 30% nascosto dietro il telefono più in primo piano. Profondità ottenuta solo con z-index e dimensioni decrescenti.
  - Center: 175px, z-index 10
  - Inner L/R: 158px, z-index 8 → `left: calc(50% - 198px)` / `calc(50% + 40px)`
  - Outer L/R: 140px, z-index 6 → `left: calc(50% - 296px)` / `calc(50% + 156px)`
  - Tutti a `bottom: 0` (allineati in basso)
- **Notch uniforme**: aggiunto `phone-sm` al telefono centrale → dynamic island 86×24px uguale per tutti (era 110×30px solo per il centrale).
- **Responsive aggiornato**: tablet (<1024px) stack a 1 colonna + 3 telefoni con posizioni ricalcolate; mobile solo centrale.

#### Pendente 📋
1. Pietro apre `v2/index.html` in Chrome — approvazione finale o iterazioni hero
2. Acquistare dominio `kolay.it` (sblocca DNS + `[EMAIL]` + Resend SMTP)
3. Altre pagine landing in v2 (lingue, pricing, faq, registrati) — sessione dedicata
4. Testi lettura inglese (A1/A2/B1) — contenuti app mancanti
5. Pietro testa v3 turco → cleanup backup (data_v2bak/, data_bak/)

#### Decisioni prese
- **Layout split confermato**: Pietro voleva testo sx + immagini dx — abbandonato il layout centrato della prima versione
- **Nessuna rotazione 3D**: più pulito, più moderno, coerente con estetica flat dell'app
- **Sovrapposizione 70%**: Pietro ha specificato il numero preciso — rispettato nel calcolo delle posizioni
- **Laptop mantenuto in MacBook frame**: Pietro ha confermato di volere la cornice

---

## Sessione 2026-07-08 (sessione 58) — Redesign landing v2: design system + homepage

#### Completato ✅
- **Analisi conversazione Gemini** su redesign: validati e corretti i consigli su tool (stack, Higgsfield MCP, skill React non applicabili a HTML/CSS), confermata scelta HTML/CSS puro
- **`landing/design.md`** creato — sistema design Kolay adattato da Paste/Refero: palette crema+rosso, Inter, token CSS, componenti, do/don'ts, prompt guide per Claude
- **`landing/v2/`** creato — cartella non-distruttiva per il redesign (vecchie pagine intatte in `landing/`)
  - `v2/index.html` — homepage completa riscritta
  - `v2/css/style.css` — CSS completo con design tokens
- **Hero rinnovato**: testo centrato sopra + formazione a V di dispositivi (5 iPhone in prospettiva + laptop dietro) — risolve bug "schermo vuoto su monitor grande" della v1
- **5 feature rows alternanti** (testo sx/dx, sfondo alternato): Lezioni, Flashcard, Grammatica, Lettura, Tutor AI — con screenshot reali dell'app
- **Phosphor Icons** (CDN) per tutte le icone — zero emoji
- **flag-icons** (CDN) per bandiere TR/GB — risolve rendering "TR"/"GB" su Windows
- **Messaging corretto**: Kolay come "app per lingue" (non solo turco); inglese "Disponibile" (non "In arrivo"); numeri minimi tra le due lingue: 126+ lezioni, 1800+ vocaboli per lingua
- **Zero em-dash** in tutta la pagina
- **Urgency copy** nell'hero e CTA band: "Gratuita adesso. Iscriviti prima che arrivi il piano Pro."
- **Screenshot salvati** in `landing/assets/`: screen_flashcard, screen_grammatica, screen_lezione, screen_scrittura, screen_lettura, screen_desktop

#### Pendente 📋
1. **Pietro apre `v2/index.html` in Chrome** e approva il design complessivo
2. **Iterazioni su v2** finché soddisfacente (tono, proporzioni, copy)
3. **Dominio `kolay.it`** — ancora da acquistare (priorità alta)
4. **Altre pagine in v2** — lingue, pricing, faq, registrati ancora in v1 (chat dedicata futura)
5. **DNS + Vercel** — collegare dominio dopo acquisto
6. **`[EMAIL]` placeholder** — 4 occorrenze in privacy.html e termini.html (sblocca con dominio)
7. **Resend SMTP** — dopo dominio

#### Decisioni prese
- **HTML/CSS puro, no React/Astro/Next.js**: landing è 5 pagine statiche, nessun vantaggio nel cambiare stack
- **V2 in sottocartella non-distruttiva**: si può eliminare se non piace, vecchio sito intatto
- **Feature rows alternanti (non griglia)**: scalabile, ogni feature respira, aggiungere lettura/altre in futuro è banale
- **Sezione "Come funziona" rimossa**: era filler, le feature rows già mostrano come funziona
- **Hero centrato** (non split): risolve definitivamente il problema responsive del vecchio hero split con blocco rosso
- **Formazione V con 5 iPhone + laptop**: mostra prodotto su mobile E desktop, effetto visivo forte
- **flag-icons library** al posto di emoji: emoji bandiere non rendono su Windows Chrome
- **Numbers: minimo tra le lingue**: 126 lezioni (turco min), 1800 vocaboli (inglese min) — onesti e verificabili

---

## Sessione 2026-07-05 (sessione 46) — Audit landing + fix completo + preparazione SEO

#### Completato ✅
- **pricing.html**: nomi piani "Piano Gratuito"/"Piano Pro" grandi, riga "Prezzo" in corpo tabella, "Da definire" al posto di "Presto", nota sotto tabella, bug rettangolo giallo risolto, CTA unico. Commit `826fff7`.
- **registrati.html**: allineamento lista bullet a sinistra, page-hero rosso aggiunto in cima. Commit `826fff7` + `0877564`.
- **index.html**: nav "Registrati" → `registrati.html` (fix bug noto), "La prima" al posto di "L'unica", hero CTA → registrati.html, accenti ("riceverà", "diventerà"), Formspree `xzdlkeqb`, Google Fonts preconnect, favicon, nav "Kolay" (rimossa K). Commit `0877564` + `de80abf`.
- **lingue.html**: box feedback "Che lingua vorresti imparare?" con Formspree `mojorazq`, Google Fonts, favicon, titolo SEO. Commit `0877564` + `de80abf`.
- **faq.html**: merge FAQ 4+6 (iPhone+Android in una risposta), form contatti Formspree `xpqgbaeq` (email obbligatoria), titolo SEO, nav, Google Fonts, favicon. Commit `de80abf`.
- **pricing.html**: "Funzionalità" (accent), titolo SEO, nav, Google Fonts, favicon. Commit `de80abf`.
- **registrati.html**: accenti ("uscirà", "riceverà"), titolo SEO, nav, Google Fonts, favicon. Commit `de80abf`.
- **css/base.css**: rimosso `@import` Google Fonts (ora caricato in HTML con preconnect). Commit `de80abf`.
- **css/pages.css**: rimosso CSS morto (vecchie classi card pricing). Commit `de80abf`.
- **assets/icon.svg**: icona K rossa copiata dall'app. Commit `de80abf`.
- **404.html**: pagina 404 custom branded con riferimento a *kaybolmak*. Commit `de80abf`.
- **Audit completo** della landing: 15 issues identificate, tutte alta/media priorità risolte.
- **Formspree**: 3 endpoint separati per tipologia — `xzdlkeqb` (feedback), `mojorazq` (lingua), `xpqgbaeq` (FAQ domande).
- **AI Act disclosure**: verificato che "● Tutor AI attivo" in Speaking.jsx riga 110 soddisfa già il requisito — nessuna modifica necessaria all'app.
- **Prompt SEO** preparato per sessione dedicata (vedi conversazione).

#### Pendente 📋 — PRIORITÀ PROSSIMA SESSIONE
1. **⚠️ Compra `kolay.it`** (Pietro lo fa domani) → DNS su Vercel → `[EMAIL]` placeholder in privacy.html + termini.html (4 occorrenze)
2. **Sessione SEO dedicata** — prompt già pronto, usare `kolay.it` come canonical domain in tutto. Discutere anche Vercel Analytics.
3. **Resend SMTP** — dopo dominio, configurare email transazionale
4. **Fix localhost app**: copiare env vars Supabase in `.env.local`

#### Decisioni prese
- Formspree: 3 form separati per tipologia (non uno solo) — più facile triaging email.
- Dominio: comprare `kolay.it` subito, fare SEO ora con `kolay.it` come canonical — i frutti arrivano dal primo giorno sul nuovo dominio.
- App su `app.kolay.it` (subdomain), non `kolay.it/app` — più semplice, nessun problema con auth cookies.
- "La prima app italiana" al posto di "L'unica" — più difendibile legalmente.
- Piano Pro: "Da definire" al posto di "Presto" — più onesto, meno vago.
- EU AI Act: "Tutor AI attivo" già presente nel Speaking screen — nessuna modifica necessaria. Obbligo formale da agosto 2026.
- Vercel Analytics: da discutere nella sessione SEO (gratuito, no cookie banner, dati base).

---

## Sessione 2026-07-03 (sessione 40) — Deploy PP+ToS + branch rename

#### Completato ✅
- Deploy `9f7aa56` (Privacy Policy + ToS) completato via `vercel --prod` — landing ora live con le pagine legali
- Branch rinominato da `master` a `main` su GitHub (`git branch -m master main` + push + delete remote master + default branch aggiornato su GitHub)
- Vercel ora collegato a `main` — auto-deploy attivo per i push futuri

#### Pendente 📋
1. **Verificare account Google `kolaylingue@gmail.com`** — account creato ma verifica telefono bloccata ("numero usato troppe volte"). Pietro ha accesso temporaneo via codice. Opzioni: usare numero diverso tra qualche giorno, oppure comprare `kolay.it` e usare Cloudflare Email Routing (`info@kolay.it` → forward a Gmail personale)
2. **Sostituire `[EMAIL]`** — 4 placeholder in `privacy.html` e `termini.html` (sblocca dopo punto 1)
3. **Dominio `kolay.it`** — acquistare e collegare (landing su root, app su `app.kolay.it`)
4. **Aprire registrazione** — flow automatico invece di inviti manuali

#### Decisioni prese
- Hosting: landing rimane su Vercel (non su OVH shared hosting del padre — OVH non supporta Node.js, utile solo per HTML statico)
- App rimane su Vercel free finché non ci sono utenti paganti; al primo revenue → Vercel Pro ($20/mese)
- Monetizzare su OVH + app su Vercel non bypassa i ToS Vercel (guardano l'app, non dove vanno i pagamenti)

---

## Sessione 2026-07-16 (sessione 87) — Redesign hero homepage: laptop + telefono (stile realistico)

Pietro aveva fatto rifare a un'altra chat Claude il visual del box dispositivi (`PROJECTS/Kolay/device-mockup.html`, tenuto come reference, mai modificato) e voleva portarlo nella homepage live, restando nello spazio hero attuale. Discusso anche (non implementato) l'obiettivo di preparare in futuro `learnkolay.com/it` e `/en` con rilevamento lingua browser — rimandato a quando il sito IT sarà definitivo, come deciso esplicitamente da Pietro.

#### Completato ✅
- **Hero `index.html`/`css/style.css`**: sostituito il vecchio cluster a 5 telefoni (`.device-outer-l/r`, `.device-inner-l/r`, `.device-center-phone`, `.device-laptop`) con una struttura nuova (classi `.mockup-*`) copiata il più fedelmente possibile dai valori pixel di `device-mockup.html`: bezel realistico (notch a pillola, home indicator, tasti volume/power laterali), scalata con un unico `transform:scale()` su un canvas 1080×720 invece di ricalcolare ogni valore a mano.
- **Composizione finale** (dopo diverse iterazioni con Pietro): non più 5 telefoni ma **laptop (`screen_desktop_3.png`) + 1 solo telefono (`screen_flashcard.png`)** appoggiato sul lato sinistro del laptop (~30% coperto dietro il bordo, stesso principio di sovrapposizione già usato in passato).
- **Dimensioni finali**: `.mockup-stage` scale `0.75`, `.mockup-stage-wrap` 810×540px, `.hero-devices` height 540px — dopo vari tentativi (0.6→0.72→0.936→0.75) per bilanciare "abbastanza grande" senza schiacciare il testo o uscire dalla viewport.
- **Bug reale trovato e risolto**: `.hero-devices` era stato cambiato da `position:relative` (originale, figli tutti `position:absolute` quindi a larghezza-zero per la grid) a `display:flex` con un figlio (`mockup-stage-wrap`) a larghezza fissa normale-flow — questo forzava la colonna grid a espandersi oltre la sua quota `fr`, schiacciando il testo a sinistra. Diagnosticato confrontando `git diff` coi valori originali di `.hero-inner` (`grid-template-columns: 5fr 6fr`, `min-height:520px`, mai cambiati altrove). Fix strutturale: `.hero-devices` tornato `position:relative`, `.mockup-stage-wrap` reso `position:absolute` — non può più ripetersi anche a device più grandi in futuro.
- **Rimossi** i due div-ombra decorativi (`.mockup-shadow-ground`, `.mockup-shadow-laptop`) che creavano un alone scuro visibile oltre il bordo destro della pagina.
- **Rimosso `overflow:hidden`** da `.hero-devices` (aggiunto e poi tolto su richiesta esplicita di Pietro — il clip naturale lo fa già `.hero` padre).
- `.hero-inner` (`max-width:1200px`, `grid-template-columns:5fr 6fr`, `gap:64px`, `min-height:520px`) confermato identico all'originale live — nessuna modifica netta a fine sessione.
- Tablet/mobile: breakpoint aggiornati di conseguenza (stage scalato ulteriormente su tablet, singolo telefono ingrandito standalone su mobile).

#### Pendente 📋
1. ~~Conferma visiva finale da Pietro~~ ✅ confermata a inizio sessione 88 (17/07)
2. ~~Architettura `/it` `/en`~~ ✅ implementata sessione 88 (17/07) — vedi sotto
3. **Dominio**: la voce storica "comprare `kolay.it`" in questo file è superata — `learnkolay.com` è stato comprato e collegato (vedi `PROJECTS/Kolay/andare_public/`, sessioni 84-85 del progetto App). Restano comunque aperti da lì: `[EMAIL]` placeholder in `privacy.html`/`termini.html`, Resend SMTP.
4. Redesign pagine secondarie (lingue, pricing, faq, registrati) in stile v2 — non ancora fatto, resta da sessione dedicata futura.

#### Decisioni prese
- `device-mockup.html` resta intoccato come reference visiva — ogni modifica va fatta solo su `index.html`/`css/style.css`, mai su quel file.
- Sequenza esplicita di Pietro: prima perfezionare il sito italiano, poi tradurre in inglese — l'architettura multilingua è solo pianificata, non implementata ora.

---

## Sessione 2026-07-17 (sessione 88) — Split /it + /en, fix hero, copy, nav unificata, dominio app

Continuazione diretta della sessione 87 (hero confermato a video da Pietro a inizio sessione). Obiettivo: sistemare il sito prima di tradurlo in inglese — struttura cartelle, poi contenuti pagina italiana, poi nav.

#### Completato ✅

**Struttura `/it` + `/en`**
- Tutte le 7 pagine spostate in `it/` con `git mv` (storia preservata): `index`, `lingue`, `pricing`, `faq`, `privacy`, `termini` + `registrati` (poi ritirata, vedi sotto). `en/` creata vuota con `.gitkeep`.
- `css/`, `assets/`, `404.html` restano condivisi in root.
- Nuova `index.html` in root: redirect (meta refresh + JS) verso `/it/` — hardcoded per ora dato che `/en/` non esiste ancora, un solo punto da cambiare quando si attiva il rilevamento lingua vero.
- `vercel.json`: redirect 301 dai vecchi path piatti (`/pricing.html`, `/lingue.html`, ecc.) a `/it/...` per non rompere link già condivisi/indicizzati.
- Verificato dal vivo con `serve` locale + Playwright: path relativi, clean URL, redirect tutti funzionanti.

**Fix hero (bug reale trovato con Playwright)**
- `.hero-devices`/`.mockup-stage-wrap` erano alti 540px ma il contenuto visibile (laptop+telefono) occupava solo ~327px → 213px di spazio morto prima della sezione "Lezioni". Misurato con `getBoundingClientRect()`, non solo a occhio. Fix: altezza ridotta al contenuto reale (340px desktop, 190px tablet), il respiro sotto l'hero ora è un `padding-bottom` esplicito e prevedibile invece di dipendere dal box sovradimensionato.
- Aggiunta un'ombra a terra morbida (radial-gradient blur) sotto il cluster dispositivi, contenuta da `overflow:hidden` su `.hero` (non può ripetere il vecchio problema dell'alone che sbordava a destra, tolto in sess.87). **Confermata da Pietro.**

**Sezione "Lingue disponibili"**
- Card ingrandite, sostituito il paragrafo piatto con le tag pillola già usate nelle feature row (coerenza col resto della pagina).
- Provati badge colorati A1/A2/B1 (componente "Level Badge" da `design.md`, mai usato prima) — **scartati da Pietro**, tornati a tag testuale neutra "A1, A2, B1".

**Copy hero/CTA/footer**
- Tolto "italiana" da "la prima app" (claim ora "la prima app", su richiesta esplicita di Pietro — nota: claim più ampio e meno difendibile legalmente di "la prima app italiana", segnalato a Pietro).
- Rimossa la ripetizione quasi verbatim del claim "prima app" tra hero e sezione Lingue.
- Ammorbidita la frase da senso di colpa nella CTA band ("ogni giorno che aspetti...") — ora punta su accesso gratuito + status early adopter, senza ripetere l'urgenza già detta nell'hero.
- Fix ambiguità reale: "Solo una lingua" nell'hero poteva leggersi come "l'app copre una sola lingua" (falso, contraddiceva la sezione Lingue subito sotto) → "Solo te e la lingua che vuoi imparare." (proposta di Pietro).
- Aggiunto riferimento al Quadro Comune Europeo nella sezione Lingue (non in hero, per non rompere la coerenza con le tag "A1, A2, B1" usate altrove).
- Footer: aggiunto simbolo ©.

**Nav unificata su tutte le pagine**
- Le pagine secondarie usavano un sistema di design completamente diverso dall'index (font Lora/Noto Sans invece di Inter, logo solo testo invece di icona+wordmark, layout flex non centrato invece di grid, CTA "Vai all'app →" invece di "Inizia gratis", link "Home"+"Registrati" in più, mobile drawer diverso). Creato `css/nav.css`, componente unico e self-contained (valori espliciti, non dipende dai design token delle due pagine ospitanti) usato da tutte le 7 pagine + `404.html`.
- Logo diventato wordmark **"Learn Kolay"** (Learn nero/bianco + Kolay rosso, K maiuscola) — stile identico ai post social e al dominio, usato in nav e footer di ogni pagina. Scelto di non toccare l'headline hero "Kolay. Facile." (gioco di parole kolay=facile in turco, si sarebbe perso e avrebbe messo inglese dentro la pagina italiana).
- Nav ridotta a 3 link (Lingue, Pricing, FAQ) ovunque, tolti "Home" e "Registrati".
- **`registrati.html` ritirata**: contenuto ridondante con home+pricing (stessi bullet, stesso messaggio early-adopter, styling bespoke fuori dal design system), unico valore reale ("Hai già un account? Accedi") non giustificava una pagina a sé. Redirect 301 aggiunti in `vercel.json`.
- Aggiunto **switch lingua IT/EN** in nav (pillola, IT attivo/EN disabilitato con tooltip "Presto disponibile" — `/en/` non esiste ancora).
- Su richiesta di Pietro: tolto il bottone separato "Accedi" (andava alla stessa schermata di "Inizia gratis", solo con tab diverso — l'app ha già il toggle login/signup interno), rinominato il CTA nav unico in **"Vai all'app"**.
- **Tutti i link `kolay-ochre.vercel.app` sostituiti con `app.learnkolay.com`** (verificato prima che il dominio rispondesse 200 diretto, nessun redirect intermedio) — un utente che clicca ora non vede più il vecchio dominio `.vercel.app` caricarsi per un istante.
- Bug trovati e risolti durante il lavoro: pallini elenco sui link nav delle pagine secondarie (mancava `list-style:none` in base.css), link nav duplicati/tagliati su mobile (dimenticato di nascondere `.nav-links` sotto 680px), link interni di `404.html` rotti (puntavano a `lingue.html` ecc. in root, ma le pagine si erano spostate in `it/` durante il lavoro sulle cartelle — root-relative `/it/...` ora), un riferimento testuale in FAQ al vecchio CTA "Vai all'app"/dominio vecchio.

**Deploy**
- Commit `edf4bcd` pushato su `main` — Vercel auto-deploy in corso a fine sessione.

#### Pendente 📋
1. **Verifica visiva del deploy live** — tutte le modifiche di oggi sono state validate in locale (server statico + Playwright), non ancora controllate su `learnkolay.com` dopo il deploy Vercel.
2. **Traduzione inglese**: prossimo step esplicito di Pietro — creare le pagine in `en/`, speculari a quelle italiane. Promemoria contenuto già deciso: dalla pagina IT si dice che l'app offre turco+inglese, dalla pagina EN si dirà solo turco; lo svedese sarà annunciato "work in progress, arriva ad agosto 2026" in entrambe.
3. **Limiti piano Free/Pro da aggiornare** nel sito (pricing.html attuale è disallineato) — discusso a inizio sessione, poi rimandato per concentrarsi su struttura+nav. L'app resta gratis finché non viene integrato Stripe.
4. Switch lingua nav: oggi è solo un placeholder visivo (EN disabilitato) — va collegato per davvero quando `/en/` esiste.
5. Redesign pagine secondarie (lingue, pricing, faq) in stile v2 — ancora non fatto.
6. Resta aperto tutto il pendente del filone "Andare Public" (vedi `PROJECTS/Kolay/andare_public/`).

#### Decisioni prese
- "La prima app" (non più "italiana") — scelta esplicita di Pietro nonostante il rischio legale maggiore segnalato.
- "Learn Kolay" come wordmark solo in nav/footer, non nell'headline — mantiene il gioco di parole "Kolay. Facile." intatto.
- Un solo bottone CTA in nav ("Vai all'app"), niente "Accedi" separato — l'app gestisce già login/signup nella stessa schermata.
- `app.learnkolay.com` ovunque al posto di `kolay-ochre.vercel.app` nella landing.
- `registrati.html` ritirata invece di redesignata — non aggiungeva contenuto reale rispetto a home+pricing.

---

## Sessione 2026-07-17 (sessione 89) — Svedese "in arrivo" su lingue.html + copy box suggerimenti

Pietro ha chiesto di valutare copy/design di `lingue.html` e aggiungere lo svedese come lingua "work in progress, in arrivo ad agosto 2026" (coerente con la nota lasciata a fine sess.88). Chiesto esplicitamente **scope ridotto**: solo copy + aggiunta svedese, **senza** portare la pagina al nuovo stile v2 (redesign completo rimandato, resta pendente).

#### Completato ✅
- **Card Svedese aggiunta** in `it/lingue.html`: badge arancio "In arrivo · Agosto 2026" (classe `.lang-card.coming` + `.badge-orange`, già esistenti in CSS ma mai usate finora), bandiera 🇸🇪, CTA "Avvisami al lancio ↓" che punta al form in fondo pagina (`#langForm`) invece che all'app.
- **CSS `pages.css`**: `.lang-grid` da 2 a 3 colonne (`repeat(3,1fr)`), nuovo breakpoint 900px per 2 colonne in tablet (prima saltava da 2 a 1 colonna senza stadio intermedio). `.lang-card.coming` da `opacity:0.75` su tutta la card (rendeva il testo poco leggibile) a sfondo `--card2` + opacity solo su flag/nome.
- **Copy**: meta title/description aggiornati (menzionavano solo il turco). Box suggerimenti in fondo pagina riscritto: prima chiedeva "che lingua vorresti imparare" dando per scontato che la prossima lingua fosse ancora da decidere — ora distingue "avvisami per lo svedese" (già deciso) da "suggerisci la prossima dopo quella". Campo email reso obbligatorio (prima opzionale) e spostato per primo, campo lingua reso opzionale (prima obbligatorio) — la maggior parte di chi userà il form ora vuole solo essere avvisato per lo svedese, non suggerire una lingua nuova.
- Nessun cambio di sistema di design (font Lora/Noto Sans, `base.css`/`pages.css` invariati nella struttura) — resta disallineato dalla homepage v2, come già notato in sess.88.

#### Non fatto (scope escluso esplicitamente da Pietro)
- Redesign di `lingue.html` in stile v2 (Inter, flag-icons, card a tag pillola) — resta nel pendente storico "redesign pagine secondarie", non toccato oggi.
- Pagina inglese `en/lingue.html` non esiste ancora (tutto `en/` è vuoto, traduzione rimandata come da sess.88) — quando verrà creata, andrà annunciato lo svedese anche lì (nota già lasciata in sess.88).

#### Pendente 📋
1. ~~Deploy~~ ✅ pushato sess.90.
2. Redesign pagine secondarie (lingue, pricing, faq) in stile v2 — ancora pendente da sessioni precedenti.
3. ~~Traduzione inglese (`en/`)~~ ✅ fatta sess.91-92, vedi sotto.

---

## Sessione 2026-07-17 (sessione 90) — Prezzo Pro reale, FAQ aggiornata, legal + Vercel Analytics

Continuazione diretta di sess.89. Pietro ha confermato i limiti Free/Pro rimasti in sospeso da sess.88 e chiesto di sistemare privacy/termini/analytics prima di passare alla traduzione inglese.

#### Completato ✅
- **Card Svedese aggiunta anche in `index.html`** (homepage v2): sezione lingue ridotta a 2 card (Turco disponibile + Svedese in arrivo), headline "Un metodo, più lingue." Grid a 2 colonne.
- **`pricing.html`**: prezzo Pro reale **3,99€/mese o 29,99€/anno (-37%, barrato su 47,88€)**, mostrato nell'header della tabella (CSS già pronto, mai usato). Tabella 5 righe con i limiti futuri decisi in chat: Lezioni/Flashcard sempre sbloccate su entrambi i piani, Testi di lettura e Grammatica solo Pro, AI Speaking 3 msg/giorno Free vs **70 msg/settimana** Pro (non illimitato). Banner riscritto: "hai già accesso a tutte le funzionalità Pro senza costo, finché non attiviamo gli abbonamenti".
- **`faq.html`**: domanda "È davvero gratuita?" → "Quanto costa?" con risposta allineata a pricing.html + link. Nuova FAQ sui limiti AI (perché 3/giorno Free vs 70/settimana Pro). Risposta lingue future aggiornata con lo svedese.
- **`privacy.html`/`termini.html`**: placeholder `[EMAIL]` (4 totali) sostituiti con `hello@learnkolay.com` (mailbox attivata dopo ticket OVH). Tolta la frase falsa "accesso su invito" (il signup è pubblico da sess.45). Tabella dati aggiornata (contatore messaggi AI, i 2 form Formspree reali invece della vecchia waitlist). Aggiunti Vercel Analytics e OVH come sub-processori. **Verificata la documentazione ufficiale Groq** (Services Agreement + Your Data in GroqCloud, via WebSearch/WebFetch): confermato che Groq non usa i dati per training e non li conserva oltre l'elaborazione salvo log 30gg per abusi/affidabilità — chiudeva un pendente aperto da settimane nel piano `andare_public` §0 punto 5.
- **Vercel Web Analytics** aggiunto: snippet vanilla JS su tutte e 7 le pagine della landing; sul progetto app (`kolay`, React/Vite) installato `@vercel/analytics` e montato `<Analytics />` in `main.jsx`.
- **Deciso di non usare Cloudflare Web Analytics** (il piano free sembra vietare uso commerciale) — si resta solo su Vercel Analytics, gratis ora, passa a Web Analytics Pro incluso quando si upgraderà a Vercel Pro (già previsto al primo pagamento, non è un costo aggiuntivo). Dettagli in `andare_public/00_piano_generale.md` Fase 3.
- Card lingue (Turco/Inglese/Svedese) ingrandite, bottoni ancorati in fondo con `margin-top:auto` invece che subito sotto il testo (le descrizioni di lunghezza diversa creavano card di altezza diversa), bandiere emoji sostituite con flag-icons (su Windows le emoji rendevano come testo "TR"/"EN"/"SE").
- Tutto pushato e verificato live (incluso un redeploy manuale dell'app per un bug scoperto **non causato da queste modifiche**: un deploy Vercel aveva silenziosamente costruito senza le env var Supabase, bundle rotto — risolto con un redeploy pulito, vedi diagnosi completa in questa sessione).

#### Pendente 📋 (portato avanti)
1. Redesign pagine secondarie in stile v2 — ancora aperto.
2. Formspree: cambiare l'email di notifica sui 2 form (`mojorazq`, `xpqgbaeq`) dalla dashboard — azione manuale di Pietro, non ancora fatta.
3. IMAP locale di backup su `hello@learnkolay.com` — ancora da fare.
4. Resend SMTP — ancora da fare.
5. Traduzione inglese `en/` — prossimo step esplicito di Pietro.

---

## Sessione 2026-07-17 (sessione 91-92) — Traduzione inglese completa + 2 bug reali trovati da Pietro

#### Completato ✅
- **6 pagine `/en/` create** (index, lingue, pricing, faq, privacy, termini) con un **workflow a 7 agenti Sonnet in parallelo** (6 traduttori + 1 verificatore) — piano concordato con Pietro prima di lanciarlo, autonomo fino a fine processo. `index.html`/`lingue.html` EN mostrano solo Turkish (disponibile) + Swedish (coming August 2026), **niente card English** (l'audience la parla già). hreflang reciproci IT/EN/x-default su tutte le coppie. Switch lingua nella nav reso funzionante in entrambe le direzioni (prima l'opzione EN era sempre disabilitata). `privacy.html`/`termini.html` EN tradotte fedelmente senza alterare fatti/citazioni legali.
- **`404.html`** reso bilingue (rilevamento `navigator.language`, prima era rimasto con lo switch EN disabilitato).
- **`index.html` root**: il redirect ora manda davvero i visitatori non italiani su `/en/` (prima era hardcoded sempre `/it/`).
- **Bug 1 (trovato da Pietro)**: su mobile, le pagine a 2 card lingua (index/lingue EN) facevano uscire la seconda card dallo schermo invece di andare sotto, perché uno `style` inline forzava 2 colonne **a qualunque larghezza**, ignorando le media query mobile che invece funzionano correttamente sulle pagine a 3 card. Fix: spostata la regola in una classe `.lang-grid-2col` nei fogli di stile, con le media query aggiornate per includerla.
- **Bug 2 (trovato da Pietro, il più serio)**: dalla home (IT o EN), cliccare Lingue/Pricing/FAQ/Privacy/Termini o il logo riportava sempre in italiano, anche partendo dall'inglese. Causa: `trailingSlash:false` rende l'URL pulito della home `.../it` o `.../en` **senza slash finale** — i link relativi tipo `href="lingue.html"` su quella pagina si risolvono sostituendo l'ultimo segmento (`it`/`en` viene trattato come un file), quindi scappano fuori dalla cartella lingua e finiscono sui redirect legacy di `vercel.json`, che puntano sempre a `/it/...`. Bug invisibile lato italiano (il redirect ci finiva comunque), rompeva solo la navigazione dalla home inglese. Le altre pagine non erano affette (il loro ultimo segmento URL non è mai `it`/`en`). Fix: link di nav/footer/logo sulla home resi assoluti (`/it/...` o `/en/...`).
- Tutto verificato live con Playwright (screenshot + `console --errors`) prima e dopo ogni fix, non solo build locale.

#### Non fatto / segnalato ma non risolto
- **`vercel.json` — redirect legacy sempre fissi a `/it/...`**: `{"source":"/lingue.html","destination":"/it/lingue",...}` e simili non guardano mai la lingua di chi arriva da un link esterno vecchio/condiviso (es. `learnkolay.com/lingue.html`) — vanno sempre in italiano. Proposto a Pietro di renderli lingua-aware, non ancora deciso/fatto.
- Redesign pagine secondarie in stile v2 — resta il pendente più vecchio, mai affrontato.

#### Pendente 📋
1. `vercel.json`: valutare se rendere i redirect legacy consapevoli della lingua del browser.
2. Redesign pagine secondarie (lingue, pricing, faq) in stile v2.
3. Formspree: cambiare email di notifica (azione manuale Pietro).
4. IMAP backup + Resend SMTP (azioni manuali Pietro).
5. Fix età minima 13→14 in `App.jsx` — **ora sbloccato** (i testi legali veri sono stati sistemati in sess.90), prossimo step naturale secondo `00_piano_generale.md` Fase 1.
6. Tutto il resto del filone "Andare Public" (Fase 0 fiscale, Fase 2 Stripe/paywall) — vedi `andare_public/00_piano_generale.md`.
