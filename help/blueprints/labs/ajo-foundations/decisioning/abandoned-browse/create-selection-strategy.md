---
hold: true
title: Crea strategia di selezione
description: Configura una strategia di selezione che colleghi una raccolta di offerte, regole di idoneità e una formula di classificazione per le decisioni.
doc-type: article
solution: Experience Platform
exl-id: 066ad087-6845-4ab5-9a6e-8dad1aa848f8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# Crea strategia di selezione

## Obiettivo

Fino a questo punto, hai creato le offerte, definito l’idoneità delle offerte con una regola di decisione, le hai raccolte in una raccolta e creato una formula che le riordina dinamicamente in base agli attributi del profilo che richiede la personalizzazione. Poiché utilizziamo un singolo set di 4 offerte per un singolo caso d’uso, è invitante pensare che ciascuno di questi elementi sia correlato, soprattutto quando li abbiamo denominati in modo simile. Tuttavia, è importante pensare in modo più astratto quando si considera una strategia a lungo termine e una portata di dimensione aziendale. Le offerte possono essere ordinate in una o più raccolte. Le formule di classificazione possono essere applicate a qualsiasi raccolta di offerte. In realtà, la prima volta che si collegano questi elementi è quando si crea una strategia di selezione.

Immagina che abbiamo avuto centinaia di offerte utilizzate in quaranta raccolte e una dozzina di formule di classificazione o giù di lì. Come farebbe un pacchetto decisionale a sapere quale formula di classificazione applicare a quale raccolta di offerte? La strategia di selezione crea tale collegamento. Quando aggiungi Decisioning a un canale, stai aggiungendo una o più strategie di selezione.

## Creare la strategia di selezione

1. Se necessario, espandi **Decisioning** nella barra a sinistra e fai clic su **Configurazione strategia**. Arriva alla pagina &quot;Regole di decisione&quot;, in cui viene visualizzata la regola di decisione &quot;Piani di livello superiore&quot; creata in precedenza e utilizzata come requisiti di idoneità per gli articoli dell’offerta telefonica di livello superiore.
2. Fai clic su **Strategie di selezione** sotto il menu &#39;Metodi di classificazione&#39;. Senza strategie di selezione disponibili, fare clic sul pulsante blu **Crea strategia di selezione**.

![Pagina Strategie di selezione con il pulsante Crea strategia di selezione](assets/create-selection-strategy-create-button.png)

3. Assegna un nome alla strategia di selezione **Strategia di selezione iPhone 17**
4. È possibile notare che una strategia di selezione richiede 3 elementi.
   - Una raccolta di offerte
   - Requisiti di idoneità
   - Un metodo di classificazione

Fai clic sul pulsante **Seleziona raccolta**, seleziona la casella accanto all&#39;unica raccolta disponibile (**Raccolta iPhone 17**) e fai clic su **Salva**.

5. Lascia il menu a discesa &quot;Idoneità&quot; impostato su Tutti i visitatori.

>[!NOTE]
>
>L’idoneità può essere applicata a livello di offerta, di strategia di selezione o di Percorso/campagna tramite i criteri di inserimento nel Percorso o nella campagna. Dipende tutto dal caso d’uso che stai cercando di realizzare. Se fai clic sull&#39;elenco a discesa **Idoneità**, vengono visualizzate le stesse opzioni per Pubblico e Regola di decisione visualizzate a livello di offerta. Nel nostro caso d’uso, volevamo solo limitare offerte specifiche, quindi aveva senso fare l’idoneità a livello di offerta.

6. Imposta il **metodo di classificazione** su **formula,** quindi fai clic sul pulsante **Seleziona formula**

>[!NOTE]
>
>Potresti aver notato le opzioni &quot;Priorità offerta&quot; e &quot;Modello di IA&quot; nel menu a discesa del metodo di classificazione. Se desideri restituire solo le offerte utilizzando solo la priorità originale, scegli l’opzione &quot;Priorità offerta&quot;.
>
>L’opzione Modello di intelligenza artificiale utilizza un modello di intelligenza artificiale che analizza impression, clic e conversioni per le offerte restituite per determinare quale offerta visualizzare all’utente. Non li utilizzeremo in questo laboratorio perché sono richieste soglie minime di dati e due settimane per addestrare i modelli.

7. Selezionare la casella accanto all&#39;unica formula di classificazione disponibile (**iPhone 17 Ranking Formula**) e fare clic su **Salva**. Al termine, la strategia di selezione sarà simile alla seguente:

![Strategia di selezione completata con raccolta, idoneità e formula di classificazione impostate](assets/create-selection-strategy-completed-configuration.png)

8. Una volta corretta la strategia di selezione, fai clic sul pulsante blu **Crea**.

>[!TIP]
>
>La strategia di selezione di iPhone 17 è ora visibile nel menu &quot;Strategia di selezione&quot;

>[!NOTE]
>
>Decisioning consente di selezionare e ordinare offerte molto semplici o molto complesse. Per finire, potresti avere una raccolta di offerte con la loro priorità predefinita, un’idoneità impostata su tutti i visitatori e il metodo di classificazione &quot;Priorità offerta&quot;, e tutti gli utenti finali vedrebbero le offerte nell’ordine dei loro punteggi di priorità originali. All’estremo opposto, potresti avere una raccolta enorme con punteggi di priorità iniziali complessi, una formula di classificazione personalizzata e regole di idoneità a livelli sia a livello di offerta che di strategia di selezione. Quello che hai costruito in questo laboratorio si trova nel mezzo ed è stato progettato per dimostrare i diversi modi in cui potevano essere configurati i pacchetti decisionali.

## Riassunto

In questa pagina è stata creata una strategia di selezione che unisce i componenti core creati finora, ovvero la raccolta delle offerte, le regole di idoneità e la formula di classificazione.
