# Dansk/engelsk sprogskift på House of Muralia

**Task:** Gøre siden international ved at tilføje mulighed for at skifte
mellem dansk og engelsk.
**Udført af:** Claude (Angel)
**Dato:** 2026-08-18
**Status:** Færdig

## Baggrund

Kunden ønsker at siden kan henvende sig internationalt, ikke kun til danske
bygherrer/kommuner. Da sitet er rent statisk HTML (Tailwind via CDN, ingen
build-step), blev løsningen valgt til at være en client-side JS-toggle
(bekræftet med kunden frem for separate `/en/`/`/da/`-URL'er), så det passer
til den eksisterende skabelon-tankegang for kunstner-sider.

## Ændringer

- Ny delt fil `i18n.js`: læser `data-i18n`-attributter på elementer og
  erstatter deres tekst ud fra en `window.I18N`-ordbog for det aktive sprog.
  Gemmer valgt sprog i `localStorage` under nøglen `hom-lang`, så valget
  huskes på tværs af sider.
- `index.html` og `jens-stentoft.html`: alle brødtekster, overskrifter,
  navigations-links, knapper og footer-tekst er markeret med `data-i18n`-
  nøgler og har fået tilsvarende dansk/engelsk oversættelse i en
  `window.I18N = { da: {...}, en: {...} }`-blok i bunden af hver side.
- Ny DA/EN-knap tilføjet i navigationen på begge sider.

## Tests

- **Automatiseret:** Ingen (statisk site uden testrammer).
- **Manuel verifikation:** Kørt lokal statisk server (`python -m http.server`)
  og testet i browser-preview:
  - Dansk vises korrekt som standard ved første besøg.
  - Klik på "EN" oversætter hele forsiden (nav, hero, kunstner-sektion,
    galleri, footer) korrekt til engelsk uden at ødelægge layout, billeder
    eller styling.
  - Sprogvalget (`localStorage`) følger med, når man navigerer videre til
    `jens-stentoft.html` — siden loader automatisk på engelsk uden at
    kunstner-siden skal klikkes om igen.

## Anbefaling / åbne spørgsmål

- Nuværende løsning er god til brugeroplevelse, men svagere til SEO end
  separate sprog-URL'er, fordi Google kun ser ét sprog pr. URL. Hvis
  international synlighed i søgemaskiner bliver vigtig, bør det genovervejes.
- Når flere kunstner-sider tilføjes fremover (jf. kundens plan om at rykke
  flere kunstnere ind), skal hver ny side have sin egen `window.I18N`-blok med
  oversættelser — det er ikke automatiseret endnu.
