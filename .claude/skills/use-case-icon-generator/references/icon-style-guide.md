---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---
# Guida allo stile dell’icona del caso d’uso

## Panoramica

Le icone dei casi d’uso fungono da identificatori visivi nella tabella del catalogo dei casi d’uso. Devono essere immediatamente riconoscibili con una larghezza di visualizzazione di 40px, mantenendo la qualità alla risoluzione nativa di 1024x1024.

## Specifiche tecniche

| Proprietà | Valore |
| --- | --- |
| Dimensioni | 1024 x 1024 pixel |
| Formato | PNG (RGB a 8 bit o RGBA) |
| Dimensione file | 900 KB - 1,4 MB tipico |
| Dimensioni visualizzazione | Larghezza 40 px nelle tabelle catalogo |
| Denominazione | `icon-{kebab-case-name}.png` |
| Percorso di archiviazione | `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/` |

## Linee guida per lo stile visivo

### Composizione
- **Singolo soggetto centrale**: ogni icona deve contenere una metafora visiva chiara che rappresenti il concetto di caso d&#39;uso
- **Composizione centrata** — L&#39;oggetto principale deve essere centrato con uno spazio vuoto bilanciato
- **Nessun testo** — Il testo è illeggibile a 40 px; utilizzare esclusivamente la metafora visiva
- **Nessuna scena complessa** — Evita composizioni con più elementi, sfondi con molti oggetti o scene narrative
- **Siluette grassetto**: la forma dell&#39;icona deve essere riconoscibile anche come una siluetta piccola

### Colore e tono
- **Palette pulita e moderna**: utilizza colori professionali appropriati per le aziende
- **Coesione del settore**: le icone all&#39;interno dello stesso settore dovrebbero essere considerate come appartenenti a un insieme
- **Contrasto elevato** - Assicurarsi che il soggetto principale si distingue chiaramente dallo sfondo
- **Evitare colori al neon o eccessivamente saturi**. Mantenere la tavolozza raffinata e professionale

### Stile
- **Moderno e professionale** — Linee pulite, finitura lucida
- **Rendering coerente** - Tutte le icone dovrebbero provenire dallo stesso sistema di progettazione
- **3D o flat è accettabile** — ma è comunque coerente all&#39;interno di un settore verticale
- **Evita il fotorealismo** — Stile illustrato o di rendering preferito per coerenza
- **Nessun logo di marchio o immagini con marchio registrato**. Utilizzare metafore visive generiche

### Test di leggibilità per piccole dimensioni
Prima della finalizzazione, ridimensiona mentalmente l&#39;immagine a 40px:
- Riesci a identificare il soggetto principale?
- Esiste un contrasto sufficiente tra primo piano e sfondo?
- Ci sono dettagli che si trasformano in rumore visivo?
- La forma viene letta chiaramente senza colore (in caso di accessibilità)?

## Esempi di metafora visiva per settore

### Retail
| Caso d’uso | Metafora visiva |
| --- | --- |
| Carrello abbandonato | Carrello con articoli |
| Consigli di prodotto | Confezione regalo o prodotti curati |
| Vendita incrociata | Oggetti che hai connesso |
| Serie di benvenuto | Biglietto di benvenuto o regalo |
| Riduzione prezzo | Tag prezzo con freccia giù |

### Settore automobilistico
| Caso d’uso | Metafora visiva |
| --- | --- |
| Promemoria del servizio | Calendario chiavi o servizio |
| Acquisto veicolo | Auto con chiavi |
| Trade-In | Frecce cambio auto |
| Auto collegata | Auto con collegamento digitale |

### Assistenza sanitaria
| Caso d’uso | Metafora visiva |
| --- | --- |
| Promemoria appuntamento | Calendario con stetoscopio |
| Aderenza al medicinale | Flacone di pillola o prescrizione |
| Preventive Care | Scudo con simbolo di salute |

### Servizi finanziari
| Caso d’uso | Metafora visiva |
| --- | --- |
| Coltivazione del piombo | Grafico di crescita o plantule |
| Prevenzione abbandono | Simbolo di schermatura o di fissaggio |
| Fase di vita | Timeline delle milestone della vita |

### B2B
| Caso d’uso | Metafora visiva |
| --- | --- |
| ABM | Target con compilazione |
| Punteggio lead | Sagoma o termometro |
| Rinnovo del contratto | Documento con simbolo di aggiornamento |

### Viaggi e ospitalità
| Caso d’uso | Metafora visiva |
| --- | --- |
| Abbandono del carrello | Valigia o prenotazione |
| Programma fedeltà | Carta fedeltà o badge stella |
| Promemoria prenotazione | Calendario con aereo/hotel |

### Assicurazioni
| Caso d’uso | Metafora visiva |
| --- | --- |
| Rinnovo criteri | Documento con frecce di rinnovo |
| Processo richieste di rimborso | Appunti con segno di spunta |
| Effettuare azioni di cross-selling | Documenti dei criteri connessi |

### Media e intrattenimento
| Caso d’uso | Metafora visiva |
| --- | --- |
| Nuovo contenuto | Pulsante Riproduci o in evidenza |
| Consigli sui contenuti | Playlist curata o contenuti con protagonista |
| Abbonamento e abbandono | Scheda di abbonamento rotta |

### Telecomunicazioni
| Caso d’uso | Metafora visiva |
| --- | --- |
| Ottimizzazione piano | Barre del segnale con ingranaggio |
| Aggiornamento dispositivo | Telefono con freccia su |
| Prevenzione abbandono | Schermo con segnale |

## Modello di richiesta di generazione immagine

Utilizza questo modello come punto di partenza, personalizzando l’oggetto e i dettagli per ogni caso d’uso:

```
A clean, modern icon illustration of {visual metaphor} representing {use case concept}. Professional corporate design style with bold shapes and clean lines. Single centered subject on a {solid/gradient} background. High contrast, vibrant but refined color palette. No text, no fine details, no complex backgrounds. The icon must be clearly recognizable when scaled down to 40 pixels. Square format, 1024x1024 pixels.
```

### Suggerimenti per la personalizzazione dei prompt

- **Specifica l&#39;oggetto**: &quot;Un carrello rosso brillante con due scatole regalo colorate all&#39;interno&quot; è meglio di &quot;un carrello&quot;
- **Specificare il trattamento dello sfondo**: &quot;su uno sfondo sfumato blu morbido&quot; o &quot;su uno sfondo bianco pulito con ombre sottili&quot;
- **Illuminazione di riferimento**: &quot;illuminazione soft studio&quot; o &quot;luce ambientale delicata&quot; consente di ottenere coerenza
- **Aggiungi modificatori di stile**: &quot;minimalista&quot;, &quot;geometrico&quot;, &quot;isometrico&quot; o &quot;design piatto&quot; per gestire l&#39;estetica
- **Includi prompt negativi se supportati**: &quot;nessun testo, nessuna filigrana, nessun bordo, nessun elemento fotorealistico&quot;

## Icona inventario esistente

### Per settore

**Vendita al dettaglio (9 icone):**
icon-abbandonato-carrello, icon-inventario-urgenza, icon-prezzo-rilascio, icon-prodotto-consigli, icon-categoria-pagine, icon-benvenuto-serie, icon-rifornimento, icon-post-acquisto, icon-cross-selling-upselling

**Automotive (12 icone):**
icon-service-reminders, icon-recall-notifications, icon-test-drive, icon-model-launch, icon-trade-in, icon-parts-accessories, icon-warranty, icon-connected-car, icon-dealer-network, icon-vehicle-purchase, icon-financing, icon-owner-loyalty

**Servizi finanziari (6 icone):**
icon-lead-nurturing, icon-account-dashboard, icon-product-recommendations, icon-churn-prevent, icon-life-stage

**Sanità (4 icone):**
icon-appuntamento-promemoria, icon-post-visita, icon-prevenzione-cura, icon-farmaco-aderenza

**Assicurazione (3 icone):**
icon-policy-refresh, icon-claim-process, icon-cross-sell

**Media e intrattenimento (3 icone):**
icon-new-content, icon-content-recommendations, icon-subscription-churn

**Telecomunicazioni (3 icone):**
icon-plan-optimization, icon-device-upgrade, icon-churn-prevent

**Viaggi e ospitalità (12 icone):**
icon-cart-andonment, icon-booking-reminders, icon-season-campaigns, icon-personalized-homepage, icon-high-intent, icon-post-booking-upsell, icon-win-back, icon-dynamic-itinerary, icon-recentsed, icon-group-booking, icon-exit-intent, icon-loyalty-program

**B2B (11 icone):**
icon-webinar-demo, icon-abm, icon-lead-scoring, icon-content-personalization, icon-event-registration, icon-trial-conversion, icon-customer-onboarding, icon-competitive-replace, icon-case-study, icon-contract-RENEW, icon-upsell-expand
