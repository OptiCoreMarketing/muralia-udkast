# House of Muralia

Statisk markedsføringssite for et eksklusivt mural art-bureau, der repræsenterer
gadekunstnere/muralister over for bygherrer, kommuner og virksomheder.

## Arkitektur

- Ren HTML + Tailwind (via CDN, `cdn.tailwindcss.com`) — ingen build-step, ingen
  framework, ingen server-side kode.
- Én side pr. kunstner (`jens-stentoft.html` er den første). Forsiden
  (`index.html`) linker ind til hver kunstner-underside fra "Kunstnere"-sektionen.
- Billeder og video ligger direkte i rodmappen og refereres med relative stier.
  Navngivning: `gallery-NN.jpg` for portefølje-galleriet, `<kunstner-navn>-*.jpg`
  for kunstnerspecifikke billeder, `hero-*` for forsidens hero-sektion.

## Sådan køres det lokalt

Ingen build nødvendig — åbn `index.html` direkte i en browser, eller kør en
simpel statisk server fra mappen, fx:

```bash
python -m http.server 8080
```

og åbn `http://localhost:8080`.

## Tilføj en ny kunstner

1. Kopiér `jens-stentoft.html` som skabelon til `<kunstner-navn>.html`.
2. Udskift billeder, bio, erfaring-tags og "Udførte værker"-metabox.
3. Tilføj et nyt `artist-card` i `index.html`'s kunstner-grid, der linker til
   den nye side (erstat "+ Ny Kunstner"-pladsholderen).
