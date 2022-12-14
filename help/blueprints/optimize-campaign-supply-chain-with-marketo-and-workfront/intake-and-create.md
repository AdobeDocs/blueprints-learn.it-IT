---
description: Acquisizione e creazione - Ottimizzare la catena di fornitura di Campaign con Marketo e Workfront
title: Acquisizione e creazione
source-git-commit: fd8dd3caee5cbf450c5f00266c74ccdef7cd1de9
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 0%

---

# Acquisizione e creazione {#intake-and-create}

Il numero di richieste di marketing che entrano in un team di marketing per lanciare nuove campagne può trasformare un team altamente funzionante in una porta girevole di attività ripetitive, causando bruciature e innovazione stagnante.

Stabilendo un processo per l’invio delle richieste di campagne e automatizzando la creazione di campagne di marketing comunemente richieste, puoi: velocizza le campagne, riduci gli errori, indirizza le richieste al membro giusto delle operazioni di marketing, bilancia e migliora l’utilizzo delle risorse e concentra maggiormente le operazioni di marketing su attività più strategiche.

Con Workfront e Marketo Engage, una connessione da sistema a sistema permette di ottenere i dettagli da un [Modulo di richiesta Workfront](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/customize/custom-forms/create-or-edit-a-custom-form.html){target=&quot;_blank&quot;} per creare un programma di Marketo Engage, quindi compilare variabili chiave come: oggetto, copia e-mail, immagini, date, ore, informazioni sull’evento e altro ancora.

Per ottenere questa integrazione, si utilizzerà Workfront Fusion, un livello di automazione del lavoro che consente di automatizzare i flussi di lavoro tra Workfront e altri sistemi.

Il flusso di lavoro seguente mostra una richiesta di un webinar effettuata da un gestore di campagne utilizzando un modulo di richiesta Workfront. I dettagli inviati nella richiesta attivano quindi un programma e un&#39;e-mail da creare in Marketo Engage per il webinar. Inoltre, dal modulo di richiesta vengono ricavati i dettagli per compilare il contenuto dell’e-mail.

![](assets/intake-and-create-1.png)

>[!TIP]
>
>Per ulteriori informazioni sui diversi tipi di oggetti in Workfront utilizzati per organizzare il lavoro delle campagne di marketing e su come è mappato a un programma di Marketo Engage, consulta la sezione [Panoramica di Marketo e Workfront](/help/blueprints/optimize-campaign-supply-chain-with-marketo-and-workfront/overview.md){target=&quot;_blank&quot;}.

## Preparare il processo di sviluppo della campagna per l’automazione {#prepare-your-campaign-development-process-for-automation}

Dietro ogni grande automazione del flusso di lavoro c&#39;è un processo definito che garantisce a team e parti interessate il massimo valore dall&#39;automazione.

**Quali tipi di richieste di marketing riceverai?**

Pensa a quali tipi di tattiche di marketing eseguirai come e-mail, infermieri, webinar di prima parte ed eventi. Esegui anche webinar di terze parti o annunci display? Ognuna di queste richieste deve essere considerata in quanto potrebbe aver bisogno di campi di input specifici nel modulo di richiesta e verrà mappata su diversi modelli di programma in Marketo Engage che verranno clonati.

Inoltre, è importante comprendere se si eseguono campagne in più aree geografiche. In questo caso, è necessario tenere conto di un progetto in Workfront che crea più programmi in Marketo Engage, con ogni programma che rappresenta un supporto linguistico diverso.

È importante sapere in anticipo quali tipi di richieste di marketing si prevede di ricevere per garantire che le richieste possano essere facilitate in modo automatico.

**Quali informazioni devono essere acquisite nella richiesta della campagna?**

Pensa alle informazioni chiave che dovranno essere acquisite nel modulo di richiesta per ciascuna delle diverse tattiche che esegui. Di seguito sono riportati alcuni esempi di informazioni che è possibile acquisire in un modulo Workfront per automatizzare lo sviluppo della campagna.

<table> 
  <tr> 
   <td><b>Strategia di marketing</b></td>
   <td><b>Informazioni da acquisire</b></td>
  </tr>
  <tr> 
   <td>Invia e-mail</td>
   <td>・ Oggetto e-mail<br />
・ Data pianificata<br />
・ Copia e-mail<br />
・ Invito all'azione<br />
・ Immagini - È possibile fare riferimento diretto agli URL di AEM Assets da utilizzare in Marketo<br />
・ Criteri di qualificazione del pubblico</td>
  </tr>
  <tr>
   <td>Webinar/Evento</td>
   <td>・ Nome evento<br />
・ Data evento<br />
・ Ora evento<br />
・ Città Evento<br />
・ Descrizione evento<br />
・ Pagina di registrazione Webinar - PageURL OnDemand<br />
・ Nomi dei diffusori<br />
・ Titoli dei diffusori<br />
・ Immagini dei diffusori<br />
・ E-mail necessarie (invito, conferma, promemoria, follow-up)<br />
・ Immagini di intestazione e-mail<br />
・ Criteri di qualificazione del pubblico</td>
  </tr>
  <tr>
   <td>Infermiera</td>
   <td>・ Numero di e-mail<br />
・ Copia e-mail<br />
・ Intestazioni e-mail<br />
・ Invito all'azione<br />
・ Criteri di qualificazione del pubblico</td>
  </tr>
  </tbody>
</table>

>[!NOTE]
>
>Oggi, la creazione programmatica di tipi di pubblico tramite automazione è limitata nel Marketo Engage perché i token non sono supportati negli elenchi avanzati. Ciò significa che i tipi di pubblico dovranno essere creati in Marketo Engage da un utente, oppure che se si dispone di un pubblico predeterminato a cui si comunica continuamente, è possibile includere un elenco smart configurato come parte del modello di programma clonato durante il processo di automazione.

### Stabilire il centro di eccellenza {#establish-your-center-of-excellence}

Se desideri automatizzare la creazione di programmi, avrai bisogno di un centro di eccellenza nel Marketo Engage. Un centro di eccellenza include programmi e risorse modellati per accelerare e standardizzare il processo di sviluppo delle campagne. Ad esempio, puoi avere un modello di programma per diverse esigenze di campagna: e-mail, nurture, evento di persona e webinar. Inoltre, puoi disporre di più modelli di programma e-mail da utilizzare per aree geografiche diverse o per diversi tipi di annunci e-mail.

La creazione di un centro di eccellenza con modelli di programma in Marketo Engage è uno dei primi passi per un approccio più programmatico all’esecuzione delle campagne e fungerà da base per automatizzare le richieste di campagne.

Una volta che si dispone di un set di modelli di programma riutilizzabili, è possibile aumentare ulteriormente le attività utilizzando l&#39;automazione descritta in questo blueprint per velocizzare lo sviluppo della campagna.

Per saperne di più sulla creazione del proprio centro di eccellenza, consulta la sezione [Community Marketo](https://nation.marketo.com/t5/product-blogs/marketo-master-class-center-of-excellence-with-chelsea-kiko/ba-p/243221){target=&quot;_blank&quot;} per le best practice.

### Utilizzare i token per popolare il contenuto {#use-tokens-to-populate-content}

Al Marketo Engage, i token possono essere utilizzati per popolare i contenuti nelle risorse delle campagne. Ad esempio, dopo aver clonato un modello di e-mail dal centro di eccellenza, Workfront Fusion può prendere i dettagli dalla richiesta della campagna in Workfront e trasmetterli ai Token personali nel programma di Marketo Engage. I valori del token possono quindi essere ereditati direttamente nell’e-mail per creare l’e-mail.

![](assets/intake-and-create-2.png)

### Popolare immagini da AEM Assets {#populate-images-from-aem-assets}

Puoi automatizzare ulteriormente lo sviluppo di e-mail e pagine di destinazione utilizzando token di Marketo Engage in combinazione con i collegamenti alle risorse in AEM Assets. I richiedenti di Campaign possono inviare collegamenti immagine pubblicati da AEM Assets come parte del processo di richiesta. Workfront Fusion può quindi prendere questi collegamenti e incorporarli nel HTML di un&#39;e-mail utilizzando i token di Marketo Engage.

Ricorda che dovrai creare i programmi e i modelli di programma in Marketo Engage per utilizzare i miei token in modo che Fusion possa aggiornare i valori dei token con le informazioni inviate in Workfront.

>[!NOTE]
>
>AEM Assets non è necessario per supportare questo flusso di lavoro, ma può consentire un processo più semplificato per la gestione delle risorse delle campagne nell’intera catena di fornitura dello sviluppo delle campagne.

### Assembla una libreria di ricerca per tutti i tipi di richieste di programma {#assemble-a-lookup-library-for-all-program-request-types}

Quando si automatizza la creazione di nuovi programmi di Marketo Engage da richieste Workfront, è importante includere un passaggio nell&#39;automazione Workfront Fusion che può prendere informazioni dalla richiesta Workfront e cercare i modelli di programma corretti che devono essere clonati nel Marketo Engage.

A questo scopo, è possibile importare un set di dati in Workfront Fusion che include un elenco di tutti i diversi modelli di programma nel centro di eccellenza del Marketo Engage.

Alcune informazioni di base da includere nella libreria di ricerca modelli di programma sono:

<table> 
  <tr> 
   <td><b>Colonna</b></td>
   <td><b>Descrizione</b></td>
  </tr>
  <tr> 
   <td>Tipo di campagna</td>
   <td>Questo potrebbe essere e-mail, webinar, nurture, evento, webinar di terze parti, importazione di elenchi, ecc.. Il tipo di campagna agirà come una descrizione leggibile per ciò che viene richiesto.</td>
  </tr>
  <tr> 
   <td>Tipo di richiesta Workfront</td>
   <td>Si tratta del tipo di richiesta selezionato nel modulo Workfront, che può essere lo stesso del tipo di campagna, ad esempio e-mail, webinar, nurture o evento. Viene utilizzato per mappare l’input selezionato nel modulo Workfront su un modello di programma in Marketo.</td>
  </tr>
  <tr> 
   <td>ID modulo Workfront</td>
   <td>L’ID univoco del modulo di richiesta Workfront utilizzato per convalidare la richiesta di scrittura viene mappato sul modello di programma Marketo Engage.</td>
  </tr>
  <tr> 
   <td>ID programma Marketo</td>
   <td>Questo è l’ID del modello di programma in Marketo Engage associato alla richiesta in corso. Avere queste informazioni prontamente disponibili in Workfront Fusion consentirà a Fusion di fare la richiesta al Marketo Engage e sapere esattamente quale programma clonare.</td>
  </tr>
  </tbody>
</table>

## Flusso di entrata e creazione dell’automazione {#intake-and-create-automation-flow}

Ecco un esempio di come la logica del flusso di lavoro può essere assemblata in Fusion utilizzando [Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target=&quot;_blank&quot;} e [Marketo Engage](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html)Moduli {target=&quot;_blank&quot;} che consentono di distribuire l&#39;automazione più rapidamente.

![](assets/intake-and-create-3.png)

## Risorse {#resources}

* [Moduli Adobe Marketo Engage](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html){target=&quot;_blank&quot;}

* [Moduli Adobe Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target=&quot;_blank&quot;}

* [Panoramica di Marketo e Workfront](/help/blueprints/optimize-campaign-supply-chain-with-marketo-and-workfront/overview.md){target=&quot;_blank&quot;}
