---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%
---
# Convenzioni di denominazione: diagrammi di architettura e blueprint

Questo documento è l&#39;origine di verità per il nome delle categorie in `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`. Sia l&#39;abilità `architecture-diagram-category-builder` (nuove categorie) che l&#39;abilità `architecture-diagram-page-builder` (nuove pagine all&#39;interno di categorie esistenti) devono seguire queste regole.

## La regola

**Nome cartella = Slug ancoraggio sommario = maiuscole/minuscole dell&#39;etichetta sommario completa.** Tutti e tre devono corrispondere esattamente, senza abbreviazione o troncamento.

| Etichetta sommario | Ancoraggio | Cartella |
| --- | --- | --- |
| Panoramiche dell’architettura | `#architecture-overviews` | `architecture-overviews/` |
| Attivazione in base a pubblico e profili | `#audience-profile-activation` | `audience-profile-activation/` |
| Attivazione e marketing B2B | `#b2b-activation-marketing` | `b2b-activation-marketing/` |
| Informazioni sul cliente | `#customer-insights` | `customer-insights/` |
| Percorsi di clienti | `#customer-journeys` | `customer-journeys/` |

Questo è lo stato corrente e corretto di tutte e cinque le categorie (al 16 settembre 2026). In precedenza nella cronologia di questo archivio alcune di queste erano state abbreviate (`architecture-overview`, `audience-activation`, `b2b-activation`). L&#39;incoerenza è stata corretta. Non reintrodurre nomi abbreviati di cartelle/ancoraggi per categorie nuove o esistenti.

## Perché è importante

- **Predittività.** Un collaboratore (umano o agente) deve essere in grado di indovinare il percorso della cartella dall’etichetta del sommario e viceversa, senza aprire TOC.md.
- **Automazione sicura.** Le abilità e gli script che generano percorsi da etichette (o etichette da percorsi) funzionano in modo affidabile solo quando la mappatura è esatta e meccanica (caso kebab, nessuna abbreviazione).
- **Igiene di reindirizzamento.** Ogni ridenominazione richiede nuove voci in `redirects.csv`. Mantenendo i nomi stabili e completamente descrittivi fin dall’inizio si evita di rinominarli più volte.

## Come ricavare un campione da un’etichetta

1. Metti in minuscolo l’etichetta.
2. Eliminare completamente `&` e unire le parole circostanti con un trattino (ad esempio `Audience & Profile Activation` -> `audience-profile-activation`).
3. Sostituire gli spazi con i trattini.
4. Segno di punteggiatura diverso dai trattini.
5. Non abbreviare, troncare o eliminare parole dall&#39;etichetta (no `b2b-activation` per &quot;B2B activation &amp; marketing&quot; — utilizzare `b2b-activation-marketing`).

## Risorse richieste per categoria

Ogni cartella delle categorie direttamente in `help/blueprints/architecture-diagrams/` deve contenere:

1. **`overview.md`**: una pagina di destinazione per la categoria. Vedere `./category-overview-template.md` per la struttura richiesta. Ogni pagina di panoramica della categoria deve avere lo stesso aspetto: paragrafi introduttivi, quindi una singola tabella `| Diagram | Description |` che elenca ogni pagina della categoria (in ordine di sommario). Non utilizzare celle `<ul><li>` nidificate, immagini di diagrammi incorporate o una terza colonna, in quanto corrispondono esattamente alle cinque categorie esistenti.
2. **`assets/`**: cartella per le immagini del diagramma, anche se vuota al momento della creazione (creala una volta aggiunto il primo diagramma).

## Requisiti TOC.md

- La voce `+ [Overview](/help/blueprints/architecture-diagrams/{folder}/overview.md)` della categoria è sempre la voce **first** sotto l&#39;intestazione della categoria, prima di qualsiasi pagina di contenuto.
- L&#39;intestazione della categoria e il relativo ancoraggio passano immediatamente sotto `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, allo stesso livello di rientro a 2 spazi delle altre cinque categorie.
- Il rientro delle pagine di contenuto è di 4 spazi (`+` con prefisso e quattro spazi iniziali). I sottogruppi nidificati (ad esempio, il raggruppamento di RTCDP in Audience &amp; Profile Activation) hanno un rientro di 6 spazi.

## Requisiti della pagina di destinazione

`help/blueprints/architecture-diagrams/overview.md` (la pagina di destinazione principale Diagrammi architettura e Blueprint) deve avere esattamente una scheda per categoria, in ordine di sommario. Ogni scheda:

- Collegamenti a `overview.md` della categoria (non una pagina di contenuto).
- Utilizza come miniatura un&#39;immagine di diagramma rappresentativa della cartella `assets/` di quella categoria, con lo stile CSS scheda standard (`background-color:#ffffff; border:1px solid #d3d3d3;` oltre alle regole di ridimensionamento/spaziatura condivise già presenti nel file).
- Include il nome della categoria (grassetto/forte) e una descrizione di una frase che corrisponde all’introduzione della panoramica della categoria.

Quando il numero di categorie è un multiplo di 3, la tabella viene riprodotta come righe intere e pulite (3 colonne, `table-layout:fixed`, `width:33%` per cella). Se non è un multiplo di 3, aggiungere un `<td>` vuoto per slot mancante nell&#39;ultima riga (non lasciare la tabella irregolare/senza stile).
