# PROMPT 07 — Historia cen, Ceneo i obserwacje

Pracuj w istniejącym repo. Sprawdź stan projektu, zachowaj lokalne zmiany, stosuj dokumenty `dokumentacja/ANALITYK_RYNKU_2_0.md` oraz `dokumentacja/ADAPTERY_I_ZRODLA.md`. Ten etap ma dodać sensowną historię cen, a nie budować własne Ceneo.

## Implementacja
1. Dodaj `PriceObservation` powiązane z ofertą i produktem: data, źródło, kwota, waluta, cena z/bez transportu, metoda odczytu/importu, link źródłowy.
2. Historia wartości z wykresem i wyborami zakresu; mediana, minimum, maksimum, cena ostatnia, ostrzeżenie jeśli mało danych. Nie generuj punktów z braku obserwacji.
3. Udostępnij link do Ceneo i pole `odczyt z historii cen Ceneo` jako obserwację przekazaną świadomie przez użytkownika; dozwolony import CSV gdy istnieje, ręczne przepisywanie punktów jako pełnoprawny fallback.
4. Nie przechowuj loginu/hasła Ceneo, nie eksportuj cookies, nie próbuj zdalnego odczytu sesji zalogowanej. Jeśli rozważysz rozszerzenie przeglądarki obsługiwane kliknięciem użytkownika, opisz je jako OSOBNY, przyszły spike wraz z oceną uprawnień, regulaminu i dozwolonej integracji — bez implementacji teraz.
5. Własny monitoring zmian od momentu pierwszej obserwacji jako opcja; adapter `changedetection.io` oceniaj jako osobny proces / usługę, nie kopiowanie kodu do projektu. Alert tylko tam, gdzie monitorowanie legalne i technicznie trwałe.
6. Oddziel historyczny wykres Ceneo dostępny w zewnętrznej usłudze od prawdziwego, lokalnego szeregu liczbowego. Link do wykresu NIE jest punktami cenowymi.

## Kryteria
- 4 realnie wpisane obserwacje tworzą poprawny wykres.
- Zapisane ceny z różnych walut nie są agregowane bez jawnej metody przeliczenia i daty kursu.
- Dla jednej oferty w dwóch wariantach dostawy wyniki nie są bezwiednie porównywane.
- Działa offline; pokazuje braki danych i ślady źródłowe.
- Żadnych zmian poza zakresem, minimalne testy i raport.
