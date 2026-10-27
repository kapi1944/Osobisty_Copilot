# Model danych MVP

Tabela `products`:
- `id` UUID/INTEGER PK
- `source_url` oryginalny pełny link, obowiązkowy; `canonical_url` po bezpiecznej normalizacji; `platform` (ALIEXPRESS/OTHER)
- `title`, `category`, `music_related` bool, `notes`, `problem_solved`, `wow_reason`, `target_customer`
- `price_amount`, `price_currency`, `shipping_amount`, `shipping_currency`, `observed_at`, `retail_price_pln`
- `score_wow`, `score_problem`, `score_novelty`, `score_demonstration`, `score_competition`, `score_risk` — INT 0..5 lub NULL; brak danych ≠ zero
- `quality_risk`, `delivery_risk`, `compliance_risk`, `seller_evidence`, `source_evidence`
- `shortlisted` bool, `status` enum NEW/REVIEWED/REJECTED/SHORTLISTED/SENT
- `created_at`, `updated_at`

`price_snapshots`: id, product_id, observed_at, amount, currency, shipping, origin, verification (MANUAL/AUTO_UNVERIFIED/CONFIRMED).
`mentor_tasks`: id, origin_message_id, instruction, status, date, evidence.
`decisions`: id, product_id, timestamp, type, note, previous_value, new_value.

**Zasady:** brak nadpisania oryginalnego URL; brak wyciągania ID, jeśli pewność niska; unikaty dla kanonicznych linków z możliwością ręcznego override; wszystkie zmiany rankingowe odwracalne; eksport CSV w UTF-8 BOM dla Excel PL. Kopia SQLite przed importem.

## Punktacja v1
Dodatnio: WOW 25%, rozwiązanie problemu 25%, nowość 15%, demonstracyjność 15%, konkurencja (korzystna = 5) 10%, ryzyko (niskie = 5) 10%.
Wynik obliczaj tylko gdy wszystkie 6 pól jest wypełnione; inaczej `BRAK_OCENY`. Sortuj bez narzucania decyzji: człowiek ostatecznie oznacza 10.

## Budżet jednostkowy
`koszt_dostarczony_PLN = cena_towaru_PLN + wysyłka_PLN + należne_opłaty_i_podatki_PLN`
`wkład_przed_reklamą = cena_sprzedaży_brutto - podatki_od_sprzedaży - koszt_dostarczony - opłaty_transakcyjne - rezerwa_na_zwroty - inne_koszty_zmienne`
`maks_CAC = wkład_przed_reklamą - docelowy_wkład_po_reklamie`
W razie braku dowolnej wielkości wyświetlić wynik jako niepełny szacunek, nie jako faktyczną marżę.
