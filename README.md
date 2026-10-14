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

## Kalkulatory

- **Moc i prąd – układ 3-fazowy:** `P = √3 · U · I · cos φ`, `I = P / (√3 · U · cos φ)`.
  Napięcie 380 / 400 / 440 V. Wpisz moc albo prąd, a druga wartość obliczy się sama. Dodatkowo
  pokazuje moc pozorną S i bierną Q.
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

## Aktualizacja aplikacji

Po zmianie plików wgraj je ponownie do repozytorium na GitHubie i w pliku `sw.js` podnieś numer
wersji (np. `el_fuszka-v1.1.3` → `el_fuszka-v1.1.4`). Telefon pobierze nową wersję przy następnym uruchomieniu
z dostępem do internetu. Dane nie zostaną usunięte.
