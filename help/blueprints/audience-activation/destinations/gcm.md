---
title: Attivazione a Customer Match di Google
description: Attivazione a FGoogle Customer Match.
solution: Experience Platform, Real-time Customer Data Platform, Data Collection
kt: 7086
source-git-commit: 0a0181a5fd84a645344fadefd47838237807c97c
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 3%

---


# Attivazione a FGoogle Customer Match

Acquisisci i dati dei clienti da più sorgenti per creare una singola visualizzazione del profilo del cliente, segmenta questi profili a tipi di pubblico generati per il marketing e la personalizzazione, condividi questi tipi di pubblico in Social Ad Networks, come Google Customer Match (Corrispondenza cliente), per eseguire il targeting e la personalizzazione delle campagne rispetto a tali tipi di pubblico. Customer Match di Google consente di utilizzare i dati online e offline per raggiungere e coinvolgere nuovamente i clienti sulle proprietà possedute e gestite di Google, ad esempio: Ricerca, acquisti, Gmail e YouTube.

## Casi di utilizzo

* Targeting per tipi di pubblico noti su destinazioni social e pubblicitarie.
* Personalizzazione online con attributi online e offline.

## Applicazioni

* Real-time Customer Data Platform

## Architettura

<img src="../assets/gcm.png" alt="Architettura di riferimento per l’attivazione di Customer Match di Google" style="width:80%; border:1px solid #4a4a4a" />

## Fasi di implementazione

1. Configura i namespace Identity da utilizzare nelle origini dati Profilo.
   * Utilizza i namespace predefiniti come E-mail, hash SHA256 e-mail, se disponibile.
   * Google Customer Match contiene un elenco di identità supportate. Per attivare Google Customer Match, una delle identità supportate deve essere presente nei profili da attivare.
   * Le seguenti identità sono attualmente supportate da Google Customer Match: GAID, IDFA, phone_sha256_e.164, email_lc_sha256, user_id.
   * Per ulteriori dettagli consulta la sezione [Guida alla destinazione di Google Customer Match](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/google-customer-match.html).
   * Crea spazi dei nomi personalizzati in cui gli spazi dei nomi predefiniti non sono disponibili per le identità applicabili.
1. Configura gli schemi e i set di dati dell’origine dati del profilo.
   * Crea schemi di record del profilo per tutti i dati di origine dei record del profilo.
      * Specifica l&#39;identità principale e le identità secondarie per ogni schema.
      * Abilita lo schema per l’acquisizione del profilo.
   * Crea set di dati di record di profilo per tutti i dati di origine dei record di profilo, assegnando lo schema associato.
      * Abilita il set di dati per l’acquisizione del profilo.
   * Crea schemi evento esperienza profilo per tutti i dati sorgente basati su serie temporali del profilo.
      * Specifica l&#39;identità principale e le identità secondarie per lo schema.
   * Abilita lo schema per l’acquisizione del profilo.
   * Crea set di dati evento esperienza profilo per tutti i dati origine evento esperienza profilo, assegnando lo schema associato.
      * Abilita il set di dati per l’acquisizione del profilo.
1. Acquisisci i dati di origine utilizzando un connettore di origine nel set di dati associato configurato in precedenza.
   * Configura l’account del connettore di origine con le credenziali.
   * Configura un flusso di dati per acquisire i dati dal file di origine o dalla posizione della cartella in una pianificazione specifica al set di dati specificato.
   * Mappare tutti i campi dai dati di origine allo schema di destinazione.
   * Trasforma tutti i campi nel formato corretto per l’acquisizione in Experience Platform.
      * Trasformazioni delle date
      * Se appropriato, effettua la trasformazione in minuscolo, ad esempio l’indirizzo e-mail
      * Trasformazioni pattern (ad esempio numero telefonico)
      * Aggiungi ID di record univoci per i record degli eventi di esperienza se non presenti nei dati di origine.
      * Trasforma array e mappa campi di tipo per garantire la corretta mappatura e modellazione di array e mappe per la segmentazione in Experience Platform.
1. Configura i criteri di unione profili per garantire la corretta configurazione del grafico delle identità e quali set di dati devono essere inclusi nell’unione dei profili.
1. Dopo l’esecuzione dei flussi di dati, assicurati che l’inserimento dei dati del profilo sia andato a buon fine senza errori.
   * Inspect è il grafico delle identità di diversi profili per garantire la corretta elaborazione delle relazioni di identità.
   * Inspect gli attributi e gli eventi di diversi profili per garantire la corretta acquisizione di attributi ed eventi ai profili.
1. Creare segmenti per creare tipi di pubblico di profilo
   * Crea segmenti nel generatore di segmenti utilizzando regole per attributi ed eventi.
   * Salva il segmento per la valutazione. I segmenti vengono valutati in base alla pianificazione specificata una volta al giorno.
      * Se le regole del segmento sono idonee per la segmentazione in streaming, il segmento verrà valutato come nuovi dati di streaming vengono acquisiti per i profili. I segmenti in streaming verranno valutati anche una volta al giorno durante la segmentazione batch pianificata.
1. Assicurati che i risultati del segmento siano come previsto.
   * Esamina il conteggio dei risultati del segmento per i segmenti specificati.
   * Investiga il profilo che deve essere incluso nel segmento per verificare che l’appartenenza al segmento sia inclusa nella parte di appartenenza al segmento del profilo.
1. Configura la distribuzione del pubblico alla destinazione nella configurazione di Destinazione.
   * Consulta la sezione [Guida alla destinazione di Google Customer Match](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/google-customer-match.html) per ulteriori dettagli sulla configurazione della destinazione Facebook.
   * Durante la configurazione di una destinazione, seleziona il pubblico da attivare nella destinazione.
   * Determina la data di inizio pianificata per cui desideri che il flusso di dati di destinazione inizi a consegnare il pubblico alla destinazione.
   * Ogni destinazione dispone degli attributi obbligatori e facoltativi che verranno inviati.
      * Per Google Customer Match una delle identità richieste deve essere inclusa e viene utilizzata per far corrispondere i profili nei tipi di pubblico all’interno di Experience Platform a un profilo che può essere targetizzato da Google Customer Match.
   * Ogni destinazione dispone anche di un tipo di consegna specificato, in streaming o batch, in base a file o a payload JSON.
      * Per Customer Match di Google, le iscrizioni al pubblico vengono distribuite in streaming a un endpoint Customer Match di Google in formato JSON.
      * Le iscrizioni al pubblico verranno consegnate in modo in streaming dopo la valutazione dello streaming o della segmentazione in batch, ad Experience Platform.
1. Assicurati che il flusso di destinazione abbia consegnato il pubblico alla destinazione come previsto.
   * Controlla l’interfaccia di monitoraggio per confermare che il pubblico è stato consegnato con il numero di profili previsti. La dimensione del pubblico deve riflettere il numero previsto di profili attivati, osservando che una destinazione specifica come Google Customer Match richiederà alcuni campi, come un’identità hash e-mail, e se non presente nel profilo membro del pubblico, non verrà attivata nella destinazione.
   * Controlla eventuali profili ignorati per le identità di profilo mancanti o gli attributi mancanti che erano obbligatori.
   * Controlla eventuali altri errori che potrebbero essere da risolvere.
1. Verifica che il pubblico sia stato attivato nella destinazione finale con il numero previsto di appartenenze al pubblico.
   * Dopo aver completato il flusso di attivazione, passa al tuo account Google Ads. I segmenti attivati vengono visualizzati nel tuo account Google come elenchi di clienti. Tieni presente che a seconda della dimensione del segmento, alcuni tipi di pubblico non vengono compilati a meno che non vi siano più di 100 utenti attivi da servire.

## Guardrail

[Guardrail di profilo e segmentazione](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=it)

## Documentazione correlata

Attivazione a Customer Match di Google - [Configurazione della destinazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/google-customer-match.html)