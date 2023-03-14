---
title: Blueprint per l’accesso ai dati e l’esportazione
description: Questo blueprint fornisce una panoramica di tutti i metodi con cui è possibile accedere ai dati ed esportarli da Adobe Experience Platform e dalle relative applicazioni.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Data Collection
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: f22ff4ac15b21592226f6645ab28f30473996776
workflow-type: tm+mt
source-wordcount: '2052'
ht-degree: 76%

---

# Blueprint per l’accesso ai dati e l’esportazione

Il blueprint per l’accesso ai dati e l’esportazione descrive tutti i metodi possibili che consentono di accedere ai dati o esportarli da Adobe Experience Platform e dalle relative applicazioni.

Questo blueprint è suddiviso in due categorie per l’accesso ai dati da Experience Platform e dalle relative applicazioni. La prima categoria presenta gli approcci per ottenere in uscita i dati provenienti da Experience Platform e dalle relative applicazioni; si tratta di un metodo per l’uscita dei dati di tipo push. La seconda categoria presenta gli approcci per l’accesso ai dati provenienti da Experience Platform e dalle relative applicazioni; si tratta di un metodo per l’accesso ai dati di tipo pull.

Approcci per l’accesso ai dati:

* [API di accesso per il profilo cliente in tempo reale](#rtcp-profile-access-api)
* [API di accesso ai dati](#data-access-api)
* [Query Service](#query-service)

Approcci per l’esportazione dei dati:

* [Tag lato client](#client-side-tags-extensions)
* [Inoltro eventi](#event-forwarding)
* [Destinazioni di Real-time Customer Data Platform](#RTCDP-destinations)
* [Azioni personalizzate di Journey Optimizer](#jo-custom-actions)

## Architettura d’insieme per l’accesso ai dati e l’esportazione

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Architettura di riferimento del blueprint per preparazione e acquisizione dei dati" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />

## Accesso ai dati e metodi di esportazione

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1133px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1133px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Destinazioni di streaming</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Metodo</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Casi d’uso comuni</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocoli</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Considerazioni</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it" style="color:#0563c1; text-decoration:underline">Inoltro eventi</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Inoltro di dati non elaborati raccolti dagli SDK Adobe per l’analisi e la raccolta ai sistemi aziendali</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Applicazione di tag leggeri per 3<sup>rd</sup> raccolta dati di parti tramite estensioni</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Eventi non elaborati di basso livello</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Nessun contesto di aggregazione o record precedente aggiunto</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en#:~:text=containing%20profile%20exports.-,Streaming%20segment%20export%20destinations,-Segment%20export%20destinations" style="color:#0563c1; text-decoration:underline">RTCDP - Esportazioni dei segmenti in streaming</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Attiva i tipi di pubblico da RTCDP a sistemi marketing e pubblicitari.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Dati aggregati che rappresentano l’iscrizione al pubblico</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Nessuna attivazione dei dati grezzi dell’evento esperienza</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en#:~:text=file%2Dbased)%20destinations-,Streaming%20profile%20export%20destinations%20(enterprise%20destinations),-IMPORTANT" style="color:#0563c1; text-decoration:underline">RTCDP - Destinazioni esportazione profilo</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Sfrutta i profili comportamentali e di pubblico avanzati di RTCDP per migliorare le esperienze dei consumatori e il marketing.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Attiva i tipi di pubblico e gli attributi del profilo da RTCDP a sistemi di marketing e pubblicità che funzionano su tipi di pubblico e attributi del profilo. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Attiva i profili AEP nei provider di servizi e-mail, nei sistemi di sviluppo dei lead e nei sistemi di gestione delle relazioni con i clienti.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Dati aggregati che rappresentano l’iscrizione al pubblico e gli attributi dei record del profilo</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Nessuna attivazione dei dati grezzi dell’evento esperienza</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=it" style="color:#0563c1; text-decoration:underline">RTCDP - Destinazioni di personalizzazione</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Accedi a Real-time Customer Profile nelle esperienze lato browser e lato client per arricchire la personalizzazione lato client. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Richiede la distribuzione di Web SDK</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-sdk/overview.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - DESTINATION SDK</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Configura una scheda di destinazione personalizzata nelle destinazioni RTCDP.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Supporta le destinazioni per file e tipi di streaming</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Consente ai partner e ai marchi di configurare schede di destinazione personalizzate</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=it" style="color:#0563c1; text-decoration:underline">RTCDP - API dell’hub di ricerca profili</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Accedi al profilo per arricchire le esperienze dei consumatori con l’assistenza dell’agente, ad esempio tramite il supporto o le interazioni con l’agente di vendita.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Ricerca hub ideale solo per casi d’uso &gt; 500 ms+</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">RTCDP - API Edge di ricerca profilo* Beta</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Accedi al profilo Edge per arricchire le esperienze dei consumatori per esperienze in tempo reale &lt;200 ms, ad esempio personalizzazioni o decisioni di offerta su web e dispositivi mobili.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Per esperienze in tempo reale e integrazioni server-to-server</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=it" style="color:#0563c1; text-decoration:underline">Azioni personalizzate di Journey Optimizer</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Attivazione di eventi di percorso 1:1 e trigger per la notifica a un sistema esterno. Abbandoni del carrello, abbandoni dell'applicazione, registrazioni.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Attivazione di un singolo evento per un determinato profilo. Non per aggregazione o operazioni di massa</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>

<p> </p>

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1132px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1132px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Destinazioni batch</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Metodo</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Casi d’uso comuni</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocoli</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Considerazioni</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/data-access/api.html?lang=en" style="color:#0563c1; text-decoration:underline">API di accesso ai dati</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Accesso ai dati non elaborati per la data science e flussi di lavoro ML al di fuori di Experience Platform.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">File Parquet</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Richiede processi di sviluppo per accedere ed elaborare file parquet in set di dati utilizzabili</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=it" style="color:#0563c1; text-decoration:underline">Query Service</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Mantenere i risultati delle query dei set di dati, per informazioni e rapporti aggregati. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">PostgreSQL </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Client SQL</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Solo dati aggregati. Limite di query di 10 minuti.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/export-datasets.html?lang=en" style="color:#0563c1; text-decoration:underline">Esportazione set di dati* Beta</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Esporta dati di eventi di Experience Platform per l’accesso a strumenti esterni di reporting, analisi e data science. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Esportazione di informazioni di profilo aggregate e appartenenza a un pubblico per reporting esterno, analisi e strumenti di data science. </span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">API REST </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Attualmente in versione beta, a partire da un sottoinsieme di tipi di set di dati</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>



## Approcci per l’accesso ai dati

### API di accesso per il profilo cliente in tempo reale {#rtcp-profile-access-api}

I clienti possono accedere a singoli profili unificati dall’archivio di profili cliente in tempo reale (incluse le identità di profilo, le appartenenze al pubblico, gli attributi e gli eventi delle esperienze) mediante l’API di accesso per il profilo cliente in tempo reale.

Per ulteriori informazioni, consulta [API di accesso per il profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=it).

#### Casi di utilizzo

* Ricerca di un singolo profilo per aggiungere contesto all’interazione tra il cliente e l’agente, ad esempio per le interazioni di assistenza tramite chat e call center o le interazioni di vendita presso il punto vendita.
* Ulteriore contesto per le decisioni di personalizzazione effettuate da sistemi esterni, ad esempio da un sistema di personalizzazione web o di decisioni per offerte.

#### Considerazioni

* Soggetto ai [guardrail](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it) per profilo cliente in tempo reale.
* Progettato per la ricerca in singoli profili alla volta. Non utilizzato per l’accesso a profili in blocco né per il download dell’intera popolazione del profilo da utilizzare a scopo di analisi o data science.
* Il tempo di risposta della ricerca nel profilo è conforme ai guardrail per i profili. Requisiti di latenza in tempo reale bassa: ad esempio per la personalizzazione sulla stessa pagina, i requisiti prevedono l’utilizzo del profilo Edge dalla [Connessione Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=it) o la [Connessione per personalizzazione customizzata](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=it) per l’accesso in tempo reale ai profili per la personalizzazione nel browser e nell’app.

### API di accesso ai dati {#data-access-api}

Utilizzando l’API di accesso ai dati, i clienti possono accedere direttamente ai file di set di dati non elaborati memorizzati nel data lake di Experience Platform.

* Per ulteriori informazioni sull’utilizzo dell’API di accesso ai dati, consulta la [documentazione](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=it).

#### Casi di utilizzo

* Estrazione di file di dati grezzi ed elaborati da Experience Platform a scopo di archiviazione e valutazione in ambienti aziendali.

#### Considerazioni

* Poiché l’accesso ai dati avviene in modo asincrono in batch, questo metodo è soggetto a una latenza intrinseca rispetto agli approcci che consentono di ottenere i dati in uscita mediante streaming, come l’utilizzo di tag, inoltro eventi o destinazioni RTCDP.
* I file di dati elaborati in Experience Platform vengono memorizzati come raccolte di file in batch, compressi e memorizzati in formato parquet. Pertanto, quando si accede ai file per scaricarli in un ambiente diverso, l’accesso avviene sistematicamente per batch e file, e non per un intero set di dati; eventuali operazioni sui dati devono quindi tenere conto del fatto che i file sono compressi in formato parquet.

### Query Service {#query-service}

Utilizzando Experience Platform Query Service, i clienti possono eseguire query sui set di dati direttamente in Experience Platform e rendere persistenti i risultati della query. È possibile utilizzare un client SQL per eseguire le query e rendere persistenti le risposte alla query nella destinazione di archiviazione desiderata supportata dal client SQL. È possibile utilizzare l’interfaccia utente di Query Service per memorizzare i risultati SQL in un set di dati target in Experience Platform; in alternativa, i risultati possono essere salvati nel computer locale.

* Per ulteriori dettagli sulla connessione a client SQL in modo da rendere persistenti i risultati SQL da Experience Platform Query Service, consulta questa [documentazione](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=it).

#### Casi di utilizzo

* Esecuzione di query su dati non elaborati dai set di dati di Experience Platform e rendere persistenti i risultati delle query.
* Esecuzione di query sul set di dati dello snapshot del profilo per estrarre informazioni sul profilo cliente in tempo reale. [Documentazione](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=it#profile-attribute-datasets).
* Puoi archiviare le query in un set di dati separato per l’accesso oppure in un set di dati abilitato per il profilo che sarà poi possibile ottenere in uscita tramite RTCDP e altre applicazioni Experience Cloud in grado di accedere al profilo cliente in tempo reale.

#### Considerazioni

* Poiché le query sui dati avvengono in modo asincrono in batch, questo metodo è soggetto a una latenza intrinseca rispetto agli approcci che consentono di ottenere i dati in uscita mediante streaming, come l’utilizzo di tag, inoltro eventi o destinazioni RTCDP.
* Query Service può essere utilizzato per eseguire query solo sui dati disponibili nel data lake di Experience Platform. Query Service non consente di eseguire query direttamente nell’archivio dei profili cliente in tempo reale, nel grafo delle identità e in Customer Journey Analytics. È possibile eseguire query sui set di dati solo dopo che questi siano stati esportati nel data lake, come nell’esempio del set di dati dello snapshot del profilo.
* Tieni presente che sono applicabili i guardrail per il numero di risultati e il timeout delle query, come descritto in [Guardrail per il servizio Query](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=it).

## Approcci per l’esportazione dei dati

### Estensioni tag lato client {#client-side-tags-extensions}

Le estensioni possono essere implementate mediante la soluzione Tag di Adobe. Una volta implementata un’estensione, le richieste di dati vengono distribuite direttamente a un browser client o un’applicazione, dopodiché è possibile invocare una richiesta per inviare dati e richieste alla destinazione desiderata.

Per ulteriori informazioni, consulta [Panoramica sui tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it).

#### Casi di utilizzo

* Raccolta di informazioni non elaborate in streaming direttamente dagli ambienti lato client tramite l’utilizzo di tag.

#### Considerazioni

* Nessun accesso diretto a informazioni lato server, come il Profilo cliente in tempo reale di Experience Platform e le appartenenze al pubblico.
* L’aggiunta di ulteriori tag di raccolta dati alla pagina potrebbe comportare tempi di caricamento più lunghi per la pagina.
* È possibile impostare delle regole per richiedere i dati solo se vengono soddisfatti determinati criteri.
* I dati vengono raccolti direttamente dal client, con limiti sui tipi di trasformazione e arricchimento che possono essere eseguiti prima della raccolta dei dati.

### Inoltro eventi {#event-forwarding}

Le richieste di raccolta dati vengono raccolte direttamente nella rete Edge di Adobe. Dalla rete Edge, le richieste agli endpoint RESTful esterni possono essere configurate affinché vengano inoltrate alla destinazione esterna.

Per ulteriori informazioni, consulta [Inoltro eventi](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=it).

#### Casi di utilizzo

* Raccolta di informazioni non elaborate in streaming direttamente dagli ambienti lato client a un endpoint aziendale mediante l’inoltro degli eventi lato server di Adobe.

#### Considerazioni

* Per utilizzare l’inoltro eventi, i dati devono essere inviati alla rete Edge tramite Web SDK o Mobile SDK.
* L’approccio basato sull’inoltro eventi riduce i tempi di caricamento e il peso delle pagine associati all’aggiunta di ulteriori tag alla pagina.
* Al momento l’arricchimento dal profilo Edge o da altre origini di dati non è supportato.
* Sono supportate alcune possibilità di filtraggio dei dati e semplici trasformazioni di mappatura.

### Destinazioni di Real-time Customer Data Platform {#RTCDP-destinations}

I dati degli attributi del profilo e di appartenenza al pubblico possono essere attivati nelle destinazioni aziendali e pubblicitarie. Pertanto i dati in uscita devono essere acquisiti nel Profilo cliente in tempo reale di Experience Platform.

Per ulteriori informazioni, consulta [Destinazioni di Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=it).

#### Casi di utilizzo

* Attivazione di informazioni sugli attributi del profilo (inclusa l’appartenenza al pubblico) in archivi dati aziendale, strumenti di analisi o sistemi per e-mail o assistenza.
* Attivazione dell’appartenenza al pubblico del profilo presso un fornitore pubblicitario esterno a scopo di targeting e personalizzazione del contenuto per il profilo.

#### Considerazioni

* È possibile attivare gli attributi del profilo e le appartenenze al pubblico. Al momento, gli eventi delle esperienze non elaborati non possono essere attivati come parte delle destinazioni RTCDP.
* Le attivazioni avvengono in streaming o in batch a seconda della natura dell’analisi dei segmenti e del protocollo di acquisizione accettati dalla destinazione.

### Azioni personalizzate di Journey Optimizer {#jo-custom-actions}

Chi utilizza Journey Optimizer può richiamare un’azione personalizzata dall’area di lavoro del percorso per inviare un payload o un messaggio a un endpoint API esterno configurato. Un’azione può essere configurata per qualsiasi servizio proveniente da qualsiasi provider che possa essere chiamato tramite un’API REST con un payload in formato JSON. Tale payload può includere informazioni sull’evento, attributi di profilo e dati evento precedenti, trasformazioni e arricchimenti configurati nel percorso.

Per ulteriori informazioni, consulta [Azioni personalizzate Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=it).

#### Casi di utilizzo

* Eventi di attivazione da Experience Platform e Journey Optimizer che includono informazioni aggiuntive dal profilo cliente in tempo reale.
* Invio di notifiche a sistemi esterni quando un cliente ha raggiunto un punto specifico di un percorso.

#### Considerazioni

* Sono applicabili i guardrail sulle velocità supportate da [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=it) e gli arricchimenti supportati dal [Profilo cliente in tempo reale](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it).
* È possibile eseguire azioni personalizzate in streaming una alla volta, per ogni evento o profilo in un percorso. Non è possibile eseguire operazioni in blocco o ottenere dati in uscita in blocco sotto forma di file o richieste aggregate tra diversi percorsi del cliente.
* Accesso in streaming agli attributi del profilo cliente in tempo reale e agli eventi dell’esperienza che possono essere inclusi nel payload di attivazione.
* È possibile filtrare i dati evento e applicare semplici trasformazioni di mappatura prima di inviare gli eventi alle destinazioni esterne.
