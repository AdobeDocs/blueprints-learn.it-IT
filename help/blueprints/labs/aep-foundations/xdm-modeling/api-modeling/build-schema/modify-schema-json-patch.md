---
title: Modifica schema - Patch JSON
description: Utilizza una chiamata API PATCH JSON per aggiungere un nuovo campo a un gruppo di campi tenant esistente e visualizzare la modifica riflessa nello schema.
doc-type: article
solution: Experience Platform
exl-id: c0313594-d998-4525-a0a4-d9d844bed5ef
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%
---

# Modifica schema - Patch JSON

## Panoramica

Si supponga che dopo la creazione dello schema sia necessario aggiungere un campo aggiuntivo all&#39;oggetto `plan` denominato `planDescription`. Questa necessità potrebbe sorgere perché hai dimenticato di aggiungerlo quando hai creato lo schema o perché si trattava di una richiesta pervenuta dopo mesi. Per eseguire questa attività, eseguire un&#39;operazione `PATCH` che aggiorna lo schema con il nuovo campo.

Per ulteriori informazioni su JSON PATCH, consulta i collegamenti riportati di seguito. Per questo laboratorio, supponiamo di avere una conoscenza generale di come funziona.

- [https://jsonpatch.com/](https://jsonpatch.com/)
- [Nozioni di base sulle API di Experience League](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-fundamentals.html?lang=en#json-patch)

![Diagramma dell&#39;applicazione della patch a un campo planDescription mancante in uno schema esistente](assets/modify-schema-json-patch-patching-missing-plan-description-field.png "Applicazione della patch a un campo Plan Description mancante")

>[!NOTE]
>
>Tenere presenti i punti seguenti:
>
>- Uno schema è composto da una classe e da uno o più gruppi di campi
>- È necessario aggiungere nuovi campi a un gruppo di campi prima di aggiungerli a uno schema. Questa restrizione garantisce la riutilizzabilità di un campo in qualsiasi schema che utilizza tale gruppo di campi.



Per aggiungere un nuovo campo a uno schema, è necessario eseguire le operazioni seguenti in ordine. Questo processo è quello che si fa nei seguenti passaggi di laboratorio.

- Identifica il gruppo di campi in cui desideri aggiungere la nuova proprietà
- Creare una chiamata PATCH JSON per aggiornare il gruppo di campi
- Esegui la chiamata PATCH JSON per aggiornare il gruppo di campi (ereditato dallo schema)



## Individua e identifica il gruppo di campi da aggiornare

1. Selezionare la chiamata API `Step 1 - Get Tenant Field groups` che si trova nella cartella `XDM Schema Lab -> Customize Schema`
1. Eseguire la richiesta facendo clic sul pulsante `Send`

   ![Passaggio 1 - Ottieni richiesta API per gruppi di campi tenant](assets/modify-schema-json-patch-step-1-get-tenant-field-groups.png "Passaggio 1 - Ottieni gruppi di campi tenant")

   >[!NOTE]
   >
   >Ricorda che hai creato l&#39;oggetto `plan` all&#39;interno di un gruppo di campi personalizzato. Gli oggetti creati personalizzati nel registro dello schema XDM sono denominati &quot;tenant&quot;, pertanto la chiamata API che utilizza il percorso `/schemaregistry/tenant/mixins/`.



1. Nella risposta cerca l&#39;ID schema per il gruppo di campi personalizzati creato in precedenza con titolo `Customer Account Details - Sandbox <your number here> `

1. Copia `$meta:altId` e salvalo in un luogo sicuro per il passaggio successivo

![Individuazione del gruppo di campi Dettagli account cliente personalizzato nella risposta API](assets/modify-schema-json-patch-search-field-group-response.jpeg "Cercare la risposta per il gruppo di campi Dettagli account cliente")

>[!CAUTION]
>
>Assicurati di selezionare il gruppo di campi corretto da copiare. Non utilizzare il gruppo di campi con nome simile denominato `dep: Customer Account Details`

>[!WARNING]
>
>È necessario `$meta:altId` per i futuri passaggi del laboratorio, quindi salvarlo in qualche punto prima di continuare



## Cerca il gruppo di campi per $meta\:altId

1. Selezionare la chiamata API `Step 2 - Fetch path for the object to be modified` nella cartella `XDM Schema Lab -> Customize Schema`
1. Nell&#39;URL della richiesta sostituisci `<replace me>` con `$meta:altId` salvato dal passaggio della sezione precedente alla fine della chiamata come mostrato di seguito
1. Salva le modifiche apportate alla richiesta
1. Eseguire la richiesta facendo clic sul pulsante `Send`

![Passaggio 2 - Recupero del percorso per la chiamata API dell&#39;oggetto da modificare](assets/modify-schema-json-patch-step-2-fetch-object-path.jpeg "Passaggio 2 - Recupero del percorso per l&#39;oggetto da modificare passaggi")



Rivedi la risposta e osserva che il percorso del puntatore JSON per l&#39;oggetto **plan** è costruito utilizzando ciascuna delle proprietà evidenziate di seguito.

![Proprietà evidenziate che compongono il percorso del puntatore JSON per l&#39;oggetto del piano](assets/modify-schema-json-patch-customer-account-details-path-to-the-plan-object.png "Percorso dettagli account cliente per l&#39;oggetto del piano")



Il percorso completo è simile a quello visualizzato di seguito.  Copia questo percorso e salva da qualche parte come riferimento

```none
/definitions/customFields/properties/_devbc/properties/plan/properties
```

>[!NOTE]
>
>Ricordati di aggiornare il nome tenant precedente (\_devbc) con il tuo



## PATCH il gruppo di campi

### Esempio di corpo dell’API PATCH JSON

```none
[
    {
        "op": "",
        "path": "",
        "value": {
            "title": "",
            "type": "",
            "description": ""
        }
    }
]
```

- **op (Operazione)** -> indica l&#39;azione che deve essere eseguita da PATCH
- **Percorso** -> si tratta del percorso che si desidera creare, aggiornare o eliminare, ovvero il puntatore JSON alla posizione del nuovo campo
- **Valore** -> è un campo facoltativo ed è utilizzato solo per creare o sostituire un campo esistente



### Eseguire la richiesta API

1. Fai clic sulla chiamata API `Step 3 - Modify Tenant Field group` nella cartella `XDM Schema Lab -> Customize Schema`

   ![Passaggio 3 - Modifica chiamata API gruppo di campi tenant](assets/modify-schema-json-patch-step-3-modify-tenant-field-group.png "Passaggio 3 - Modifica gruppo di campi tenant")



2. Aggiorna il corpo della richiesta con le seguenti informazioni

   - **op** ->` add`
   - **percorso** -> `path from previous step +`&#x200B;` the new field name`
   - **valore** ->
     - **titolo** -> `Plan Description`
     - **tipo** -> `string`
     - **descrizione** -> `High-level details about the plan`

   Al termine la richiesta API dovrebbe avere un aspetto simile al seguente

   ![Corpo della richiesta JSON PATCH completato aggiungendo il campo planDescription](assets/modify-schema-json-patch-step-3-final-call-example.png "Passaggio 3 - Esempio di chiamata finale")

   >[!WARNING]
   >
   >Assicurati di includere il nuovo nome del campo, **planDescription,** nel percorso



3. Se tutto sembra buono `Save` la tua chiamata

4. `Execute` la chiamata per eseguire PATCH

Nel gruppo di campi viene visualizzata una risposta `200 OK` e il campo `planDescription`, come segue:

![200 Risposta OK dopo aver applicato correttamente la patch al gruppo di campi con planDescription](assets/modify-schema-json-patch-step-3-200-ok-successful-patch.png "Passaggio 3 - 200 OK PATCH") completato

>[!SUCCESS]
>
>Congratulazioni! Aggiornamento di un gruppo di campi/schema tramite JSON PATCH completato



## Visualizzare la modifica nell’interfaccia utente

Sfoglia lo schema tramite l’interfaccia utente e visualizza il campo appena aggiunto.

![Campo Descrizione piano visibile nello schema dopo la patch JSON nell&#39;interfaccia utente di Experience Platform](assets/modify-schema-json-patch-plan-description-added-to-field-group.png "Descrizione piano aggiunta al gruppo di campi Dettagli account cliente - Sandbox \&lt;numero>. Modifica schema JSON")
