---
layout: page
title:  "Bakgrunn"
---

NextMove er arbeidsnavnet på neste generasjon programmeringsgrensesnitt (API) for sending og mottak av meldinger for en virksomhet.

Utgangspunktet 
-------------------
Dersom man ser på offentlig sektor som en stor distribuert organisasjon med varierende digital modenhet, så er meldingsorienterte asynkrone løsningsarkitekturer blitt en defacto måte å oppnå løse koblinger slik at man unngå gjensidige avhengigheter.

Alternative arkitekturer kan være prosessorienterte (brukerorienterte) eller funksjonsorienterte (forretningstjenester) løsningsarkitekturer. Svakeheten med disse blir fort at man får stor fokus på gjenbruk gjennom sentralisering. Utfordringen blir ofte at man innfører flaskehalser eller "single point of failure", eller at man får overlappende/konkurrende løsninger fordi utbredelse ikke går fort nok.

Ved å la hver enkel deltaker fokusere på å produsere og konsumere meldinger i en asynkron meldingsinfrastruktur så kan man snu dette til en fordel. Det er lettere å å tilby "0-alternativ" løsninger slik at alle kan ta i bruk løsningene fort, samtidig som at man gradvis kan innføre nye sentrale tjenester som virksomhetene tar i bruk etter behov. 

Integrasjonspunktet
-------------------

Integrasjonspunktet er per definisjon grenselinjen mellom det interne og eksterne miljøet. Intensjonen er at denne grenselinjen skal være så enkel som mulig. Erfaring viser at det kan være aktuelt å eksponere enkelte tjenester gjennom integrasjonspunktet. Dette vil være tjenester som i dag medfører kompleksitet for hver enkel leverandør, men der vi alle kan ha stor nytte av at det er en felles løsning. Eksempel på dette kan være tjenester for å bygge en sikker melding (lage ASIC-kontainer) og lokal eksponering av nasjonale tjenester relatert til adressering. En mulig tanke er at man legger alle tjenester som krever virksomhetssertifikat inn i integrasjonspunktet. Hvilke applikasjonstjenester trengs for avsender, og hvor bør de realiseres?
Ved mottak av en melding, er det behov for en tilsvarende fordeling av ansvar. 

* Hvem validerer at meldingen er korrekt?
* Hvordan skal denne gjøres tilgjengelig for de løsninger som skal håndtere meldingen lokalt?
* Skal vi legge opp til en push eller pull arkitektur, eller begge deler?
* Skal vi ha forskjellige strategier for å håndtere meldinger basert på størrelse? (strømmende vs pull baserte grensesnitt). 

Grensesnittet er utformet basert på innspill mottatt i workshop som Difi har gjennomført med flere interessenter høsten 2016 rundt fremtidig grensesnitt på innsiden av integrasjonspunktet.
