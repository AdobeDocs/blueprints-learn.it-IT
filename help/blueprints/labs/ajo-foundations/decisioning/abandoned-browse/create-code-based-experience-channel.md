---
hold: true
title: Creare un canale di esperienza basato su codice
description: Configura un canale di esperienza basato su codice in Adobe Journey Optimizer che restituisce i dati dell’offerta JSON a qualsiasi sistema web, mobile o IoT che richiede una decisione.
doc-type: article
solution: Experience Platform
exl-id: c3353d3d-cd97-46b7-8ef8-c72fa9e7dfe5
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Creare un canale di esperienza basato su codice

## Obiettivo

Ricorda che i requisiti aziendali sono che qualsiasi sistema di Connection 5G deve essere in grado di restituire un&#39;offerta appropriata. Che si tratti del computer di un agente cliente, di un chiosco in-store, di un’app mobile o del sito web, il cliente deve ricevere la stessa esperienza di offerta. L’unico canale AJO in grado di farlo è un’esperienza basata su codice (CBE), uno dei canali AJO in entrata. Mentre un CBE può restituire HTML, la sua funzione principale è quella di restituire informazioni sull&#39;offerta da presentare al sistema ricevente, con quel sistema che sa cosa fare con quelle informazioni sull&#39;offerta. A differenza del canale web, i CBE non vengono renderizzati o segnalati automaticamente. Anche se per il cliente è un po’ più di lavoro manuale, offrono molta flessibilità in quanto possono essere configurate per restituire JSON che qualsiasi sistema mobile, web o IoT può utilizzare per eseguire le decisioni.

1. Se necessario, espandi la voce di menu **Amministrazione** nella barra a sinistra (probabilmente dovrai scorrere verso il basso) e fai clic su **Canali**. Arrivi alla pagina &quot;Configurazioni canale&quot;.
2. Fai clic sul pulsante blu **Crea configurazione canale**
3. Nella pagina &quot;Dettagli configurazione canale&quot;, denomina il canale **jsonOffer\_cbe**

>[!NOTE]
>
>Poiché un CBE può essere chiamato da un numero qualsiasi di client su *N* numero di piattaforme, questo CBE verrà denominato generico per la posizione, ma specifico per il fatto che restituisce offerte in formato JSON.

4. Imposta il menu a discesa **Seleziona canale** su **Esperienza basata su codice.**

>[!WARNING]
>
>Non imposteremo un’azione di marketing in questo laboratorio perché aggiunge complessità superflua alla dimostrazione, ma poiché i CBE sono accessibili da qualsiasi numero di sistemi, in un caso d’uso reale puoi impostare tutte le possibili azioni di marketing per questo canale in modo da applicare le etichette DULE.

5. Selezionare la casella **Web** nell&#39;area &#39;Impostazioni esperienza basate su codice&#39; e mantenere selezionata l&#39;opzione **Pagina singola**.
6. Nella casella di testo **URL pagina** immettere il testo `https://connection5g.com/home`
7. Nella casella di testo **Posizione a pagina**, immetti il testo **jsonOfferContainer**

>[!NOTE]
>
>Non tutti gli eventi di esperienza inviati ad Edge attivano una richiesta di offerte personalizzate. Nella sezione successiva verrà creato un Percorso in cui questo CBE verrà configurato con la strategia di selezione appena configurata. L’impostazione &quot;Posizione nella pagina&quot; è il nome del parametro passato in Eventi esperienza che indica all’Experience Edge di restituire tutte le offerte assegnate a quel CBE. Spesso ci si riferisce ad essa anche come a una superficie. Che si tratti di un’app mobile, di una pagina web o di un altro dispositivo IoT, se il valore jsonOfferContainer viene passato ad Edge, insieme al eventType corretto tramite un evento esperienza, Edge eseguirà la logica configurata finora in laboratorio e restituirà l’offerta appropriata.

8. Fare clic sul pulsante di scelta **JSON** nella sezione &#39;Formato&#39;. Al termine, la configurazione del canale CBE sarà simile alla seguente:

![Configurazione del canale esperienza basata su codice completata con formato JSON selezionato](assets/create-code-based-experience-channel-completed-config.png)

9. Una volta che tutto sembra corretto, fai clic sul pulsante blu **Invia** nell&#39;angolo in alto a destra.

>[!TIP]
>
>Una volta effettuato il salvataggio, vieni riportato alla pagina di configurazione del canale e visualizzi il CBE appena creato.

## Riassunto

In questa pagina, hai configurato un canale di esperienza basata su codice (CBE) e hai impostato un nuovo canale in entrata che può restituire decisioni sulle offerte in formato JSON, in modo che i sistemi esterni (come pagine web, app o chioschi) possano richiedere e ricevere le offerte appropriate in base alla strategia di selezione creata in precedenza.
