---
title: Creare un pubblico Edge
description: Crea e pubblica un pubblico valutato da Edge insieme a un equivalente batch per confrontare il modo in cui ciascuno di essi risponde agli eventi in arrivo in tempo reale.
doc-type: article
solution: Experience Platform
exl-id: 79265a8f-81dd-41a3-89c5-c6646e435328
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Creare un pubblico Edge

Questo pubblico verrà utilizzato per qualificare un utente quando un payload (ad esempio, visualizzazione pagina) proviene dal client (ad esempio, Web SDK) per Edge.

>[!NOTE]
>
>Valutiamo un pubblico su Edge di solito in modo da poterlo utilizzare in Personalization. Se non utilizziamo Personalization su Edge, possiamo semplicemente far sì che il pubblico valuti come Streaming sull’hub.

## Creare un pubblico

1. Nella barra a sinistra, fai clic su Audiences.
1. Quindi fai clic su Crea pubblico nell’angolo superiore destro dello schermo
1. Quindi fai clic su Genera regola



![Pagina Tipi di pubblico con pulsante Crea pubblico e opzione Genera regola evidenziati](assets/create-edge-audience-create-audience-step-1.png)



![Area di lavoro della regola di compilazione aperta per creare un nuovo pubblico](assets/create-edge-audience-create-audience-step-2.png)



## Convertire il pubblico in regole

1. Vai a **Tipi di pubblico** e fai clic nella cartella **Experience Platform**
1. Trascina &#39;n rilasciare il pubblico denominato **dep: qualsiasi streaming di eventi (entro un&#39;ora)** nell&#39;area di lavoro

   ![Trascinamento del pubblico Dep: Qualsiasi evento in streaming (entro un&#39;ora) nell&#39;area di lavoro del generatore di regole](assets/create-edge-audience-drag-audience-to-canvas.png)



1. Converti il pubblico in un set di regole nell&#39;area di lavoro facendo clic sull&#39;**icona** mostrata di seguito e quindi su **Converti**

![Icona Converti nell&#39;area di lavoro utilizzata per convertire il pubblico in un set di regole](assets/create-edge-audience-convert-to-rules-icon.png)

## Aggiorna regole evento

Apporta le seguenti modifiche alle regole dell’evento (potrebbe essere necessario espandere l’evento per visualizzarlo)

1. In Ultimo
1. 15
1. Minutes

![Regola eventi configurata per l&#39;attivazione negli ultimi 15 minuti](assets/create-edge-audience-update-event-rules.png)

## Pubblica segmento

1. Aggiorna il nome del segmento in **Qualsiasi Edge evento (entro 15 minuti)**
1. Aggiornare il metodo di valutazione ad Edge
1. Pubblicare il segmento

![Dettagli del segmento che mostrano il metodo di valutazione Edge prima della pubblicazione](assets/create-edge-audience-publish-segment.png)

## Crea segmento valutato in batch

Ripetete le stesse operazioni eseguite per il segmento di spigolo creato, ma utilizzate le seguenti informazioni:

>[!NOTE]
>
>Creeremo un pubblico batch in modo da poter vedere che, anche se un evento viene passato in Edge, tutti i tipi di pubblico salvati come valutazione batch non vengono valutati in streaming.

Regole evento:

- In Ultimo
- 1
- Giorno



Dettagli segmento:

- Nome -> **Qualsiasi batch di eventi (entro 1 giorno)**
- Metodo di valutazione -> Batch
