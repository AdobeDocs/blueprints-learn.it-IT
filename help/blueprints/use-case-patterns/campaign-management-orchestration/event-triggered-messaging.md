---
title: Messaggi attivati da eventi
description: Scopri come inviare messaggi contestuali in tempo reale in risposta a eventi comportamentali o di sistema.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1955'
ht-degree: 5%

---

# Messaggistica attivata da eventi

In questa guida viene descritto il modello di casi d&#39;uso per la messaggistica attivata da eventi, che utilizza [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) e [!DNL Adobe Experience Platform] (AEP) per inviare messaggi contestuali in tempo reale in risposta a eventi comportamentali o di sistema. È progettato per architetti di soluzioni, tecnici di marketing e tecnici di implementazione che devono comprendere il funzionamento di questo modello, gli obiettivi aziendali supportati, i casi di utilizzo tattici che consente e le applicazioni Adobe coinvolte.

Questo modello copre l’intero ciclo di vita, dall’inserimento degli eventi alla creazione del percorso, fino alla consegna dei messaggi e al reporting delle prestazioni.

## Schema del caso d’uso

Questa sezione descrive il modello di base e il piano di esecuzione che gestisce la messaggistica attivata da eventi.

**Messaggi attivati da eventi**

Ascolta un evento comportamentale o di sistema in tempo reale, quindi distribuisci un messaggio contestuale al profilo che attiva.

**Piano di esecuzione:** Acquisizione evento > Inserimento Percorso > Valutazione condizione > Consegna messaggio > Reporting

## Panoramica del caso d’uso

La messaggistica attivata da eventi fornisce un messaggio contestuale in risposta a un evento comportamentale o di sistema in tempo reale. A differenza dell’attivazione batch dei messaggi in uscita, che invia a un pubblico pre-valutato secondo una pianificazione, questo modello ascolta un evento idoneo (ad esempio l’abbandono del carrello, una sessione di navigazione, l’invio di un modulo o una modifica dello stato del sistema) e inserisce immediatamente il profilo di attivazione in un percorso che valuta le condizioni e consegna un messaggio.

Il modello si basa sullo streaming di eventi in tempo reale in AEP (tramite Web SDK, Mobile SDK o API lato server), un percorso con una voce evento unitaria in AJO e una logica di valutazione delle condizioni che determina se e cosa inviare. Il messaggio viene generalmente inviato entro pochi minuti dall’evento di attivazione, rendendo questo modello ideale per comunicazioni pertinenti dal punto di vista temporale.

Le organizzazioni utilizzano questo modello per rispondere alle azioni dei clienti in tempo reale, aumentando la rilevanza e aumentando i tassi di coinvolgimento e conversione rispetto alle comunicazioni batch pianificate. Gli scenari comuni includono il recupero del carrello abbandonato, il follow-up post-acquisto, i messaggi di benvenuto dopo la registrazione e le notifiche sensibili al tempo come errori di pagamento o avvisi di calo dei prezzi.

## Obiettivi aziendali chiave

I seguenti obiettivi di business sono supportati da questo modello di casi d’uso.

**[Ripristina percorsi e carrelli abbandonati](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Coinvolgi nuovamente gli utenti che abbandonano durante i flussi di acquisto, applicazione o iscrizione con follow-up personalizzati e tempestivi.

| KPI |
| --- |
| Tassi di conversione, ricavi incrementali, coinvolgimento |

**[Aumentare i tassi di conversione](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Migliora la percentuale di visitatori e potenziali clienti che completano le azioni desiderate, ad esempio acquisti, iscrizioni o invii di moduli.

| KPI |
| --- |
| Tassi di conversione, conversione lead, costo per lead |

**[Distribuisci esperienze cliente personalizzate](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Personalizza contenuti, offerte e messaggi in base a preferenze, comportamenti e fasi del ciclo di vita individuali.

| KPI |
| --- |
| Coinvolgimento, tassi di conversione, soddisfazione del cliente (CSAT) |

**[Miglioramento dell&#39;onboarding dei clienti](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Accelerare il time-to-value per i nuovi clienti con esperienze di benvenuto e percorsi di attivazione semplificati e personalizzati.

| KPI |
| --- |
| Coinvolgimento, fidelizzazione, tassi di conversione |

## Esempi di casi d’uso tattici

Gli scenari seguenti illustrano come la messaggistica attivata da eventi può essere applicata in contesti aziendali diversi.

- **E-mail di abbandono carrello o SMS**: invia un messaggio di promemoria quando un cliente aggiunge articoli al carrello ma non completa l&#39;acquisto entro un intervallo di tempo definito
- **Follow-up abbandono navigazione** — Coinvolgi nuovamente i visitatori che hanno visualizzato prodotti o contenuti ma non hanno eseguito un&#39;azione di conversione
- **Grazie dopo l&#39;acquisto o cross-selling**: invia una conferma e consigli di cross-selling subito dopo un evento di acquisto
- **Promemoria sulla scadenza della versione di prova** — Avvisa gli utenti che si stanno avvicinando alla fine di una versione di prova gratuita con messaggi di rinnovo o conversione
- **Messaggio di benvenuto dopo la registrazione** - Invia un messaggio di onboarding immediato quando un nuovo utente registra o crea un account
- **Conferma invio modulo** - Conferma invio modulo (richieste di contatto, applicazioni, iscrizioni) con una conferma contestuale
- **Notifica di errore pagamento** - Avvisa i clienti quando un pagamento ricorrente non riesce, richiedendo loro di aggiornare le informazioni di pagamento
- **Notifica push di riconversione dell&#39;app** — Attiva un messaggio di riconversione quando un utente disinstalla un&#39;app mobile
- **Conferma prenotazione o appuntamento** - Invia conferma immediata dopo la pianificazione di una prenotazione, una prenotazione o un appuntamento
- **Avviso di calo prezzo per gli elementi della lista dei desideri** — Notifica ai clienti quando un prodotto nella lista dei desideri scende di prezzo

## Indicatori chiave di prestazioni

I KPI seguenti aiutano a misurare l’efficacia delle implementazioni di messaggistica attivate da eventi.

| KPI | Descrizione | Approccio di misurazione |
| --- | --- | --- |
| Tasso di conversione | Percentuale di destinatari del messaggio attivato che hanno completato l’azione desiderata (acquisto, iscrizione, rinnovo) | Conversioni/Messaggi recapitati * 100 |
| Reddito Incrementale | Ricavi aggiuntivi attribuibili ai messaggi attivati da eventi rispetto ai gruppi di controllo senza invio | Ricavi da invii attivati - Linea di base gruppo di controllo |
| Percentuale aperture | Percentuale di messaggi recapitati aperti dai destinatari | Aperture / Consegnate * 100 |
| Percentuale di click-through (CTR) | Percentuale di messaggi consegnati che generano almeno un clic | Clic / Consegnato * 100 |
| Tempo di conversione | Tempo medio trascorso tra la consegna del messaggio e l’evento di conversione | Media(timestamp di conversione - timestamp di consegna) |
| Percentuale di completamento percorso | Percentuale di profili che entrano nel percorso e raggiungono il passaggio di consegna del messaggio (non eliminati da condizioni o uscite) | Profili che raggiungono la consegna / Profili che entrano nel percorso * 100 |
| Percentuale di soppressione dei messaggi | Percentuale di profili idonei soppressi a causa di limiti di frequenza, consenso o valutazione delle condizioni | Profili soppressi / Profili qualificati totali * 100 |
| Percentuale non recapitate | Percentuale di messaggi che non è stato possibile recapitare a causa di mancati recapiti permanenti o non permanenti | Rimbalzi / Inviati * 100 |

## Applicazioni

In questo modello di caso d’uso vengono utilizzate le seguenti applicazioni Adobe.

- **[!DNL Adobe Journey Optimizer] (AJO)**: orchestrazione del Percorso con voce evento unitaria, valutazione delle condizioni, passaggi di attesa, authoring dei messaggi, configurazione dei canali, governance della frequenza e reporting sulla consegna
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Valutazione del pubblico per filtraggio basato su condizioni all&#39;interno di percorsi, applicazione del consenso e della governance, arricchimento del profilo
- **[!DNL Adobe Experience Platform] (AEP)** — Acquisizione di eventi in tempo reale tramite Web SDK, Mobile SDK o API lato server; modellazione dati; risoluzione identità; Edge Network

## Documentazione correlata

Le risorse seguenti forniscono ulteriori dettagli sulle funzionalità utilizzate in questa implementazione.

### Orchestrazione percorso

- [Introduzione ai percorsi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Creare un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Proprietà del percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Eventi generali](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Eventi di qualificazione del pubblico](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Attività Condizione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Attività Attendi](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Aggiungere un messaggio in un percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Criteri di uscita](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Gestione voci percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test del percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Pubblicare il percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Configurazione dei canali

- [Introduzione alla configurazione delle e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delega sottodomini](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Creare pool IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Piani di riscaldamento IP](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Impostazioni superficie e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configurare il canale SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configurare il canale di notifica push](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Gestire l’elenco di soppressione](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Authoring e personalizzazione dei messaggi

- [Creare un messaggio e-mail](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/email/create-email)
- [Progettare contenuti e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aggiungere personalizzazione](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Sintassi Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Funzioni di supporto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Contenuto dinamico](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utilizzare i modelli di contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilizzare i frammenti di contenuto](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anteprima e test del contenuto](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Creare un messaggio SMS](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/sms/create-sms)
- [Progettare una notifica push](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/channels/push/design-push)

### Frequenza e regole aziendali

- [Regole di frequenza](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Panoramica sulle regole business](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Limitazione di utilizzo API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Gestione dei conflitti e delle priorità

- [Introduzione alla gestione dei conflitti e delle priorità](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identificare potenziali conflitti](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Punteggi di priorità](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Limitazione di percorso e arbitrato](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Reporting e prestazioni

- [Rapporto live del percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Rapporto globale percorso](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Guida all’integrazione di AJO e CJA](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Raccolta e acquisizione dei dati

- [Panoramica di Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/home)
- [Panoramica di Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Panoramica dell’API del server Edge Network](https://experienceleague.adobe.com/it/docs/experience-platform/edge-network-server-api/overview)
- [Configurare gli stream di dati](https://experienceleague.adobe.com/it/docs/experience-platform/datastreams/configure)
- [Panoramica sull’acquisizione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/ingestion/streaming/overview)

### Modellazione dati e schemi

- [Panoramica del sistema XDM](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/home)
- [Nozioni di base sulla composizione dello schema](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/schema/composition)

### Identità e profilo

- [Panoramica del servizio Identity](https://experienceleague.adobe.com/it/docs/experience-platform/identity/home)
- [Panoramica sugli spazi dei nomi delle identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)
- [Regole di collegamento del grafo identità](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/identity-linking-logic)
- [Panoramica del profilo](https://experienceleague.adobe.com/it/docs/experience-platform/profile/home)
- [Panoramica sui criteri di unione](https://experienceleague.adobe.com/it/docs/experience-platform/profile/merge-policies/overview)

### Segmentazione e tipi di pubblico

- [Panoramica del servizio di segmentazione](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/home)
- [Guida dell’interfaccia utente di Segment Builder](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentazione in streaming](https://experienceleague.adobe.com/it/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Governance dei dati e consenso

- [Panoramica sulla governance dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/home)
- [Panoramica sulle etichette di utilizzo dei dati](https://experienceleague.adobe.com/it/docs/experience-platform/data-governance/labels/overview)
- [Gruppo di campi Consenso e preferenze](https://experienceleague.adobe.com/it/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consenso in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Attributi calcolati

- [Panoramica degli attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/overview)
- [Guida dell’interfaccia utente attributi calcolati](https://experienceleague.adobe.com/it/docs/experience-platform/profile/computed-attributes/ui)

### Monitoraggio e osservabilità

- [Panoramica degli avvisi](https://experienceleague.adobe.com/it/docs/experience-platform/observability/alerts/overview)
- [Panoramica di Observability Insights](https://experienceleague.adobe.com/it/docs/experience-platform/observability/home)

### Guardrail

- [Guardrail Journey Optimizer](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/get-started/guardrails)
- [Guardrail del profilo cliente in tempo reale](https://experienceleague.adobe.com/it/docs/experience-platform/profile/guardrails)
- [Guardrail di acquisizione](https://experienceleague.adobe.com/it/docs/experience-platform/ingestion/guardrails)

### Tutorial e guide

- [Tutorial sulla creazione di un percorso](https://experienceleague.adobe.com/it/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Installare Web SDK](https://experienceleague.adobe.com/it/docs/experience-platform/web-sdk/install/overview)
