---
hold: true
title: Correzione degli errori MAPPER per CreateDate
description: Risolvere i problemi e risolvere un errore MAPPER causato da un valore createDate formattato in modo errato che si stava trasformando in un campo vuoto.
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Correzione degli errori MAPPER per CreateDate

In questo esercizio, dovrai capire come rimuovere l’errore MAPPER visualizzato nel laboratorio di acquisizione batch. È necessario correggere l’errore perché anche se createDate non è un campo obbligatorio, i record vengono comunque acquisiti perché la data con formato non valido viene trasformata in un campo vuoto.

![createDate con un formato non valido che causa l&#39;errore MAPPER](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
