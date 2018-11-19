# Gangen in Amsterdam

De [Alfabetische Lijst van Gangen in Amsterdam](http://opleid.info/alfabetische-lijst-van-gangen-in-amsterdam-samengesteld-door-w.html), samengesteld door Willem Blok, is een waardevol naslagwerk voor een ieder die de geschiedenis van Amsterdam bestudeert.

De lijst vermeldt van duizenden gangnamen in welke bronnen ze aangetroffen zijn en op welke gang ze betrekking hebben (voor zover dat met zekerheid te zeggen is).

Het werk bouwt voort op de [Alphabetische Lijst van Gangen te Amsterdam](https://www.delpher.nl/nl/boeken/view?coll=boeken&identifier=MMUBL07%3A000000035%3A00004), samengesteld door Dr. Joh. C. Breen.

## Van naslagwerk naar data

Om de lijst wat [gestructureerder](bb.csv) te maken (voor gebruik in machinale toepassingen) heb ik het tekstdocument opgeknipt in records en elk record een id gegeven, het zgn. BBid (van Breen en Blok, natuurlijk).

Zowel gangen als straten heb ik zo veel mogelijk gekoppeld aan [Adamlink straten](https://adamlink.nl/geo/streets/list).

Elk record heeft de volgende velden:

- `BBid` het B[lok]B[reen] id
- `naam` de naam of aanduiding van de gang
- `uri` de Adamlink URI van de gang
- `straatnaam` de naam van de straat
- `straat_uri` de Adamlink URI van de straat
- `breen` 'ja' als al genoemd in Breen, anders 'nee'
- `kleinnr` het aan de gang gelegen [kleinnummer](https://www.amsterdam.nl/stadsarchief/nieuws/omnummering/)
- `nr1876` het aan de gang gelegen huisnummer volgens de 'huidige' nummering, zoals te zien op de Loman buurtkaarten
- `tekst` de oorspronkelijke tekst zoals die in de lijst voorkomt

Realiseert u zich dat er aan de data nog een hoop te verbeteren valt. Ik heb me nu nog vooral gericht op de gangnamen die al door Breen genoemd worden (in de lijst van Blok herkenbaar aan de 'B:' achter de gangnaam, in de data ook aan de waarde 'ja' in het veld `breen`).

## Van adres naar geometrie

Dankzij de in de lijst vermeldde adressen en het werk van [HisGis](http://www.hisgis.nl/), dat recentelijk de 26000+ adressen van de Loman Buurtkaarten heeft ingetekend (link volgt zodra bekend), kunnen we al heel wat gangen op de kaart tonen.

- [gangen die reeds op Adamlink voorkwamen](adamlink.geojson), deels geautomatiseerd gekoppeld op basis van naam en nabijheid, deels handmatig (484 namen, 337 gangen)
- [gangen geplaatst op basis van het 1876 nummer](adressen1876.geojson)
- [gangen geplaatst op basis van het kleinnummer](kleinnummers.geojson)
