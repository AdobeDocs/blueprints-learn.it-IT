---
hold: true
title: Monitorare l’evento
description: Utilizza Adobe Experience Platform Assurance per creare una sessione di debug, inviare un evento convalidato tramite Postman e controllare i registri di elaborazione degli eventi edge.
doc-type: article
solution: Experience Platform
exl-id: 94b200c0-6714-4996-a266-119cc8f7f4e2
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 1%

---


# Monitorare l’evento

## Passa ad Assurance

[Adobe Experience Platform Assurance](https://experienceleague.adobe.com/it/docs/experience-platform/assurance/home) è un prodotto di Adobe Experience Cloud che consente di verificare, verificare, simulare e convalidare le modalità di raccolta dei dati nell&#39;Edge di Adobe Experience Platform.

1. Passa a Adobe Experience Platform -> Assurance -> Crea sessione

![Passa ad Adobe Experience Platform Assurance e crea una sessione](assets/monitor-your-event-navigate-to-assurance-create-session.png)



&#x200B;2. Fai clic sul pulsante **Avvia**

![Fare clic sul pulsante Start per iniziare la configurazione della sessione Assurance](assets/monitor-your-event-click-start-button.png)



## Configurare una sessione

1. Nome —> \[Sandbox] Sessione Edge
1. URL —> https\://www\.adobe.com
   - Questo URL verrà sostituito dal sito effettivo del cliente
1. Fare clic sul pulsante Avanti

![Fare clic su Avanti dopo aver immesso il nome della sessione e l&#39;URL](assets/monitor-your-event-click-next-button.png)

&#x200B;4. Copia il collegamento da qualche parte a cui puoi fare riferimento in un secondo momento

&#x200B;5. Fai clic sul pulsante **Fine**

![Copia il collegamento della sessione di Assurance e fai clic su Fine](assets/monitor-your-event-copy-link.png)



&#x200B;6. Passa a **Impostazioni**

![Passa alla scheda Impostazioni nella sessione Assurance](assets/monitor-your-event-navigate-to-settings.png "Fai clic sulle impostazioni")



&#x200B;7. Abilita **Transazioni evento** e **Edge Delivery** facendo clic sul pulsante **+**, quindi **Fine**

![Abilita transazioni eventi e Edge Delivery, quindi fai clic su Fine](assets/monitor-your-event-enable-event-transactions-and-edge-delivery.png)


## Apri Postman

Vai a Postman -> Crea Edge evento web (nessuna autenticazione) -> Intestazioni

1. Aggiungi **x-adobe-aep-validation-token** alle intestazioni con il collegamento copiato in precedenza da Assurance. Prendi **solo il valore ID** dopo il = nel collegamento copiato da Assurance. esempio: [https://www.adobe.com/?adb\_validation\_sessionid=](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0) [`efa4a9ed-02d8-4647-80fa-f01a5be273d0`](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)
1. Il valore [`efa4a9ed-02d8-4647-80fa-f01a5be273d0`](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0) verrebbe semplicemente utilizzato, non l&#39;URL completo

![Aggiungi l&#39;intestazione x-adobe-aep-validation-token con l&#39;ID sessione Assurance in Postman](assets/monitor-your-event-populate-the-x-adobe-aep-validation-token.png)



&#x200B;3. In Postman, salva ed esegui la richiesta **Crea evento Web Edge (nessuna autenticazione)**



## Visualizza registri di Assurance

Torna ad Assurance per visualizzare una serie di eventi. Puoi filtrare per individuare solo i tipi di evento rilevanti inserendo il tuo ID dello stream di dati nella ricerca

![Filtra gli eventi di Assurance ricercando il tuo ID dello stream di dati](assets/monitor-your-event-filter-using-search.png)



Seleziona un evento e, se necessario, apri eventuali messaggi nella barra a destra.

![Seleziona un evento ed espandi i messaggi nella barra a destra](assets/monitor-your-event-expand-messages.png)

Tipi di evento da cercare:

- hitReceived (mostra il payload ricevuto da Edge)
- evaluateRule (se si imposta SSF, mostra le regole da valutare)
- fireDestinations (a quali destinazioni è stato inviato questo oggetto)
- segmentsDiscovered (era valido per qualsiasi segmento edge)
- com.adobe.experience\_platform.edge\_segmentation/response (con quali segmenti ha risposto)

![Seleziona ogni tipo di evento per vedere come Assurance lo interpreta](assets/monitor-your-event-select-each-event.png)

Esplora questi e osserva come ogni passaggio viene interpretato da Assurance.
