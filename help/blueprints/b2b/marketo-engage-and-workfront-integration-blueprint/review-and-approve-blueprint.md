---
title: Blueprint per la revisione e l’approvazione
description: Blueprint per la revisione e l’approvazione - Blueprint per l’integrazione di Marketo Engage e Workfront
exl-id: a446faab-7db4-42a2-b4b9-395725c49c9f
source-git-commit: 3d6a2416cdb9956e59be4b2918ba19f88cd2150b
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 87%

---

# Blueprint per la revisione e l’approvazione {#review-and-approve-blueprint}

Per assicurarsi che le risorse e le campagne di marketing soddisfino le aspettative e gli standard di un’azienda, occorre andare oltre la consegna dei contenuti e messaggi giusti al pubblico giusto. Quando si intraprendono nuove iniziative di marketing, le organizzazioni hanno anche la responsabilità di rispettare le politiche interne, le normative di uno specifico settore e persino i prerequisiti legali. Incorporando i passaggi di revisione e approvazione nel processo di sviluppo delle campagne, i team di marketing possono garantire che i contenuti e i messaggi siano accurati e conformi agli standard del proprio settore, in particolare per settori come finanza, assistenza sanitaria e prodotti farmaceutici.

Con Workfront e Marketo Engage, i team di marketing possono disporre di un sistema di marketing strettamente connesso, con messaggistica accurata e conforme.

## Verifica di bozze e approvazioni avanzate per Marketo Engage con Workfront {#unlock-proofing-and-advanced-approvals}

Nella creazione di campagne di marketing, è importante tenere presente che più sistemi supportano i diversi passaggi coinvolti, quali pianificazione, creazione, revisione, feedback, approvazione ed esecuzione. Workfront e Marketo Engage offrono ai team tutti gli strumenti necessari per svolgere tutti i processi richiesti per una nuova campagna di marketing, dalla pianificazione al lancio. Inoltre, i team possono semplificare ulteriormente il processo di revisione e approvazione per velocizzare lo sviluppo delle campagne, garantendo al contempo che vengano rispettati i massimi standard in termini di accuratezza e conformità.

### Revisione e approvazione dei casi d’uso sbloccati con il Marketo Engage e Workfront {#review-and-approve-use-cases-unlocked-with-marketo-engage-and-workfront}

* Elimina modalità di feedback eterogenee e aumenta la collaborazione in un luogo centralizzato applicando le funzionalità di annotazione e commenti di Workfront alle risorse di Marketo Engage.

* Centralizza le approvazioni attivandole in Marketo Engage dai flussi di lavoro di approvazione di Workfront.

* Supporta e semplifica complessi flussi di lavoro di approvazione delle risorse di marketing applicando le funzionalità avanzate di approvazione di Workfront alle risorse di Marketo Engage.

* Semplifica l’accesso alle bozze di marketing rendendo disponibili in Workfront, in modo programmatico, le risorse Marketo affinché possano essere riviste dalle diverse parti interessate.

* Tieni traccia delle modifiche e crea una documentazione cartacea centralizzando in Workfront tutto il lavoro di revisione e verifica di bozze per le risorse di Marketo Engage.

## Pianificazione del flusso di lavoro di verifica di bozze e approvazione {#planning-your-proof-and-approval-workflow}

Prima di impostare l’integrazione tra Marketo Engage e Workfront per la verifica di bozze e l’approvazione, considera i seguenti aspetti:

* Quali risorse dovranno essere riviste e approvate?
* Da chi devono essere approvate?
* È richiesta l’approvazione di più persone prima che una risorsa di marketing possa essere pubblicata?
* In quale fase dello sviluppo della campagna le risorse di marketing verranno assemblate e saranno pronte per essere riviste?

Rispondendo a queste domande potrai farti un’idea di come dovrà essere il flusso di approvazione e capire come iniziare a configurare l’istanza di Workfront.

## Creazione di un flusso di lavoro di verifica di bozze e approvazione tra Marketo Engage e Workfront {#building-a-proof-and-approval-workflow}

Per semplificare il processo di verifica di bozze e approvazione tra Workfront e Marketo Engage, puoi integrare le due soluzioni mediante Workfront Fusion. Workfront Fusion fornisce un’interfaccia per flussi di lavoro con cui è possibile attivare delle azioni e trasmettere informazioni tra le istanze di Workfront e Marketo Engage.

Per un’esperienza di revisione e approvazione integrata, considera i passaggi seguenti.

1. Configurare il progetto Workfront con un’attività Ready for Review (Pronto per la revisione).
1. Attivare la sincronizzazione con Workfront dell’e-mail di Marketo Engage quando cambia lo stato dell’attività.
1. Convertire il file e-mail di Marketo Engage in una bozza da visualizzare in Workfront.
1. Utilizza la verifica Workfront per collaborare tramite commenti e annotazioni.
1. Approvare la bozza di Workfront in modo che venga attivata l’approvazione delle risorse in Marketo Engage, quindi contrassegnare l’attività come completata.

### Configurare il progetto Workfront con un’attività Ready for Review (Pronto per la revisione) {#configure-a-workfront-project-with-a-ready-for-review-task}

Utilizza i [modelli di progetto](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/create-and-manage-project-templates/project-template-overview.html?lang=it){target="_blank"} per acquisire la maggior parte delle informazioni, delle impostazioni e dei processi ripetibili associati ai progetti gestiti dalla tua organizzazione. Puoi definire le attività e gli argomenti coda, creare dei moduli personalizzati e allegare dei documenti al modello.

Nel modello di progetto Workfront, includi le attività di revisione delle risorse che fanno parte della campagna di marketing. Inoltre puoi aggiungere un processo di approvazione per gestire sia approvazioni singole che approvazioni più complesse e a più livelli.

Nel caso di una nuova campagna e-mail, il modello di progetto dovrà includere un’attività di revisione dell’e-mail nonché un processo di approvazione affinché l’e-mail venga approvata dalle parti interessate prima di essere inviata.

![schermata attività](assets/review-and-approve-blueprint-1.png){zoomable="yes"}

### Attivare la sincronizzazione con Workfront dell’e-mail di Marketo Engage quando cambia lo stato dell’attività {#trigger-your-marketo-engage-email-to-sync-to-workfront}

Il processo di revisione dovrà includere la sincronizzazione delle e-mail con il relativo progetto Workfront, una volta che queste saranno pronte per la revisione da parte del team di marketing. A questo scopo, consigliamo di impostare un’attività Ready for Review (Pronto per la revisione) con uno [stato attività](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/update-work-on-a-project/update-task-status.html?lang=it){target="_blank"} che indichi quando l’e-mail è pronta per essere rivista. Nel nostro esempio, abbiamo aggiunto all’attività lo stato Review Marketo Email (Rivedi e-mail Marketo), da selezionare quando la bozza dell’e-mail è pronta per essere rivista dalle parti interessate.

Una volta impostato questo stato nel progetto Workfront, puoi configurare uno scenario Workfront Fusion che rilevi l’attività Ready for Review (Pronto per la revisione) e aggiorni lo stato a Review Marketo Email (Rivedi e-mail Marketo). Dopo questo aggiornamento, lo scenario può recuperare l’e-mail di Marketo Engage come file HTML, comprimerlo in un file .zip e salvarne una copia nei documenti del progetto Workfront da rivedere.

![pronto per la schermata di revisione](assets/review-and-approve-blueprint-2.png){zoomable="yes"}

### Convertire l’e-mail di Marketo Engage in una bozza da visualizzare in Workfront {#convert-your-marketo-engage-email-to-reviewable-proof-in-workfront}

Una volta che lo stato dell’attività Ready for Review (Pronto per la revisione) diventa Review Marketo Email (Rivedi e-mail Marketo) e che l’e-mail di Marketo Engage viene salvata in Workfront, puoi configurare lo scenario Workfront Fusion affinché l’e-mail venga convertita in una bozza Workfront.

### Utilizza la verifica Workfront per collaborare tramite commenti e annotazioni {#use-workfront-proofing-to-collaborate}

Le funzionalità di [verifica di Workfront](https://experienceleague.adobe.com/docs/workfront/using/review-and-approve-work/proofing/proofing-overview/proofing-basics.html?lang=it){target="_blank"} consentono al team marketing di acquisire una nuova risorsa, ad esempio un&#39;immagine o un messaggio e-mail, e collaborare tramite commenti e annotazioni. Quando una bozza è pronta per essere pubblicata, i responsabili decisionali possono approvare la risorsa dallo strumento di bozza.

![converti schermata e-mail](assets/review-and-approve-blueprint-3.png){zoomable="yes"}

### Approva Workfront Proof e attiva l’approvazione delle risorse nel Marketo Engage, contrassegna l’attività come completata {#approve-workfront-proof-and-trigger-asset-approval-in-marketo-engage}

Workfront Fusion può rilevare quando l’e-mail è stata approvata dalle parti interessate e inviare una richiesta al Marketo Engage per approvare l’e-mail all’interno di Marketo.

Con l’e-mail rivista/approvata dai membri del team giusto, l’e-mail è pronta per essere pubblicata in Marketo Engage.

## Modelli di scenario Fusion {#fusion-scenario-templates}

Per semplificare lo sviluppo dei flussi di lavoro di revisione e approvazione nella tua istanza di Workfront e Marketo Engage, abbiamo creato dei modelli Fusion che ti aiuteranno a iniziare a utilizzare l’integrazione. Per utilizzare tali modelli, cerca “Marketo” nella sezione Modelli pubblici di Fusion e scaricali nella tua istanza.

### Rivedere in Workfront una bozza dell’e-mail di Marketo Engage {#review-an-email-proof-of-your-marketo-engage-email-draft-in-workfront}

Lo scenario Fusion riportato di seguito illustra la prima metà del flusso di revisione e approvazione, in cui la bozza dell’e-mail può essere acquisita da Marketo Engage e salvata in Workfront come bozza. Una volta salvata come bozza nei documenti del progetto Workfront, può essere rivista dal personale marketing preposto, che potrà aggiungere commenti e annotazioni durante il processo di revisione.

![flusso di revisione e approvazione dello scenario di fusione](assets/review-and-approve-blueprint-4.png){zoomable="yes"}

### Approvare un’e-mail in Workfront e attivare l’approvazione della risorsa in Marketo Engage {#approve-an-email-in-workfront-that-triggers-approval}

Lo scenario Fusion riportato di seguito può essere utilizzato per rilevare quando una bozza in Workfront è stata approvata e indirizzare quindi tale approvazione a Marketo Engage affinché la bozza dell’e-mail possa essere aggiornata allo stato live, pronta per essere utilizzata in un programma di Marketo Engage.

![approvazione bozza scenario di fusione](assets/review-and-approve-blueprint-5.png){zoomable="yes"}

Insieme, questi due scenari consentono di creare un percorso bidirezionale per portare le risorse di marketing da Marketo Engage ai solidi flussi di lavoro di Workfront per la revisione e l’approvazione, e quindi trasmettere nuovamente le approvazioni da Workfront a Marketo Engage.
