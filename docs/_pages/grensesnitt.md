---
layout: page
title: Grensesnitt
---

Forslått grensesnitt er basert på en REST-tjeneste tankegang som implementerer et [AbstractFactory](https://en.wikipedia.org/wiki/Abstract_factory_pattern) mønster, samtidig som at det delvis er inspirert [HATEOAS](https://en.wikipedia.org/wiki/HATEOAS).

Utgangspunktet er at hver melding består av tre nøstede lag:

<div class="mermaid">
graph LR
subgraph Konvolutt 
el1[<b>Standard Business Document Header</b><br/> brukt til ruting av meldingen frem til mottaker]
subgraph Forretningsmelding
el2[<b>Meldingsspesifikk struktur</b><br/>brukt til effektiv håndtering av mottak]
subgraph Innhold
el3[<b>ASIC-E med innhold</b><br/>En eller flere filer med strukturert informasjon som skal frem til mottaker]
end
end
end
</div>

Hver melding blir i utgangspunktet en unik ressurs i grensesnittet, og kan i løpet av livsløpet sitt spores og endres gjennom denne ressurslenken. 

For å sikre høyest mulig kvalitet så tilbyr grensesnittet oppslag mot hvilke typer meldinger det lokale endepunktet søtter, samt tilby mulighet til å hente ut maler/prototyper på meldinger. I praksis er dette de to ytterste lagene i meldingsstrukturen, det vil si konvolutten (SBDH) og det forretningsmeldingsformatet som er assosiert med meldingstypen. Innholdet som skal frem til mottaker blir lagt til med et egne kall, slik at det i fremtiden er mulig å støtte flere forskjellige løsninger (mellom annet tilpasse for opplasting av store filer).

Tanken med denne løsningsarkitekturen er at man skal kunne integrere individuelle/tilpassede valideringsløsninger for hver meldingstype. Et annet motiv er at man skal eliminere behovet for virksomhetssertifikater andre plasser enn i integrasjonspunktet.

Dette gir en sekvens på opplasting:

<div class="mermaid">
sequenceDiagram
Fagløsning->> IP_types: Støtte meldingstype?
IP_types->> Fagløsning: Liste av meldingstyper 
Fagløsning->> IP_types: Få prototype/mal?
IP_types->> Fagløsning: Mal med obligatoriske felter
Fagløsning->> IP_message: Opprette melding basert på mal
Fagløsning->> IP_message: Legg til dokument i payload
IP_message->> Validator: Gydlig melding?
Validator->> IP_message: ok
IP_message->> Sertifikat: signer og evt. krypter
IP_message->> IP_message: Gjer klar til sending
Fagløsning->> IP_message: Send
</div>