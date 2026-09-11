---
title: Recupera gruppi di campi standard
description: Esegui una query sull’API del registro dello schema globale per trovare e salvare i $id dei gruppi di campi XDM standard necessari per creare uno schema del profilo cliente.
doc-type: article
solution: Experience Platform
exl-id: 62017ece-eef2-4785-afed-5c690c00ed02
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Recupera gruppi di campi standard

>[!NOTE]
>
>**&quot;Gruppo di campi&quot;** era precedentemente indicato come **&quot;Mixin&quot;**, pertanto questi termini possono essere utilizzati in modo intercambiabile nelle richieste API e nella guida.



## Richiedi gruppi di campi standard XDM

1. Fai clic sulla chiamata API `Step 1 - Get XDM Standard Field Groups` nella cartella `XDM Schema Lab -> Create Schema`
1. Eseguire la chiamata facendo clic sul pulsante `Send`



**Richiesta**

![Passaggio 1 - Ottieni richiesta API per gruppi di campi standard XDM](assets/get-standard-field-groups-step-1-request.jpeg "Passaggio 1 - Richiesta")

>[!NOTE]
>
>Nota l&#39;utilizzo del valore `global` nell&#39;URL delle richieste di seguito:
>
>https\://platform.adobe.io/data/foundation/schemaregistry/**global**/mixins
>
>`global` viene utilizzato per richiedere solo componenti standard XDM (gruppo di campi/mixin in questo caso). Esistono due tipi di proprietari nel registro XDM di Experience Platform: Adobe e Tenant (cioè personalizzato).
>
>- Gli oggetti creati da Adobe utilizzano sempre la parola `global` in qualsiasi richiesta di elenco o di ricerca XDM
>- Gli oggetti creati dal tenant (ovvero personalizzati) utilizzano sempre la parola `tenant` in qualsiasi chiamata di ricerca o elenco XDM



**Risposta**

![Risposta API con elenco dei gruppi di campi standard XDM](assets/get-standard-field-groups-step-1-response.png "Passaggio 1 Risposta")


## Identificare i gruppi di campi standard XDM richiesti

Uno schema è sempre composto da uno o più gruppi di campi e da una classe.  Per lo schema Connection 5G Individual Profile, individua i gruppi di campi XDM standard necessari per lo schema.

- Dettagli demografici
- Dettagli di contatto personali
- Dettagli su consenso e preferenze



1. Cerca il gruppo di campi `Demographic Details` nella risposta della chiamata
1. Copia il `$id` del gruppo di campi e salvalo in un punto qualsiasi per riferimento futuro
1. Ripeti i passaggi 1 e 2 per gli altri due gruppi di campi elencati sopra

![Gruppo di campi Dettagli demografici nella risposta API](assets/get-standard-field-groups-demographic-details-field-group.png)

>[!WARNING]
>
>Non continuare finché non avrai salvato tutti e tre (3) `$ids` da qualche parte.  Saranno necessari in un secondo momento per creare lo schema Account cliente
