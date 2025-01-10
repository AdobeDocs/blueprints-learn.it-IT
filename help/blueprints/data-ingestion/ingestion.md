---
title: Blueprint per la preparazione e l’acquisizione dei dati
description: Questo blueprint mostra tutti i metodi con cui i dati possono essere acquisiti e preparati in Adobe [!DNL Experience Platform].
solution: Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1
source-git-commit: 1b35f6955a7bb10d07c6ce796e80a18b92f25d18
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 83%

---

# Blueprint per la preparazione e l’acquisizione dei dati

Blueprint per la preparazione e l&#39;acquisizione dei dati include tutti i metodi con cui i dati possono essere preparati e acquisiti in Adobe [!DNL Experience Platform].

La preparazione dei dati include la mappatura dei dati di origine sullo schema Experience Data Model (XDM). Include inoltre l’esecuzione di trasformazioni sui dati, tra cui formattazione della data, suddivisione/concatenazione/conversioni di campi e unione/fusione/riconfigurazione di record. La preparazione dei dati è utile per unificare i dati dei clienti al fine di fornire analisi aggregate/filtrate, inclusa la creazione di rapporti o la preparazione dei dati per assemblaggio/data science/attivazione dei profili cliente.

## Architettura

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Architettura di riferimento del blueprint per preparazione e acquisizione dei dati" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />

## Guardrail per l’acquisizione dei dati

Il diagramma seguente illustra i guardrail delle prestazioni e la latenza media per l&#39;acquisizione dei dati in Adobe [!DNL Experience Platform].

<img src="../experience-platform/deployment/assets/aep_data_flow_guardrails.svg" alt="[!DNL Experience Platform] Flusso di dati" style="border:1px solid #4a4a4a; margin-bottom: 15px;" width="90%" class="modal-image" />

## Metodi di acquisizione dei dati

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1123px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:31px; vertical-align:top; width:1123px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Origini di streaming</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:20px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Metodo</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:20px; vertical-align:top; width:401px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Casi d’uso più comuni</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:20px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocolli</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:20px; vertical-align:top; width:282px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Considerazioni</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=it" style="color:#0563c1; text-decoration:underline">Adobe Web/Mobile SDK</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:401px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Raccolta dati da siti web e app mobili.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Metodo preferito per la raccolta lato client.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, HTTP, JSON</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Implementa più applicazioni Adobe con un unico SDK.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=it" style="color:#0563c1; text-decoration:underline">Connettore API HTTP</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:401px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Raccolta da origini di streaming, transazioni, eventi pertinenti dei clienti e segnali</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, REST API, JSON</span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">I dati vengono trasmessi in streaming direttamente all’hub, senza inoltro eventi o segmentazione Edge in tempo reale.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/data-collection/interactive-data-collection.html?lang=it" style="color:#0563c1; text-decoration:underline">[!DNL Edge Network] API</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:401px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Raccolta da fonti di streaming, transazioni, eventi rilevanti per i clienti e segnali provenienti da tutto il mondo [!DNL Edge Network]</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, REST API, JSON</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Streaming dei dati tramite [!DNL Edge Network]. Supporto della segmentazione in tempo reale nella rete Edge. </span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=it" style="color:#0563c1; text-decoration:underline">Applicazioni Adobe</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:401px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Precedente implementazione di Adobe Analytics, Marketo, Campaign, Target, AAM</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, connettori di origini e API</span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">L’approccio consigliato prevede la migrazione dagli SDK tradizionali delle singole applicazioni a Web/Mobile SDK.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=it" style="color:#0563c1; text-decoration:underline">Connettori per origini in streaming</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:401px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Acquisizione di uno stream di eventi aziendali, solitamente utilizzato per la condivisione di dati aziendali con più applicazioni a valle. </span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, REST API, JSON</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">È necessaria la trasmissione in streaming in formato XDM.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:222px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">SDK per origini di streaming</span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:401px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Simile al connettore API HTTP, consente una scheda di configurazione self-service per un flusso di dati esterno.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:218px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, HTTP API, JSON</span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">[!DNL Edge Network]</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1105px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:37px; vertical-align:top; width:1105px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Origini batch</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:34px; vertical-align:top; width:217px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Metodo</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:34px; vertical-align:top; width:397px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Casi d’uso più comuni</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:34px; vertical-align:top; width:215px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocolli</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:34px; vertical-align:top; width:277px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Considerazioni</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:217px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=it" style="color:#0563c1; text-decoration:underline">API per acquisizione batch</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:397px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Acquisizione da una coda gestita dall’azienda. Pulizia e trasformazione dei dati prima dell’acquisizione.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:215px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, JSON o Parquet</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:277px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Deve gestire batch e file per l’acquisizione</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:217px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob-s3.html?lang=it" style="color:#0563c1; text-decoration:underline">Connettori per origini batch</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:397px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Approccio comune per l’acquisizione di file da archiviazione cloud.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Connettori alle più comuni applicazioni CRM e marketing.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Ideale per l’acquisizione di grandi quantità di dati storici.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:215px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull, CSV, JSON, Parquet</span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:277px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Non sempre attivi, acquisizione immediata. </span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:217px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/data-landing-zone.html?lang=it" style="color:#0563c1; text-decoration:underline">Zona di destinazione dati</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:397px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Percorso di archiviazione file con provisioning Adobe a cui inviare in push i file da acquisire.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:215px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push, CSV, JSON, Parquet</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:277px">
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:217px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/sources/sdk/overview.html?lang=it" style="color:#0563c1; text-decoration:underline">SDK per origini batch</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:397px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Consente una scheda di configurazione self-service per un’origine dati esterna.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Ideale per connettori partner o per un’esperienza di flusso di lavoro personalizzata per l’impostazione di un connettore aziendale.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:215px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull, REST API, CSV o JSON</span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:62px; vertical-align:top; width:277px">
<ul>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Esempi: MailChimp, One Trust, Zendesk</span></span></span></li>
</ul>

<p> </p>
</td>
</tr>
</tbody>
</table>