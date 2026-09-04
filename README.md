# De lange reis

Cadeau voor Ruben. Staat live op https://chef1992.github.io/delangereis/ en is
te bereiken via de QR-code op de A0-poster.

Alles zit in `index.html`. Eén bestand, geen build, geen afhankelijkheden.
De foto's zitten in het bestand zelf ingebakken, dus er kan geen plaatje ontbreken.

## Hoe het loopt

1. Openingsscherm met de foto en de belofte dat hij rijkelijk beloond wordt
2. Briefkaart met een woordje vooraf
3. Drie vragen, elk met een foto op de voorkant
4. Een teller die aftelt naar 3 februari 2027

Eén fout antwoord is meteen raak: hij gaat naar de FOUT-pagina en begint overnieuw.

## Iets aanpassen

Open `index.html` en zoek op `INSTELLINGEN`. Alles wat je wilt wijzigen staat
in dat blok bij elkaar:

| Wat | Waar |
|---|---|
| Datum en tijdstip van de teller | `DOEL` |
| Datum onder de teller (leeg = verborgen) | `DATUMTEKST` |
| Tekst op het openingsscherm | `INTROTEKST` |
| Tekst op de briefkaart vooraf | `VOORAF` |
| Tekst op de tellerkaart | `WACHTTEKST` |
| Tekst als de datum voorbij is | `OPENTEKST` |
| Naam op de foutpagina | `NAAM` |
| Aantal pogingen per vraag | `MAX_POGINGEN` |
| De vragen zelf | `RONDES` |

### Let op de tijdzone

In `DOEL` staat `+01:00`. Dat is wintertijd. Valt je datum tussen eind maart
en eind oktober, gebruik dan `+02:00`, anders opent het een uur te vroeg.

### Een kaart toevoegen

In `RONDES`, komma achter de vorige kaart en dan:

```js
{ type:"tekst", tekst:"Een handgeschreven briefje." }

{ type:"foto",
  foto:"fotos/naam.jpg",
  bijschrift:"Regel onder de foto." }

{ type:"vraag",
  foto:"fotos/naam.jpg",
  bijschrift:"Regel onder de foto.",
  vraag:"Je vraag?",
  goed:["antwoord","ook goed"],
  hint:"Verschijnt alleen als MAX_POGINGEN hoger dan 1 staat.",
  na:"Wat er verschijnt als hij het goed heeft." }
```

Bij `goed` is één treffer genoeg. Gebruik `alle:[...]` als álle woorden erin
moeten staan, zoals bij de naamvraag. Hoofdletters, spaties en leestekens
worden genegeerd.

Nieuwe foto's zet je in een map `fotos` naast `index.html`. De drie bestaande
foto's zitten ingebakken en staan onderaan het script; daar hoef je niets aan
te doen.

## Deel 2

Op 3 februari 2027 vervang je `index.html` door de volgende versie. De link
en de QR-code blijven werken. Zeg tegen hem dat hij de pagina moet verversen,
dat staat ook op het scherm zodra de teller nul is.

## Waar je op moet letten

De antwoorden staan gewoon leesbaar in `index.html`. Wie de broncode opent of
deze repo bekijkt, ziet ze staan. Voor dit doel prima, maar stuur de repo dus
niet naar Ruben.
