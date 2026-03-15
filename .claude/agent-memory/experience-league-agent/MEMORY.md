---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---
# Memoria agente Experience League

## File di riferimento chiave in questo archivio
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` — valori predefiniti metadati a livello di repository
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` — metadati a livello di guida
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` — modelli di authoring blueprint

## Regole metadati (consulta metadata-fields.md per riferimento completo)
- Argomento richiesto: `title`, `description`, `exl-id`
- Argomento consigliato: `solution`
- `exl-id` deve essere un UUID valido; elimina/lascia vuoto durante la copia dei file (assegnati automaticamente dal sistema)
- `description` deve iniziare &quot;Scopri come...&quot; o &quot;Ulteriori informazioni su...&quot; linee guida di Adobe
- `title` max ~60 caratteri per SEO; utilizza `[!DNL ProductName]` per i nomi dei prodotti nel titolo
- I valori `solution` fanno distinzione tra maiuscole e minuscole e devono corrispondere all&#39;enum approvato (vedere metadata-fields.md)
- `thumbnail: null` o `thumbnail:` (vuoto) sono entrambi utilizzati; vuoto è accettabile
- `kt:` è un campo legacy (numero JIRA dell&#39;articolo della Knowledge Base); è ancora visibile in questo repository; il valore vuoto è accettabile
- I file sommario utilizzano: `user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`
- Il livello repository `metadata.md` utilizza: `cloud`, `solution`, `product`, `type`, `doc-type`, `mini-toc-levels`, `git-repo`, `index`

## Modelli comuni in questo archivio (blueprints-learn.en)
- La maggior parte dei file blueprint contiene: `title`, `description`, `solution`, `exl-id`
- Alcuni file meno recenti includono anche: `kt`, `thumbnail`
- Alcuni file utilizzano `version` (blueprint di Campaign v8)
- Le pagine di panoramica utilizzano `doc-type: overview-page`
- `solution` contiene spesso più valori separati da virgole: ad esempio `Real-Time Customer Data Platform, Campaign`
- I file SENZA `solution` superano ancora la convalida se `exl-id` è presente

## Estensioni Adobe Markdown utilizzate in questo archivio
- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`
- `>[!BEGINTABS]` / `>[!TAB Name]` / `>[!ENDTABS]` per contenuti a schede
- `[!DNL ProductName]` — Non localizzare i tag per i nomi dei prodotti
- `[!UICONTROL Label]` - Riferimenti controllo interfaccia utente
- `{zoomable="yes"}` — attributo zoom immagine
- `{width="1000"}` — attributo larghezza immagine
- `{target="_blank"}` — destinazione collegamento esterno

## Riferimenti dettagliati
- Riferimento campo metadati completo: `metadata-fields.md`
- Guida all’authoring scansionata: https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home (febbraio 2026)
