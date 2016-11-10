
NextMove!
===================
NextMove er arbeidsnavnet på neste generasjon programmeringsgrensesnitt (API) for sending og mottak av meldinger for en virksomhet.

Grensesnittet er utformet basert på innspill mottatt i workshop som Difi har gjennomført med flere interessenter høsten 2016 rundt fremtidig grensesnitt på innsiden av integrasjonspunktet.

## Basis flyt
```sequence
Avsender->IP: Hvilke meldinger støtter mottaker?
IP->Adresseregister: Oppslag
Adresseregister->IP: Støtter meldinger
IP->Avsender: Hurra!
```

### UML diagrams

You can also render sequence diagrams like this:

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

And flow charts like this:

```flow
st=>start: Start
e=>end: Sendt
adresse=>operation: Støtter meldingstype x?
opprett=>operation: Opprett melding av type x?
vedlegg=>operation: Legg til flere vedlegg
send=>operation: Støtter meldingstype x?
cond=>condition: Ja eller nei?

st->adresse->cond->opprett
cond(yes)->e
```
