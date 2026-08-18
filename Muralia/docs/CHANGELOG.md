# Changelog

## [Unreleased] - 2026-08-18 (2)

### Tilføjet
- Dansk/engelsk sprogskift tilføjet til begge sider (`index.html`,
  `jens-stentoft.html`) via en DA/EN-knap i navigationen. Løsning: delt
  `i18n.js`, der læser `data-i18n`-attributter og en per-side
  `window.I18N`-oversættelsesordbog, og gemmer valgt sprog i `localStorage`
  (`hom-lang`), så det huskes på tværs af sider.

### Verificeret
- Testet manuelt via lokal statisk server (`python -m http.server`) i
  browser-preview: DA er default, EN-knap oversætter hele forsiden korrekt,
  og sprogvalget følger med, når man navigerer videre til kunstner-siden
  (bekræftet via `localStorage`-persistens).

## [Unreleased] - 2026-08-18

### Ændret
- Omdøbt brandet fra "MURALIA" til "HOUSE OF MURALIA" i titel, nav, hero-tekst,
  footer og kunstner-underside.
- Kontaktmail ændret fra `kontakt@muralia.dk` til `kontakt@houseofmuralia.dk`.
- Alle billed- og videofiler omdøbt fra rodede/tilfældige navne (fx
  `AGSAGDFASFAE.jpeg`, `725032751_...n.jpg`, `video.mp4.mp4`) til sigende navne
  (`gallery-01.jpg`..`gallery-14.jpg`, `hero-video.mp4`, `hero-poster.jpg`,
  `jens-stentoft-portrait.jpg`, `jens-stentoft-card.jpg`,
  `jens-stentoft-featured-slagelse.jpg`).

### Tilføjet
- 5 portefølje-billeder, der lå i mappen men ikke var brugt nogen steder
  (nu `gallery-10.jpg` til `gallery-14.jpg`), tilføjet til forsidens
  portefølje-galleri.
- Oprettet `docs/`, `memory/decisions.md` og `reports/`-struktur for projektet
  (fandtes ikke tidligere).

### Verificeret
- Grep-tjek at ingen referencer til gamle filnavne eller "MURALIA" (uden "HOUSE
  OF") er tilbage i `index.html` / `jens-stentoft.html`.
- Alle `src=`/`poster=`-stier i begge HTML-filer bekræftet at pege på filer,
  der faktisk findes på disk.
- Sidens tekstindhold verificeret via browser-preview (title, nav, hero,
  footer viser korrekt det nye navn).

### Fejl fundet og rettet
- `jens-stentoft.html` havde en ødelagt Google Fonts-URL (manglende `?` foran
  `family=Playfair+Display...`), som ville have fejlet i at hente fonten.
  Rettet til korrekt query-string-syntaks.
