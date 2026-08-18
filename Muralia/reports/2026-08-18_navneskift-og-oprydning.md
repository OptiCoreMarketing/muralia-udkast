# Navneskift til House of Muralia + oprydning af udkast

**Task:** Skift bureau-navnet fra "MURALIA" til "House of Muralia" og ryd op i
det rodede udkast (filnavne, brand-referencer), som forberedelse til at gå
videre med sitet.
**Udført af:** Claude (Angel)
**Dato:** 2026-08-18
**Status:** Færdig

## Baggrund

Udkastet lå i `Muralia/`-mappen som to statiske HTML-sider (`index.html`,
`jens-stentoft.html`) plus en bunke billeder med kamera-/opload-genererede
filnavne (fx `AGSAGDFASFAE.jpeg`, `725032751_...n.jpg`) og en fil med dobbelt
filendelse (`video.mp4.mp4`). Kunden bekræftede at det nye navn skulle være
"House of Muralia", men navnet stod ikke direkte i den kundesamtale, der blev
delt — så det blev tjekket for ledighed før implementering.

## Ændringer

- **Domænetjek:** `houseofmuralia.dk` og `houseofmuralia.com` bekræftet ledige
  via whois-opslag (punktum.dk / whois.com). Ingen eksisterende brand/virksomhed
  med samme navn fundet ved websøgning.
- **Navneskift:** "MURALIA" → "HOUSE OF MURALIA" i title, nav, hero-tekst,
  footer og kunstner-underside. Kontaktmail opdateret til
  `kontakt@houseofmuralia.dk`.
- **Filnavne:** Alle 18 billeder + video omdøbt til et sigende, konsistent
  skema (se `docs/CHANGELOG.md` for fuld liste). Alle `src=`/`poster=`-
  referencer i begge HTML-filer opdateret tilsvarende.
- **5 ubrugte billeder** (lå i mappen, men var ikke koblet til nogen `<img>`)
  tilføjet til portefølje-galleriet på forsiden, så de faktisk bliver vist.
- Oprettet den faste dokumentationsstruktur (`docs/`, `memory/decisions.md`,
  `reports/`) for projektet, da den ikke fandtes.

## Tests

- **Automatiseret:** Grep-verifikation af at ingen gamle filnavne eller
  "MURALIA" (uden "HOUSE OF") er tilbage i HTML-filerne. Shell-loop, der
  tjekker at hver `src=`/`poster=`-reference i begge HTML-filer faktisk
  peger på en fil, der findes på disk — alle 18 bestået.
- **Manuel verifikation:** Sidens renderede tekstindhold hentet via
  browser-preview (title, nav-menu, hero-tekst, footer) — bekræfter korrekt
  visning af "HOUSE OF MURALIA" og den nye kontaktmail.

## Fejl fundet og rettet

- `jens-stentoft.html` havde en syntaksfejl i Google Fonts-URL'en (manglende
  `?` foran `family=`), som ville have fået fontimporten til at fejle. Rettet
  i samme ombæring.

## Anbefaling / åbne spørgsmål

- Kunden bør selv tjekke navnet "House of Muralia" i DKPTO's varemærkeregister,
  hvis det skal beskyttes formelt — jeg har kun tjekket domæne-ledighed og
  generel websøgning.
- Domænet er endnu ikke registreret/sat op — det er næste skridt, når kunden
  vil "smide domæne på" som nævnt i kundesamtalen.
- Sitet bruger stadig Tailwind via CDN (ingen build-pipeline). Fint til et
  udkast, men bør overvejes ændret til en rigtig build, hvis siden skal være
  produktionsklar og performant.
