# Osobisty Copilot — pakiet projektu v2.0
**Opracowanie: 19.10.2026**  
Repo lokalne użytkownika: `C:\GitHub\Projects\Osobisty_Copilot` (niezmodyfikowane przez ten pakiet).

## Definicja produktu
**Osobisty Copilot** = osobiste, lokalne centrum decyzji dla zadań mentora TakeDrop. Pierwszym celem pozostaje **50 kandydatów → TOP 10 → raport z linkami AliExpress**; rozszerzenie v2 dodaje dwa oddzielne obszary:

1. **Analityk rynku:** popyt, wyszukiwania, porównanie ofert i substytutów, historia cen, rentowność, ryzyka i dowody źródłowe.
2. **Studio reklamowe:** trendy formatów/hashtagów/reklam, pomysły na rolki, scenariusze i ujęcia, plan zakupu próbki, publikacja i wnioski z wyników.

## Kolejność prac i powstrzymanie rozrostu
- Zachować stary plan 00–03: bez działającej listy produktów i selekcji TOP 10 **nie rozbudowywać** modułów.
- v2 etap 04: schemat danych i źródła/proweniencja.
- v2 etap 05: Google Trends / trendspyg z importem ręcznym jako awaryjnym.
- v2 etap 06: porównanie ofert po linkach, z bezpieczną półautomatyczną identyfikacją produktów.
- v2 etap 07: historia cen i obserwacje, z importem z Ceneo tylko po potwierdzeniu dozwolonej ścieżki.
- v2 etap 08: studio scenariuszy i szablony bez AI.
- v2 etap 09: łączenie trendów marketingowych z produktami; opcjonalne lokalne AI.

## Główne granice
- Żadnych płatnych API, tworzenia kont usługowych bez potrzeby, bypassu CAPTCHA/antybotów, przechowywania loginu i hasła Ceneo, automatycznego kopiowania cudzych reklam.
- **Google Trends** podaje względny indeks zainteresowania, NIE liczbę osób ani dokładną liczbę wyszukań.
- **Ceneo** udostępnia historię zalogowanym użytkownikom; brak potwierdzonego ogólnodostępnego API do jej odczytu przez Copilota.
- Wyniki badań muszą mieć link, pobraną datę, walutę, źródło i etykietę pewności; brak danych ≠ zero.
- Dane osób i zachowania konkretnych użytkowników nie mogą być wywnioskowane z zagregowanych trendów.
- Jeśli istniejący repo ma działający React/TS, NIE przepisywać projektu na inny stack. Adapter `trendspyg` może być małą lokalną usługą Python; najpierw wykonać analizę integracji.

## Dokumenty
- `dokumentacja/PLAN_ETAPOWY_2_0.md` — kolejność, bramki, skróty czasowe.
- `dokumentacja/ANALITYK_RYNKU_2_0.md` — metodologie trendów i porównywarki.
- `dokumentacja/STUDIO_REKLAMOWE_2_0.md` — taksonomia filmów, plan nagrań, analytics.
- `dokumentacja/ADAPTERY_I_ZRODLA.md` — aktualny research i ograniczenia dostępu.
- `dokumentacja/SCHEMAT_DANYCH_2_0.md` — encje i zasady wiarygodności.
- `prompty/05_...` do `prompty/09_...` — osobne zadania dla Codexa.
- `prompty/00_...` do `prompty/04_...` — zachowane z poprzedniej wersji.

## Realizacja
Po wypakowaniu skopiować pliki dokumentacji do istniejącego repo i uruchamiać prompty **pojedynczo**, nie wszystkie naraz. Przed implementacją sprawdzić stan repo i zachować lokalne zmiany.
