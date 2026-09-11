---
title: Percorso di prova
description: Utilizza il simulatore modalità test di percorso per attivare un evento Ordine spedito e confermare che la logica di attivazione e azione sia eseguita correttamente prima della pubblicazione.
doc-type: article
solution: Experience Platform
exl-id: fc3dbfb9-b44b-4866-acc9-398a8b52f2b9
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---


# Percorso di prova

## Finalità di apprendimento

Utilizza gli strumenti di test del percorso per verificare che l’attivatore dell’evento e la logica di percorso siano configurati correttamente.

## Test del percorso

1. Fai clic su **Percorsi** nella barra a sinistra e sulla **scheda Sfoglia** se non trovi un elenco di Percorsi
2. Fai clic sul **Percorso** per aprirlo
3. Fai clic su **Avvisi** e assicurati che non vi siano errori (gli avvisi sono corretti)

   ![Il pannello Avvisi non mostra errori dopo l&#39;apertura del percorso](assets/test-journey-alerts-no-errors.png)

   >[!NOTE]
   >
   >**Cos&#39;è CJMMAS - 2001-200**
   >
   >Indica che in una variante e-mail manca il collegamento di rinuncia

4. Fai clic su **Simula** e, a sinistra, seleziona **Modalità test**

   ![Modalità test selezionata in Simula sul lato sinistro](assets/test-journey-select-test-mode.png)



   >[!NOTE]
   >
   >Potrebbe volerci un minuto per prepararsi. Durante tale periodo, il pulsante Attiva un evento non sarà disponibile.



5. Fai clic su **Attiva un evento** e compila le seguenti proprietà:
   - **Tipo evento**: `orders.shipped`
   - **E-mail personale**: `henry.creel@emailsim.io`
   - **ID ordine**: `123`
6. Fai clic su **Invia** (la risposta richiede alcuni secondi dopo aver fatto clic su Invia)

   ![Attiva un modulo evento compilato e Invia selezionato](assets/test-journey-trigger-event-send.png)

   >[!WARNING]
   >
   >Alcuni studenti ricevono errori e devono inviarli alcune volte. Potrebbe essere necessario eseguire **più** volte.
   >
   >**A volte** il primo invio restituisce un errore di:
   >
   >**L&#39;ingresso non esiste (ID riferimento: 3216a850-c40d-11f0-8fa5-73d1522cc9a2)**
   >
   >Se ricevi un errore, fai clic su **Attiva un evento**, quindi **invia** di nuovo.  Potrebbe essere necessario eseguire **più volte**.



7. In **Risultati** -> Fai clic su **Mostra registro** a sinistra

![Mostra opzione di registro in Risultati dopo l&#39;attivazione dell&#39;evento di test](assets/test-journey-show-log-results.png)

>[!NOTE]
>
>Alcuni studenti che hanno ricevuto errori a volte ricevono registri diversi che mostrano un array di istanze vuoto `{"instances": []}`. Questo non è un bloccante. Procedi e passa al passaggio successivo.

Dovresti vedere qualcosa di simile a questo nel registro:

>[!NOTE]
>
>Stiamo cercando i campi chiave utilizzati: **actionsHistory**, **transiionsHistory**, **eta**, **tracking_number**, **eventType**, **personalEmail** e **orderID**.

```json
{
  "actionsHistory": {
    "8919055f-1b00-4a43-8bd6-c8af894474b2": {
      "eta": "11/27/2025",
      "tracking_number": "091204404",
      "jo_status_code": "http_200"
    }
  },
  "transitionsHistory": {
    "orderShipped (1158856989)": {
      "eventType": "orders.shipped",
      "_id": "joTestModeEvent_5abbfdcd-561d-45a7-ba42-d0640539831a",
      "_dep": {
        "personalEmail": "henry.creel@emailsim.io"
      },
      "order": {
        "orderID": "123"
      },
      "timestamp": "2025-11-17T23:30:49.576289372Z"
    }
  }
}
```



&#x200B;8. **Chiudi** il browser **scheda**
&#x200B;9. **Chiudi modalità test** in alto a destra

   ![Pulsante Chiudi modalità test in alto a destra](assets/test-journey-close-test-mode.png)

&#x200B;10. Fai clic su **Pubblica** il Percorso in alto a destra

![Pulsante Pubblica per il Percorso in alto a destra](assets/test-journey-publish-journey.png)

&#x200B;11. **Chiudi** il **Percorso** facendo clic sulla freccia \&lt;- in alto a sinistra

![Freccia indietro in alto a sinistra per chiudere il Percorso](assets/test-journey-close-journey-back-arrow.png)

Ora invieremo un evento ordine spedito reale in AEP

## Riassunto

Il percorso ha superato la convalida della configurazione ed è pronto a ricevere eventi
