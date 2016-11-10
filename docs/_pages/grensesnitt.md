---
layout: page
title: Grensesnitt
---

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