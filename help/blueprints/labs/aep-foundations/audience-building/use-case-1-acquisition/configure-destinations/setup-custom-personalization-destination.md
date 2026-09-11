---
hold: true
title: Impostare una destinazione Personalization personalizzata
description: Configura una destinazione Personalization personalizzata per inviare gli attributi del profilo ad Edge Network per l’utilizzo in tempo reale da parte di un sistema di personalizzazione di terze parti.
doc-type: article
solution: Experience Platform
exl-id: 46073f7c-00f4-4a4f-9fa3-8827ef15ec4a
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Impostare una destinazione Personalization personalizzata

L&#39;utilizzo di una [destinazione Personalization personalizzata](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/personalization/custom-personalization) consente di rendere disponibili i tipi di pubblico in Edge per l&#39;utilizzo da parte di terzi, in genere tramite l&#39;API server di rete, da utilizzare per la personalizzazione.

Questa esercitazione configura la destinazione Personalization personalizzata in modo da poter inviare gli attributi del profilo ad Edge.



## Sfoglia catalogo di destinazione

>[!NOTE]
>
>Per la personalizzazione tramite Adobe Target, si utilizzerebbe la [destinazione Adobe Target.](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/personalization/adobe-target-v2) Il comportamento è identico a Personalization personalizzato.

1. Nella barra a sinistra, fai clic su **Destinazioni**
1. Nella barra superiore, fai clic su **Catalogo**
1. Selezionare la categoria di **Personalization**
1. Al centro della schermata dovrebbe essere visualizzata la destinazione con titolo **Personalization personalizzato con attributi.** Fare clic sul pulsante **Configura** sulla scheda.

![Sfoglia il catalogo di destinazione per la destinazione Personalization personalizzata](assets/setup-custom-personalization-destination-browse-destination-catalog.png "Sfoglia il catalogo di destinazione per la destinazione Personalization personalizzata")



## Configurare la destinazione

### Configura account

Assegna un nome all&#39;account `DEP Labs Custom PZN`, quindi fai clic sul pulsante **Connetti alla destinazione**

![Creare un account PZN e connettersi alla schermata di destinazione](assets/setup-custom-personalization-destination-create-pzn-account.png)



### Aggiungi dettagli destinazione

Compila i seguenti dettagli sulla destinazione:

1. Nome -> **Destinazione Edge**
1. Alias integrazione -> **edgeAlias**
1. ID dello stream di dati -> *seleziona il nome dello stream di dati creato in precedenza*
1. Al termine, fai clic sul pulsante **Avanti**

![Inserisci i dettagli della destinazione](assets/setup-custom-personalization-destination-fill-destination-details.png "Inserisci i dettagli della destinazione")

>[!CAUTION]
>
>Dopo aver fatto clic su Avanti non sarà possibile modificare **Name** o **Integration alias**.  Questi elementi verranno visualizzati più avanti nelle risposte di Edge Network



### Seleziona criterio di governance

Seleziona **Personalization in loco**, quindi fai clic sul pulsante **Crea**

![Seleziona criterio di governance](assets/setup-custom-personalization-destination-select-governance-policy.png "Seleziona criterio di governance")

>[!NOTE]
>
>Anche se questo passaggio è facoltativo, è consigliabile che a qualsiasi destinazione creata sia assegnato un criterio di governance per evitare di attivare erroneamente i profili



Al termine, dovresti vedere questa schermata che mostra il tuo successo.

![Creazione destinazione PZN completata](assets/setup-custom-personalization-destination-successful-creation-screen.png "Creazione destinazione PZN completata")



## Attiva destinazione

### Seleziona tipi di pubblico

Seleziona la destinazione appena creata facendo clic sulla riga per evidenziarla, quindi fai clic sul pulsante **Successivo**

![Seleziona destinazione PZN](assets/setup-custom-personalization-destination-select-destination-row.png "Seleziona destinazione PZN")



Seleziona **Tutti i tipi di pubblico** e fai clic su **Avanti**

![Seleziona tipi di pubblico PZN](assets/setup-custom-personalization-destination-select-all-audiences.png "Seleziona tipi di pubblico PZN")



### Mappatura

Aggiungi un **nuovo mapping** come segue:

| Campo Source | Campo di destinazione |
| ---------------------- | ------------ |
| \_tenantName.plan.name | Nome piano |

&#x200B;> [!NOTE]
>
>Ricorda di sostituire **\_tenantName** con il nome tenant

>[!NOTE]
>
>Il campo di destinazione consente di fornire un nome descrittivo che può essere diverso dal nome XDM



Al termine della procedura, lo schermo dovrebbe essere simile all&#39;immagine seguente.  Puoi quindi fare clic sul pulsante **Avanti**

![Crea mapping PZN](assets/setup-custom-personalization-destination-create-mapping.png "Crea mapping PZN")

>[!NOTE]
>
>Poiché gli attributi del profilo possono contenere dati sensibili, tutte le [chiamate API server Edge Network](https://experienceleague.adobe.com/it/docs/experience-platform/edge-network-server-api/overview)devono essere effettuate in un contesto autenticato per recuperare l&#39;attributo una volta inserito in Edge.


### Revisione

Nella schermata finale è possibile esaminare i dettagli della configurazione e quindi fare clic sul pulsante Fine.

![Rivedi e pubblica destinazione PZN](assets/setup-custom-personalization-destination-review-and-publish.png "Rivedi e pubblica destinazione PZN")

>[!NOTE]
>
>Questo è il punto in cui [Imposizione automatica](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/enforcement/auto-enforcement) controllerà in base ai tuoi [Criteri di utilizzo dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/policies/overview). Verifica le azioni di marketing con le regole create e genera eventuali errori.
