# Dokumentasjon til arbeidskrav 1 for PG5500-1 19V

## Innledning

Arbeidskravet omhandlet å kunne få til scrollende tekst via en LED-matrise.
For å få dette til måtte vi ta i bruk en intergrated circut (IC) MAX7219 og en 8x8 LED-matrix 1588AS.
Samme dag vi fikk arbeidskravet jobbet vi med shift-registere og dette gav meg et godt grunnlag for å komme i gang.

## Forstå MAX7219 og 1588AS (Virkemåte)

Det absolutt første jeg gjorde var å finne fram dataarkene til MAX7219 og 1588AS *(vedlegg datasheet1588AS.pdf, datasheetMAX7219)*. 

Deretter ble det å lese seg opp på MAX7219 og finne ut ren betydning av hva PIN-configuration hjelper med. Som vi har lært tidligere kan MAX7219 brukes som et mellomledd i stedet for å måtte bruke alle pin-portene til Arduinoen. Dette frigjør masse ekstra som ved senere anledning kan brukes til å bygge videre på et prosjekt. Med MAX7219 må man dermed kun bruke tre pins til Arduinoen (fem totalt med bruk av GND og 5V). 

Videre gikk det ut på å finne ut av hva DOUT, LOAD (CS), CLK, ISET, og DIN sine pins holder rede på *(1)*

Når det gjaldt LED-matrix 1588AS fant jeg ut at disse er veldig like/identiske med en annen LED-matrix kalt 1088AS.

For å finne ut hvilken orientasjon LED-matrixen skulle ha under oppkobling gjaldt det å finne ut av hva som er rad 1, kolonne 1 og PIN 1. Dette fant jeg fram til under dataarket til 1588AS, og ved å se på undersiden av 1588AS hvor det er markert en liten halvmåne rett under komponentnavnet. 

Under datasheet_2 *(vedlegg datasheet1588as_2.pdf) står det "Forward Voltage: 2.1V - 2.5V" og "Forward Current: 20mA" som tilsier at under tabell 11 i datasheetMAX7219 vil være 25.9-28K kOhm. Derfor har jeg brukt tre 10k resistorer satt sammen som går til ISET pinnen til MAX7219.

## Framgangsmåte/Problemer underveis?

Ved første fire forsøk på oppkobling støttet jeg på ren brukerfeil hvor pins ble feilkoblet, og andre mer merkelige problemer hvor kun noen LEDS lyste opp.

I tilfellet hvor jeg var veldig sikker på at oppkoblingen var korrekt, men ikke alle LED-lysene lyste prøvde jeg ut først å sette kablene i et "zig-zag" mønster som jeg senere valgte å bruke som standard for oppkoblingsskjema og endelig løsning. Dette var et tips jeg leste om hvor at det er en mulighet for at kablene treffer hverandre. I tillegg dro jeg innom Kjell & Company og kjøpte et nytt sett med kabler for å utelukke potensielle problemer.

Når jeg tok i bruk tips om krysskobling på brødkortet og bruk av nye kabler fungerte gikk jeg over til selve kodebiten.

## Beskrivelse av koden

Koden (vedlegg scrollendeText mappe) følger med kommentarer. Videre har jeg brukt et bibliotek (vedlegg MaxMatrix mappe) som et støttebibliotek for å få til scrollende tekts. Har lest igjen .h og .cpp filene for å vite mer om hva de nødvendige funksjonene gjør. Ble en tidsklemme mot slutten og så meg nødt til å få ekstern hjelp for å komme i gang med å sjekke at løsningen fungerte som tiltenkt. Videre har jeg lest på Arduino sin hjemmeside *(2)*   

## Koblingsskjema

**Vedlegg koblingsArk.fzz**


## Hvor jeg har funnet informasjon

*(1) https://www.quora.com/What-is-CS-and-CLK-pin-on-Arduino-Dot-Matrix-What-are-their-functions*  

*(2) https://playground.arduino.cc/Main/MAX72XXHardware?fbclid=IwAR1csC-K0Kczxl1ofEI8a_hfJTQFiQockzvDi0Azup0t9itga62-MBfPT_8*