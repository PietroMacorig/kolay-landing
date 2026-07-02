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

#### Pendente 📋 — prossima sessione
**→ Eseguire il piano con subagent-driven-development (tutti Sonnet)**

Prompt per la prossima chat (copiare e incollare):

```
Devi costruire la landing page di Kolay seguendo il piano già scritto.

Piano: C:\Users\pimac\Desktop\Claude\docs\superpowers\plans\2026-07-02-kolay-landing.md
Spec: C:\Users\pimac\Desktop\Claude\docs\superpowers\specs\2026-07-02-kolay-landing-design.md
Cartella progetto: C:\Users\pimac\Desktop\Claude\PROJECTS\Kolay\landing\
Screenshot app: C:\Users\pimac\Desktop\Claude\PROJECTS\Kolay\homepage_kolay.PNG

Usa la skill superpowers:subagent-driven-development per eseguire i task del piano uno alla volta.
Tutti i subagenti devono usare Sonnet (non Opus).
Usa la skill frontend-design:frontend-design per i task di costruzione HTML/CSS.
Inizia dal Task 1 (copia screenshot) e prosegui in ordine.
```

#### Azioni manuali che Pietro deve fare
1. **Formspree** — creare account su formspree.io → ottenere endpoint → inserire in `registrati.html` Task 9 (può farlo dopo il build)
2. **GitHub repo** — creare repo `kolay-landing` per il Task 10 deploy
3. **Dominio** — acquistare `kolay.it` (~€8-10/anno) quando pronto per il lancio

#### Decisioni prese
- Architettura dominio: **un solo dominio** (`kolay.it`) copre sia landing che app (`app.kolay.it` = subdomain gratuito). NON servono due domini.
- Stack landing: HTML/CSS puro (no framework) — più semplice, deploy immediato
- Form: Formspree gratuito (non Google Forms, non Netlify) per controllo sul markup
- Pricing Pro: badge "Presto" con design elegante (non N/A né TBD)
- Claim copy: valutare "prima" invece di "unica" per "unica app italiana" — più difendibile legalmente
- Futuro: quando Pietro avrà render Blender dell'iPhone, sostituire il blocco CSS con `<img>`
