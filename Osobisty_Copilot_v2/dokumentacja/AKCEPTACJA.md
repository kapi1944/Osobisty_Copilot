# Testy akceptacyjne (minimalne)

1. Dodanie 50 unikalnych produktów ze źródłem; po restarcie 50 pozostaje.
2. Duplikat URL jest ostrzegany; oryginał zachowany; link z parametrami nie jest niszczony.
3. Brak ceny lub oceny nie jest traktowany jako 0.
4. Filtr `bez oceny` pokazuje produkty wymagające decyzji.
5. Ranking nie wybiera automatycznie 10 bez zgody użytkownika.
6. Eksport/import polskich znaków i 50 rekordów działa bez strat.
7. Paczka do mentora zawiera dokładnie 10 różnych URL AliExpress, które użytkownik ręcznie zatwierdził.
8. Nie ma wysyłki e-mail bez wyraźnej czynności użytkownika.
9. Żadne źródło danych nie jest opisane jako „sprawdzone na żywo”, jeśli to wpis ręczny/stary snapshot.
10. App daje się uruchomić lokalnie prostą komendą i posiada kopię zapasową danych.
