---
title: Creare
description: Crea un pubblico di visitatori della pagina di prodotto di iPhone 14 e combinalo con altri tipi di pubblico utilizzando audience per abilitare l’attivazione dello streaming.
doc-type: article
solution: Experience Platform
exl-id: 999f9a20-1655-4eab-a796-a19d69a06879
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%

---


# Creare #3 di pubblico

## Obiettivo del laboratorio

Creare un pubblico che ha visitato una pagina di prodotto di iPhone 14



## Attività di analisi

Questo pubblico dovrebbe essere diretto.  Potremmo avere più pagine di prodotto, ma non c’è nulla di complicato qui.



## Creare un pubblico (visitato in qualsiasi pagina)

1. Trova l’evento Visualizzazione pagina nella scheda Evento in Tipi di evento nella barra a sinistra e aggiungi al pubblico

   ![Trova l&#39;evento Visualizzazione pagina in Tipi di evento nella barra a sinistra](assets/build-audience-3-find-page-view-event.png)

   >[!NOTE]
   >
   >**Utilizzo dei tipi di evento**
   >
   >Utilizzando l’evento Visualizzazione pagina, ci assicuriamo che il pubblico valuti solo il nome della pagina nel contesto di una visualizzazione pagina. Dovrebbe essere ridondante in quanto un Nome pagina esiste solo in una Visualizzazione pagina, ma offre due vantaggi:
   >
   >- Fornisce all’utente una documentazione visiva di alto livello quando cerca nell’interfaccia utente
   >- Fornisce un filtro per garantire che, quando vengono aggiunti nuovi eventi, questi non vengano inclusi quando questa non era l’intenzione
   >
   >Per questo motivo, consigliamo di tenere presente che ogni schema evento generato dovrebbe tenere conto dei tipi di evento utilizzati. Sono fondamentali per filtrare e visualizzare le guide.



2. Fornisci una descrizione e impostala in streaming.

3. Sopra l’evento inserito, cambia &quot;Qualsiasi momento&quot; in &quot;Oggi&quot;

   ![Modifica il filtro dell&#39;ora evento da Qualsiasi ora a Oggi](assets/build-audience-1-change-any-time-to-today.png)

4. Salva questo pubblico come &quot;*Visitato qualsiasi pagina*&quot;

5. Fai clic sul pulsante blu **Attiva pubblico** nella destinazione

6. Selezionare la destinazione del webhook **Protezione esecuzione programmi in streaming** e fare clic su Avanti

7. Fare clic su Avanti e su Fine

## Creare un pubblico (ha visitato la pagina di iPhone 14 ma non ne è proprietario/l’ha ordinato)

1. Creare un nuovo pubblico e aggiungere l’evento Visualizzazioni pagina

   ![Crea un nuovo pubblico e aggiungi l&#39;evento Visualizzazioni pagina](assets/build-audience-3-create-a-new-audience-and-add-the-page-views-event.png)



2. Passa alla posizione in cui si trova Nome pagina e aggiungi il campo Nome pagina all’Evento, in modo da poterlo filtrare.

   - XDM ExperienceEvent —> Web —> Dettagli pagina Web —> Nome

   ![Passa a XDM ExperienceEvent > Web > Dettagli pagina Web > Nome](assets/build-audience-3-navigate-to-page-name-field.png)



3. Aggiungi contiene &quot;iPhone 14&quot;

   ![Aggiungi una condizione contains per &quot;iPhone 14&quot;](assets/build-audience-3-add-contains-iphone-14.png)

   >[!TIP]
   >
   >**Ricerca di &quot;Page&quot;** in corso
   >
   >Invece di passare al campo, prova a cercare &quot;Pagina&quot;
   >
   >Vedi che Nome pagina non viene visualizzato. Il nome è dovuto al modo in cui è stato denominato:
   >
   >- XDM ExperienceEvent > Web > Dettagli pagina web > Nome
   >
   >Quindi verrà visualizzata la cartella, ma non il campo stesso. Quando metti insieme le convenzioni di denominazione, considera questo e altri termini comuni su cui le persone potrebbero cercare e incorporarli nel nome.
   >
   >La ricerca non cerca le descrizioni
   >
   >![La ricerca di &quot;Pagina&quot; non fa emergere il campo Nome pagina](assets/build-audience-3-searching-for-page-does-not-find-field.png)



4. Sopra l’evento inserito, cambia &quot;Qualsiasi momento&quot; in &quot;Oggi&quot;

   ![Modifica il filtro dell&#39;ora evento da Qualsiasi ora a Oggi](assets/build-audience-1-change-any-time-to-today.png)

   >[!NOTE]
   >
   >Poiché l’attivazione si basa sugli eventi che si sono verificati oggi, per oggi ci concentriamo solo sulle visualizzazioni di pagina.



5. Verifica che sia in streaming e fornisci una descrizione.

6. Salva pubblico come &quot;*Pagina visitata di iPhone 14*&quot;

   ![Salva il pubblico come &quot;Pagina visitata di iPhone 14&quot;](assets/build-audience-3-save-audience-as-visited-iphone-14-page.png)



7. Fai clic sul pulsante blu **Attiva pubblico** nella destinazione

8. Selezionare la destinazione del webhook **Protezione esecuzione programmi in streaming** e fare clic su Avanti

9. Fare clic su Avanti e su Fine



## Creare un pubblico di tipi di pubblico

1. Passa alla scheda Tipi di pubblico nella barra di navigazione in alto a sinistra
1. Eseguire un drill-down ad Experience Platform
1. Richiama gli altri tre tipi di pubblico creati in precedenza
1. Modifica l’opzione Includi in Non include per iPhone 14 di proprietà e iPhone 14 di ordine inoltrato.

   ![Imposta come Proprietario di iPhone 14 e come Ordine inoltrato iPhone 14 su Non include nel pubblico di tipi di pubblico](assets/build-audience-3-audience-of-audiences-does-not-include.png)



&#x200B;5. Fornisci una descrizione.

&#x200B;6. Cambia in streaming

&#x200B;7. Salva come &quot;*ha visitato la pagina iPhone 14 ma non ne è proprietario né l&#39;ha ordinata*&quot;

&#x200B;8. Fai clic sul pulsante blu **Attiva pubblico** nella destinazione

&#x200B;9. Selezionare la destinazione del webhook **Protezione esecuzione programmi in streaming** e fare clic su Avanti

&#x200B;10. Fare clic su Avanti e su Fine

>[!NOTE]
>
>**Filtro Ora**
>
>I requisiti non avevano requisiti temporali, quindi se qualcuno visitasse tre anni fa, si qualificherebbe. A seconda del nostro caso d’uso che potrebbe funzionare o meno. Vale la pena chiedere. Ne abbiamo aggiunto uno perché attiviamo in base alle persone che hanno visitato il nostro sito oggi stesso.  Questo potrebbe non funzionare in tutti i casi d’uso.  Se aggiungiamo un filtro temporale, quanto indietro possiamo andare prima che un pubblico di Edge diventi in streaming o anche in batch?

>[!NOTE]
>
>**Ramificazioni di interruzione**
>
>Abbiamo suddiviso quello che è un requisito semplice in molti tipi di pubblico per alcuni motivi. Il requisito è lo streaming, ma questi due requisiti trasformano il nostro pubblico in batch. Ulteriori dettagli qui sulle regole di idoneità per lo streaming qui:
>
>[https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/streaming-segmentation.html](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/streaming-segmentation.html)

>[!NOTE]
>
>**Tipi di pubblico in streaming**
>
>Il nostro blog *Peeking Underunder the Hood of Audience* (link qui sotto), ne parla un po&#39; qui sotto. Mostra come viene memorizzato nel profilo il risultato di un pubblico. Questo è importante perché, quando i dati vengono trasmessi al suo interno e si osservano i risultati di un pubblico memorizzato nel profilo, il pubblico non viene rieseguito in quel momento. Una sfumatura semplice ma che vale la pena comprendere. La maggior parte degli attributi del profilo viene aggiornata periodicamente, quindi questo approccio ha senso.
>
>Dobbiamo comprendere che quando utilizziamo un pubblico all’interno di un pubblico, AEP tenterà di sequenziarlo quando possibile. In alcuni casi questo non è possibile, ad es. Se utilizzi un pubblico di tipi di pubblico, l’interdizione dal profilo avviene ogni 24 ore.
>
>[https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/peeking-underneath-the-hood-of-segments-in-aep-adobe-experience/ba-p/453535](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/peeking-underneath-the-hood-of-segments-in-aep-adobe-experience/ba-p/453535)



## Perché creare più tipi di pubblico?

Se dovessimo creare tutti questi tipi di pubblico in un pubblico invece di quattro, otterremmo un metodo di valutazione batch anche se ogni pubblico singolarmente è in streaming.

![Creazione di un pubblico combinato in una valutazione in batch anziché in streaming](assets/build-audience-3-why-are-we-creating-multiple-audiences.png)



Suddividendo questi tipi di pubblico e utilizzando un pubblico di tipi di pubblico, otteniamo questo comportamento.  Qualificazione in tempo reale di questi tipi di pubblico come flussi di dati in

- IPhone ordinato 14
- È proprietario di iPhone 14
- Pagina visitata di iPhone 14

>[!WARNING]
>
>Oggi c&#39;è una squalifica di pubblico con latenza giornaliera/24 ore



In fondo: abbiamo barattato l&#39;ingresso più rapido nel pubblico suddividendolo in pezzi con una latenza di 24 ore di loro che ricadono fuori dal pubblico.

>[!TIP]
>
>**Laboratorio di verifica facoltativo**
>
>Finito presto?
>
>Voglio indirizzare un&#39;email alle persone che hanno un vecchio telefono.  Crea un pubblico di &quot;Ha un telefono vecchio&quot;.  Come potremmo mirarle?
