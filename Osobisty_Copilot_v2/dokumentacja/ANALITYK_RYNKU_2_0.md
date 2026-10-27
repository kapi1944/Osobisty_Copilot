# Specyfikacja Analityka Rynku

## 1. Badanie popytu
Dla każdego produktu utrzymuj 3–8 wariantów fraz (PL, EN, nazwa potoczna, nazwa problemu rozwiązywanego przez produkt, nazwy kategorii) oraz typ frazy (`produkt`, `zastosowanie`, `problem`, `marka`). Czas: 7 dni, 90 dni, 12 miesięcy, 5 lat (gdy źródło wspiera). Geo: Polska jako domyślny; osobno inne rynki. Osobno Google Web, YouTube, Shopping, jeżeli dane są dostępne i porównywalne.

Wyniki: seria czasowa, kierunek zmian (np. ostatnie 90 dni wobec porównywalnych 90 dni wcześniej), sezonowość (przez porównanie analogicznych okresów), zainteresowanie geograficzne, zapytania powiązane, 'breakout'. Nie wyciągać wniosku o demografii z Google Trends, gdy jej nie udostępnia.

**Zasada liczb:** publiczny Trends to indeks relatywny 0–100, nie liczba wyszukiwań ani liczba unikalnych osób. Zapisywać typ metryki `relative_search_interest`. Jeśli użytkownik osobno poda dane z Keyword Planner, zapisywać `estimated_monthly_searches` i nie mieszać skali. Miarę Google Trends z porównania wielu haseł opisywać wraz z listą fraz, bo jej normalizacja jest inna niż dla pojedynczego hasła.

**Wykrywanie:** niewystarczający wolumen, gwałtowny jednorazowy wzrost, możliwa sezonowość, trend podtrzymany, obszar niepewności. Nie nazywać każdego wzrostu trendem sprzedażowym.

## 2. Skan rynku
Katalog źródeł: Ceneo, Allegro, polskie sklepy, AliExpress, Amazon, eBay — tylko dopuszczone ścieżki pobierania/odczytu. Pierwsza wersja: zapytania prowadzące do wyszukiwarki i linki przekazane ręcznie, **nie** masowy scraper.

### Matching
1. `EXACT`: zgodny zweryfikowany EAN/GTIN/model i kluczowe parametry — najwyższa wiarygodność.
2. `PROBABLE_EXACT`: ten sam model i komplet cech, bez potwierdzonego GTIN — wymagane ręczne potwierdzenie.
3. `SIMILAR`: ta sama funkcja, lecz inne parametry/jakość/marka.
4. `SUBSTITUTE`: rozwiązuje ten sam problem innym sposobem.
5. `UNRELATED`: odrzucić z porównania.

Nie mieszać produktów bezprzewodowych z przewodowymi, innych wymiarów, zestawów 2/4 szt. oraz modeli o innych funkcjach jako `EXACT`. Ceneo może agregować wiele ofert dla jednego produktu, co nie znaczy, że są różnymi konkurującymi produktami. Zapisuj `liczba sklepów` i `liczba odrębnych modeli` osobno.

Dla każdej oferty: `product_id`, URL, merchant, marketplace, tytuł, waluta, cena brutto, cena transportu, finalny koszt dla klienta w Polsce, dostępność, wersja, data obserwacji, źródło, matching, legalność odczytu oraz typ ceny (`promo/regular/unknown`).

Statystyki EXACT: min/median/max, rozrzut, liczba sprzedawców, wrażliwość na koszt dostawy. SIMILAR i SUBSTITUTE pokazywać w osobnych grupach. Raport mówi `sprawdzono N ofert` zamiast `znaleziono wszystkie oferty na rynku`.

## 3. Historia cen
- `source_observed`: obserwacja własna, historyczna od chwili rozpoczęcia monitorowania.
- `source_imported`: użytkownik zaimportował tabelę/CSV lub ręcznie przepisał dane z usługi.
- `source_external_reference`: odnośnik do wykresu Ceneo, brak roszczenia do posiadania punktów szeregu.
- Dane z Ceneo: wymagają zalogowania; opis marketingowy Ceneo niespójnie mówi o 6 miesiącach oraz roku; nie zakładać stałego horyzontu lub pełnej rozdzielczości. Własne archiwum **nie odtwarza** przeszłości sprzed rozpoczęcia obserwacji.
- Wykresy 7d/30d/90d/180d/1r tam, gdzie istnieją dane, wraz z zakresem pokrycia.
- Alert typu 'cena pod progiem' porównuje konkretne oferty/dopasowania i sposób liczenia dostawy, a nie samą wartość na karcie produktu.

## 4. Ekonomia
`landed_cost = zakup + wysyłka + koszty importu + opłaty i inne koszty przewidziane w danym scenariuszu`; `contribution_before_ads = cena_klienta - landed_cost - koszt_prowizji - koszt_płatności - rezerwa_zwrotów - pozostałe jednostkowe`. `break_even_CPA` (maksymalny koszt pozyskania klienta przed zerowym wynikiem) = contribution_before_ads. Nie utożsamiać go z przewidywanym rzeczywistym CPA ani z zyskiem netto; prawidłowo odróżnić podatek VAT i sposób fakturowania od kosztu. Pozostawić pola nieznane, zamiast zakładać zerowe.

## 5. Wynik i uzasadnienie
Podział: (A) zgodność/regulacje i podstawowy sens ekonomiczny jako warunki dyskwalifikujące; (B) ocena jakościowa WOW, problemu, unikatowości, demonstracji na filmie; (C) dowody rynkowe popyt, ceny, konkurencja; (D) `confidence_score`, liczony osobno od potencjału. Gdy brakuje danych nie obniżać mechanicznie wyniku do zera; wyraźnie wskazać `nierozstrzygnięte`. Ranking służy decyzji użytkownika, nie jest samodzielną prawdą rynkową.
