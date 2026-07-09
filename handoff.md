# Kolay Landing Page — Handoff
_Creato: 2026-07-02 (sessione 36)_

---

## Cos'è
Sito marketing separato dall'app Kolay. Progetto Vercel indipendente in `PROJECTS/Kolay/landing/`.
HTML/CSS puro, 5 pagine. L'app resta su `kolay-ochre.vercel.app`.

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
