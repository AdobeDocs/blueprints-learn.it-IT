---
hold: true
title: Parte 2 - Settori chiave
description: Identifica i campi di identità principali, di persona e di relazione più i campi obbligatori di Experience Event nelle tabelle ERD etichettate.
doc-type: article
solution: Experience Platform
exl-id: 24b6fdbd-0d59-4fe7-828e-c4bc7036db90
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---


# Parte 2 - Settori chiave

## Lezione

Questo video illustra come identificare l’identità principale, le identità delle persone e le identità di relazione in ogni tabella, oltre ai campi _id, timestamp e tipo di evento richiesti per gli eventi esperienza.

>[!VIDEO](https://video.tv.adobe.com/v/3459085/?quality=12&learn=on)



## Dettagli laboratorio

### Campi di identità

- **Identità persona** - Utilizzata per identificare in modo univoco una persona. Vengono utilizzati solo nelle tabelle di entità principale. Deve esserci almeno uno di questi, ma ce ne può essere più di uno.
- **Identità di relazione (ovvero non persona)** - Utilizzata per descrivere le relazioni dalle tabelle di entità primaria del profilo cliente in tempo reale a una classe di entità di supporto associata (ovvero le ricerche).
- **Identità primaria** - Può essere un&#39;identità di persona o un&#39;identità di relazione (non persona) che viene utilizzata come chiave di archiviazione e richiesta per qualsiasi schema utilizzato dal profilo cliente in tempo reale. Anche per le tabelle di entità principale l’identità identifica in modo univoco una persona. Se specificato per schemi di profilo XDM e schemi di ricerca, questo campo determina se viene creato un nuovo record o se viene aggiornato un record esistente. Deve esserci esattamente uno di questi.

### Campi obbligatori (solo XDM Experience Event)

- **\_id** - utilizzato da Real-Time Customer Profile insieme all&#39;identità primaria per creare una chiave di archiviazione univoca per l&#39;evento. Necessario per evitare la duplicazione accidentale dei dati evento all’interno del servizio profili
- **Marca temporale** - tutti gli eventi si verificano in un momento specifico e pertanto ogni evento richiede una marca temporale

Non obbligatorio ma fortemente incoraggiato:

- **Tipo evento**: descrive il comportamento di alto livello dei dati dell&#39;evento (ad esempio acquisto, prenotazione prenotata, ecc.)

### Norme generali

1. #2 regola tabella Bridge: nelle situazioni in cui esiste una tabella bridge tra un elemento padre &quot;**P**&quot; o &quot;**E**&quot; (ovvero una tabella padre) e una tabella &quot;**L**&quot;, la tabella bridge viene considerata parte della tabella padre
1. In questa fase, verifica sempre che le identità siano univoche per una persona **singola** per evitare la rielaborazione durante l&#39;acquisizione dei dati
1. Per gli schemi Experience Event, l’identità principale è ciò che identifica in modo univoco tale comportamento per una singola persona.
1. Per le tabelle di ricerca, la chiave primaria (PK) del modello relazionale sarà sempre l’identità primaria non-persona

Per ogni tabella dell&#39;ERD di Connection 5G Warehouse e dell&#39;ERD di streaming etichettata come **&quot;P&quot;, &quot;E&quot; o &quot;L&quot;,** è ora necessario eseguire i passaggi seguenti per identificare le identità primarie, le identità di persona, le identità di relazione e tutti i campi obbligatori per le classi di schema specificate.

>[!NOTE]
>
>Fai riferimento al diagramma seguente durante i laboratori quando etichetti le identità sugli schemi
>
>![Diagramma che mostra le etichette di identità primaria, identità persona e identità relazione applicate alle tabelle ERD](assets/part-2-key-fields-identity-labeling-diagram.png)



## Passaggio 1: etichettare i campi chiave nelle tabelle dei singoli profili XDM

Per identificare i campi chiave nella tabella Account cliente, effettua le seguenti operazioni:

- Identifica il campo che verrà utilizzato come identità primaria e lo etichetta con `PI`
- Identifica tutte le altre identità della persona e le etichetta con `I`
- Identificare le identità di relazione ed etichettarle con `R`



## Passaggio 2: etichettare i campi chiave nelle tabelle XDM Experience Event

Esegui lo stesso set di attività eseguito nel passaggio 1, ma ora per le tabelle XDM Experience Event:

- Identifica il campo in ogni tabella che sarà l&#39;identità primaria e lo etichetta con `PI`
- Identifica tutte le altre identità persona in ogni tabella e le assegna un&#39;etichetta `I`
- Identifica tutte le identità di relazione ed etichettale con `R`

Oltre alle etichette di cui sopra, etichettare anche quanto segue:

- Identifica o crea l’ID evento univoco per ogni tabella XDM Experience Event e assegnagli un’etichetta `_id`
- Identifica la marca temporale dell&#39;evento per ogni tabella ed etichettala con `T`
- Identificare o creare il Tipo di evento per ogni tabella ed etichettarlo con un `ET`



## Passaggio 3: etichettare i campi chiave nelle tabelle di ricerca

Identificare in ogni tabella di ricerca il campo che sarà Identità primaria e etichettarlo con `PI`



## Revisione

Il video seguente esamina i campi chiave identificati nelle tabelle Connection 5G, tra cui il motivo per cui un campo concatenato era necessario come ID evento univoco per i record di ordini mutabili.

>[!VIDEO](https://video.tv.adobe.com/v/3459088/?quality=12&learn=on)
