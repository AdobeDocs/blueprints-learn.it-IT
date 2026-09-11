---
title: Effettuare il forking del risultato
description: Scopri come aggiungere un’attività Fork a una campagna orchestrata per diramare un risultato per salvare un pubblico e inviare messaggi SMS.
doc-type: article
solution: Experience Platform
exl-id: 8f1d0839-e4ca-4b7c-bc97-4e271a457296
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Effettuare il forking del risultato

## Obiettivo

Questo passaggio è semplice in quanto tutto ciò che desideri è aggiungere un’attività Fork in modo da poter duplicare il risultato per fare due cose diverse con esso nei passaggi futuri:

1. Salvare il pubblico affinché altri possano utilizzarlo a scopo pubblicitario o cross-channel
1. Invia messaggi SMS alle singole righe.



## Creare il fork

1. Nell&#39;area di lavoro del flusso di lavoro, fai clic sull&#39;icona **+** **&#x200B;**&#x200B;dopo l&#39;attività Genera pubblico e seleziona l&#39;**Attività Fork**

   ![Aggiungi un&#39;attività Fork dopo l&#39;attività Genera pubblico](assets/fork-the-result-add-fork-activity.png)



2. Aggiorna i nomi di ciascuna transizione nel fork facendo clic sulla transizione e assegnando i nomi come descritto di seguito:
   - **Primi** —> `Save Audience`
   - **Inferiore** —> `SMS`

   ![Transizioni Fork rinominate in Salva pubblico e SMS](assets/fork-the-result-rename-transitions.png)



   Una volta terminata, l&#39;area di lavoro dovrebbe ora essere simile a così...

   ![Area di lavoro del flusso di lavoro dopo l&#39;aggiunta dell&#39;attività fork](assets/fork-the-result-final-canvas.png)

   >[!NOTE]
   >
   >Un’attività fork consiste essenzialmente nel duplicare il risultato dell’attività precedente in due rami indipendenti



3. Fai clic su **Salva** nella parte superiore dell&#39;area di lavoro del flusso di lavoro.

![Pulsante Salva sulla barra degli strumenti dell&#39;area di lavoro del flusso di lavoro](assets/fork-the-result-click-save.png)

>[!TIP]
>
>È stato piuttosto difficile, vero 😁



## Riassunto

Benvenuto, hai creato una Fork del risultato (ovvero duplicare il risultato) che ti consente di dettare chiaramente un ramo per elaborare un pubblico di tipo Save, mentre l’altro può essere utilizzato per l’invio di SMS.

>[!NOTE]
>
>Devi utilizzare le Fork, soprattutto se prevedi di salvare il pubblico come un’attività Save Audience che non consente alle attività di seguirlo.
