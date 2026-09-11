---
hold: true
title: Verifica set di mappatura finale
description: Confronta le mappature di acquisizione in streaming con la passthrough finale prevista e il set di mappatura campo calcolato.
doc-type: article
solution: Experience Platform
exl-id: 8802aaca-f566-4972-8bd6-41aca9fae9bf
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# Verifica set di mappatura finale

## Mappature pass-through

&#x200B;> [!NOTE]
>
>Prima di continuare, assicurati che la mappatura finale corrisponda a quanto mostrato di seguito.

>[!NOTE]
>
>Sostituisci \&lt;tenant-name> con il valore della sandbox

| Campo Source | Campo di destinazione |
| ------------------------- | --------------------------------- |
| account\_create\_date | \&lt;nome-tenant>.account.createDate |
| account\_end\_date | \&lt;nome-tenant>.account.endDate |
| customer\_id | \&lt;nome-tenant>.customerID |
| plan\_name | \&lt;nome-tenant>.plan.name |
| plan\_id | \&lt;nome-tenant>.plan.planID |
| billing\_city | billingAddress.city |
| billing\_zip\_code | billingAddress.postalCode |
| billing\_state | billingAddress.state |
| billing\_street\_address | billingAddress.street1 |
| e-mail\_optIn | consents.marketing.email.val |
| cellulare\_phone | mobilePhone.number |
| firstName | person.name.firstName |
| lastName | person.name.lastName |
| email | personalEmail.address |
| createDate | repo.createDate |
| modifyDate | repo.modifyDate |
| shipping\_city | shippingAddress.city |
| shipping\_zip\_code | shippingAddress.postalCode |
| shipping\_state | shippingAddress.state |
| shipping\_street\_address | shippingAddress.street1 |



## Mapping calcolati

>[!NOTE]
>
>Tieni presente che le mappature per `birth_Date` sono diverse dalle mappature lab di acquisizione batch a causa della formattazione della data.  Il batch utilizza barre `/`, mentre il flusso utilizza trattini `-`

| Campi calcolati | Campo XDM |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null o sms\_optIn == &quot;&quot;, &#39;n&#39;, sms\_optIn) | consents.marketing.sms.val |
| concat(date\_part(&quot;mm&quot;, date(nascita\_Date, &quot;aaaa-M-g&quot;)).toString(), &quot;-&quot;, date\_part(&quot;gg&quot;, date(nascita\_Date, &quot;aaaa-M-g&quot;)).toString()) | person.bornDayAndMonth |
| date\_part(&quot;aaaa&quot;,date(nascita\_Date,&quot;aaaa-M-g&quot;)) | person.bornYear |

&#x200B;> [!NOTE]
>
>Prima di continuare, assicurati che la mappatura finale corrisponda a quanto mostrato di seguito



## Finalizzare il flusso di dati

Al termine, fai clic sul pulsante **Avanti** e quindi sul pulsante Fine per aggiornare il flusso di dati con la nuova logica di mappatura.

![Verifica dei dettagli del flusso di dati prima di fare clic su Fine per salvarlo](assets/check-final-mapping-set-review-and-finish-dataflow.png)



Ora dovrebbe essere visualizzata una schermata che mostra l’account API HTTP creato con tutti i flussi di dati associati che utilizzano tale account. Dovresti visualizzare anche il flusso di dati creato.
