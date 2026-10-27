# Schemat danych analizy i reklam v2.0

## Encje minimalne
```
Product(id, title, sourceUrl, category, purchasePrice, currency, createdAt, mentorTaskId)
Keyword(id, productId, text, language, intent, region, searchProperty)
TrendSeries(id, keywordId, source, scaleType, region, periodStart, periodEnd, termsCompared, fetchedAt, status)
TrendPoint(id, trendSeriesId, measuredAt, value, isPartial)
MarketScan(id, productId, scope, startedAt, finishedAt, searchQueries, coverageNote, status)
MarketOffer(id, marketScanId, productId, url, platform, shop, title, gtin, model, attrsJson, matchClass, matchConfidence, price, deliveryCost, totalCost, currency, observedAt, status)
PriceObservation(id, marketOfferId, observedAt, value, currency, originType, provenanceUrl, importMethod, confidence)
SourceEvidence(id, entityKind, entityId, sourceName, sourceUrl, observedAt, provenanceType, quality, note)
ScoreRecord(id, productId, formulaVersion, potentialScore, confidenceScore, disqualifier, missingDimensions, reasoning, calculatedAt)
CreativeTrend(id, platform, url, format, narrativeMechanic, soundLicenseState, region, noticedAt, lastVerifiedAt, lifecycle, evidenceId)
CreativeBrief(id, productId, platform, audienceHypothesis, goal, lengthSeconds, productBenefits, forbiddenClaims, createdAt)
VideoIdea(id, creativeBriefId, creativeTrendIdNullable, angle, hook, plot, score, rationale, status)
StoryboardShot(id, videoIdeaId, order, durationSeconds, action, visual, onScreenText, voiceOver, sfx)
SampleOrder(id, productId, orderDate, actualCost, expectedArrival, receivedAt, status, trackingUrlOptional)
CreativeResult(id, videoIdeaId, platform, publishedAt, measurementStart, measurementEnd, metricSchemaVersion, source, rawMetricsJson)
```

## Rozdzielenie prawdziwych danych i sugestii
`originType` ∈ `API_OFFICIAL`, `PUBLIC_PAGE_USER_REVIEWED`, `MANUAL`, `USER_IMPORT`, `MODEL_GENERATED_HYPOTHESIS`.
`quality` ∈ `CONFIRMED`, `POSSIBLE`, `UNKNOWN`, `FAILED`.
**Nigdy** nie wstawiać generowanych przez model danych do tabel obserwacji z rynku; trzymać je w hipotezach i oszacowaniach.

## Obowiązkowe pola raportu
- Źródło i URL; czas pozyskania; dzień obserwacji ceny; region i waluta.
- Informacja czy to cena brutto i czy koszt przesyłki wliczony.
- Status dopasowania i poziom pokrycia rynku.
- Źródło trendu i znana definicja skali.
- Czy trend jest aktualny czy historyczny, data ostatniej weryfikacji.
- Składnik oceny potencjału oddzielny od wiarygodności.

## Reużycie
Jeśli repo ma już encje Product lub Task — rozszerzyć je przez migracje addytywne, nie duplikować ich w nowym schemacie. Adapter danych powinien być wymienny bez zmiany UI.
