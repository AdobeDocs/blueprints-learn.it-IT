---
title: Diagramma dell’architettura di Adobe Experience Platform e relative applicazioni
description: Questo diagramma di architettura mostra come Adobe Experience Platform si correla ad altre applicazioni e servizi applicativi Adobe Experience Cloud.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 70b3bf294741888c3d109a2d4ef710d428800abf
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 11%

---

# Adobe Experience Platform e relative applicazioni

## Diagramma dell’architettura di Adobe Experience Platform e relative applicazioni

Questo diagramma di architettura mostra come Adobe Experience Platform si correla alle applicazioni e ai servizi applicativi Adobe Experience Cloud.

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform e applicazioni" style="border:1px solid #4a4a4a" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Diagramma dettagliato dell’architettura di Adobe Experience Platform e relative applicazioni

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform e applicazioni" style="border:1px solid #4a4a4a" />

## Integrazioni di applicazioni Adobe Experience Platform e Experience Cloud

<table class="relative-table wrapped" style="width: 100%;" >
   <colgroup>
    <col style="width: 16.0202%;"/>
    <col style="width: 29.3423%;"/>
    <col style="width: 33.5582%;"/>
    <col style="width: 21.0793%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>Applicazione</th>
      <th>Experience Platform all'applicazione</th>
      <th>Applicazione all'Experience Platform</th>
      <th>Blueprint correlate</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>I tipi di pubblico definiti in Real-time Customer Data Platform possono essere condivisi con Ad Cloud per il targeting tramite Audience Manager.</li>
        </ul>
      </td>
      <td colspan="1">Nessuna integrazione corrente</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Attivazione del pubblico con dati anonimi</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Attivazione del pubblico con dati online/offline</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Attivazione con Experience Platform e applicazioni</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>Nessuna integrazione corrente</td>
      <td>
        <ul>
          <li>I dati raccolti da Analytics possono essere inviati ad Experience Platform data lake e all'archivio dei profili. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Connettore dati Analytics</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Experience Platform Flussi di dati</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>I tipi di pubblico definiti in Real-time Customer Data Platform possono essere condivisi con Audience Manager per l'attivazione a destinazioni di cookie di terze parti.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>I dati raccolti e valutati per l’appartenenza al pubblico possono essere condivisi con Experience Platform data lake e l’archivio dei profili. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Connettore origini di Audience Manager</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Attivazione del pubblico con dati anonimi</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Attivazione del pubblico con dati online/offline</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Attivazione con Experience Platform e applicazioni</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>I tipi di pubblico definiti in Real-time Customer Data Platform possono essere condivisi con Campaign Classic come pubblico per avviare campagne.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>I dati di interazione e campagna raccolti da Campaign possono essere acquisiti in Experience Platform come origine di dati per un ulteriore utilizzo nella creazione di audience tramite Real-time Customer Data Platform e analisi tramite Customer Journey Analytics e Experience Platform Query Service e Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">Messaggistica in batch</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>I tipi di pubblico definiti in Real-time Customer Data Platform possono essere condivisi con Campaign Standard come pubblico per avviare campagne.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>I dati di interazione e campagna raccolti da Campaign possono essere acquisiti in Experience Platform come origine di dati per un ulteriore utilizzo nella creazione di audience tramite Real-time Customer Data Platform e analisi tramite Customer Journey Analytics e Experience Platform Query Service e Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">Messaggistica in batch</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>I dati raccolti e acquisiti in Experience Platform data lake sono disponibili per l’elaborazione in Customer Journey Analytics. </li>
        </ul>
      </td>
      <td colspan="1">Nessuna integrazione corrente disponibile. La possibilità di condividere i risultati del pubblico in Experience Platform dal Customer Journey Analytics è nella roadmap di .</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Il profilo di Experience Platform è accessibile direttamente dal lato server per sviluppare esperienze personalizzate fornite tramite Experience Manager. Le attività di personalizzazione vengono generalmente consegnate tramite Experience Manager tramite l’integrazione di Target. </li>
        </ul>
      </td>
      <td colspan="1">L’integrazione, i comportamenti e le interazioni correnti eseguiti sui siti di Experience Manager non vengono raccolti direttamente tramite l’SDK per web e dispositivi mobili di Experience Platform.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Attivazione del pubblico con dati online/offline</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>Gli eventi di dati e i profili acquisiti in Experience Platform sono resi disponibili a Journey Optimizer per avviare e alimentare percorsi in Journey Optimizer.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>I dati di interazione e campagna prodotti da Journey Optimizer vengono raccolti in Experience Platform per un ulteriore utilizzo nella creazione di tipi di pubblico tramite Real-time Customer Data Platform e analisi tramite Customer Journey Analytics, Experience Platform Query Service e Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/triggered-messaging.html?lang=en">Messaggi attivati</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">Nessuna integrazione corrente</td>
      <td colspan="1">Nessuna integrazione corrente</td>
      <td colspan="1">Nessuna integrazione corrente</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>I tipi di pubblico definiti in Real-time Customer Data Platform possono essere condivisi con Marketo come audience per avviare campagne Marketo e aggiornare oggetti Marketo.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Gli account Marketo, i contatti e i dati sulle opportunità, insieme ai dati di interazione e campagna prodotti da Marketo, vengono acquisiti in Experience Platform per un ulteriore utilizzo nella creazione di audience tramite B2B-CDP e analisi tramite Customer Journey Analytics, Experience Platform Query Service e Data Science Workspace. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Connettore Marketo Engage</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Attivazione B2B - in fase di sviluppo</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Real-time CDP</td>
      <td colspan="1">
        <ul>
          <li>I dati acquisiti e raccolti in Experience Platform sono l’origine dati per l’assemblaggio dei profili cliente in tempo reale che alimentano la piattaforma dati cliente in tempo reale.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Le metriche Pubblico e Profilo vengono inviate al data lake di Experience Platform per abilitare le dashboard di reportistica di approfondimenti profilo.</li>
          <li>I dati Pubblico e Profilo nel lago dati possono essere utilizzati per ulteriori informazioni tramite Query Service, Data Science Workspace e Customer Journey Analytics.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Attivazione del pubblico con dati online/offline</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Attivazione con Experience Platform e applicazioni</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Target</td>
      <td colspan="1">
        <ul>
          <li>I tipi di pubblico definiti in Real-time Customer Data Platform possono essere condivisi con Target e utilizzati nelle esperienze di personalizzazione e targeting fornite da Target. </li>
          <li>L’integrazione diretta di Experience Edge con Target per l’appartenenza ai segmenti in tempo reale e l’accesso agli attributi del profilo è indicata nella roadmap.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>I dati raccolti per le esperienze e le interazioni Target possono essere raccolti ad Experience Platform tramite l’SDK per web di Experience Platform. Questi dati possono essere utilizzati nella creazione di un pubblico tramite Real-time Customer Data Platform e per l’analisi tramite il Customer Journey Analytics,  Experience Platform Query Service e Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Attivazione del pubblico con dati online/offline</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Attivazione con Experience Platform e applicazioni</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
