---
title: Visualizza schema
description: Visualizza i descrittori di identità di uno schema tramite l’interfaccia utente e l’API e confronta le opzioni di intestazione Accept per le risposte dello schema risolte e non risolte.
doc-type: article
solution: Experience Platform
exl-id: 44eedb82-259f-4f7f-84fe-acc2b42376eb
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Visualizza schema

## Visualizza tramite l’interfaccia utente

1. Apri il browser e torna alla sezione `Schema -> Browse`.
1. Cerca lo schema **Account cliente**
1. Le identità vengono aggiunte allo schema

![Visualizzazione esplorazione schema che mostra le identità aggiunte allo schema](assets/view-schema-schema-ui-with-identities.png "Visualizzazione interfaccia utente schema con identità")


## Visualizza tramite API

1. Selezionare l&#39;API `Step 3 - Get Customer Account Schema and its descriptors` facendo clic su di essa.

   ![Passaggio 3 - Ottieni schema account cliente con richiesta API descrittori](assets/view-schema-step-3-get-customer-account-schema-w-descriptors.png "Passaggio 3 - Ottieni schema account cliente con descrittori")



1. Nell&#39;URL della richiesta sostituisci `<replace me>` con `$meta:altId` salvato dalla sezione precedente (Crea schema) alla fine della chiamata come mostrato di seguito

   ![Richiesta passaggio finale 5 con altId aggiunto all&#39;URL](assets/view-schema-final-step-5-request.png "Richiesta passaggio finale 5")



1. Salva le modifiche apportate alla richiesta

1. Eseguire la richiesta facendo clic sul pulsante `Send`

Dovresti visualizzare una risposta `200 OK` e poter sfogliare lo schema creato attraverso l&#39;obiettivo della struttura JSON XDM

![Corpo della risposta API che mostra la struttura JSON XDM dello schema](assets/view-schema-body-of-the-api-response.png "Corpo della risposta API")



Sfoglia più in basso nella risposta API per visualizzare i descrittori di identità creati

![Descrittori identità visualizzati nella risposta API](assets/view-schema-descriptors-displayed-in-api-response.png "Descrittori visualizzati nella risposta API")


## Accetta intestazioni

Nota l&#39;intestazione **Accept** utilizzata nella richiesta. Questa intestazione comunica al registro dello schema XDM di restituire `$refs` dello schema non risolto (ovvero mostrare la quantità minima di informazioni) insieme ai relativi descrittori associati nella risposta API.  Adobe fornisce altre intestazioni **Accept** che è possibile utilizzare per ottenere vari gradi di dettaglio sullo schema.

![Accetta campo intestazione nel passaggio 3 Ottieni richiesta schema account cliente](assets/view-schema-accept-header.png "Passaggio 3 - Ottieni intestazione accettazione schema account cliente")

>[!NOTE]
>
>Puoi trovare ulteriori informazioni sulle varie intestazioni Accept qui -> [Endpoint API dello schema di Experience League](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/schemas.html?lang=it#lookup)



Per vedere questo in azione, modifica l&#39;intestazione **Accept** per indicare al Registro di sistema dello schema di rispondere con tutti i `$ref` e `allOf` completamente risolti (cioè esplosi) ed eventuali descrittori associati

1. Aggiorna il valore dell&#39;intestazione `Accept` nel modo seguente:
   `application/vnd.adobe.xed-full-desc+json; version=1`
1. Salva la richiesta utilizzando il pulsante `Save`
1. Eseguire la richiesta utilizzando il pulsante `Send`

Dovresti trovare una risposta ora simile alla seguente:

![Risposta schema esplosa che mostra tutte le proprietà risolte](assets/view-schema-fully-exploded-schema-showing-all-properties.png "Schema esploso che mostra tutte le proprietà")

>[!NOTE]
>
>Osserva come tutte le proprietà dello schema sono ora completamente visualizzate nella risposta, mentre nella chiamata precedente venivano mostrati solo i valori `$ref` dello schema (ovvero i gruppi di campi a cui faceva riferimento) e nulla era completamente risolto per ogni singolo campo/proprietà.

>[!NOTE]
>
>Questo è importante da capire perché quando si lavora con le API non è sempre necessario ricevere una risposta completamente risolta se tutto ciò che si sta facendo è ottenere `$id` dello schema o semplicemente verificarne la composizione
