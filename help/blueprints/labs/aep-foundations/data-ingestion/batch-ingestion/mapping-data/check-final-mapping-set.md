---
hold: true
title: Verifica set di mappatura finale
description: Confronta le mappature di campi semplici e calcolate per lo schema Account cliente con il set di mappatura finale previsto.
doc-type: article
solution: Experience Platform
exl-id: d1521d08-1ccb-405f-b728-a2777598cb9f
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Verifica set di mappatura finale

&#x200B;> [!NOTE]
>
>Se si proviene da Streaming Ingestion Lab, fare clic sul link seguente per procedere al passaggio successivo:
>
>[Streaming Ingestion Lab - Verifica il set di mappatura finale](../../stream-ingestion/check-final-mapping-set.md)



## Mappature semplici

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

&#x200B;> [!NOTE]
>
>Prima di continuare, assicurati che la mappatura finale corrisponda a quanto mostrato di seguito.



## Mapping calcolati

| Campi calcolati | Campo XDM |
| ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null o sms\_optIn == &quot;&quot;, &#39;n&#39;, sms\_optIn) | consents.marketing.sms.val |
| concat(date\_part(&quot;mese&quot;, date(nascita\_Date,&quot;M/g/aaaa&quot;)).toString(), &quot;-&quot;, date\_part(&quot;giorno&quot;, date(nascita\_Date,&quot;M/g/aaaa&quot;)).toString()) | person.bornDayAndMonth |
| date\_part(&quot;yyyy&quot;,date(nascita\_Date,&quot;M/d/yyyy&quot;)) | person.bornYear |

&#x200B;> [!NOTE]
>
>Prima di continuare, assicurati che la mappatura finale corrisponda a quanto mostrato di seguito
