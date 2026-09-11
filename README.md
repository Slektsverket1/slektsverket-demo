# slektsverket-demo

Den offentlige vareprøven, servert på **demo.slektsverket.no**.

## Dette repoet er en utrulling, ikke en kilde

`index.html` er **generert** av `slektsarkivet` og skal aldri redigeres her.
Kilden er `~/code/slektsarkivet/ut/demo-offentlig.html`, og den kopieres hit av

    python3 ~/code/slektsverket-nettbutikk/demo/rull_ut.py --skriv

Skriptet nekter å legge ut en fil som henter noe utenfra, som nevner «claude»,
eller som bærer demodata-stripa. En demo som henter noe eksternt kan slutte å
virke uten at noen ser det.

## Hvorfor den ligger her og ikke hos Cloudflare

Demoen lå først på `claude.ai/code/artifact/…`. Det var funn 3 i rollelesinga
10.09.2026: butikken bruker en hel seksjon på å svare «Er dette skrevet av KI?»,
og så lå vareprøven på KI-selskapets egen adresse. Slektsforskermiljøet
straffer den mistanken hardt.

Neste forsøk var en Cloudflare Worker. Den virket, men adressen var
`workers.dev` — fortsatt ikke vår. **Et egendefinert domene på en Worker krever
at DNS-sona ligger hos Cloudflare**, og `slektsverket.no` ligger hos Domeneshop
(`ns1.hyp.net`). Å flytte navneservere ville dratt med seg butikken, e-posten og
GSC-verifiseringen.

**GitHub Pages virker med en vanlig CNAME fra hvilken som helst DNS-leverandør.**
Derfor her. Repoet må være offentlig for at Pages skal være gratis — innholdet er
uansett offentlig, og slekta i demoen er oppdiktet.

**Butikken selv var også vurdert.** Demoen kan ikke ligge som en Shopify-sidemal:
temafiler har et tak på 256 KB, og fila er 803 KB. Formen passet ellers — null
`{{` og null `{%`, så Liquid ville ikke tolket noe i den.

## Slekta er oppdiktet

Ingen ekte personopplysninger. Alt annet — formen, kildeføringen, kartet,
tidslinja — er slik en ekte leveranse ser ut.
