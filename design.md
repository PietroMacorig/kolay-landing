# Kolay — Style Reference
> Mezzaluna turca su crema calda — un segno rosso audace in spazio bianco generoso, come la bandiera turca che galleggia nel cielo.

**Theme:** light

Sembra un pomeriggio caldo in un'aula mediterranea — spazio crema generoso con testi scuri e un unico punto focale rosso che trasmette energia senza rumore. La pagina riposa su superfici crema calde (`#FFF8F2`) con testo quasi-nero (`#1A1A1A`), creando contrasto forte. Inter a display sizes (48-72px) con letter-spacing negativo e peso 600-700 dà ai titoli chiarezza e calore. Il rosso turco (`#E8431A`) è l'unico elemento cromatico su una tela altrimenti neutra — usato per logo, CTA primari e accenti di sezione. Tutto il resto gli cede spazio.

## Tokens — Colors

| Name | Value | Token | Role |
|------|-------|-------|------|
| Turkish Red | `#E8431A` | `--color-turkish-red` | Logo, CTA primari, titoli accento — l'unico ancoraggio cromatico dell'intera identità |
| Red Hover | `#CF3A14` | `--color-red-hover` | Stato hover/active per CTA rossi |
| Warm Cream | `#FFF8F2` | `--color-warm-cream` | Sfondo primario pagina — bianco caldo, accogliente |
| Soft Cream | `#FFF0E6` | `--color-soft-cream` | Sfondo sezioni alternate |
| Pale Cream | `#FFE8D6` | `--color-pale-cream` | Contenitori sottili, dividers |
| Silver | `#D8D0C8` | `--color-silver` | Bordi, divisori decorativi |
| Pewter | `#9B9B9B` | `--color-pewter` | Testo secondario, caption, label mute |
| Smoke | `#6B6B6B` | `--color-smoke` | Testo terziario, body secondario |
| Ink | `#1A1A1A` | `--color-ink` | Testo primario — titoli e corpo principale |
| Level A1 | `#34C759` | `--color-level-a1` | Badge livello A1 |
| Level A2 | `#FF9500` | `--color-level-a2` | Badge livello A2 |
| Level B1 | `#0088FF` | `--color-level-b1` | Badge livello B1 |

## Tokens — Typography

### Inter — Typeface primario per tutto il contenuto
- **Pesi:** 400, 500, 600, 700
- **Dimensioni:** 14px, 16px, 18px, 22px, 40px, 54px, 72px
- **Line height:** stretto a display sizes (1.05-1.1), rilassato a body (1.55-1.65)
- **Letter spacing:** -1.5px a 72px, -0.7px a 54px, -0.3px a 40px; 0 a body

### Type Scale

| Role | Size | Line Height | Letter Spacing | Token |
|------|------|-------------|----------------|-------|
| caption | 14px | 20px | 0 | `--text-caption` |
| body | 16px | 26px | 0 | `--text-body` |
| subheading | 18px | 28px | 0 | `--text-subheading` |
| heading-sm | 22px | 30px | -0.2px | `--text-heading-sm` |
| heading | 40px | 46px | -0.3px | `--text-heading` |
| heading-lg | 54px | 58px | -0.7px | `--text-heading-lg` |
| display | 72px | 76px | -1.5px | `--text-display` |

## Tokens — Spacing & Shapes

**Density:** comfortable

### Spacing Scale

| Name | Value | Token |
|------|-------|-------|
| 4 | 4px | `--spacing-4` |
| 8 | 8px | `--spacing-8` |
| 12 | 12px | `--spacing-12` |
| 16 | 16px | `--spacing-16` |
| 20 | 20px | `--spacing-20` |
| 24 | 24px | `--spacing-24` |
| 32 | 32px | `--spacing-32` |
| 48 | 48px | `--spacing-48` |
| 64 | 64px | `--spacing-64` |
| 80 | 80px | `--spacing-80` |
| 120 | 120px | `--spacing-120` |

### Border Radius

| Elemento | Valore |
|----------|--------|
| card | 16-20px |
| badge / pill livello | 100px |
| immagini | 16px |
| bottoni | 100px |
| contenitori | 20-32px |

### Shadows

| Name | Value | Token |
|------|-------|-------|
| card | `rgba(26, 26, 26, 0.08) 0px 0px 32px 0px` | `--shadow-card` |

### Layout

- **Page max-width:** 1200px
- **Section gap:** 80-120px
- **Card padding:** 24-32px
- **Element gap:** 16-20px

## Components

### Primary CTA Button
Background `#E8431A`, testo bianco, border-radius 100px (pill piena). Padding 12px 28px. Inter weight 600, 16px. Nessun bordo. Hover → `#CF3A14`.

### Ghost Button (Secondario)
Background trasparente, border 2px `#E8431A`, testo `#E8431A`, border-radius 100px. Stesse dimensioni. Hover: bg `#E8431A`, testo bianco.

### Navigation Bar
Background `#FFF8F2`, max-width 1200px centrata, sticky. Sinistra: icona K rossa (28px) + "Kolay" Inter weight 700 20px `#1A1A1A`. Centro: link "Lingue", "Pricing", "FAQ" a 16px weight 500 `#1A1A1A`, gap 32px. Destra: pill CTA "Inizia gratis" `#E8431A`.

### Hero Section
Background `#FFF8F2`. Layout centrato. Titolo grande 60-72px Inter weight 700 `#1A1A1A` letter-spacing -1.5px. Sottotitolo 18px `#6B6B6B` max-width 560px. CTA sotto. Screenshot app in frame iPhone sotto o lato.

### Feature Section Header (Accento Rosso)
Background `#FFF0E6`. Titolo grande 48-54px Inter weight 700 color `#E8431A` — questa è la mossa caratteristica: display text in rosso brand contro sfondo crema chiaro. Body in `#6B6B6B`. Centro-allineato, 100px padding verticale.

### Feature Card
Background `#FFFFFF`, border-radius 20px, padding 28px, shadow `rgba(26,26,26,0.08) 0px 0px 32px`. Top: icona Phosphor 28px in `#E8431A`. Titolo 22px Inter weight 600 `#1A1A1A`, margin-top 16px. Body 16px weight 400 `#6B6B6B` line-height 26px.

### Level Badge
Pill (100px radius), 12px Inter weight 600. A1 verde (`#34C759` su sfondo `#E8FFE8`), A2 arancio (`#FF9500` su `#FFF3E0`), B1 blu (`#0088FF` su `#E8F4FF`). Indica il livello associato a una feature o contenuto.

### Language Pill
Flag emoji + nome lingua. Pill 100px radius. Background `#FFE8D6`. Testo `#1A1A1A` 14px weight 500.

### Section Divider (Surface Shift)
Nessuna linea visibile — sezioni separate da alternanza di sfondo tra `#FFF8F2` e `#FFF0E6` con 80-120px di spazio verticale. La transizione stessa è il divisore.

### Pricing Table
3 colonne: Funzionalità / Gratuito / Pro. Header row background `#FFF0E6`. Colonna Pro: bordo sinistro 3px `#E8431A`, sfondo `#FFFAF7`. CTA in fondo: "Scegli Pro" pill rosso, "Inizia gratis" ghost rosso.

### CTA Band (Sezione Finale)
Background `#E8431A`. Testo bianco. Titolo 40-48px Inter weight 700, letter-spacing -0.3px. Sottotitolo 18px `rgba(255,255,255,0.85)`. Bottone bianco con testo `#E8431A`, 100px radius. Unica sezione con sfondo rosso pieno — usata una sola volta come chiusura della pagina.

## Do's and Don'ts

### Do
- Usare `#E8431A` per TUTTI i CTA primari, il logo e i titoli accento di sezione — è l'unico ancoraggio cromatico
- Alternare sezioni tra `#FFF8F2` e `#FFF0E6` per creare ritmo senza divisori visibili
- Usare border-radius 100px per tutti i bottoni e elementi pill
- Impostare titoli display (40px+) con letter-spacing negativo — tracking stretto a grandi dimensioni è essenziale
- Usare `#6B6B6B` per il body text e `#9B9B9B` per le caption — i titoli dominano
- Usare Phosphor Icons in un solo colore (`#E8431A` o `#1A1A1A`) — mai icone multicolore
- Mantenere max-width 1200px e centrare tutto il contenuto

### Don't
- Mai usare un secondo colore CTA — il rosso è l'unico colore azione
- Mai angoli netti (0px radius) — minimo 8px su qualsiasi contenitore
- Mai rosso su rosso o crema su crema — mantenere sempre contrasto leggibile
- Mai body text più pesante di weight 500
- Mai linee orizzontali visibili tra sezioni
- Mai ombre direzionali o hard-edged — solo blur ambientale morbido
- Mai il rosso `#E8431A` come sfondo di sezioni (tranne la CTA band finale — una sola volta)

## Surfaces

| Level | Name | Value | Purpose |
|-------|------|-------|---------|
| 0 | Page Canvas | `#FFF8F2` | Sfondo primario pagina |
| 1 | Section Alternate | `#FFF0E6` | Sfondo sezioni alternate |
| 2 | Elevated Card | `#FFFFFF` | Card che galleggiano sopra lo sfondo crema |
| Special | CTA Band | `#E8431A` | Unica sezione con sfondo rosso — solo in chiusura |

## Imagery

Screenshot dell'app Kolay (flashcard, lezioni, grammatica, Speaking AI) dentro frame iPhone. La palette crema-e-rosso dell'app si allinea naturalmente con la landing — gli screenshot sembrano nativi. Nessuna fotografia lifestyle. Nessuna illustrazione astratta. Icone da Phosphor Icons (mono-weight, single color, funzionali). La K con mezzaluna turca è il brand mark — può apparire come motivo decorativo a grandi dimensioni in sezioni speciali.

## Layout

Max-width 1200px centrata. Hero: titolo centrato + body + CTA + mockup iPhone con screenshot sotto. Nav sticky: logo a sinistra, link al centro, CTA a destra. Sezioni alternate `#FFF8F2` ↔ `#FFF0E6` con gap 80-120px. Sezioni feature: titolo rosso grande → card grid. Contenuto prevalentemente centrato — no sidebar. Ritmo sezioni: hero → features intro (titolo rosso su crema chiaro) → feature cards → lingue → pricing → CTA band → footer.

## Agent Prompt Guide

**Quick Color Reference:**
- Testo (primario): `#1A1A1A`
- Testo (secondario): `#6B6B6B`
- Testo (muted): `#9B9B9B`
- Background (primario): `#FFF8F2`
- Background (alternato): `#FFF0E6`
- CTA / accento: `#E8431A`
- CTA hover: `#CF3A14`

**Example Component Prompts:**

1. "Crea una hero section: background `#FFF8F2`. Centrata. Titolo 64px Inter weight 700 `#1A1A1A` letter-spacing -1.5px. Sottotitolo 18px weight 400 `#6B6B6B` max-width 560px line-height 28px. CTA pill rosso (`#E8431A`, testo bianco, 100px radius, 12px 28px padding, weight 600). 80px sotto CTA: frame iPhone con screenshot app."

2. "Crea una feature section header: background `#FFF0E6`. Titolo grande 54px Inter weight 700 color `#E8431A`, letter-spacing -0.7px. Body 18px `#6B6B6B` sotto. Centro-allineato, 100px padding verticale."

3. "Crea una nav bar: background `#FFF8F2`, max-width 1200px centrata, sticky, border-bottom 1px `#D8D0C8`. Sinistra: immagine `assets/icon.svg` 28px + 'Kolay' Inter weight 700 20px `#1A1A1A`. Centro: link 'Lingue' 'Pricing' 'FAQ' a 16px weight 500 `#1A1A1A`, gap 32px. Destra: pill 'Inizia gratis' bg `#E8431A` testo bianco 100px radius 12px 24px padding."

4. "Crea una feature card: background `#FFFFFF`, border-radius 20px, padding 28px, shadow `rgba(26,26,26,0.08) 0px 0px 32px`. Top: tag `<i class='ph ph-cards' style='font-size:28px;color:#E8431A'></i>`. Titolo 22px Inter weight 600 `#1A1A1A` margin-top 16px. Body 16px weight 400 `#6B6B6B` line-height 26px."

5. "Crea una CTA band: background `#E8431A`. Testo bianco. Titolo 44px Inter weight 700 letter-spacing -0.3px. Sottotitolo 18px `rgba(255,255,255,0.85)`. Bottone bianco con testo `#E8431A` 100px radius 14px 32px padding weight 600. Centrata, 100px padding verticale."

## CSS Custom Properties

```css
:root {
  /* Colors */
  --color-turkish-red: #E8431A;
  --color-red-hover: #CF3A14;
  --color-warm-cream: #FFF8F2;
  --color-soft-cream: #FFF0E6;
  --color-pale-cream: #FFE8D6;
  --color-silver: #D8D0C8;
  --color-pewter: #9B9B9B;
  --color-smoke: #6B6B6B;
  --color-ink: #1A1A1A;
  --color-level-a1: #34C759;
  --color-level-a2: #FF9500;
  --color-level-b1: #0088FF;

  /* Typography */
  --font-primary: 'Inter', ui-sans-serif, system-ui, -apple-system, sans-serif;

  /* Type Scale */
  --text-caption: 14px;
  --text-body: 16px;
  --text-subheading: 18px;
  --text-heading-sm: 22px;
  --text-heading: 40px;
  --text-heading-lg: 54px;
  --text-display: 72px;

  /* Spacing */
  --spacing-4: 4px;
  --spacing-8: 8px;
  --spacing-12: 12px;
  --spacing-16: 16px;
  --spacing-20: 20px;
  --spacing-24: 24px;
  --spacing-32: 32px;
  --spacing-48: 48px;
  --spacing-64: 64px;
  --spacing-80: 80px;
  --spacing-120: 120px;

  /* Border Radius */
  --radius-sm: 8px;
  --radius-md: 16px;
  --radius-lg: 20px;
  --radius-xl: 32px;
  --radius-full: 100px;

  /* Shadows */
  --shadow-card: rgba(26, 26, 26, 0.08) 0px 0px 32px 0px;

  /* Layout */
  --page-max-width: 1200px;
}
```
