---
title: Configurazione
description: Completa i passaggi di implementazione della sandbox e configurazione del Postman necessari prima di avviare i laboratori AJO Foundations.
doc-type: article

solution: Experience Platform
exl-id: 7c1a9e3d-5b8f-4a2e-9c6d-3f7b0e4a8c2d
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%
---

# Configurazione

Prima di avviare i laboratori AJO Foundations, completa i passaggi di configurazione indicati di seguito. I passaggi necessari dipendono da come si sta effettuando il bootcamp.

## Configurazione sandbox

>[!NOTE]
>
>Se partecipi a un corso o evento di formazione live, la sandbox è già stata distribuita: salta questa sezione e passa direttamente a Configurazione di Postman di seguito.

Se non disponi già di una sandbox funzionante con le risorse lab distribuite, completa i passaggi seguenti:

- [Configurazione Developer Console](sandbox-setup/developer-console-setup.md)
- [Istruzioni di distribuzione](sandbox-setup/deployment-instructions.md)

## Configurazione Postman

Postman è richiesto per i laboratori in questo corso, indipendentemente da come è stato eseguito il provisioning della sandbox. Prima di continuare, completare le operazioni seguenti:

- [Installazione di Postman](postman-setup/postman-installation.md)
- [Importa file di ambiente](postman-setup/import-environment-file.md)
- [Importa raccolta API](postman-setup/import-api-collection.md)

## Preparazione on-demand

Prima di avviare i laboratori, completa la configurazione Postman descritta sopra. Gli Allievi con ritmo autonomo necessitano anche di un sottodominio delegato per i laboratori dipendenti dalle e-mail e le credenziali SMS per il laboratorio di avvio del telefono di punta.

## Prerequisiti per il canale

Due laboratori più avanti in questo campo di avvio dipendono da account esterni che solo gli Allievi autodidatti devono organizzare — se sei in un corso di formazione o un evento live, questi sono già predisposti per te.

### Sottodominio delegato

Il laboratorio [Configura i canali e-mail](data-stores/configure-email-channels/overview.md) e tutto ciò che dipende da esso ([Consegna dei messaggi in azione](orchestrated-campaigns/message-delivery-in-action/overview.md), [Eccitazione post-acquisto](journeys/post-purchase-excitement/overview.md) e [Marchi AJO](content-authoring-with-ai/overview.md)) richiede un sottodominio delegato ad Adobe per l&#39;invio delle e-mail. Se non disponi già di un dominio, registrane uno con qualsiasi registrar di dominio (ad esempio, NameCheap). Quindi, per delegare un sottodominio di esso (ad esempio, `email.yourdomain.com`) ad Adobe, segui le [istruzioni di delega del sottodominio di Adobe](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/delegate-subdomains/delegate-subdomain).

>[!NOTE]
>
>La propagazione della delega dei sottodomini può richiedere del tempo. Avvia questa delega molto prima di raggiungere il laboratorio Configurare i canali e-mail.

### Credenziali SMS

Il laboratorio [Flagship phone launch](orchestrated-campaigns/flagship-phone-launch/overview.md) configura un canale SMS tramite Twilio. Non viene inviato alcun messaggio, ma è necessario disporre di credenziali di lavoro per completare la configurazione. L&#39;opzione più semplice è un account di prova gratuito di [Twilio](https://www.twilio.com/try-twilio). Per informazioni su come registrarsi e trovare il SID account e il token di autenticazione, consulta la [guida introduttiva](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account) di Twilio.
