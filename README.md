# Gangen in Amsterdam

De [Alfabetische Lijst van Gangen in Amsterdam](http://opleid.info/alfabetische-lijst-van-gangen-in-amsterdam-samengesteld-door-w.html), samengesteld door Willem Blok, is een waardevol naslagwerk voor een ieder die de geschiedenis van Amsterdam bestudeert.

De lijst vermeldt van duizenden gangnamen in welke bronnen ze aangetroffen zijn en op welke gang ze betrekking hebben (voor zover dat met zekerheid te zeggen is).

Het werk bouwt voort op de [Alphabetische Lijst van Gangen te Amsterdam](https://www.delpher.nl/nl/boeken/view?coll=boeken&identifier=MMUBL07%3A000000035%3A00004), samengesteld door Dr. Joh. C. Breen.

## Van naslagwerk naar data

Om de lijst wat [gestructureerder](bb.csv) te maken (voor gebruik in machinale toepassingen) heb ik het tekstdocument opgeknipt in records en elk record een id gegeven, het zgn. BBid (naar Breen en Blok, natuurlijk).

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

Er komt nog een hoop voor verdere schoning en verbetering in aanmerking. Ik heb me nu nog vooral gericht op de gangnamen die al door Breen genoemd worden (in de lijst van Blok herkenbaar aan de 'B:' achter de gangnaam, in de data ook aan de waarde 'ja' in het veld `breen`).

## Van adres naar geometrie

Dankzij de in de lijst vermeldde adressen en het werk van [HisGis](http://www.hisgis.nl/), dat recentelijk de 25000+ adressen van de Loman Buurtkaarten heeft ingetekend (link volgt zodra bekend), kunnen we een aanzienlijk deel van de gangen op de kaart tonen.

- [gangen die reeds op Adamlink voorkwamen](adamlink.geojson), grotendeels geautomatiseerd gekoppeld op basis van naam en nabijheid, deels handmatig (484 namen, 337 gangen)
- [gangen geplaatst op basis van het 1876 nummer](adressen1876.geojson) (393 namen, 313 gangen)
- [gangen geplaatst op basis van het kleinnummer](kleinnummers.geojson) (186 namen, 159 gangen)

De nauwkeurigheid waarmee de 1876 adressen zijn geplaatst is groot. Dit ligt anders bij plaatsing op basis van de kleinnummers. HisGis zelf maant tot voorzichtig gebruik van de kleinnummerlocaties, omdat die vooral gebaseerd zijn op het niet altijd even betrouwbare [omnummerregister](https://www.amsterdam.nl/stadsarchief/archief/downloads/omnummerregister/).

Nu is het zo dat de gangen met 1876 adres meestal ook een kleinnummer hebben. Het verschil daartussen heb ik opgemeten, en dat bleek gemiddeld 24 meter (laten we de 14 gevallen boven de 100 meter buiten beschouwing 16 meter). Wat opviel is dat de kleinnummers vaak aan de straat lagen, terwijl de 1876 nummers de in het blok gelegen adressen waren - dat verklaart ook een deel van de afstand. Al met al vond ik dat voldoende vertrouwen geven om de gangen met enkel een kleinnummer toch te geocoderen.

Op de naamloze gangen na zijn alle gangen die in de drie geojsonbestanden voorkomen inmiddels opgenomen in het Adamlink stratenregister.

## licentie

[![cc-by-sa](https://licensebuttons.net/l/by-sa/3.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) 

De BB-dataset wordt aangeboden onder een [CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/) licentie
