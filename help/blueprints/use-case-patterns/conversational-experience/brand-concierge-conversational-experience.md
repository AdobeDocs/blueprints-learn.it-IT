---
title: Esperienza conversazionale Brand Concierge
description: Scopri come trasformare le proprietà digitali in esperienze di conversazione basate sull’intelligenza artificiale e brand-safe che guidano l’individuazione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform
exl-id: a9545328-316d-446a-9308-18af61c58d1c
source-git-commit: fe4353cfe34855ad91ccb5698e30030322246c08
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Esperienza di conversazione Brand Concierge

Questa guida fornisce un riferimento completo all&#39;implementazione per le esperienze di conversazione basate sull&#39;intelligenza artificiale che utilizzano [!DNL Adobe Brand Concierge], integrato con [!DNL Adobe Experience Platform] (AEP) e [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]). È progettato per architetti di soluzioni, tecnici di marketing e ingegneri di implementazione che devono implementare agenti di conversazione sicuri per il brand nelle proprietà digitali.

Descrive tutti gli approcci possibili per la distribuzione di esperienze conversazionali, dai chatbot per la consulenza sui prodotti agli assistenti completi per la navigazione del sito, con indicazioni su quando scegliere ogni opzione. Il piano tratta la configurazione dell’agente, la governance del brand, l’integrazione dei contenuti, le strategie di distribuzione, l’arricchimento dei profili dai segnali di conversazione e l’ottimizzazione delle analisi.

[!DNL Brand Concierge] consente ai brand di distribuire agenti conversazionali intelligenti che comprendono la voce del brand, accedono a cataloghi di prodotti e contenuti approvati, forniscono consigli personalizzati basati su dati di profilo in tempo reale e acquisiscono segnali di intento e di sentiment nel profilo cliente unificato. Il risultato è un&#39;esperienza di conversazione che si sente naturale e sul marchio, arricchendo la comprensione di ogni cliente da parte dell&#39;organizzazione.

## Panoramica del caso d’uso

Le organizzazioni cercano sempre più di trasformare le esperienze digitali statiche in conversazioni dinamiche basate sull’intelligenza artificiale che guidano i clienti attraverso l’individuazione, la selezione dei prodotti e le decisioni di acquisto. [!DNL Adobe Brand Concierge] affronta questo problema fornendo un livello di intelligenza artificiale conversazionale orchestrato che si trova sopra le proprietà digitali esistenti, basato su AEP Agent Orchestrator.

Questo modello è distinto dalle implementazioni chatbot tradizionali perché è integrato in modo nativo con il profilo unificato di AEP, utilizza guardrail di governance del brand per garantire che ogni risposta sia allineata agli standard del brand e invia segnali conversazionali nella piattaforma dati del cliente per la personalizzazione e l’attivazione a valle.

Il pubblico di destinazione include team di esperienza digitale, manager di e-commerce, content strategist e tecnici di marketing che devono distribuire esperienze conversazionali intelligenti per stimolare il coinvolgimento, la conversione e l’arricchimento dei profili.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

### Fornire esperienze cliente personalizzate

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

**KPI:** coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT)

[Ulteriori informazioni sulla distribuzione di esperienze cliente personalizzate](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Migliorare il coinvolgimento dei clienti

Aumenta la frequenza e la profondità di interazione tra tutti i punti di contatto digitali e fisici.

**KPI:** coinvolgimento, pagina Time On (web), tassi di apertura

[Ulteriori informazioni sul miglioramento del coinvolgimento dei clienti](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Aumentare i tassi di conversione

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

**KPI:** Tassi di conversione, Conversione lead, Costo per lead

[Ulteriori informazioni sull’aumento dei tassi di conversione](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Acquisire nuovi clienti

Espandi la base di clienti tramite campagne di acquisizione mirate, tipi di pubblico simili e ottimizzazione di contenuti multimediali a pagamento.

**KPI:** nuovi clienti, costo acquisizione cliente, conversione potenziali clienti/lead

[Ulteriori informazioni sull&#39;acquisizione di nuovi clienti](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come questo modello può essere applicato nella pratica.

- **Assistente all&#39;individuazione del prodotto**: distribuzione di un agente di conversazione nelle pagine dell&#39;elenco dei prodotti che pone domande mirate e limita i consigli sui prodotti in base alle esigenze, alle preferenze e al budget del cliente
- **Consulente confronto guidato**: aiuta i clienti a confrontare i prodotti uno accanto all&#39;altro tramite un dialogo naturale, evidenziando le differenze pertinenti alle priorità dichiarate
- **Concierge dimensioni e adattamento** — Abbigliamento guida o calzature per gli acquirenti attraverso la selezione delle dimensioni utilizzando domande e risposte conversazionali, riducendo i resi e aumentando la fiducia negli acquisti
- **Selettore abbonamento o piano**: guida i clienti attraverso le opzioni del livello di servizio o del piano di abbonamento con consigli personalizzati in base ai modelli di utilizzo e alle esigenze dichiarate
- **Assistente alla navigazione del sito**: aiuta i visitatori a trovare contenuti rilevanti, risorse di supporto o categorie di prodotti in base all&#39;intento dichiarato, riducendo le percentuali di mancato recapito su siti complessi
- **Consulenza pre-acquisto**: fornisci indicazioni di acquisto di alta considerazione (ad esempio, elettronica, prodotti finanziari, assicurazione) tramite conversazioni a più turni che generano un consiglio
- **Responsabile del programma fedeltà**: aiuta i membri fedeltà a scoprire premi, comprendere i vantaggi a livello e trovare opportunità di rimborso tramite l&#39;interazione conversazionale
- **Conversazione di ricoinvolgimento**: avvia un&#39;estensione conversazionale proattiva per i visitatori di ritorno in base alla cronologia di esplorazione precedente o agli elementi del carrello abbandonati
- **Riassegnazione di agenti live con contesto**: consegna senza problemi di richieste complesse agli agenti di vendita o di supporto live, mantenendo al contempo il contesto di conversazione completo e i dati del profilo cliente
- **Supporto post-acquisto e upselling**: coinvolgi i clienti dopo l&#39;acquisto con assistenza per la configurazione, suggerimenti di prodotti complementari e check-in di soddisfazione tramite canali conversazionali

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare il successo di questo modello di caso d’uso.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Tasso di coinvolgimento conversazione | Percentuale di visitatori che avviano e sostengono una conversazione | Conversazioni avviate / visualizzazioni pagina idonee |
| Tasso di completamento conversazione | Percentuale di conversazioni che raggiungono una risoluzione significativa | Conversazioni/conversazioni completate avviate |
| Tasso di conversione conversazionale | Percentuale di conversazioni che hanno portato all’azione desiderata (acquisto, iscrizione, modulo lead) | Conversioni da conversazione / conversazioni totali |
| Profondità media conversazione | Numero di giri per conversazione, che indica la qualità del coinvolgimento | Numero medio di messaggi per sessione |
| Soddisfazione del cliente (CSAT) | Punteggio di soddisfazione post-conversazione dal feedback in-experience | Risposte ai sondaggi o valutazioni &quot;pollici-su/giù&quot; |
| Tasso di accettazione consigli | Percentuale di consigli di prodotto accettati o su cui è stato fatto clic | Consigli seguiti/consigli serviti |
| Frequenza handoff agente live | Percentuale di conversazioni inoltrate ad agenti live | Conversazioni / Totale conversazioni |
| Percentuale di arricchimento del profilo | Percentuale di conversazioni che generano nuovi segnali di intento o preferenza | Profili arricchiti / Totale conversazioni |
| Ricavi influenzati dalla conversazione | Ricavi da acquisti in cui una conversazione [!DNL Brand Concierge] ha preceduto la conversione | Analisi dell’attribuzione sui percorsi conversazione-acquisto |
| Tempo di risoluzione | Durata media dall&#39;inizio della conversazione alla risoluzione o all&#39;handoff | Analisi delle marche temporali tra gli eventi di conversazione |

## Schema del caso d’uso

**Esperienza di conversazione Brand Concierge**

Trasforma le proprietà digitali in esperienze di conversazione basate sull’intelligenza artificiale e brand-safe che guidano l’individuazione dei clienti attraverso il dialogo naturale, arricchiscono i profili con segnali di intento e di sentiment e forniscono consigli di prodotto personalizzati.

**Catena di funzioni:** Configurazione agente > Impostazione Brand Governance > Integrazione dei contenuti > Distribuzione esperienza conversazionale > Arricchimento profilo > Analytics e ottimizzazione

## Applicazioni

Per implementare questo modello di caso d’uso vengono utilizzate le seguenti applicazioni.

- **[!DNL Brand Concierge]** - Applicazione di esperienza conversazionale basata sull&#39;intelligenza artificiale che fornisce l&#39;agente orchestrator, Product Advisor Agent, Site Advisory Agent, brand governance e analisi conversazionale
- **[!DNL Adobe Experience Platform] (AEP)** — Unified data foundation che fornisce schemi XDM, risoluzione delle identità, profili cliente in tempo reale e infrastruttura di raccolta dati per i segnali conversazionali
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** — Piattaforma dati cliente che fornisce la ricerca dei profili in tempo reale per conversazioni personalizzate, segmentazione del pubblico da segnali conversazionali e arricchimento dei profili con dati di intento e sentiment

## Documentazione correlata

Per istruzioni sull&#39;implementazione e ulteriori informazioni, consulta [Panoramica di Brand Concierge](https://experienceleague.adobe.com/en/docs/brand-concierge/content/documentation/overview) su Adobe Experience League.
