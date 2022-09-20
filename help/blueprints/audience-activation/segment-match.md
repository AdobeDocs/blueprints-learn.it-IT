---
title: Corrispondenza segmento
description: Scopri [!UICONTROL Corrispondenza segmento] per Adobe Experience Platform (AEP). [!UICONTROL Corrispondenza segmento] è un servizio di collaborazione dati che ti consente di scambiare dati sui segmenti basati su identificatori comuni del settore in modo sicuro, gestito e rispettoso della privacy.
solution: Experience Platform
source-git-commit: a4ae1eaa864f85144b8bdfbff23b4389847c8cfa
workflow-type: tm+mt
source-wordcount: '1750'
ht-degree: 0%

---

# Corrispondenza segmento

La chiave per i marchi è quella di connettersi con i clienti in base ai dati raccolti dalle loro relazioni dirette con i consumatori. Grazie a migliori sistemi di governance, autorizzazioni e gestione delle preferenze, gli esperti di marketing possono migliorare ulteriormente i tipi di pubblico autenticati di prime parti con i partner chiave.

[!UICONTROL Corrispondenza segmento] è un servizio di collaborazione dati per consentire ai clienti di Experience Platform (AEP) (denominato _partner_) per scambiare dati sui segmenti basati su identificatori comuni del settore in modo sicuro, regolamentato e rispettoso della privacy.

Il servizio consente ai clienti di identificare in modo sicuro gli ID corrispondenti in modo sicuro e neutro senza dover divulgare l’intero database. I partner ricevono solo gli attributi designati (nome del segmento) per gli ID sovrapposti, consentendo una condivisione più rapida e semplice in modo controllabile e gestito dal consenso.

[!UICONTROL Corrispondenza segmento] utilizza la governance dei dati AEP e il framework di consenso come spina dorsale. È disponibile per tutti i clienti Real-time Customer Data Platform B2C e B2P. Funzioni principali di [!UICONTROL [!UICONTROL Corrispondenza segmento]] include:

* Condivisione dei segmenti per clienti che acconsentono alla sovrapposizione
* Report di sovrapposizione pre-condivisione per informazioni sul volume di corrispondenza stimato
* Politica DULE completamente integrata e applicazione delle autorizzazioni
* spina dorsale del framework di consenso per la condivisione dei dati
* Feed di dati per l’organizzazione di segmenti e partner

## Applicazioni

Brand to Publisher:

Il &quot;caso d’uso dell’editore&quot; è il più interessato dalla deprecazione dei cookie di terze parti e dei dati dell’id della pubblicità mobile. Questo caso d&#39;uso ha un impatto importante sull&#39;industria dei media e dell&#39;intrattenimento che si concentra sulla vendita della pubblicità come modello di business. [!UICONTROL Corrispondenza segmento] è un percorso per gli editori con un pubblico di prima parte di grandi dimensioni che desiderano collaborare direttamente con i loro inserzionisti. Gli inserzionisti possono collaborare direttamente con gli editori per promuovere tipi di pubblico corrispondenti sulle proprietà dell’editore per il targeting granulare o le campagne di ricerca.

### Brand to Brand

I percorsi al consumo non sono mai lineari. Ad esempio, un cliente può essere fedele a una compagnia aerea e alla sua società con carta di credito. Utilizzando [!UICONTROL Corrispondenza segmento], la compagnia aerea e la società di carte di credito possono creare una partnership di dati per comprendere i tipi di pubblico che si sovrappongono e quindi personalizzare le offerte per personalizzare le esperienze ai consumatori fedeli di ciascuna azienda.

### BU a BU

Le multinazionali globali hanno delle sfide con la collaborazione dei dati tra business unit indipendenti. La combinazione di dati in un unico sandbox potrebbe non essere possibile a causa della diversa informativa sulla privacy, acquisizioni o gestione delle autorizzazioni tra le BU.

[!UICONTROL Corrispondenza segmento] aiuta diversi team di marketing di grandi organizzazioni a collaborare in modo più efficiente, continuando a operare in modo indipendente

## Architettura

![Architettura di corrispondenza dei segmenti](assets/architecture-segment-match.png)

[!UICONTROL Corrispondenza segmento] non è un data marketplace in cui i dati possono essere acquistati. Si tratta piuttosto di una funzione AEP che funziona con dati di prime parti con partner selezionati, utilizzando i controlli sulla privacy e sul consenso per collaborare. [!UICONTROL Corrispondenza segmento] aiuta a concentrare gli sforzi sul miglioramento delle relazioni con i clienti e sulla crescita del brand. È utile quando esistono marchi o relazioni di partner preesistenti. [!UICONTROL Corrispondenza segmento] l’esperienza è facile da gestire, scalabile e consente agli amministratori di condividere i segmenti in modo opt-in e controllabile.

[!UICONTROL Corrispondenza segmento] abilita:

* I dati di appartenenza al segmento devono essere inviati in modo sicuro tra le organizzazioni utilizzando identificatori standard a livello di persona, come e-mail con hash o numero di telefono
* Interfaccia utente e flussi di lavoro di condivisione del pubblico con le notifiche
* Stime di sovrapposizione pre-condivise
* Configurazione del partner self-service
* Sovrapposizioni su specifici namespace standardizzati (e-mail con hash, telefono con hash, ECID, IDFA, GAID)
* Applicazione del consenso per la condivisione dei dati
* Gestione del ciclo di vita dell&#39;audience condivisa
* Applicazione DULE nel flusso di lavoro di condivisione
* Aggiornamenti batch giornalieri

[!UICONTROL Corrispondenza segmento] consente di creare un’esperienza cliente interconnessa. Gli identificatori durevoli supportati sono e-mail con hash, numeri di telefono con hash e identificatori come ECID, IDFA e GAID. I clienti possono creare feed che corrispondono e spostano i dati del pubblico tra le sandbox del brand, con una governance forte, trasparenza e funzionalità di revoca per l’utilizzo nelle attività pubblicitarie e di marketing

## Prerequisiti

I prerequisiti per [!UICONTROL Corrispondenza segmento] sono:

* Licenza attiva RT-CDP
* Gli identificatori con hash standard supportati sono e-mail con hash SHA256, telefono con hash, ECID, Apple IDFA e GAID
* Framework per la privacy e strategia di consenso
* Accordi sulla condivisione dei dati tra i clienti

## Sicurezza

### RBAC

La [!UICONTROL Corrispondenza segmento] Il flusso per gestire i partner è protetto da RBAC. Solo gli individui con la giusta autorizzazione possono avviare, accettare o gestire i partner. Questa operazione può essere eseguita nella sezione Acquisizione dati del profilo di prodotto. Sono necessarie le seguenti autorizzazioni:

![Connessione Condivisione pubblico](assets/data-ingestion.png)

| Autorizzazione | Descrizione |
|---|---|
| **Gestire le connessioni di Audience Share** | Questa autorizzazione consente di completare il processo di handshake del partner, che collega due organizzazioni IMS per abilitare [!UICONTROL Corrispondenza segmento] flussi. |
| **Gestire le condivisioni di pubblico** | Questa autorizzazione consente di creare, modificare e pubblicare feed (il pacchetto di dati utilizzato per [!UICONTROL Corrispondenza segmento]) con partner attivi (partner che sono stati collegati dall&#39;utente amministratore con **Connessioni di Audience Share** accesso). |

Fai riferimento a [documentazione ufficiale](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=en#understanding-segment-match-permissions) per ulteriori informazioni sulle autorizzazioni.

### ID connessione

Il processo di connessione del partner è gestito dal **[!UICONTROL ID connessione],** è un identificatore generato in modo casuale associato a una specifica sandbox AEP. Questo ID di connessione è necessario per avviare e gestire le sandbox dei partner. È inoltre possibile rigenerare l’ID di connessione per riconfigurare una connessione partner, se necessario.

### Governance

Qualsiasi set di dati o attributi di dati con *C11* l&#39;etichetta del contratto è limitata per [!UICONTROL Corrispondenza segmento] servizio. I segmenti che utilizzano tali attributi non possono essere utilizzati per [!UICONTROL Corrispondenza segmento]. Questo fornisce il controllo per il quale i segmenti possono o non possono essere utilizzati [!UICONTROL Corrispondenza segmento]. Vengono inoltre applicati i criteri personalizzati e le azioni di marketing create. Per impostazione predefinita, i criteri sono disabilitati e devono essere abilitati per l’applicazione. Vengono inoltre propagate e condivise con i partner restrizioni quali il marketing e la pubblicità on-site selezionate durante la condivisione dei segmenti.

### Consenso

Impostazioni di consenso per [!UICONTROL Corrispondenza segmento] possono essere gestiti nei seguenti modi:

* A livello di organizzazione, durante l’onboarding, utilizzando l’impostazione di rinuncia o consenso per i controlli del consenso.

   Questa impostazione determina se i dati utente possono essere condivisi o meno. L’impostazione predefinita è impostata su rinuncia che indica che i dati utente possono essere condivisi con il presupposto che il cliente AEP abbia già il consenso richiesto per l’utilizzo della condivisione dei dati. Questa impostazione può essere modificata in opt-in contattando Adobe Account Manager, effettuando un check-in aggiuntivo per forzare i clienti AEP a monitorare esplicitamente il consenso.

* Impostazione dell&#39;attributo di condivisione specifico per le identità (idSpecific) utilizzando il [Gruppo di campi Consensi e Preferenze](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/consents.html?lang=en).

   Questo gruppo di campi fornisce un singolo campo di tipo oggetto, consensi, per acquisire le informazioni sul consenso e sulle preferenze. [!UICONTROL Corrispondenza segmento], per impostazione predefinita, includerà tutte le identità che non sono state esplicitamente rifiutate, ad esempio:

   ```
   "share": {
   `                `"val": "n"
   `     `}
   ```

   Per modificare questa impostazione, contatta Adobe Account Manager e includi solo le identità con consenso esplicito, ad esempio:

   ```
   "share": {
   `                `"val": "y"
   `     `}
   ```

### Avvisi

Gli avvisi vengono generati quando si avvia una connessione partner o quando i feed di segmento sono condivisi con i partner.

## Flusso di lavoro di configurazione

Il flusso di lavoro per la configurazione della connessione partner viene gestito con il RBAC come indicato in precedenza. Con le autorizzazioni appropriate in posizione, la connessione a una sandbox partner richiede la condivisione dell’ID di connessione di tale sandbox/istanza all’interno dell’organizzazione del partner.

Una volta richiesta la connessione al partner mittente, la connessione deve essere approvata dal lato ricevente per garantire una configurazione sicura e sicura del partner. L&#39;handshake di connessione dei partner garantisce l&#39;esistenza dell&#39;accordo tra le due organizzazioni e consente ad Adobe di facilitare l&#39; [!UICONTROL Corrispondenza segmento] per conto dell&#39;organizzazione. Con la connessione approvata e in stato attivo, il processo di condivisione del segmento può essere avviato da entrambi i lati.

### Condivisione dei segmenti

La condivisione dei segmenti con il partner avviene solo quando esiste una corrispondenza sull’identificatore selezionato. Può esistere una relazione di tipo uno-a-molti, il che significa che i segmenti possono essere condivisi con più partner.

Per avviare la condivisione dei segmenti dopo l’impostazione della connessione partner, il partner mittente deve creare un feed. Quindi, seleziona i casi di utilizzo o le azioni di marketing da cui i dati del segmento devono essere esclusi insieme agli identificatori durevoli. È quindi possibile aggiungere al feed segmenti rilevanti per la condivisione.

Come parte di questo flusso di lavoro di condivisione dei segmenti, il partner mittente può individuare potenziali segmenti di alto valore tramite sovrapposizioni stimate prima dello spostamento di qualsiasi dato.

Il flusso complessivo del processo è il seguente:

![Condivisione dei segmenti](assets/segment-sharing.png)

Queste stime di sovrapposizione offrono informazioni chiave, analisi dei partner e dati per alimentare gli accordi di collaborazione sui dati. Per ottenere queste metriche di stima della sovrapposizione, non vengono spostati dati di clienti o segmenti tra le sandbox. Le identità applicabili selezionate dal cliente e prehashed in una data sandbox vengono aggiunte a una struttura di dati probabilistica che consente ad Adobe di eseguire operazioni di unione e intersezione tra di loro. Queste operazioni sono utili [!UICONTROL Corrispondenza segmento] ottenere l’intersezione stimata di due strutture di dati composte da identità di due diverse sandbox senza dover confrontare i valori effettivi

Il processo di sovrapposizione delle identità dipende dal **esportazione a pieno profilo giornaliera** set di dati dalle sandbox del mittente e del destinatario per identificare i profili comuni che appartengono ai segmenti condivisi. Il flusso dettagliato del processo di sovrapposizione è illustrato di seguito:

![Processo di sovrapposizione identità](assets/overlap-process.png)

Una volta completata la condivisione dei segmenti dal partner di invio, il ricevitore riceve una notifica sul feed di segmento condiviso. Questo feed di segmento deve essere abilitato affinché il profilo del ricevitore avvii il flusso di dati dell’appartenenza al segmento. Solo l’appartenenza al segmento viene acquisita nei frammenti di profilo sovrapposti dell’organizzazione IMS ricevente e non viene trasferita alcuna identità aggiuntiva dal mittente al destinatario.

Il segmento condiviso è disponibile nella sezione `AEPSegmentMatch` della sezione **[!UICONTROL Tipi di pubblico]** nella scheda **[!UICONTROL Generatore di segmenti]** e può essere utilizzato per includere o eliminare i tipi di pubblico durante la creazione di segmenti nella sandbox del ricevitore.

Il processo di sovrapposizione giornaliera mantiene l’appartenenza al segmento sincronizzata tra il mittente e il destinatario. Il ricevitore può disabilitare il profilo per il feed di segmento ricevuto per mettere in pausa il processo di condivisione del segmento.

#### Uscita/entrata segmento

Come parte dell’esportazione del profilo completo, lo stato degli ID del segmento condiviso sotto l’appartenenza del segmento per i profili ha uno dei valori corrispondenti - _realizzato_, _uscito_ oppure _esistente_ per riflettere lo stato corrente.

Durante il processo di sovrapposizione dell’identità giornaliera, se l’identità corrispondente esiste nella sandbox del ricevitore, questi stati di appartenenza del segmento per i segmenti condivisi vengono inviati al ricevitore per l’acquisizione.

#### Revoca dei segmenti

La revoca/cancellazione del segmento da parte del mittente è un processo on-demand in cui l’elenco di tutti i profili con gli ID del segmento revocati viene ottenuto dal destinatario. Gli ID segmento vengono rimossi dall’appartenenza al segmento di tali identità e riacquisiti presso il ricevitore. Questa azione sovrascrive il frammento di appartenenza del segmento esistente, che elimina l’appartenenza per quel segmento.

## Ulteriori informazioni

* [Corrispondenza segmento](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=en#)
* [Autorizzazioni](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=en)
* [Risoluzione dei problemi](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/troubleshooting.html?lang=en)
* [XID](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=en)
