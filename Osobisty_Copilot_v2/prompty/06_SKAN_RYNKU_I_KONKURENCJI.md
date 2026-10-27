# PROMPT 06 — Skan rynku i konkurencji

Kontynuuj istniejący projekt Osobisty Copilot; nie twórz projektu od zera. Przeczytaj `dokumentacja/ANALITYK_RYNKU_2_0.md`, `dokumentacja/SCHEMAT_DANYCH_2_0.md` i `dokumentacja/ADAPTERY_I_ZRODLA.md`. Zbadaj zastany repo, zachowaj zmiany lokalne. Zakres WYŁĄCZNIE skan rynku.

## Wymagania
1. Dla produktu wygeneruj zestaw wyrażeń do wyszukania (PL/EN, model, GTIN, synonimy) oraz linki do wyszukiwań Ceneo, Allegro, AliExpress i innych źródeł dopuszczonych przez dokumentację — bez niestabilnego scrapowania w MVP.
2. Pozwól wkleić ofertę, zapisać platformę, sprzedawcę, walutę, wariant/model, cenę produktu, przesyłkę, dostępność, czas obserwacji, źródło, etykiety, notatkę.
3. Dodaj porównanie EXACT / PROBABLE_EXACT / SIMILAR / SUBSTITUTE / UNRELATED. Rozpocznij od ręcznego oznaczania; tylko dobrze uzasadnione sugestie dopasowania (GTIN/model/specyfikacja), nigdy fałszywa pewność na podstawie podobieństwa nazwy.
4. Rozdziel statystyki IDENTYCZNYCH produktów i SUBSTYTUTÓW. Pokaż min/median/max kosztu końcowego dostarczonego do PL, liczbę ofert, liczbę sprzedawców, pokrycie badania, datę skanu.
5. Dodaj raport "Gdzie i po ile konkurencja sprzedaje ten produkt". Raport zawiera linki i datę oraz dokładne kryterium dopasowania.
6. Nie zakładaj dostępności Allegro `GET /offers/listing` (dostęp dla zweryfikowanych aplikacji), ani publicznego API Ceneo. Nie omijaj CAPTCHA/antybotów i nie zapisuj haseł.

## Warunki akceptacji
- Zapisz 3 oferty od co najmniej 2 sprzedawców, w tym 1 świadomie oznaczoną jako SUBSTITUTION/SIMILAR; jej ceny NIE wolno doliczyć do min/median/max EXACT.
- Ten sam SKU w dwóch sklepach powinien być widoczny jako 2 oferty 1 modelu.
- Różne koszty dostawy uwzględnione w porównaniu końcowym.
- Poprawnie działa import/export i restart.
- Brak źródeł jest jawnie pokazany, nie jako `0 konkurentów`.

Nie buduj robota do automatycznego pozyskiwania tysięcy ofert. Raport końcowy + ograniczenia, bez automatycznego commita/pusha.
