# el_Fuszka – notatnik projektów i wycen

Aplikacja na telefon (PWA) do prowadzenia projektów usług elektrycznych i ich wyceny.
Działa bez internetu, dane są zapisane w telefonie.

https://gwozdziu123.github.io/el_Fuszka/

## Pliki

| Plik | Do czego |
|---|---|
| `index.html` | cała aplikacja |
| `manifest.webmanifest` | nazwa i ikona przy instalacji na telefonie |
| `sw.js` | działanie offline |
| `icons/` | ikony aplikacji |


## Instalacja na telefonie

- **Android (Chrome):** otwórz adres → menu ⋮ → **Zainstaluj aplikację** / **Dodaj do ekranu głównego**.
- **iPhone (Safari):** otwórz adres → przycisk Udostępnij → **Do ekranu początkowego**.

Po instalacji aplikacja otwiera się z ikony jak zwykła aplikacja i działa offline.

## Pierwsze uruchomienie

1. **Ustawienia** → wpisz stawkę za km i stawkę godzinową → **Zapisz stawki**.
2. **Katalog** → dodaj części, których często używasz (można też dodawać je w trakcie pracy z projektu).
3. **Projekty** → **Nowy projekt**.

## Zasady obliczeń

- **Przyjazd** = odległość × 2 (tam i z powrotem) × stawka za km
- **Robocizna** = czas pracy × stawka godzinowa (domyślnie dziś, 4 h)
- **Część** = cena × ilość
- Cena pozycji zapisuje się w chwili dodania. Zmiana stawek lub cen w katalogu nie zmienia
  starych wycen. Projekt można przeliczyć według aktualnych stawek z menu ⋮ w projekcie.

## Import / eksport katalogu części

W zakładce **Katalog** → menu **⋮** u góry:
- **Eksportuj do pliku CSV** – zapisuje katalog jako `el_fuszka-katalog-RRRR-MM-DD.csv` (otwiera się w Excelu).
  Przy pustym katalogu zapisuje pusty wzór do uzupełnienia.
- **Udostępnij katalog** – wysyła plik np. mailem lub na Dysk Google.
- **Importuj z pliku** – wczytuje CSV lub JSON (także pełną kopię zapasową – brany jest tylko katalog).
  Do wyboru: *dodaj nowe i zaktualizuj ceny* albo *zastąp cały katalog*.

Format CSV: dwie kolumny `Nazwa;Cena`, pierwszy wiersz to nagłówek, cena z przecinkiem, np.:

```
Nazwa;Cena
Wyłącznik nadprądowy B16;18,50
Przewód YDY 3x2,5;3,20
```

Części dodane już do projektów nie zmieniają się przy imporcie.

## Narzędzia

Zakładka **Narzędzia** (dolny pasek) zawiera kalkulatory oraz **Uprawnienia SEP**.

### Uprawnienia SEP

Miejsce na świadectwa kwalifikacyjne. **Nowe uprawnienie** → tytuł (np. „SEP E1 – eksploatacja do 1 kV”)
i opis (np. nr świadectwa, zakres, data ważności). Na liście tytuł jest pogrubiony, opis pod spodem.
Kliknięcie uprawnienia pozwala je edytować lub usunąć. Uprawnienia są zapisywane w kopii zapasowej.

### Kalkulatory

- **Moc i prąd 1 oraz 3 fazy:** napięcie 230 V (1-faz.) lub 400 V (3-faz.).
  3-faz.: `P = √3 · U · I · cos φ`, `I = P / (√3 · U · cos φ)`; 1-faz.: `P = U · I · cos φ`, `I = P / (U · cos φ)`.
  Wpisz moc albo prąd, a druga wartość obliczy się sama. Dodatkowo pokazuje moc pozorną S i bierną Q.
- **Spadek napięcia i prąd w przewodzie:** napięcie 12 V DC / 24 V DC / 230 V (1-faz.) / 400 V (3-faz.),
  moc lub prąd, cos φ, przekrój, długość trasy, Cu (γ = 56) / Al (γ = 34). Dopuszczalny spadek napięcia: stałe 2%.
  - 3-faz.: `ΔU = √3 · L · I · cos φ / (γ · S)`, 1-faz.: `ΔU = 2 · L · I · cos φ / (γ · S)`, DC: `ΔU = 2 · L · I / (γ · S)`
  - Pokazuje też straty mocy, orientacyjną obciążalność Iz (PN-HD 60364-5-52, metoda C, PVC 70°C, 30°C)
    i najmniejszy przekrój spełniający warunek spadku i obciążalności.
  - Pominięta reaktancja przewodu – wynik dokładny dla przekrojów do ok. 50 mm².

Kalkulatory zapamiętują ostatnio wpisane wartości (nie trafiają do kopii zapasowej).

## Kopia zapasowa – ważne

Dane są tylko w telefonie (w pamięci przeglądarki). Odinstalowanie aplikacji, wyczyszczenie
danych przeglądarki albo zmiana telefonu = utrata danych.
Regularnie rób kopię: **Ustawienia → Udostępnij kopię** (np. na Dysk Google) lub **Zapisz kopię do pliku**.
Na nowym telefonie: **Ustawienia → Wczytaj kopię z pliku**.

