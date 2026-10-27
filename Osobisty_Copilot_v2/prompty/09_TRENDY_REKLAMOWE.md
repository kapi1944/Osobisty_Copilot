# PROMPT 09 — Trendy marketingowe i wykorzystanie w rolkach

Kontynuuj istniejące repo `Osobisty_Copilot`, nie przepisuj już działających modułów. Najpierw stan repo, sprawdzenie postępu i dokumentacja `STUDIO_REKLAMOWE_2_0.md`, `ADAPTERY_I_ZRODLA.md` i `SCHEMAT_DANYCH_2_0.md`. Zakres to **most między trendami a scenariuszami**.

## Zakres
1. Rejestr trendów z pól: serwis, URL, region, daty odkrycia i ostatniej weryfikacji, mechanika trendu (hook, montaż, dźwięk, temat, format, społeczna sytuacja), grupa odbiorców i poziom pewności; status trendu aktywny/schyłkowy/nieznany.
2. Przygotuj wygodne przyciski do publicznych narzędzi TikTok Creative Center (Trends, Top Ads), Meta Ad Library, Pinterest Trends, Google Trends. Zapewnij ręczne zapisanie obserwacji. Nie reklamuj przycisków jako automatycznej analizy.
3. Dla wybranego trendu użytkownik wskazuje produkt i otrzymuje minimum 3 strategie wykorzystania: dosłowna mechanika z nowymi ujęciami (legalna i własna), luźna inspiracja, reinterpretacja dla innej grupy. Każda zawiera uzasadnienie dopasowania i podpowiedź terminowości.
4. Zmierz czy trend jest aktualny na podstawie faktycznego pola `lastVerifiedAt`, a nie domysłów modelu. Jeśli starszy niż konfigurowany próg, status `wymaga weryfikacji`.
5. W kartach zapisz prawa do wykorzystania audio: wolne/na daną platformę/do sprawdzenia/nie; nie zakładaj, że utwór trendujący jest dopuszczalny w reklamie i na wszystkich platformach.
6. Podłącz do wcześniej stworzonego kreatora briefów/ujęć i pozwól edytować wszystkie propozycje.
7. **Opcjonalnie**, za flagą `localAI`, integracja z Ollama po sprawdzeniu zasobów komputera oraz licencji konkretnego modelu. Model otrzymuje wyłącznie ustandaryzowany, odfiltrowany brief i dane źródłowe, a nie surowy kod HTML instrukcji z sieci; nie może wymyślać statystyk trendu ani faktów o produkcie. Bez Ollama szablony muszą działać.

## Kryteria
- Jeden ręcznie zaobserwowany trend z TikTok + źródło + data → trzy odmienne scenariusze wykorzystania dla jednego produktu.
- Brak aktywnego połączenia z internetem nie blokuje wcześniej zapisanych pomysłów.
- Trend przeterminowany wyświetla ostrzeżenie.
- Bez lokalnego modelu AI wszystkie główne akcje nadal działają.
- Wynik testów, lista zmienionych plików, uzasadnienie decyzji o zależnościach i ryzyka.
