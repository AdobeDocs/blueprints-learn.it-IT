---
title: null
description: Crea un pubblico batch che utilizza variabili contenitore per far corrispondere eventi inseriti nell’ordine e annullati dall’ordine per lo stesso ordine entro una settimana.
doc-type: article
solution: Experience Platform
exl-id: 4b72b76f-de64-4712-85a6-ec7890b23b97
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# #3 del caso di utilizzo della build

## Creare il pubblico

1. Crea un nuovo pubblico
1. Aggiungere l’evento Ordine inserito all’area di lavoro
1. Aggiungere l&#39;evento di annullamento ordine a destra dell&#39;evento di inserimento ordine
1. Modifica l’ora in entro una settimana

>[!NOTE]
>
>**Campo Tipo Evento**
>
>Avremmo potuto utilizzare:
>
>- Qualsiasi evento filtrato per Tipo evento=order.placed
>- Qualsiasi evento filtrato per Tipo evento=order.canceled

![Modifica la finestra temporale dell&#39;evento in entro una settimana](assets/build-use-case-3-change-time-to-within-a-week.png)



![Eventi di ordine inoltrato e di ordine annullato configurati per verificarsi entro una settimana](assets/build-use-case-3-change-time-to-within-a-week--2.png)

>[!NOTE]
>
>**Ora**
>
>Il motore del pubblico utilizza solo la marca temporale per interpretare l’ordine degli eventi. Pertanto, se sull’evento sono presenti più campi datetime, tieni presente che quello utilizzato è il campo Timestamp.



## Configurare l’evento annullato

Cercare l&#39;ID ordine e trascinare il campo sull&#39;evento di annullamento ordine.

![Cerca ID ordine e trascina il campo sull&#39;evento Ordine annullato](assets/build-use-case-3-search-order-id-drag-onto-order-cancelled-event.png)

>[!NOTE]
>
>Stiamo aggiungendo un filtro per l’ID ordine per garantire che l’ordine inoltrato corrisponda a quello annullato



Cancella qualsiasi ricerca e fai clic su **Posizionato** sotto le **Variabili di navigazione**

![Fai clic su in Posizionato sotto Sfoglia variabili](assets/build-use-case-3-click-into-placed-under-browse-variables.png)



Espandere fino a ID ordine, quindi trascinare per aggiungere un operando di confronto

![Espandere fino all&#39;ID ordine e trascinare per aggiungere un operando di confronto](assets/build-use-case-3-drill-down-to-order-id-add-compare-operand.png)

>[!WARNING]
>
>**Non utilizzare la ricerca in una variabile**
>
>Non manterrà il contesto della variabile



Il risultato finale dovrebbe essere quello riportato di seguito

![Configurazione finale del pubblico con operando di confronto ID ordine aggiunto](assets/build-use-case-3-final-audience-configuration-result.png)

>[!NOTE]
>
>**Contenitori**
>
>In questo modo viene utilizzato il contenitore delle variabili per garantire che l’ordine annullato corrisponda a quello inserito
>
>In precedenza abbiamo utilizzato un contenitore per isolare un elemento in un array. In questo caso utilizziamo Contenitori per fare riferimento a un evento specifico in un criterio di filtro all’interno di un altro evento.
>
>L&#39;evento di annullamento dell&#39;ordine verifica che il proprio ID ordine sia uguale all&#39;ID ordine inserito
>
>In quale altro modo potremmo usarlo?
>
>- Confrontare uno SKU di prodotto per una visualizzazione di pagina è lo SKU di prodotto acquistato
>- Il confronto tra Spedisci a città è diverso da quello tra Città
>- Il confronto di due campi dello stesso tipo di dati dovrebbe essere possibile anche se gli eventi possono provenire da schemi diversi
>
>https\://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/how-exact-do-containers-work-in-aep-segmentation-a-deeper-look/ba-p/458780

>[!NOTE]
>
>**Nomi contenitori**
>
>I contenitori ereditano il nome della variabile dal loro contesto.
>
>ad es. Se utilizzi la scheda Qualsiasi evento, il nome del contenitore sarà Qualsiasi1



## Salvare il pubblico

1. Fornisci una descrizione. Impostare il metodo di valutazione come Batch.
1. Salva il pubblico come &quot;*Ordine effettuato e Ordine annullato entro una settimana*&quot;

>[!TIP]
>
>**Laboratorio di verifica facoltativo**
>
>Finito presto? Prova...
>
>Vorremmo avviare una nuova campagna per Abandon Cart.  Crea un pubblico per il carrello di abbandono, ma assicurati che non iniziamo a eseguire il targeting delle persone per un’ora.
>
>
>
>Hai ancora tempo? Prova...
>
>L&#39;attività è stata oggetto di una fusione e ha acquisito due nuove unità operative per:
>
>- ISP
>- Cavo
>
>In che modo potrebbe essere necessario modificare gli schemi per includerli?
