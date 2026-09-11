---
title: Convalida profilo su Edge
description: Scopri come controllare l’archivio profili di Edge e la scheda Appartenenza pubblico per confermare lo stato di un profilo sulla rete Edge.
doc-type: article
solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# Convalida profilo su Edge

## Finalità di apprendimento

Verifica che il profilo non esista nell’archivio dei profili di rete di Edge.

## Controlla il profilo Edge

1. Fai clic sulla scheda **Attributi** e sul pulsante di scelta **Edge** per visualizzare il profilo Edge

   ![Profilo Edge visualizzato nella scheda Attributi](assets/validate-profile-on-edge-attributes-tab.png)

   >[!NOTE]
   >
   >È possibile che venga visualizzata una versione &quot;ridotta&quot; del profilo, costituita solo dalle identità a seconda del tempo trascorso.



2. Fai clic sulla scheda Appartenenza al pubblico.  Sarà **vuoto**.

![Scheda Appartenenza pubblico vuota nel profilo Edge](assets/validate-profile-on-edge-empty-audience-membership-tab.png)

>[!NOTE]
>
>**Perché non sei iscritto ad Edge?**
>
>Non avremmo dovuto vedere **dep: Qualunque evento Edge (entro un&#39;ora)** qualificato?
>
>Anche se abbiamo un pubblico con una valutazione di Edge, tale pubblico non esiste in Edge perché non abbiamo ancora alcun motivo per farlo... ancora.
>
>Se dovessimo utilizzare quel pubblico (ad esempio Decisioning o Destinazioni), le regole del pubblico verranno inviate ad Edge e, la prossima volta che un evento viene inviato in streaming ad Edge, il pubblico verrà valutato.
>
>Inoltre, non abbiamo attivato Edge Segmentation Services.



## Riassunto

Il profilo non esiste (ancora) in Edge
