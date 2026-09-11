---
title: Pre-lavoro
description: Esamina i campi dello schema per l’utilizzo della fatturazione e il nome del piano, evidenziando come le descrizioni mancanti e i campi duplicati possano confondere i generatori di pubblico.
doc-type: article
solution: Experience Platform
exl-id: c26de19e-82da-4070-a918-2d2c8ef2c116
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Pre-lavoro

Per questo caso d’uso non c’è molto lavoro preliminare da fare. Fondamentalmente abbiamo due cose che stiamo cercando, 1) Utilizzo, 2) Piano.  Trova dove sono.

## Utilizzo dati fatturazione

1. Crea un nuovo pubblico
1. Cerca &quot;utilizzo&quot; in Attributi. Fai clic sulla &quot;i&quot; per rivedere la descrizione (non ce n’è nessuna).

   ![Cerca utilizzo in Attributi - nessuna descrizione visualizzata](assets/pre-work-search-usage-in-attributes.png)



&#x200B;3. Cerca &quot;utilizzo&quot; negli Eventi.  Fai clic sulla &quot;i&quot; per rivedere la descrizione (non ce n’è nessuna).

![Cerca informazioni sull&#39;utilizzo negli eventi - nessuna descrizione visualizzata](assets/pre-work-search-usage-in-events.png)

>[!NOTE]
>
>Nessuno di questi elementi contiene descrizioni, pertanto l’addetto al marketing potrebbe fare alcune supposizioni e formulare ipotesi errate.
>
>Le descrizioni sono importanti.  Senza descrizioni, come farà l’addetto marketing a sapere:
>
>- Quale usare?
>- Latenza dei dati?
>- Consigliato/preferito in casi d’uso specifici?
>
>Fornendo queste informazioni nelle descrizioni, possiamo guidarli meglio.

>[!NOTE]
>
>Prova a cercare &quot;Fatturazione&quot;.  Nota che non viene visualizzato come attributo di profilo.  Viene visualizzato come scheda del tipo di evento insieme al campo &quot;Utilizzo dati fatturazione&quot;.
>
>Sono presenti convenzioni di denominazione anche per l’addetto marketing.  A seconda di cosa cercano o se stanno cercando/si aspettano che sia un evento o un profilo, influisce su ciò che trovano e alla fine utilizzano.

## Piano

Cerca &quot;Piano&quot; in Attributi.  Notate che abbiamo diverse cose tra cui scegliere.  Limitarla a &quot;Nome piano&quot;.  Abbiamo due nomi di piano?!



![Attributo Nome primo piano trovato durante la ricerca nel piano](assets/pre-work-duplicate-plan-name-field.png)



![Attributo Nome secondo piano trovato durante la ricerca nel piano](assets/pre-work-duplicate-plan-name-field--2.png)

Il nome del piano (nome del piano) sembra essere quello necessario in base alla descrizione e l’altro non dispone di una descrizione.
