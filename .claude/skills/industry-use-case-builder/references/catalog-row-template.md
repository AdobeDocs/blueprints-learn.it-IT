---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---
# Modello righe catalogo casi d’uso

## Formato riga

Ogni riga nella tabella del catalogo dei casi d’uso segue esattamente questo formato:

```
| <img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40"> | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

### Riga senza icona (da utilizzare quando l’icona non è ancora disponibile)

```
| | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

## Riferimento campo

| Campo | Formato | Esempio |
| --- | --- | --- |
| settore | nome directory kebab-case | retail, servizi finanziari, viaggi, ospitalità |
| kebab-name | kebab: nome del caso d’uso per l’icona | carrello abbandonato, piombo |
| Testo alternativo | Tutte iniziali maiuscole, breve | Carrello abbandonato, sviluppo di lead |
| header-anchor | kebab-case dell’intestazione ## in panoramica | abbandonato-carrello-e-mail-ripristino |
| Scadenza + Tipo | Sintassi del badge | `[!BADGE Foundational]{type=Neutral}`, `[!BADGE Emerging]{type=Informative}`, `[!BADGE Advanced]{type=Caution}` |

## Marcatori scheda settore nel catalogo

Il file di catalogo utilizza questa struttura a schede:

- `>[!TAB Retail]`
- `>[!TAB Automotive]`
- `>[!TAB Financial Services]`
- `>[!TAB Healthcare]`
- `>[!TAB Insurance]`
- `>[!TAB Media & Entertainment]`
- `>[!TAB Telecommunications]`
- `>[!TAB Travel & Hospitality]`
- `>[!TAB B2B]`

## Ordinamento nelle schede

Le righe sono ordinate in base al livello di scadenza:

1. **Fondamentale** righe per prime (tipo=neutro)
2. **Emergente** righe al secondo (tipo=Informativo)
3. **Avanzate** ultime righe (type=Caution)

All’interno dello stesso livello di maturità, aggiungi nuove righe alla fine del gruppo.
