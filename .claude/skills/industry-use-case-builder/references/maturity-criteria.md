---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---
# Criteri di valutazione della maturità del caso d’uso

## Livelli di maturità

### Fondamentale

**Badge:** `[!BADGE Foundational]{type=Neutral}`

Un caso d&#39;uso è **Fondamentale** quando:

- Viene mappato a un pattern attivato da un singolo passaggio o da un evento (Messaggistica attivata da eventi, Attivazione messaggi in uscita in batch)
- Ha requisiti di dati semplici (tipo di evento singolo, attributi di profilo standard)
- Richiede funzionalità di IA/ML minime o assenti
- Utilizza la consegna del canale standard (e-mail, SMS, push) senza orchestrazione complessa
- Dispone di modelli di implementazione consolidati con procedure ottimali chiare
- Richiede meno integrazioni di sistema (in genere 1-2 origini dati)

**Pattern tipici:** messaggistica attivata da eventi, attivazione di messaggi in uscita in batch

**Esempi:** recupero carrello abbandonato, promemoria appuntamenti, notifiche di servizio, avvisi di riduzione prezzo, promemoria di pagamento fatture

### Emergente

**Badge:** `[!BADGE Emerging]{type=Informative}`

Un caso d&#39;uso è **emergente** quando:

- Mapping a un pattern di personalizzazione o con più passaggi (Percorso orchestrato con più passaggi, Personalization con visitatori noti, consigli comportamentali, Personalization con visitatori anonimi)
- Richiede la raccolta e l&#39;analisi di dati comportamentali
- Utilizza modelli di consigli per la risoluzione del profilo visitatore noto
- Coinvolge sequenze di sviluppo multi-touch con logica di diramazione
- Ha una complessità di integrazione moderata (2-4 origini dati)
- Può richiedere l’attivazione del pubblico o il targeting basato su segmenti

**Pattern tipici:** Percorso orchestrato con più passaggi, Web/app Personalization con visitatore noto, consigli comportamentali, Web Personalization con visitatore anonimo, Audience Activation B2B

**Esempi:** serie di benvenuto, campagne di adesione ai farmaci, dashboard di account personalizzati, punteggio di lead, consigli sui contenuti

### Avanzate

**Badge:** `[!BADGE Advanced]{type=Caution}`

Un caso d&#39;uso è **Avanzato** quando:

- Mapping a un pattern di orchestrazione decisionale o cross-channel (Percorso cross-channel con decisioning, Offer Decisioning)
- Richiede un punteggio di previsione o tendenza basato sull’intelligenza artificiale
- Utilizza una logica decisionale centralizzata su più canali simultaneamente
- Coinvolge un&#39;orchestrazione complessa con decisioni in tempo reale in più punti del percorso
- Ha un&#39;elevata complessità di integrazione (oltre 4 origini dati, feed dati in tempo reale)
- Richiede regole aziendali sofisticate, gestione delle priorità e governance delle frequenze

**Pattern tipici:** Percorso cross-channel con decisioning, Offer Decisioning

**Esempi:** prevenzione dell&#39;abbandono con punteggio AI, consigli di prodotti per le fasi di vita, ottimizzazione cross-selling, personalizzazione del programma fedeltà, offerte esclusive VIP

## Flusso di lavoro di valutazione

1. Identificare il pattern del caso d’uso associato al caso d’uso
2. Controlla l’elenco &quot;Pattern tipici&quot; qui sopra per una corrispondenza rapida
3. Se il modello non indica chiaramente la maturità, valuta la complessità dei dati, i requisiti di IA/ML e l’ambito di integrazione
4. Presentare la valutazione all&#39;utente con una motivazione: &quot;In base alla mappatura pattern ({pattern}) e {key factors}, classificherei come {level} perché {reasoning}.&quot;
5. Consenti all&#39;utente di confermare o ignorare prima di procedere
