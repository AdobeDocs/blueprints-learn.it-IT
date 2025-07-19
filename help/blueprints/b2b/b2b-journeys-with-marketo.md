---
title: Percorsi B2B con blueprint dei dati Marketo
description: Blueprint per la distribuzione rapida di Journey Optimizer B2B edition utilizzando i dati Marketo Engage.
solution: Journey Optimizer B2B Edition
exl-id: d7bd0bd3-0f61-4e59-855f-27afc147c9aa
source-git-commit: a0cbce2b4ed06517234b18020cef7acbda7de736
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 2%

---

# Percorsi B2B con blueprint dei dati Marketo

Questa guida completa illustra il processo di integrazione di Marketo Engage con Adobe Journey Optimizer B2B edition. Copre la configurazione di schemi personalizzati, l’acquisizione di profili e account e l’orchestrazione di percorsi personalizzati per i gruppi di acquisto. Utilizzando i dati di Marketo Engage, questo blueprint assicura un targeting e un coinvolgimento precisi su più canali, stimolando una domanda più qualificata e migliorando l’esperienza dei clienti.

## Casi di utilizzo

* **Crea e gestisci gruppi di acquisto**: utilizza l&#39;intelligenza artificiale generativa per assemblare e gestire gruppi di acquisto all&#39;interno degli account target, garantendo una copertura completa delle principali parti interessate
* **Assegnazione automatica membri**: assegna automaticamente i membri ai ruoli del gruppo di acquisto in base a criteri definiti, ad esempio il consumo di contenuto e i dati CRM
* **Percorsi personalizzati**: progetta e visualizza percorsi con più passaggi personalizzati per ogni gruppo di acquisto e membro in base al ruolo, all&#39;account, all&#39;interesse per il prodotto e alla fase del ciclo di vita
* **Automazione in tempo reale**: automatizza la progressione degli account e dei gruppi di acquisto tramite percorsi con trigger di coinvolgimento in tempo reale e punteggio di qualifica
* **Cross-Channel Engagement**: coinvolgi i gruppi di acquisto su più canali, tra cui e-mail, SMS, annunci, chat, eventi e webinar, per semplificare la generazione della domanda e la qualificazione
* **Informazioni basate sull&#39;intelligenza artificiale**: utilizza informazioni basate sull&#39;intelligenza artificiale per ottimizzare la distribuzione dei contenuti e le strategie di coinvolgimento per singoli acquirenti e interi gruppi di acquisto
* **Attivazione dati unificati**: attiva gli elenchi account unificati da Adobe Real-Time Customer Data Platform per fornire i dati più recenti e completi per la creazione e la gestione dei gruppi di acquisto
* **Collaboration avanzato**: coordinare le attività di marketing e vendita per creare opportunità di vendita più precise e accelerare la creazione della pipeline

## Applicazioni

* Journey Optimizer B2B Edition
* Real-time Customer Data Platform B2B Edition
* Marketo Engage

## Modelli di integrazione

| Integrazione | Descrizione |
| :-- | :--- |
| [Connettore Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) | Adobe Experience Platform semplifica l’acquisizione dei dati da Marketo, fornendo funzionalità per strutturare, etichettare e migliorare i dati utilizzando i suoi servizi. |
| [Journey Optimizer B2B edition - Azione Marketo Engage](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes/action-nodes#marketo-engage-actions) | Sincronizza Account-Based Marketing in Journey Optimizer B2B edition con le iniziative basate sui lead in Marketo Engage utilizzando azioni basate sulle persone per gestire le appartenenze a elenchi, le partizioni di persone e le campagne di richiesta. |
| [Journey Optimizer B2B edition - Risorse Marketo Engage](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content-management/assets/marketo-engage-dam/marketo-engage-design-studio) | Marketo Engage Design Studio è l&#39;origine predefinita delle risorse per Journey Optimizer B2B edition, che consente una facile gestione delle risorse per i percorsi di account. |

## Architettura

![Architettura della soluzione per AJO B2B con solo dati Marketo](./assets/ajo-b2b-marketo-only.png){zoomable="yes"}

## Fasi di implementazione

* Installa schemi B2B e spazi dei nomi utilizzando una delle opzioni seguenti
   * Utilizzo della [raccolta Postman](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility)
   * Utilizzo di [modelli](https://experienceleague.adobe.com/en/docs/experience-platform/sources/ui-tutorials/templates) nell&#39;interfaccia utente di Platform
* Creare un dizionario dati che definisca la mappatura tra i campi di Marketo e lo schema XDM di Experience Platform
   * Utilizza [Metadati oggetto Marketo](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/export-all-object-metadata) come punto di partenza
   * [Personalizza lo schema XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/fields/overview) per includere i campi personalizzati
   * Controlla i [campi XDM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/field-mapping) standard supportati da Journey Optimizer B2B edition. Se hai bisogno di campi aggiuntivi, apri un ticket di supporto per configurarli
      * **workEmail.address** è obbligatorio nel set di dati della persona
      * **accountName** è obbligatorio nel set di dati dell&#39;account
   * Aggiungi una nuova colonna di campi XDM al foglio di calcolo dei metadati di Marketo esportati per registrare la mappatura prevista
* Configura il [connettore di origine Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
   * Utilizza il dizionario dati definito in precedenza per definire la [Mappatura importazione](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/ui/mapping#import-mapping) per il connettore di origine
   * Si consiglia di non abilitare il profilo prima di tenere conto delle [considerazioni sull&#39;implementazione](#implementation-considerations)
   * Consiglio di acquisire persone, società, opportunità e attività come minimo, in quanto questi oggetti sono i più utili durante la creazione del pubblico del tuo account
* Implementa [Regole di collegamento del grafico delle identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) per gli utenti:
   * Definire il modo in cui i record Persona vengono collegati utilizzando gli spazi dei nomi delle identità.
   * Configura gli spazi dei nomi di identità e le regole di unione delle identità in AEP.
   * Convalida il collegamento utilizzando dati di persona di esempio e strumenti di anteprima.
* Abilita i set di dati Persona, Società, Opportunità e Attività per [profilo](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/user-guide#enable-profile)
* Definisci il tuo primo [pubblico account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/account-audience-overview)
* È possibile definire [gruppi di acquisto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/buying-groups/buying-groups-overview) o un [percorso di account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview) utilizzando un pubblico di account
   * Quando un account è idoneo per il pubblico dell’account, il processo del gruppo di acquisto viene eseguito ogni giorno per creare gruppi di acquisto e assegnare ruoli alle persone associate non appena il pubblico si aggiorna.
   * Inoltre, la manutenzione di gruppo viene eseguita ogni venerdì a mezzanotte (TC). Questo processo settimanale gestisce aggiornamenti quali la rimozione di membri non più idonei o l’aggiunta di membri nuovi non acquisiti durante l’aggiornamento iniziale del pubblico.

## Configurazione consigliata

Per semplificare l’implementazione e garantire la compatibilità con Adobe Journey Optimizer B2B edition, si consiglia di eseguire la configurazione seguente:

* **Utilizzare i campi di identità predefiniti:**
   * _email_ e _b2b_person_ devono essere mantenuti come campi di identità nello schema della persona per supportare l&#39;unione di identità e l&#39;attivazione del pubblico.
* **Utilizzare i mapping predefiniti per il connettore Source di Marketo:**
   * Sfrutta le mappature di campi predefinite fornite da Adobe per semplificare l’acquisizione dei dati e ridurre il sovraccarico di configurazione.
* **Usa mappature predefinite per AJO B2B:**
   * Adottare le [mappature di campi standard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/field-mapping) per Journey Optimizer B2B edition per garantire la compatibilità con la logica di acquisto del gruppo e l&#39;orchestrazione del percorso.
* **Blocca aggiornamenti campi su tutti i campi eccetto e-mail:**
   * In Marketo Engage, configura la gestione dei campi per [bloccare gli aggiornamenti](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) da Adobe Experience Platform per tutti i campi eccetto _e-mail_. In questo modo è possibile mantenere l&#39;integrità dei dati e al tempo stesso abilitare la risoluzione delle identità.
* **Implementare le regole di collegamento delle identità utilizzando e-mail come spazio dei nomi di identità univoco**
   * Configura [le regole di collegamento del grafo delle identità](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) in Adobe Experience Platform per utilizzare _email_ in modo esplicito come spazio dei nomi di identità univoco. Queste regole garantiscono che i profili vengano uniti in modo accurato tra le origini dati in cui è presente _email_, consentendo una solida risoluzione delle identità. Seguendo le best practice di Adobe, definisci le regole di collegamento che danno priorità alle e-mail come identificatori stabili e univoci a livello globale per mantenere un grafico di identità coerente e conforme alla privacy.
Questa configurazione fornisce un equilibrio tra facilità di distribuzione e governance dei dati, garantendo una base affidabile per l’orchestrazione dei percorsi B2B.

## Considerazioni sull’implementazione

Quando si implementa Adobe Journey Optimizer B2B edition, è fondamentale comprendere le funzionalità di unione delle identità fornite da Real-time Customer Data Platform. Questa piattaforma esegue l’unione delle identità a livello di persona e di account, garantendo una visualizzazione unificata dei dati dei clienti.

### Punti chiave

* **Unione identità**: la piattaforma unisce le identità utilizzando identificatori predefiniti come Marketo ID, CRM ID e e-mail. Questo consente di creare un profilo completo unendo dati da origini diverse.
* **Rischi potenziali**: l&#39;utilizzo della posta elettronica come identificatore per l&#39;unione può causare la compressione involontaria dell&#39;identità. Ciò significa che individui diversi che condividono lo stesso indirizzo e-mail potrebbero essere uniti in modo errato in un singolo profilo. Questo collasso dell’identità può influire negativamente sull’accuratezza dei dati CRM e comprometterne l’integrità.
* **Strategia di unione**: CDP B2B utilizza una strategia di unione basata sul tempo, in cui viene utilizzato il valore lastUpdatedDate più recente per un particolare attributo di profilo. Questa strategia assicura che i dati più recenti vengano rispecchiati nel profilo.
* **Considerazioni per l&#39;e-mail**: è essenziale valutare attentamente l&#39;utilizzo dell&#39;e-mail come identificatore per l&#39;unione dei frammenti di profilo. Anche se può essere utile, il rischio di un collasso di identità deve essere attentamente considerato rispetto ai vantaggi. Uno degli svantaggi è che senza e-mail come identificatore, l’iscrizione a un pubblico esterno creata da AJO B2B non si integra nel profilo esistente.
* **Integrazione della persona Marketo**: AJO B2B utilizza la persona Marketo con l&#39;ID lead più basso quando più record Marketo vengono uniti in un singolo profilo.

Tenendo presenti questi punti, puoi prendere decisioni informate su come configurare l’unione delle identità in Adobe Journey Optimizer B2B edition, garantendo profili cliente precisi e affidabili.

### Valutazione dei risultati dell’unione delle identità

Query Service può essere utilizzato per visualizzare l’impatto dell’unione di identità in un set di dati non abilitato per il profilo. Per eseguire la valutazione è possibile utilizzare la query seguente

#### Numero di record acquisiti

Questa query restituisce il numero totale di record acquisiti nel set di dati del profilo persona

```sql
select
    count(distinct b2b.personKey.sourceKey)
from
    marketo_person_ajo_b2b
```

#### E-mail duplicate

Questa query restituisce il numero di record persona che verranno uniti come parte dell’unione di identità della piattaforma

>[!NOTE]
>
>La tabella di set di dati marketo_person_ajo_b2b viene utilizzata per fornire un esempio completo di come lavorare con il set di dati Marketo Person.
>>Puoi trovare il set di dati della sandbox nell&#39;area di lavoro [Set di dati](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/user-guide).

```sql
select
    SUM(personCount)
from
    (
        select
            emailAddress,
            count(*) as personCount
        from
            (
                select
                    MAX(workemail.address) as emailAddress
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
```

#### Indirizzi e-mail con record duplicati

Questa query restituisce le e-mail con il maggior numero di record duplicati nel set di dati.  Questo elenco può essere utilizzato per controllare alcuni di questi record per comprendere meglio come il collegamento delle identità può influire su Marketo e CRM.  Per ulteriori dettagli sul funzionamento del collegamento delle identità, consulta la [panoramica del servizio Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home).

```sql
select
    *
from
    (
        select
            emailAddress,
            MAX(personId) as personId,
            count(*) as personCount
        from
            (
                select
                    b2b.personKey.sourceKey,
                    MAX(workemail.address) as emailAddress,
                    MAX(b2b.personKey.sourceId) as personId
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
order by
    personCount desc
```

### Opzioni

#### Rimozione dell’e-mail come identità

Dopo l&#39;analisi, se si stabilisce che l&#39;e-mail non è un campo valido da utilizzare come campo di identità, è possibile modificare lo schema della persona in [rimuovi e-mail come campo di identità](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/fields/identity)

#### Blocca aggiornamenti da Adobe Experience Platform

Se è meglio mantenere l&#39;e-mail come campo di identità per i tuoi casi d&#39;uso, puoi [bloccare gli aggiornamenti dei campi](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) provenienti da AJO B2B e consentire ad AJO B2B di essere eseguito principalmente sui dati di Marketo.

## Guardrail

Per una comprensione completa dei guardrail applicabili ai Percorsi B2B con Marketo Engage, consulta la seguente documentazione ufficiale:

* [Adobe Journey Optimizer B2B edition - Descrizione del prodotto](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html)
Include guardrail e parametri di utilizzo specifici per Journey Optimizer B2B edition.
* [Guardrail di distribuzione Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails?lang=en)
Include i guardrail generali di installazione e architettura nelle soluzioni Adobe Experience Platform.
* [Adobe Marketo Engage - Descrizione del prodotto](https://helpx.adobe.com/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails)
Dettagli sulle prestazioni e sui guardrail di utilizzo per Marketo Engage, incluse considerazioni sull’attivazione e la sincronizzazione CRM.
* [Guardrail Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview?lang=en)
Fornisce indicazioni sui limiti di acquisizione, segmentazione e attivazione dei dati all’interno di Real-Time Customer Data Platform.

## Documentazione correlata

* [Real-time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Guida introduttiva di Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [Guardrail per Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
* [Servizio Adobe Experience Platform Identity](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
* [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
* [Connettore tra Adobe Experience Platform e origine Marketo](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
* [Documentazione di Adobe Journey Optimizer B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
