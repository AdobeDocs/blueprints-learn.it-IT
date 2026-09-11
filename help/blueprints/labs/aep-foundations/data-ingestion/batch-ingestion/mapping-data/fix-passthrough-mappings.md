---
title: Correggere le mappature passthrough
description: Identifica e corregge le mappature passthrough AI/ML errate, ad esempio assegnazioni di campi di destinazione duplicate o non corrispondenti, prima della convalida.
doc-type: article
solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Correggere le mappature passthrough

## Elimina mappature specifiche

Alcuni dei dati di origine devono essere gestiti utilizzando campi calcolati.  Per risolvere questi problemi, eliminali dalle mappature e riconvalida le mappature.

1. Rilascia i seguenti dati di origine dalle mappature:
   - nascita\_data
   - sorgente
   - sms\_optIn
1. Riconvalida le mappature facendo clic sul pulsante di convalida

![Pulsante Convalida utilizzato per convalidare nuovamente i mapping dopo la rimozione dei campi](assets/fix-passthrough-mappings-re-validate-mappings-using-validate-button.png "Riconvalida i mapping tramite il pulsante di convalida")

>[!NOTE]
>
>Dopo aver fatto clic su Convalida, potrebbero comunque verificarsi degli errori



## Esempi di mappatura errati

Anche se i consigli su IA/ML sono utili, a volte sono errati.  Se analizzi i consigli, potresti trovare questi tipi di errori che è necessario correggere

>[!NOTE]
>
>Di seguito sono riportati alcuni esempi di mappature non valide che potrebbero essere presenti nella tua sandbox. È possibile che vengano visualizzati anche errori di altri utenti.

## Mappature duplicate

In questo scenario, il consigliere AI/ML ha mappato due diversi campi di origine allo stesso campo di destinazione **person.name.lastName**



![Due diversi campi di origine mappati allo stesso campo di destinazione person.name.lastName](assets/fix-passthrough-mappings-person-lastname-mapped-twice.png "person.name.lastName sono mappati due volte in questa mappatura")

![Esempio di mapping passthrough duplicato relativo al campo plan_name](assets/fix-passthrough-mappings-plan-name-duplicate-mapping.png)



## Mappature non valide

Il mapping è corretto, ma dopo un&#39;ispezione più dettagliata **email** non è uguale a **emailFormat**

![Mappatura in cui la posta elettronica è mappata in modo errato invece di emailFormat](assets/fix-passthrough-mappings-email-mapped-incorrectly.png "la posta elettronica sembra essere mappata correttamente, ma non è corretta in base ai requisiti")

E questo in cui **email\_optIn** non esegue correttamente il mapping all&#39;oggetto di consenso errato

![email_optIn mappato in modo errato all&#39;oggetto di consenso &#x200B;](assets/fix-passthrough-mappings-email-optin-wrong-consent-object.png "email_optIn sembra mappato correttamente, ma non è corretto in base ai requisiti")



## Correzione delle mappature passthrough

Per correggere le mappature passthrough che puntano erroneamente al campo di destinazione errato, effettuare le seguenti operazioni.

### Esempio

1. Inizia con una mappatura non valida e fai clic sulla casella del campo di destinazione. Ad esempio, nel mapping seguente, il campo **person.name.lastName** non è mappato correttamente ed è mappato a **planName**
1. Nel pannello schema di destinazione visualizzato a destra, scegliere il campo di destinazione appropriato e selezionare **\_devbc.plan.name**
1. Il campo di destinazione ora deve essere aggiornato nella casella campo di destinazione
1. Dopo aver corretto tutti gli errori, premere il pulsante **Convalida** per assicurarsi di ridurre questo tipo di errori e di non introdurne di nuovi.



![Elaborazione dell&#39;elenco di mappatura per correggere ogni errore di mappatura](assets/fix-passthrough-mappings-work-through-mapping-errors.png "Risoluzione degli errori di mappatura")



![Pannello schema di destinazione per selezionare il campo corretto per correggere una mappatura passthrough](assets/fix-passthrough-mappings-choose-correct-target-field.png "Scegliere il campo di destinazione corretto e verificare che corrisponda ai requisiti passthrough")

>[!WARNING]
>
>Non procedere al passaggio successivo finché non sono stati risolti tutti gli errori di mappatura
