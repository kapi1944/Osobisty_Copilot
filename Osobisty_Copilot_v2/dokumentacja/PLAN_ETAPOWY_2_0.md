# Plan etapowy Osobisty Copilot v2.0

## Wspólne reguły
1. Wyłącznie istniejące repo. Przed każdą operacją `git status`, inwentaryzacja oraz kontrola nieśledzonych plików.
2. Nigdy nie kasować lokalnych zmian, nie zakładać architektury zanim sprawdzi się realny stan.
3. Nie otwierać niezamówionych zadań. Każdy etap ma implementację, demonstrację jednego przepływu i najwyżej istotne testy granic.
4. Gdy API jest niedostępne, zachować widoczny manualny fallback oraz stan `BRAK_DANYCH`.
5. Lokalnie, bez obowiązkowego serwera zewnętrznego, bez wymagania płatnego AI.

| Faza | Cel | Kryterium zatrzymania / ukończenia |
|---|---|---|
| 00–03 | Zachować poprzednie MVP: 50 produktów → ocena → 10 linków | Użytkownik może oddać raport mentorowi |
| 04 | Dane i dowody źródłowe | Oferta, słowo kluczowe, pomiar, typ źródła i timestamp przetrwają restart |
| 05 | Popyt Google Trends | Przynajmniej 1 fraza i 2 ramy czasowe dla 1 produktu, wykres i ograniczenia metryki; import ręczny działa |
| 06 | Skan rynku | Porównanie 3 ofert z min. 2 źródeł; klasy EXACT / SIMILAR / SUBSTITUTE, cena końcowa |
| 07 | Historia cen | Wykres zapisanych obserwacji, alert progu, odróżnienie danych Ceneo i własnych |
| 08 | Studio reklamowe | 8–12 różnych idei z szablonów, 3 pełne scenariusze na produkt, shot list i lista zakupów |
| 09 | Trendy kreatywne | Manualny trend ze źródłem i datą → dopasowanie do produktu → scenariusz z opisem dlaczego |
| 10 opcjonalnie | Lokalny model AI | Feature flag; bez Ollama aplikacja ma komplet działających funkcji |
| 11 później | Wyniki kampanii i feedback loop | Metryki i wnioski są powiązane z wariantami kreacji, brak fikcyjnych przewidywań |

## Dwie ścieżki pracy
- **Szybka:** gotowy katalog 50/10; jeden ręczny skan rynku dla TOP 10; szablony scenariuszy; najpierw odpowiedź mentorowi.
- **Badawcza:** automatyczne pobieranie ustandaryzowanych obserwacji z pewnością i śledzeniem źródeł; podejmować tylko gdy daje wyraźną oszczędność czasu.

## Kiedy zamawiać próbki
Dopiero po wstępnej selekcji oraz sprawdzeniu bezpieczeństwa, dostępności, całkowitego kosztu, ryzyka i zgodności wymagań mentor–sklep. Przy zakupie generować listę ujęć do nagrania po dostawie. Zakup i wysyłka nigdy automatycznie.

## Wskaźniki mierzące wartość systemu
- Czas od wklejenia linku do gotowej karty porównania.
- Odsetek obserwacji z datą i źródłem oraz jakością dopasowania.
- Odsetek zamkniętych zadań mentora, nie liczba funkcji aplikacji.
- Czas przygotowania 3 wariantów scenariusza reklamy.
- Liczba fałszywie dobranych produktów (dokładne/sobowtóry/substytuty).
