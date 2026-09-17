---
title: Attivazione di account B2B in Advertising e destinazioni di file
description: Utilizza il coinvolgimento basato sull’account per creare tipi di pubblico per gli account e attivarli nelle destinazioni pubblicitarie e nell’archiviazione cloud.
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: 7f0b624616480cf563142c08eb0598d1dd55d551
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 1%
---

# Attivazione dell’account B2B su destinazioni di file e annunci pubblicitari

Il coinvolgimento basato sull&#39;account consente agli esperti di marketing B2B di creare tipi di pubblico di account (elenchi di aziende) in **Real-Time Customer Data Platform B2B edition** e di attivare tali tipi di pubblico per le destinazioni pubblicitarie, ad esempio LinkedIn Matched Audiences, Bombora e Demandbase, nonché per le destinazioni di archiviazione cloud. Questi tipi di pubblico di account possono essere utilizzati per il targeting, la sensibilizzazione alle vendite e l’analisi a valle.

## Casi di utilizzo

Utilizzando il coinvolgimento basato sull’account, gli esperti di marketing possono sbloccare tre casi d’uso chiave:

- **Colmare le lacune nei gruppi di acquisto:** Un addetto al marketing può fare pubblicità su account in cui non ha ancora contatti per i ruoli CMO o CIO. Possono innanzitutto creare un pubblico di account senza un contatto con il titolo &quot;CMO&quot; o &quot;CIO&quot; e quindi attivare il pubblico su LinkedIn Matched Audiences o altre destinazioni pubblicitarie supportate. All’interno della destinazione, possono quindi avviare una campagna indirizzata a quel pubblico e a persone specifiche con titoli di lavoro &quot;CMO&quot; o &quot;CIO&quot; per raggiungere questi nuovi contatti e evidenziare i vantaggi delle loro offerte.
- **Upselling o cross-selling ad altre divisioni di una società che è un cliente esistente:** Un addetto al marketing può creare un pubblico di clienti che ha acquistato il prodotto X tra 3 e 9 mesi fa ma non possiede ancora il prodotto Y. Possono quindi attivare il pubblico dell’account, evidenziando i vantaggi del prodotto Y per tale pubblico di destinazione tramite LinkedIn Matched Audiences, altre piattaforme pubblicitarie o esportazioni di archiviazione cloud per attività di vendita e marketing.
- **Aziende di destinazione che utilizzano prodotti concorrenti:** Un addetto al marketing può vendere ad account per sostituire i prodotti di un concorrente, anche senza alcun contatto con tali account. Possono creare un pubblico di account in base a dati di partner o intento che mostrano la proprietà o l’utilizzo di un prodotto di un concorrente, quindi attivare tramite LinkedIn Matched Audiences o altre destinazioni pubblicitarie supportate per sorgente i contatti presso gli account di destinazione per l’espansione.

## Applicazioni

- Real-Time Customer Data Platform B2B edition
- (Facoltativo) Customer Journey Analytics B2B edition

## Modelli di integrazione

I modelli di integrazione tipici per questa blueprint includono:

- **Destinazioni → tipi di pubblico dell&#39;account RTCDP B2B edition → per il coinvolgimento B2B e → origini CRM**

  Il coinvolgimento B2B e i sistemi CRM come Marketo Engage, Salesforce e Microsoft Dynamics inviano lead/contatti, account e opportunità in **Real-Time CDP B2B edition** utilizzando gli schemi e le relazioni B2B standard. Il pubblico dell’account è basato su questo modello di dati B2B unificato e viene attivato nelle destinazioni di file e annunci pubblicitari.

- **Intento B2B e origini eventi → tipi di pubblico → destinazioni dell&#39;account RTCDP B2B edition →**

  Le origini di intenti ed eventi B2B, come l’intento di Bombora e l’intento di Demandbase, inviano eventi di intenti e coinvolgimento in Experience Platform. Questi set di dati sono mappati sugli schemi B2B standard, consentendo agli addetti al marketing di creare tipi di pubblico per gli account (ad esempio, account che si riversano su argomenti della concorrenza) e di attivarli nelle destinazioni di archiviazione di annunci pubblicitari e cloud. Il pubblico dell&#39;account può quindi essere attivato per i partner pubblicitari come Bombora e Demandbase, se supportato.

## Architettura

<img src="assets/b2b-account-activation.png" alt="Architettura di riferimento per il blueprint per l’attivazione dell’account B2B" style="border:1px solid #4a4a4a"  width="100%" />

## Destinazioni del pubblico dell’account

- **Tipi di pubblico corrispondenti a LinkedIn**
- **Bombora**
- **Demandbase**
- **Destinazioni archiviazione cloud**
  - Archiviazione Azure Data Lake Gen2
  - Zona di destinazione dati
  - SFTP
  - Blob Azure
  - AWS S3

Per un elenco più recente delle destinazioni che supportano i tipi di pubblico dell’account, consulta la documentazione di destinazione.

## Guardrail

Consulta i seguenti guardrail durante la progettazione e l’attivazione dei tipi di pubblico dell’account:

- [Guardrail per Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Pubblico dell’account](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Attiva il pubblico dell’account](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Guardrail di profilo e segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Aggiornamento dei criteri di idoneità alla segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/eligibility-criteria-update)

## Passaggi per l’implementazione di Real-Time Customer Data Platform B2B edition, la creazione di tipi di pubblico per l’account e l’attivazione

- Per i passaggi di implementazione di Real-Time Customer Data Platform B2B edition, consulta la documentazione: [Guida introduttiva a Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en).
- Per i passaggi di creazione del pubblico dell&#39;account, consulta la documentazione [Tipi di pubblico dell&#39;account](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/account-audiences?lang=en).
- Per i passaggi di attivazione del pubblico dell&#39;account, consulta la documentazione di [Attivare il pubblico dell&#39;account](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en):

  - Mappatura richiesta per [destinazione tipi di pubblico collegati](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings).

## Considerazioni sull’implementazione

LinkedIn Matched Audiences (Tipi di pubblico corrispondenti) ha un requisito di dimensione minima del pubblico (ad esempio, 300 membri corrispondenti). Se il pubblico dell’account attivato nei tipi di pubblico abbinati a LinkedIn non soddisfa questo requisito, prima di avviare una campagna potrebbe essere necessario ampliare la definizione del pubblico per aumentarne le dimensioni.

## Documentazione correlata

- [Blueprint per l&#39;attivazione di profili e pubblico B2B](b2bactivation.md): blueprint principale che include l&#39;attivazione B2B a livello di persone e di account.
- [B2B edition di Real-Time Customer Data Platform](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview?lang=en)
- [Creare e attivare il pubblico dell’account - Video tutorial](https://experienceleague.adobe.com/it/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [Creare tipi di pubblico per account](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Attivare il pubblico dell’account](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Adobe Experience Platform - Connettore di destinazione LinkedIn](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Schemi in Real-Time CDP B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/schemas/b2b)
- [Aggiornamento dell&#39;architettura a Real-Time CDP B2B edition](https://experienceleague.adobe.com/it/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Guardrail per destinazione](https://experienceleague.adobe.com/it/docs/experience-platform/destinations/guardrails)
