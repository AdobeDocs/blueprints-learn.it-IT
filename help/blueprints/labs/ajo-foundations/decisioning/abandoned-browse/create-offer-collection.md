---
title: Creare una raccolta di offerte
description: Raggruppa gli elementi di offerta correlati in una raccolta utilizzando regole basate su attributi in modo che possano essere valutati insieme da una strategia di selezione.
doc-type: article
solution: Experience Platform
exl-id: 0a54f4dc-2112-474a-8383-9dd1497c3c74
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# Creare una raccolta di offerte

## Obiettivo

Ora che le offerte sono state create, devono essere organizzate in una raccolta. Una raccolta include uno o più elementi di offerta e un elemento di offerta può trovarsi in più raccolte.

## Creare la raccolta di offerte iPhone

1. Se necessario, espandi **Decisioning** nella barra a sinistra, quindi fai clic su **Cataloghi**. Puoi vedere le quattro offerte create nella sezione precedente.
2. Fai clic su **Raccolte** a sinistra del nome dell&#39;offerta

   ![Scheda Raccolte nella pagina Cataloghi](assets/create-offer-collection-collections-tab.png)

3. Fai clic sulla **Crea raccolta** blu per creare la nuova raccolta.
4. Denomina la raccolta **iPhone 17 Collection**
5. Nella sezione &quot;Regole di raccolta&quot; fare clic sulla casella di testo contenente il testo **_Fare clic per creare un elemento di decisione_**. Dopo aver fatto clic su, vengono visualizzate le opzioni per la creazione della regola.

   ![Casella di testo della regola di raccolta aperta per la creazione di un elemento di decisione](assets/create-offer-collection-create-decision-item.png)

6. Fai clic sul pulsante **Seleziona attributo**, quindi esplora lo schema dell&#39;elemento dell&#39;offerta facendo clic su **Dispositivo > Rendi**. Fare clic su **Salva,** e l&#39;attributo &#39;Make&#39; è ora incluso nella regola di decisione.

   ![Attributo Device Make aggiunto alla regola di raccolta](assets/create-offer-collection-select-make-attribute.png)

   >[!NOTE]
   >
   >Tieni presente che le opzioni disponibili sono gli stessi campi configurabili utilizzati durante la creazione degli elementi dell’offerta. Poiché una raccolta è un raggruppamento di elementi di offerta, le regole per raggrupparli dipendono dai loro attributi.

7. Lascia l&#39;operatore &quot;È uguale a&quot; sul posto e immetti il testo **iPhone** nel campo del valore. Viene visualizzato il numero di elementi che cambia in 4, a indicare che tutti gli elementi dell&#39;offerta soddisfano tali criteri

   ![Regola di raccolta che mostra quattro elementi di offerta che corrispondono ai criteri di iPhone](assets/create-offer-collection-four-matching-offers.png)

   >[!NOTE]
   >
   >Puoi anche fare clic sul pulsante **Anteprima raccolta** per visualizzare gli elementi dell&#39;offerta che soddisfano i criteri.

8. Con tutti e quattro gli elementi dell&#39;offerta selezionati, fai clic sul pulsante blu **Crea**. Viene visualizzata una pagina che mostra la raccolta appena creata.

![Pagina di raccolta iPhone 17 appena creata](assets/create-offer-collection-created-collection-page.png)

>[!NOTE]
>
>Una raccolta è più di un semplice mezzo di organizzazione. Nei passaggi successivi, vedrai che in Decisioning viene applicata la logica di selezione a una raccolta di offerte. Considerando un’implementazione di dimensioni Enterprise, non è difficile immaginare quante offerte verrebbero create negli anni di utilizzo. Al fine di determinare quali offerte applicare a una strategia di selezione, viene illustrata l’importanza di una corretta gestione della raccolta.
>
>In questo caso, una raccolta con solo &quot;iPhone&quot; come criterio porterebbe all’inserimento di troppe offerte dopo alcuni anni di rilasci di iPhone. Avremmo potuto utilizzare criteri aggiuntivi come &quot;Rendere uguale a 17&quot; o usare i tag di AEP per assegnare tag alle offerte per una campagna specifica. Ma per semplicità, usiamo questa semplice logica per creare una raccolta.

## Riassunto

Ora hai creato una raccolta di offerte che raggruppa gli elementi di offerta che hai creato in precedenza. Hai aggiunto tutte le offerte di iPhone 17 in una raccolta e definito una regola basata sugli attributi dell’offerta (come make per dispositivo) in modo che solo le offerte pertinenti appartengano a questa raccolta.
