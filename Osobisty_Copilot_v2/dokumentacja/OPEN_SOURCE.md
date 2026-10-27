# Gotowce i ocena ponownego użycia (08.10.2026)

| Rozwiązanie | Link | Model licencji / ograniczenie | Przydatność | Decyzja |
|---|---|---|---|---|
| Streamlit | https://github.com/streamlit/streamlit | Apache-2.0 | lokalny szybki panel | TAK, gdy repo puste |
| Baserow | https://github.com/baserow/baserow | open-core, część MIT | gotowa baza i widoki | ALTERNATYWA, ale więcej uruchamiania |
| changedetection.io | https://github.com/dgtlmoon/changedetection.io | sprawdź licencję konkretnej wersji i warunki | późniejsze monitorowanie zmian stron | PÓŹNIEJ, raczej jako osobna usługa |
| PriceStalker | https://github.com/mikeknight85/PriceStalker | MIT według repo | historia cen / selektory | INSPIRACJA, nie do MVP |
| Ollama | https://github.com/ollama/ollama | MIT; licencje modeli osobno | lokalne sugestie AI bez opłat za tokeny | OPCJONALNIE w etapie 4 |
| Activepieces | https://github.com/activepieces/activepieces | rdzeń MIT, funkcje EE komercyjne | automatyzacje | NIE na start |
| n8n | https://github.com/n8n-io/n8n | source-available, nie klasyczne OSI open source | orkiestracja | NIE na start |
| Bright Data AliExpress tracker | https://github.com/luminati-io/aliexpress-price-tracker | kod klienta do płatnej usługi | pobór danych | ODRZUCIĆ: odpłatne API |
| OmkarCloud AliExpress Scraper | https://github.com/omkarcloud/aliexpress-scraper | bezpłatny limit, API zewnętrzne | pobór danych | NIE spełnia warunku bez zależności od usługi |

Zasada: najpierw instalować utrzymywane biblioteki i integrować API, a nie kopiować obcy kod. Przy kopiowaniu zachować informacje o autorze, licencję, oznaczyć wersję, zrobić przegląd bezpieczeństwa. Nie omijać CAPTCHA, logowania lub zabezpieczeń i nie zakładać, że scraping AliExpress lub TikToka jest zawsze dozwolony. Preferować wklejanie linków ręcznie.
