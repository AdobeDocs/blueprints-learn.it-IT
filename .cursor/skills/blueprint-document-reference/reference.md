---
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---
# Guida di riferimento del documento blueprint - Guida dettagliata

## Tipi di documenti

| Tipo | Finalità | Posizione/Esempio |
|------|---------|--------------------|
| **Panoramica / hub** | Introduce un prodotto o un’area; collegamenti alle blueprint dello scenario | Esempio: `overview.md`, `journey-optimizer-overview.md` |
| **Blueprint scenario** | Caso d’uso singolo: architettura, passaggi, guardrail | Esempio: `real-time-lookup.md`, `journey-optimizer-journeys.md` |
| **SOMMARIO** | Navigazione; non utilizzare come modello di contenuto | `help/blueprints/TOC.md` |

&#x200B;---

## Riferimento di sezione completo

### Titolo e descrizione (prima parte)

- **titolo**: breve, specifico. Utilizzare `[!DNL Product Name]` per i nomi dei prodotti (ad esempio `[!DNL Journey Optimizer]`).
- **descrizione**: una frase. Descrivi cosa mostra il blueprint e il risultato (ad esempio, &quot;Real-time Customer Profile access at the edge for web and mobile personalization.&quot;).

### Sezioni del corpo

| Sezione | Quando includere | Linee guida per i contenuti |
|---------|-----------------|-------------------|
| **Applicazioni** | Sempre per i blueprint dello scenario | Elenco puntato dei prodotti/soluzioni Adobe interessati (ad esempio Real-time Customer Data Platform, Data Collection). |
| **Casi d&#39;uso** | Sempre | Elenco puntato dei casi d’uso aziendali/tecnici supportati da questo blueprint. |
| **Prerequisiti** | Quando è richiesta la configurazione | Prodotti, sottodomini, SDK, configurazioni che devono essere implementati. Collegamento ad Experience League per i passaggi di configurazione. |
| **Diagramma architettura** | Sempre | Diagramma primario singolo (preferito da SVG). Usa stile coerente: `style="width:90%; border:1px solid #4a4a4a" class="modal-image"`. Fornisci testo `alt` significativo. |
| **Guardrail** | Sempre con guardrail | Collegamento alle pagine ufficiali del guardrail di Experience League. Aggiungi limiti specifici per blueprint (ad esempio TTL, limiti di velocità) come punti elenco. |
| **Modelli di implementazione** | Quando esistono più approcci | Denomina ogni pattern (ad esempio &quot;Pattern 1: basato sull’iscrizione del pubblico con Web SDK&quot;); utilizza i punti elenco per specificare quando utilizzare e compromessi. |
| **Passaggi di implementazione** | Per i blueprint di scenari con un percorso definito | Elenco numerato. Ogni passaggio: azione + collegamento ad Experience League in cui si trova la procedura. Non copiare le procedure complete. |
| **Considerazioni sull’implementazione** | In presenza di avvertenze importanti | Sottosezioni (ad esempio, considerazioni sull’identità, personalizzazione basata su attributi). Punti elenco o paragrafi brevi; collega per approfondimento. |
| **Documentazione correlata** | Sempre | Collegamenti raggruppati ad Experience League (e facoltativamente developer.adobe.com). Consulta &quot;Experience League link groups&quot;, di seguito. |

### Panoramica/pagine hub

- Inizia con 1-2 paragrafi sul prodotto/area e su cosa coprono i blueprint.
- **Casi d&#39;uso**: può usare `>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]` per più categorie.
- **Architettura**: un diagramma principale.
- **Scenari blueprint** o **Modelli di integrazione**: tabella con nome scenario, breve descrizione e collegamento al blueprint dello scenario.
- **Prerequisiti**, **Guardrail**, **Documentazione correlata**: Come sopra; concisa.

&#x200B;---

## Adobe Experience League — Istruzioni per l’agente

### Quando fare riferimento ad Experience League

- **Documentazione del prodotto**: funzionamento di un prodotto, flussi di interfaccia utente, concetti.
- **API**: endpoint, parametri, esempi (Experience Platform, Edge, ecc.).
- **Guardrail**: pagine guardrail ufficiali per il prodotto o servizio.
- **Esercitazioni**: guide dettagliate (ad esempio, creazione di schemi, attivazione di destinazioni).
- **Configurazione**: flussi di dati, destinazioni, criteri di unione, identità e così via.

Non incollare nella blueprint procedure lunghe da Experience League. Riepiloga e collega.

### Modelli URL

| Tipo di contenuto | URL di base | Percorso di esempio |
|--------------|----------|--------------|
| Documentazione di Experience Platform | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`, `.../destinations/catalog/...` |
| Experience League (it) | `https://experienceleague.adobe.com/en/docs/` | Stessa struttura con `/en/`. |
| Blueprint per   | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| Web SDK | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`, `.../commands/command-responses.html` |
| API server di Edge Network | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`, `.../guardrails.html` |
| Mobile SDK | `https://developer.adobe.com/client-sdks/` | `.../home/`, `.../edge/adobe-journey-optimizer-decisioning/` |
| Tag | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| Tutorial su Platform | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

Utilizza il percorso canonico corrispondente al sito Experience League corrente (preferisci `/en/docs/` quando è noto il percorso inglese).

### Formattazione dei collegamenti nel markdown

- **Testo collegamento descrittivo**: `[Create schemas](https://experienceleague.adobe.com/...)` non &quot;fare clic qui&quot;.
- **Nomi di prodotto nel testo**: utilizzare `[!DNL Product Name]` per stile Adobe (esempio: `[!DNL Real-time Customer Profile]`).
- **Collegamenti esterni**: aggiungi `{target="_blank"}` solo quando il modello o la pipeline lo richiede (controlla i blueprint esistenti nell&#39;archivio).

### Documentazione correlata — gruppi suggeriti

Utilizza questi gruppi quando si applicano:

1. **Configurazioni di destinazione** (per blueprint di attivazione/personalizzazione Edge)
2. **Documentazione di SDK** (Web SDK, Mobile SDK, Edge Network Server API, Tags)
3. **Profilo e segmentazione** (Profilo cliente in tempo reale, criteri di unione, segmentazione)
4. **Tutorial** (guide dettagliate su piattaforme o prodotti specifici)
5. **Documentazione del prodotto** (home della documentazione principale del prodotto o sottosezioni principali)
6. **Guardrail** (se non già nella sezione Guardrail)

Esempio:

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
```

&#x200B;---

## Repo e TOC

- **Percorso contenuto blueprint**: `help/blueprints/` (con sottocartelle per area, ad esempio `audience-activation/`, `customer-journeys/journey-optimizer/`).
- **Assets**: individua insieme al blueprint (ad esempio `assets/`, `images/`) o in una cartella condivisa (ad esempio `experience-platform/assets/`).
- **TOC**: modifica `help/blueprints/TOC.md` quando aggiungi, rinomina o sposta pagine blueprint. Mantenere il frontmatter (`user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`) e la gerarchia `+`.

&#x200B;---

## Riferimenti di esempio in questo archivio

- **Blueprint scenario (forma lunga)**: `help/blueprints/audience-activation/real-time-lookup.md`
- **Panoramica/hub con schede e tabelle**: `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **Focalizzato su guardrail**: `help/blueprints/experience-platform/guardrails.md`
- **Navigazione**: `help/blueprints/TOC.md`, `help/blueprints/overview.md`

Utilizzali come pattern per l’ordine delle sezioni, la gestione del materiale di prima scelta, il posizionamento dei diagrammi e l’utilizzo dei collegamenti Experience League.
