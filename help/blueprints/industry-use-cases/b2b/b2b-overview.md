---
title: Casi d’uso B2B
description: Scopri come le organizzazioni B2B utilizzano Adobe Experience Platform per accelerare la pipeline, migliorare la qualità dei lead e stimolare l’espansione dei clienti.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 6073bdc4-e148-455e-aa4e-3d5226d4b5a2
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---

# Casi d’uso B2B

Le organizzazioni business-to-business utilizzano Adobe Experience Platform per unificare i dati a livello di account e persona, consentendo ai team di marketing e vendita di fornire esperienze coordinate e rilevanti in ogni fase del percorso di acquisto. Dall’accelerazione della pipeline all’espansione del cliente, questi casi d’uso mostrano come i team B2B trasformino dati complessi in risultati di business misurabili.

>[!NOTE]
>
>Per i progetti di architettura specifici di B2B, tra cui l&#39;attivazione basata sull&#39;account e la gestione dei gruppi di acquisto, consulta i [progetti di attivazione e marketing B2B](/help/blueprints/b2b/overview.md).

## Account-Based Marketing Personalization

Personalizza le comunicazioni di marketing e i contenuti per gli account di destinazione in base al profilo dell’account, alla cronologia del coinvolgimento e ai segnali di acquisto. Allineando i messaggi al contesto univoco di ciascun account, i team di marketing possono superare ogni difficoltà e coinvolgere le parti interessate con i contenuti giusti.

### Impatto aziendale

Le organizzazioni che implementano la personalizzazione di marketing basata sull’account possono vedere un coinvolgimento dell’account migliorato, che favorisce una pipeline più solida e una progressione più rapida delle offerte.

### Come implementare

Utilizza il pattern [B2B Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) per creare tipi di pubblico a livello di account e attivare contenuti personalizzati su tutti i canali. Questo modello è progettato appositamente per le strategie basate su account, e supporta sia il targeting a livello di account che di persona. Questo è il modello corretto quando il targeting deve funzionare a livello di account anziché a livello individuale: l’attivazione del pubblico RT-CDP standard non supporta il modello di dati basato sull’account richiesto per le strategie ABM.

### Considerazioni tecniche

- Integrare i dati CRM (ad esempio, [!DNL Salesforce] o [!DNL Microsoft Dynamics]) per mantenere aggiornate le gerarchie di account, le fasi di opportunità e le assegnazioni di proprietà.
- Configurare gli schemi di profilo a livello di account per acquisire attributi firmografici quali settore, conteggio dei dipendenti, intervallo di ricavi e stack di tecnologia.
- Mappa le relazioni tra persone e account per garantire che i segnali di coinvolgimento dei singoli utenti vengano aggregati a livello di account e di segmentazione.
- Coordinati con [!DNL Marketo Engage] per allineare le campagne di automazione del marketing con i tipi di pubblico dell&#39;account basati su piattaforma.


## Punteggio di lead e sviluppo

Punteggio automatico dei lead in base ai dati e al comportamento del profilo, quindi indirizza i lead con punteggio elevato alle vendite con campagne di crescita personalizzate per altri. Questo approccio garantisce che i sales team si concentrino sulle opportunità più promettenti, mentre il marketing continua a sviluppare potenziali clienti nelle prime fasi.

### Impatto aziendale

Le aziende che implementano il lead scoring comportamentale e l’apprendimento automatizzato vedono una migliore conversione lead-to-opportunità, un’accelerazione della velocità della pipeline e un miglioramento della produttività di vendita.

### Come implementare

Utilizza il pattern [Percorso orchestrato a più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per progettare percorsi di crescita diramati che rispondono alle modifiche del punteggio del lead e ai trigger comportamentali. Questo modello supporta la logica condizionale necessaria per instradare i lead tra le tracce di sviluppo e i flussi di lavoro di handoff delle vendite. Questo è il modello corretto quando il caso d’uso richiede un flusso sequenziale di più messaggi nell’arco di giorni con diramazioni condizionali basate su modifiche del punteggio del lead ed eventi comportamentali. Un singolo messaggio attivato non può soddisfare la logica di dipendenza tra le fasi di punteggio e le decisioni di instradamento.

### Considerazioni tecniche

- Stabilire la sincronizzazione bidirezionale CRM (ad esempio, [!DNL Salesforce] o [!DNL Microsoft Dynamics]) in modo che i punteggi dei lead e gli stati di qualifica rimangano coerenti tra i sistemi di marketing e di vendita.
- Definisci le dimensioni di punteggio demografico (ruolo, dimensioni dell’azienda, settore) e comportamentale (download di contenuti, partecipazione a webinar, visite alle pagine dei prodotti).
- Coordinare i modelli di punteggio lead con [!DNL Marketo Engage] per evitare conflitti di punteggi tra piattaforme.
- Imposta le regole di decadimento del punteggio per garantire che i lead che non interrompono l’attività vengano ignorati nel tempo.


## Personalization dei contenuti per i potenziali clienti

Personalizza il contenuto del sito web, le risorse e le offerte in base al settore, al ruolo, alle dimensioni dell’azienda e alla cronologia del coinvolgimento del potenziale cliente. Quando i potenziali clienti vedono il contenuto pertinente alla loro situazione specifica, si impegnano più a fondo e passano più rapidamente attraverso il funnel.

### Impatto aziendale

Le organizzazioni B2B che personalizzano le esperienze web per potenziali clienti noti vedono un miglioramento nel coinvolgimento dei contenuti, che porta a una pipeline più qualificata e a cicli di vendita più brevi.

### Come implementare

Utilizza il pattern [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) per fornire esperienze di contenuto personalizzate basate su profili prospect unificati. Questo modello sfrutta i dati del profilo in tempo reale per fornire le risorse più rilevanti, case study e inviti all’azione per ogni visitatore. Questo è il modello corretto quando la personalizzazione è guidata dagli attributi di profilo e dall’appartenenza a un segmento anziché da un modello di affinità comportamentale, consentendo agli attributi a livello di account e di singolo utente di gestire l’esperienza.

### Considerazioni tecniche

- Implementa la risoluzione delle identità per far corrispondere il comportamento di navigazione anonima ai record prospect noti dopo l’autenticazione o l’invio di un modulo.
- Definisci le regole di personalizzazione in base agli attributi a livello di account (settore, segmento, fase di offerta) e agli attributi a livello di singolo utente (ruolo, consumo di contenuti passati).
- Integrazione con il sistema di gestione dei contenuti per cambiare dinamicamente i banner principali, le raccomandazioni sulle risorse e le chiamate all’azione.
- Assicurati che [!DNL Marketo Engage] feed di dati di tracciamento web entrino nel profilo unificato per ottenere un quadro comportamentale completo.


## Registrazione e follow-up degli eventi

Automatizza le conferme, i promemoria e il follow-up post-evento personalizzati di registrazione degli eventi in base al tipo di evento e al profilo del partecipante. In questo modo i potenziali clienti rimangono coinvolti prima, durante e dopo gli eventi, mentre il team marketing è libero dalla coordinazione manuale.

### Impatto aziendale

I flussi di lavoro automatizzati e personalizzati per la comunicazione degli eventi favoriscono una maggiore partecipazione agli eventi, ottimizzando il ritorno sull&#39;investimento e rafforzando le relazioni potenziali.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per orchestrare l&#39;intero ciclo di vita dell&#39;evento, dalla registrazione fino alla fase di sviluppo post-evento. Questo modello supporta trigger basati sul tempo, diramazioni condizionali per tipo di evento e sequenze di follow-up multicanale. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi sequenziale e multiplo nell’arco di giorni con diramazioni condizionali in base alla registrazione dell’evento e alla partecipazione: i messaggi basati sul tempo non sono in grado, da soli, di gestire la logica di diramazione complessa tra percorsi registrati, seguiti e non mostrati.

### Considerazioni tecniche

- Integrare i dati di registrazione dalle piattaforme di webinar (ad esempio, [!DNL ON24], [!DNL Zoom Webinar]) e dai sistemi di eventi di persona nel profilo unificato.
- Acquisisci i segnali di partecipazione e coinvolgimento (durata della sessione, domande poste, risposte ai sondaggi) per personalizzare i messaggi di follow-up.
- Coordinare percorsi di eventi con stati di programma [!DNL Marketo Engage] per mantenere rapporti coerenti tra i sistemi.
- Progetta rami di percorso separati per gli utenti registrati che hanno partecipato rispetto a quelli che non hanno partecipato, con contenuti personalizzati per ciascuno.


## Campagne di conversione di prova del prodotto

Coinvolgi gli utenti di prova con consigli di prodotti personalizzati, risorse di formazione e offerte per incoraggiare la conversione a piani a pagamento. Incontrando gli utenti di prova nella posizione in cui si trovano nell’esplorazione del prodotto, i team possono rimuovere gli attriti e accelerare il percorso di acquisto.

### Impatto aziendale

Le organizzazioni che distribuiscono campagne di conversione di valutazione personalizzate vedono un miglioramento della conversione da prova a pagamento, con un impatto diretto sui nuovi ricavi aziendali e una riduzione dei costi di acquisizione dei clienti.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare percorsi di conversione basati sul tempo e sul comportamento per gli utenti di prova. Questo modello supporta percorsi condizionali basati su milestone di utilizzo del prodotto, consentendo spostamenti mirati nei momenti giusti. Questo è il modello corretto quando il caso di utilizzo richiede un flusso di messaggi multipli in sequenza attivato da milestone di utilizzo con diramazione condizionale: i messaggi attivati dagli eventi non possono gestire la logica di temporizzazione predittiva e di dipendenza necessaria per lo sviluppo basato su milestone.

### Considerazioni tecniche

- Acquisisci la telemetria relativa all’utilizzo del prodotto (adozione delle funzioni, frequenza di accesso, tempo nel prodotto) per creare profili di coinvolgimento di prova in tempo reale.
- Definisci le milestone basate sull’utilizzo (ad esempio, creazione del primo progetto, funzionalità chiave utilizzata, collaborazione invitata) come trigger del percorso per una sensibilizzazione tempestiva.
- Sincronizza lo stato di prova e gli eventi di conversione in [!DNL Salesforce] o [!DNL Microsoft Dynamics] in modo che i rappresentanti commerciali abbiano piena visibilità sull&#39;attività di prova.
- Coordinarsi con [!DNL Marketo Engage] programmi di sviluppo per evitare la sovrapposizione delle comunicazioni durante il periodo di prova.


## Customer Success e onboarding

Personalizza i percorsi di onboarding dei clienti con formazione, risorse e supporto pertinenti in base al prodotto acquistato e al profilo del cliente. Un onboarding efficace riduce il time-to-value e pone le basi per la conservazione e la crescita a lungo termine dei clienti.

### Impatto aziendale

Le organizzazioni con programmi di onboarding personalizzati riscontrano un miglioramento nell’adozione delle funzioni nei primi 90 giorni, che contribuisce direttamente a un aumento dei ricavi derivanti da fidelizzazione ed espansione.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per orchestrare sequenze di onboarding personalizzate per prodotto, livello di piano e segmento cliente. Questo modello supporta la progressione basata su milestone, garantendo ai clienti la corretta guida in ogni fase del processo di onboarding. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi multipli in sequenza con avanzamento condizionale basato sui milestone di utilizzo del prodotto: la messaggistica attivata da eventi non può soddisfare la logica di staging complessa necessaria per la progressione guidata dell’onboarding.

### Considerazioni tecniche

- Acquisisci la telemetria di utilizzo del prodotto per tenere traccia delle milestone di onboarding (primo accesso, configurazione iniziale, primo flusso di lavoro completato) e attiva di conseguenza il passaggio del percorso successivo.
- Mappa i profili dei clienti sulla traccia di onboarding corretta in base al prodotto acquistato, al livello di pianificazione e al numero di utenti con licenza.
- Integra i dati della piattaforma di successo dei clienti per far emergere i punteggi di integrità e segnalare gli account a rischio per un intervento proattivo.
- Sincronizza lo stato di onboarding e le metriche di adozione con [!DNL Salesforce] o [!DNL Microsoft Dynamics] in modo che i responsabili del successo dei clienti possano dare priorità all&#39;attività.


## Campagne di rinnovo del contratto

Coinvolgi in modo proattivo i clienti che si avvicinano al rinnovo del contratto con offerte personalizzate, informazioni sull’utilizzo e incentivi di rinnovo. Un impegno di rinnovo tempestivo e basato sui dati riduce l’abbandono e protegge i ricavi ricorrenti.

### Impatto aziendale

Le aziende che implementano campagne di rinnovo proattive e personalizzate ottengono tassi di rinnovo migliori, proteggendo i ricavi ricorrenti e riducendo i costi di riacquisizione dei clienti.

### Come implementare

Utilizza il modello [Cross-Channel Percorsi with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per fornire l&#39;offerta di rinnovo giusta attraverso il canale giusto al momento giusto. Questo modello combina l’orchestrazione del percorso con Offer Decisioning, abilitando incentivi di rinnovo dinamici in base al valore e all’utilizzo dell’account. Questo è il modello giusto quando il percorso deve coordinare la consegna tra i canali e la selezione dell’offerta richiede il valore dell’account e vincoli di utilizzo: l’orchestrazione del percorso da sola non fornisce il livello decisionale in tempo reale necessario per abbinare dinamicamente gli incentivi di rinnovo.

### Considerazioni tecniche

- Recuperare le date di fine contratto, le condizioni di rinnovo e il valore dell&#39;account da [!DNL Salesforce] o [!DNL Microsoft Dynamics] per attivare i percorsi di rinnovo al lead time appropriato (ad esempio, 90, 60, 30 giorni esauriti).
- Incorpora i dati di utilizzo del prodotto e i punteggi di integrità del cliente per determinare il rischio di rinnovo e personalizzare di conseguenza la strategia di offerta.
- Utilizza il decisioning per selezionare l’incentivo di rinnovo ottimale (sconto, termini estesi, aggiornamento premium) in base al valore della durata dell’account e alla probabilità di abbandono.
- Coordinare le attività di rinnovo con i team di vendita e di successo del cliente per evitare messaggi in conflitto tramite [!DNL Marketo Engage] e l&#39;assegnazione di attività CRM.


## Opportunità di upselling ed espansione

Identifica i clienti pronti per gli aggiornamenti dei prodotti o per licenze aggiuntive in base a modelli di utilizzo, indicatori di crescita e dati sul successo dei clienti. Un impegno proattivo nell’espansione converte lo slancio del cliente in una crescita dei profitti.

### Impatto aziendale

Le organizzazioni che identificano e agiscono sistematicamente sui segnali di espansione generano maggiori ricavi di espansione, migliorando la conservazione dei ricavi netti e il valore del ciclo di vita del cliente.

### Come implementare

Utilizza il pattern [Cross-Channel con Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) per distribuire offerte personalizzate di upselling ed espansione in base all&#39;utilizzo in tempo reale e ai segnali dell&#39;account. Questo modello utilizza il processo decisionale per far corrispondere ogni account con l’offerta di espansione più rilevante tra i canali. Questo è il modello corretto quando il percorso deve coordinare la consegna tra i canali e la selezione delle offerte richiede regole di idoneità che regolino le offerte di espansione che corrispondono a account specifici: l’orchestrazione del percorso non fornisce da sola il livello decisionale necessario per la corrispondenza delle offerte basate su vincoli.

### Considerazioni tecniche

- Acquisisci la telemetria di utilizzo del prodotto per rilevare segnali di espansione quali soglie di utilizzo delle licenze, hit da soffitto delle funzioni e numero crescente di utenti.
- Crea modelli di propensione a livello di account utilizzando dati di espansione storici, tendenze di utilizzo e attributi firmografici.
- Sincronizza le opportunità di espansione e le offerte consigliate con [!DNL Salesforce] o [!DNL Microsoft Dynamics] in modo che i team di vendita possano seguire la pipeline generata dal marketing.
- Coordinarsi con [!DNL Marketo Engage] per garantire che i messaggi di espansione non entrino in conflitto con il supporto continuo o le comunicazioni di rinnovo.


## Campagne sostitutive competitive

Puoi indirizzare l’attività ai potenziali clienti utilizzando prodotti della concorrenza con messaggi personalizzati, offerte di migrazione e confronti competitivi. Affrontando i punti critici specifici associati a ciascun concorrente, i team di marketing possono distinguere in modo più efficace e accelerare le decisioni di passaggio.

### Impatto aziendale

Le organizzazioni B2B che eseguono campagne di sostituzione mirate e competitive vedono migliorare i tassi di vincita della concorrenza, acquisendo quote di mercato e sostituendo i fornitori storici.

### Come implementare

Utilizza il pattern [Percorso orchestrato con più passaggi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per orchestrare campagne competitive con più contatti personalizzate per il profilo specifico del concorrente e del potenziale cliente. Questo modello supporta la ramificazione condizionale in base al concorrente identificato, consentendo la messaggistica che affronta i punti critici specifici di ogni scenario competitivo. Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi sequenziale e multiplo con ramificazioni condizionali basate sul concorrente specifico e sul profilo potenziale: i messaggi attivati da eventi non possono gestire la complessità della logica di ramificazione specifica del concorrente in più punti di contatto.

### Considerazioni tecniche

- Integra i dati di intelligence sulla concorrenza (ad esempio, fornitori di tecnologia, campi della concorrenza CRM) nel profilo unificato per identificare il concorrente attualmente utilizzato da un potenziale cliente.
- Crea risorse di contenuti specifiche per la concorrenza (guide alla migrazione, fogli di confronto, calcolatrici del ROI) e mappale su blocchi di contenuti di percorso.
- Coordinarsi con [!DNL Marketo Engage] per eliminare le campagne della concorrenza per i potenziali clienti già in ciclo di vendita attivo o per i clienti esistenti.
- Monitora la pipeline di spostamento competitiva in [!DNL Salesforce] o [!DNL Microsoft Dynamics] con attribuzione campagna dedicata per misurare l’efficacia del programma.


## Programmazione di webinar e demo

Personalizza gli inviti al webinar e la pianificazione delle demo in base agli interessi del potenziale cliente, al settore e alla cronologia del coinvolgimento. Inviti pertinenti e tempestivi aumentano la partecipazione e generano pipeline di qualità superiore dalle interazioni live.

### Impatto aziendale

I webinar personalizzati e i programmi di invito demo visualizzano tassi di partecipazione migliorati, che derivano una pipeline più qualificata dalle opportunità di coinvolgimento live.

### Come implementare

Utilizza il pattern [Messaggistica attivata da eventi](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) per inviare inviti personalizzati quando i potenziali clienti dimostrano segnali di interesse allineati con i prossimi webinar o argomenti dimostrativi. Questo modello risponde in tempo reale ai trigger comportamentali, garantendo l’arrivo degli inviti quando l’interesse è più elevato. Questo è lo schema corretto quando l’attivatore è un’azione personalizzata del cliente allineata con la rilevanza del webinar e la risposta richiesta è un singolo invito sensibile al tempo, anziché una sequenza in più fasi o un programma di sviluppo in corso.

### Considerazioni tecniche

- Definisci eventi trigger basati su interessi (ad esempio, visita di una pagina di prodotto, download di una risorsa correlata, coinvolgimento con un confronto con un concorrente) che siano in linea con gli argomenti di webinar o demo pianificati.
- Integra i dati della piattaforma del webinar (ad esempio, [!DNL ON24], [!DNL Zoom Webinar]) per tenere traccia delle metriche di registrazione, partecipazione e coinvolgimento all&#39;interno del profilo unificato.
- Sincronizza le richieste demo e pianifica i dati con [!DNL Salesforce] o [!DNL Microsoft Dynamics] per garantire che i team di vendita ricevano notifiche e contesto tempestivi.
- Coordinare la frequenza degli inviti con i limiti di comunicazione [!DNL Marketo Engage] per evitare potenziali clienti con messaggi eccessivi che si qualificano per più eventi.


## Case study e ROI Personalization

Consegna case study personalizzati, calcolatrici del ROI e storie di successo in base al settore del potenziale cliente, alle dimensioni dell’azienda e al caso d’uso. Quando i potenziali clienti vedono punti di bozza di organizzazioni simili alle loro, la fiducia si costruisce più rapidamente e le decisioni di acquisto accelerano.

### Impatto aziendale

Le organizzazioni che personalizzano i contenuti dei punti di bozza vedono un coinvolgimento migliore nello studio dei casi, che contribuisce a rafforzare la fiducia nelle opportunità di vendita e a velocizzare i tassi di chiusura.

### Come implementare

Utilizza il pattern [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) per far emergere dinamicamente i casi aziendali più rilevanti e le prove di ROI in base al profilo di ogni potenziale cliente. Questo modello associa gli attributi del visitatore a una libreria di contenuti, garantendo che ogni potenziale cliente veda i punti di bozza del proprio settore e gruppo di pari. Questo è il modello giusto quando la personalizzazione è guidata dagli attributi di profilo e dall’appartenenza a un segmento anziché da un modello di affinità comportamentale, consentendo ad attributi di dimensioni di settore e azienda di associare i potenziali clienti a punti di bozza rilevanti.

### Considerazioni tecniche

- Assegna tag alle risorse di contenuti relativi a case study e ROI con metadati (settore, dimensioni dell’azienda, caso d’uso, prodotto) per abilitare la corrispondenza dinamica rispetto ai profili di potenziali clienti.
- Implementa regole di personalizzazione che danno priorità alla corrispondenza di settore, quindi alle dimensioni dell’azienda e al caso d’uso, con contenuti di fallback per potenziali clienti con dati di profilo limitati.
- Integra nuovamente i segnali di coinvolgimento dei contenuti (download, tempo sulla pagina, condivisioni) nel profilo unificato per informare il punteggio dei lead e la sensibilizzazione delle vendite.
- Coordinati con [!DNL Marketo Engage] per includere contenuto personalizzato di un punto di bozza nelle sequenze e-mail di sviluppo, non solo nelle esperienze sul sito.


## Programmi di Customer Advocacy

Identifica e coinvolgi i clienti soddisfatti per opportunità di advocacy come riferimenti, case study e testimonianze basate su dati di utilizzo e soddisfazione. I clienti felici sono un potente motore di crescita quando vengono riconosciuti e invitati a condividere il loro successo.

### Impatto aziendale

I programmi strutturati di sostegno ai clienti favoriscono una maggiore partecipazione alle attività di advocacy, generando un flusso costante di riferimenti, casi di studio e testimonianze a supporto di nuove acquisizioni aziendali.

### Come implementare

Utilizza il pattern [Multi-Step Orchestrated Percorsi](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) per creare flussi di lavoro di identificazione e coinvolgimento di advocacy che rispondano ai segnali di soddisfazione e di utilizzo. Questo modello supporta le domande di advocacy progressiva, a partire da una partecipazione leggera (ad es., una revisione) e avanzando verso impegni più profondi (ad es., una chiamata di riferimento o un caso di studio). Questo è il modello corretto quando il caso d’uso richiede un flusso di messaggi sequenziale e multiplo con avanzamento condizionale basato su segnali di soddisfazione e di utilizzo: un singolo messaggio attivato non può soddisfare la logica di coinvolgimento progressivo necessaria per inoltrare le richieste di supporto nel tempo.

### Considerazioni tecniche

- Acquisisci i risultati dei sondaggi sulla soddisfazione (ad es., Punteggio promotore netto, punteggi di soddisfazione del cliente) e i dati di utilizzo del prodotto per creare un punteggio di preparazione per la difesa per ogni account.
- Definisci i criteri di idoneità per il sostegno che combinano le soglie di soddisfazione, i milestone di utilizzo e la permanenza dell’account per evitare una sensibilizzazione prematura.
- Sincronizza lo stato di advocacy e la cronologia di partecipazione a [!DNL Salesforce] o [!DNL Microsoft Dynamics] in modo che i team di vendita possano fare riferimento ai sostenitori dei clienti durante la ricerca di potenziali clienti.
- Coordinati con [!DNL Marketo Engage] per eliminare le attività di sensibilizzazione durante le escalation di supporto attivo o le negoziazioni di rinnovo.

## Audience Activation basato su account B2B

Crea tipi di pubblico a livello di account che combinino dati firmografici, segnali di gruppo di acquisto e coinvolgimento a livello di persona, quindi attivali su LinkedIn, piattaforme lato domanda e destinazioni di gestione delle relazioni con i clienti. L’attivazione del pubblico basata sull’account consente alle organizzazioni B2B di indirizzare intere organizzazioni di acquisto con pubblicità digitale coordinata anziché con contatti individuali, allineando la spesa per media a pagamento alle priorità della pipeline di account.

### Impatto aziendale

Le organizzazioni B2B con attivazione del pubblico basata sull’account vedono una maggiore influenza della pipeline dai programmi a pagamento, con un impatto particolarmente elevato quando i segmenti di pubblico sono allineati con le priorità del territorio di vendita e aggiornati frequentemente con il variare dei punteggi di coinvolgimento dell’account.

### Come implementare

Utilizza il pattern [B2B Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) per creare segmenti a livello di account utilizzando relazioni account-persona e attivarli in destinazioni di supporti a pagamento con supporto B2B. Questo è lo schema corretto quando la costruzione del pubblico deve operare a livello di account, combinando segnali provenienti da più contatti all&#39;interno di un&#39;organizzazione di acquisto, piuttosto che a livello di singola persona.

### Considerazioni tecniche

- La configurazione del grafo di identità B2B deve collegare accuratamente gli individui noti ai loro record account; le lacune nelle associazioni account-persona determineranno un’aggregazione incompleta dei segnali dei gruppi di acquisto.
- I segmenti di pubblico dell’account devono essere aggiornati secondo una pianificazione in linea con le date di volo della campagna e la frequenza di revisione della pipeline: i segmenti che si allontanano dallo stato corrente della pipeline riducono l’efficienza della spesa multimediale.
- LinkedIn Matched Audiences e piattaforme B2B simili corrispondono su indirizzi e-mail professionali, che possono differire dagli indirizzi e-mail personali memorizzati in CRM; entrambi i tipi di e-mail devono essere inclusi nei payload del pubblico.
- I tipi di pubblico di attivazione dovrebbero escludere gli account nelle fasi di offerta attiva in cui la pubblicità a pagamento potrebbe creare una sovrapposizione imbarazzante con la sensibilizzazione alle vendite dirette.


## Journey Orchestration del gruppo di acquisto

Orchestrare percorsi a livello di account che coltivano i membri del gruppo di acquisto in base ai ruoli, ai punteggi di coinvolgimento e allo stato di qualifica dell&#39;account, con trasferimento automatico alle vendite. Coordinare la logica di percorso a livello di gruppo acquirente anziché a livello individuale garantisce che ogni parte interessata riceva messaggi appropriati al suo ruolo e alla sua fase decisionale, mantenendo al contempo la coerenza all’interno dell’account.

### Impatto aziendale

Le organizzazioni B2B che utilizzano l’orchestrazione dei percorsi di acquisto vedono migliorare i tassi di creazione delle opportunità dalla pipeline originata dal marketing e accelerare la progressione attraverso le prime fasi dell’offerta, in particolare quando il passaggio alle vendite viene attivato automaticamente in base a soglie di coinvolgimento misurabili.

### Come implementare

Utilizza il pattern [Acquisto di marketing basato su gruppo](/help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md) per creare percorsi qualificati per l&#39;account in grado di segmentare i membri dei gruppi di acquisto per ruolo, valutare i segnali di coinvolgimento a livello di gruppo e orchestrare campagne multi-touch coordinate con ramificazioni condizionali in base allo stato dell&#39;account. Questo è il modello corretto quando la logica di percorso deve operare a livello di gruppo di account anziché a livello di singola persona: l’orchestrazione di percorso standard a livello di persona non può gestire i requisiti di qualificazione del gruppo e di coordinamento interpersonale della gestione dei gruppi di acquisto B2B.

### Considerazioni tecniche

- Le definizioni di iscrizione al gruppo di acquisto devono essere mantenute nel modello di dati B2B, collegando i contatti noti ai loro account e assegnando loro ruoli come campione, acquirente economico o valutatore tecnico.
- Il punteggio di coinvolgimento dell’account deve aggregare i segnali provenienti da più persone all’interno del gruppo di acquisto; il coinvolgimento di un singolo contatto non è sufficiente per determinare la fattibilità a livello di account.
- La soppressione del percorso deve essere sincronizzata con le fasi dell’opportunità CRM per evitare che i messaggi di automazione del marketing entrino in conflitto con le conversazioni di vendita attive.
- Le notifiche di avviso e di trasferimento delle vendite devono essere integrate con la piattaforma CRM e Sales Engagement in modo che i rappresentanti ricevano un contesto tempestivo e actionable quando gli account raggiungono la soglia di trasferimento.


## Personalization Account-Based Marketing (ABM)

Personalizza le comunicazioni di marketing e i contenuti per gli account di destinazione in base al profilo dell’account, alla cronologia del coinvolgimento e ai segnali di acquisto. La personalizzazione ABM va oltre il targeting dell’account, personalizzando il contenuto dei messaggi e le esperienze web in base al settore specifico, alle dimensioni e alle problematiche di business note di ogni account, creando una rilevanza che i messaggi generici delle campagne non possono raggiungere.

### Impatto aziendale

Le organizzazioni B2B con personalizzazione a livello di account segnalano tassi di coinvolgimento migliorati per le campagne in uscita e una conversione più elevata da web a pipeline per gli account mirati, con risultati particolarmente positivi quando la personalizzazione si estende alle pagine di destinazione e alle esperienze web visitate tramite media a pagamento.

### Come implementare

Utilizza il pattern [B2B Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) per attivare i profili a livello di account per la personalizzazione tra canali web e in uscita. Questo è il modello corretto quando il requisito principale è il targeting a livello di account per la personalizzazione anziché l’orchestrazione del percorso a livello di contatto: i dati del profilo di account guidano le decisioni di personalizzazione anziché i singoli segnali comportamentali.

### Considerazioni tecniche

- I dati firmografici dell’account (settore, dimensioni dell’azienda, area geografica, stack tecnologico) devono essere aggiornati e modellati in modo coerente per promuovere una personalizzazione dei contenuti significativa oltre il targeting generico a livello di settore.
- La personalizzazione web per i visitatori B2B noti richiede la risoluzione IP-to-account o l’autenticazione diretta; la risoluzione basata su IP ha una precisione inferiore e non deve essere utilizzata per le decisioni di account di alto valore.
- È necessario sviluppare il contenuto per ogni segmento di account con targeting di personalizzazione; se si attiva la personalizzazione senza un numero sufficiente di varianti di contenuto, alcuni account riceveranno esperienze immutate.
- Le decisioni di Personalization a livello di account devono essere allineate con la fase CRM corrente e l’attività di vendita per evitare di fornire contenuti di sensibilizzazione top-of-funnel agli account già in offerte attive.
