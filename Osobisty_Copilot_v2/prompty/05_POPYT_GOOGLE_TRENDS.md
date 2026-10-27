# PROMPT 05 — Popyt i Google Trends

Pracujesz WYŁĄCZNIE w istniejącym repo `C:\GitHub\Projects\Osobisty_Copilot`. Wykonaj jeden etap: **Google Trends i analiza popytu**.

## Dokumenty
Przeczytaj `README.md`, `dokumentacja/PLAN_ETAPOWY_2_0.md`, `dokumentacja/ANALITYK_RYNKU_2_0.md`, `dokumentacja/ADAPTERY_I_ZRODLA.md` i `dokumentacja/SCHEMAT_DANYCH_2_0.md`. Najpierw pokaż zwięzły status istniejącego repo: gałąź, zmiany, architektura i co z wcześniejszego planu już działa. Nie nadpisuj zmian użytkownika. Nie twórz nowej aplikacji.

## Zakres
1. Dodaj do karty produktu listę fraz PL/EN z rodzajem frazy, regionem i własnym okresem; łatwe dodawanie/edycja.
2. Dodaj dane serii popytu z metadanymi źródła, datami, zakresem, dokładną skalą, zapamiętanymi punktami i importem CSV/JSON.
3. Zapewnij własny wykres, wybór zakresów 90d/1r/5r jeśli dane istnieją, i wskazanie trendu/zmienności/sezonowości, bez udawania pełnej historii.
4. Zbuduj interfejs adaptera Trends. Sprawdź realnie wykonalność MIT `trendspyg` (`https://github.com/flack0x/trendspyg`, ostatnio zbadana wersja 1.9.0). Jeżeli stos i środowisko pasują, dodaj opcjonalny moduł pobrania danych. Jeśli nie — pozostaw import, ręczne wejście do Trends i status niedostępności; nie instaluj dużego stacku tylko dla tej funkcji.
5. Zapisuj: geo, timeframe, platformę Google property, source, fetchedAt i termsCompared. W analizie kilku fraz wyłącznie poprawne porównanie w jednym żądaniu lub wyraźne oznaczenie nieporównywalnych prób.
6. Zabezpiecz limity, błędy internetu, nieobsługiwany region, brak wyników i ponowne użycie istniejącego cache.

## Bardzo ważne
Google Trends daje wskaźnik względny 0–100, NIE wolumen wyszukiwania ani liczbę użytkowników. Nie wolno prezentować wieku/płci z Trends bez potwierdzonego źródła. Nie dopisuj wymyślonych pomiarów. Oficjalne Trends API jest alpha application-gated, nie zakładaj dostępu.

## Akceptacja
- Jeden produkt z 3 frazami i seriami historycznymi przetrwa restart.
- Wykres działa z importowanym CSV nawet bez internetu.
- Wszędzie wyświetlana jest nazwa źródła i typ miary.
- Usunięcie/edycja produktu nie pozostawia osieroconych danych.
- Zgłoś dokładnie, co zostało zweryfikowane z Google na żywo, a co jedynie ze statycznego importu.

Nie dodawaj skanera ofert ani studia rolek. Uruchom tylko adekwatne testy + build/lint jeżeli istnieją. Na końcu zmienione pliki, wynik, ograniczenia, następny krok. Nie commituj/pushuj bez zgody.
