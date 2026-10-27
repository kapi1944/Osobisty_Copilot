# Źródła, adaptery, ograniczenia — stan 19.10.2026

| Źródło / narzędzie | Dostęp i wartość | Proponowana integracja | Ryzyko |
|---|---|---|---|
| Google Trends Explore | publiczny web, indeks 0–100 | Python `trendspyg` MIT w opcjonalnym adapterze | nieoficjalna metoda, może ulec awarii/limitom |
| Google Trends API Alpha | oficjalne, ograniczony dostęp | adapter w przyszłości tylko po przyznaniu dostępu | brak gwarantowanej dostępności dla każdego |
| Google Ads Keyword Planner | szacowane wyszukiwania miesięczne w określonych warunkach konta | import własnych danych przez CSV | zaokrąglenia, dostęp i szczegółowość zależne od konta |
| Ceneo | darmowe wykresy cen po zalogowaniu | otwieranie produktu + dopuszczony import danych ręcznie lub udostępnionego eksportu | brak potwierdzonego otwartego API; nie przechowuj loginów/cookies |
| Allegro | publiczne oferty w UI | otwieranie wyszukiwarki / ręczne dodanie ofert | listing API wymaga weryfikacji aplikacji; nie zakładaj dostępu |
| eBay Browse API | wyszukiwanie po frazie, GTIN, obrazie | opcjonalny adapter z tokenem aplikacji | dostęp produkcyjny do części Buy APIs może być ograniczony |
| changedetection.io | monitorowanie zmiany treści/cen, self-hosted, REST API | jako **osobna usługa**, nie kopiować kodu w ciemno | stabilność selektorów, prawa do strony i warunki licencji projektu |
| trendspyg 1.9.0 | darmowa biblioteka Trends (MIT), aktywna w październiku 2026 | połączenie Python, cache/archiwum | API Google poza kontrolą autorów; Explore to droga nieoficjalna |
| TikTok Creative Center Trends | hashtag, region, branża, trendline/audiences zależne od sesji | research wspomagany przez użytkownika + wpis trendu | brak ogólnie dostępnego API do automatycznego pobierania całości |
| TikTok Creative Center Top Ads | inspiracje reklam z filtrami rynku, branży, formatu | linki i ręczne metadane | część danych po loginie i tylko reklamy udostępnione za zgodą reklamodawców |
| Meta Ad Library | reklamy oraz wyszukiwarka | wygodne linki/brief porównawczy | nie pokazuje pełnej sprzedaży i skuteczności reklam konkurencji |
| Pinterest Trends | do 2 lat trendów zależnie od rynku, wiek/płeć gdy dostępne | link, notatka, eksport tylko jeżeli wspierany | dostępność zależna od regionu i konta, skala względna |
| YouTube Data API | informacje o filmach, limit zapytań | adapter na później | nie udostępnia demografii cudzych kanałów; własna Analytics API oddzielna |
| Ollama | local LLM, program MIT | **opcjonalnie** scenariusze, podsumowania źródeł | potrzebny RAM/CPU/GPU; licencja modelu oddzielnie |
| faster-whisper | transkrypcja lokalna, MIT | opcjonalnie napisy z własnych nagrań | obciążenie sprzętu i modele weryfikować oddzielnie |
| Playwright | automatyzacja przeglądarki, Apache-2.0 | testy / dozwolone półautomatyczne odczyty | nie usprawiedliwia obchodzenia zabezpieczeń i ToS |

## Oficjalne i źródłowe linki
- Google Trends alpha: https://developers.google.com/search/apis/trends
- Skale Trends: https://support.google.com/trends/answer/4365533
- `trendspyg`: https://github.com/flack0x/trendspyg i https://pypi.org/project/trendspyg/
- Ceneo historia cen: https://info.ceneo.pl/historia-cen (opis zawiera sprzeczną informację o 6 miesiącach i roku)
- Keyword Planner: https://support.google.com/google-ads/answer/3022575?hl=pl
- TikTok Trends: https://ads.tiktok.com/resources/help/article/how-to-use-trends
- TikTok Top Ads: https://ads.tiktok.com/business/creativecenter/inspiration/topads/pc/en?region=PL
- TikTok muzyka komercyjna: https://ads.tiktok.com/business/creativecenter/music/pc/en
- Meta Ad Library: https://pl-pl.facebook.com/ads/library/
- Pinterest: https://help.pinterest.com/en/business/article/pinterest-trends
- eBay: https://developer.ebay.com/develop/api/buy
- Allegro: https://developer.allegro.pl/documentation
- `changedetection.io`: https://github.com/dgtlmoon/changedetection.io
- `Playwright`: https://github.com/microsoft/playwright
- `faster-whisper`: https://github.com/SYSTRAN/faster-whisper

## Kontrakt adaptera (przykład niezależny od języka)
- `getCapabilities(): { manualImport, liveFetch, historyAvailable, requiresLogin, quota, limitations }`
- `getObservations(productId, source, start, end): Observation[]`
- `buildSearchUrl(query, region): string` (najbezpieczniejszy tryb dla Ceneo/Allegro)
- `saveUserObservation(payload): Observation`
- Gdy adapter nie działa: `DATA_UNAVAILABLE` + krótka przyczyna + link do manualnej ścieżki. Nigdy wyciszony pusty wykres.

## Zabezpieczenia
Nie przechowywać haseł, nie omijać blokad, CAPTCHA i paywalli, nie masowo indeksować serwisów. Zbieranie informacji w zewnętrznych usługach musi być zgodne z ich aktualnymi warunkami. Nie kopiować cudzych filmów, fotografii ani treści marketingowych do publikacji bez stosownego prawa.
