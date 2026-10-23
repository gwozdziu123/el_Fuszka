# el_Fuszka – notatnik projektów i wycen

Aplikacja na telefon (PWA) do prowadzenia projektów usług elektrycznych i ich wyceny.
Działa bez internetu, dane są zapisane w telefonie.

## Pliki

| Plik | Do czego |
|---|---|
| `index.html` | cała aplikacja |
| `manifest.webmanifest` | nazwa i ikona przy instalacji na telefonie |
| `sw.js` | działanie offline |
| `icons/` | ikony aplikacji |
| `libs/` | biblioteki do tworzenia PDF i czcionka |

## Publikacja na GitHub Pages (jednorazowo, ok. 5 minut)

1. Załóż darmowe konto na https://github.com.
2. Kliknij **New repository**, nazwij je np. `el_fuszka`, ustaw **Public**, kliknij **Create repository**.
3. Kliknij **uploading an existing file** i przeciągnij wszystkie pliki z tego folderu
   (`index.html`, `manifest.webmanifest`, `sw.js` oraz foldery `icons` i `libs`). Kliknij **Commit changes**.
4. Wejdź w **Settings → Pages**. W polu **Branch** wybierz `main`, folder `/ (root)`, kliknij **Save**.
5. Po 1–2 minutach aplikacja będzie dostępna pod adresem
   `https://<twoja-nazwa-użytkownika>.github.io/el_fuszka/`.

## Instalacja na telefonie

- **Android (Chrome):** otwórz adres → menu ⋮ → **Zainstaluj aplikację** / **Dodaj do ekranu głównego**.
- **iPhone (Safari):** otwórz adres → przycisk Udostępnij → **Do ekranu początkowego**.

Po instalacji aplikacja otwiera się z ikony jak zwykła aplikacja i działa offline.

## Pierwsze uruchomienie

1. **Ustawienia** (ikona ⚙ w prawym górnym rogu) → wpisz stawkę za km i stawkę godzinową → **Zapisz stawki**.
   Uzupełnij też **Dane wykonawcy** – pojawią się na wycenach.
2. **Katalog** → dodaj części, których często używasz (można też dodawać je w trakcie pracy z projektu).
3. **Projekty** → **Nowy projekt**.

## Nawigacja

Dolny pasek: **Projekty / Wyceny / Katalog / Narzędzia**. **Ustawienia** (stawki, dane wykonawcy,
kopia zapasowa) otwiera ikona koła zębatego ⚙ w prawym górnym rogu.

## Zasady obliczeń

- **Przyjazd** = odległość × 2 (tam i z powrotem) × stawka za km
- **Robocizna** = czas pracy × stawka godzinowa (domyślnie dziś, 4 h)
- **Część** = cena × ilość
- Cena pozycji zapisuje się w chwili dodania. Zmiana stawek lub cen w katalogu nie zmienia
  starych wycen. Projekt można przeliczyć według aktualnych stawek z menu ⋮ w projekcie.

## Stan magazynowy

Każda część w katalogu ma **stan magazynowy** (liczba całkowita, domyślnie 0) – ustawiasz go w oknie części w zakładce **Katalog**.
Stan jest widoczny (tylko gdy jest większy od 0) na liście katalogu i w podpowiedziach przy dodawaniu części do projektu i pozycji do wyceny.

- Dodanie części z katalogu do projektu **odejmuje** ilość ze stanu (stan nie spadnie poniżej 0 – jeśli brakuje, aplikacja to pokaże).
- Zmiana ilości w projekcie odejmuje lub oddaje różnicę, usunięcie części z projektu **oddaje** ją na stan.
- Przy usuwaniu projektu można wybrać: zwrócić części na stan albo uznać je za zużyte.
- Ilość ułamkowa w projekcie (np. 2,5) zdejmuje ze stanu pełne sztuki w górę (3).
- Wyceny nie zmieniają stanu.

## Import / eksport katalogu części

W zakładce **Katalog** → menu **⋮** u góry:
- **Eksportuj do pliku CSV** – zapisuje katalog jako `el_fuszka-katalog-RRRR-MM-DD.csv` (otwiera się w Excelu).
  Przy pustym katalogu zapisuje pusty wzór do uzupełnienia.
- **Udostępnij katalog** – wysyła plik np. mailem lub na Dysk Google.
- **Importuj z pliku** – wczytuje CSV lub JSON (także pełną kopię zapasową – brany jest tylko katalog).
  Do wyboru: *dodaj nowe i zaktualizuj ceny* albo *zastąp cały katalog*.

Format CSV: kolumny `Nazwa;Cena;Stan`, pierwszy wiersz to nagłówek, cena z przecinkiem, np.:

```
Nazwa;Cena;Stan
Wyłącznik nadprądowy B16;18,50;10
Przewód YDY 3x2,5;3,20;0
```

Kolumna `Stan` jest opcjonalna – starsze pliki z dwiema kolumnami nadal działają (stan istniejących części się wtedy nie zmienia).
Wartość w kolumnie `Stan` przy imporcie **nadpisuje** stan części w aplikacji.

Części dodane już do projektów nie zmieniają się przy imporcie.

## Wyceny (PDF i Word)

1. Raz uzupełnij **Ustawienia (⚙) → Dane wykonawcy** (na wycenie pojawią się tylko wypełnione pola).
   Możesz tam też wpisać domyślne uwagi, np. „Oferta ważna 14 dni”.
2. Zakładka **Wyceny** → **Nowa wycena**:
   - **Z projektu** – wybierasz projekt i sposób przeniesienia pozycji: *szczegółowo* (każdy przyjazd,
     dzień pracy i część osobno) albo *zgrupowane* (Dojazd / Robocizna / Materiały). Dane klienta
     uzupełniają się z projektu. Skrót: menu **⋮** w projekcie → **Utwórz wycenę**.
   - **Pusta wycena** – pozycje dodajesz ręcznie (nazwa z podpowiedziami z katalogu, ilość, j.m., cena).
3. Wycena ma numer (W/kolejny/rok), datę, dane zamawiającego, pole „Dotyczy” i uwagi – wszystko edytowalne.
4. Przyciski **PDF** / **Word (DOCX)** tworzą plik, który można udostępnić (WhatsApp, e-mail…) lub zapisać w telefonie.
   Nazwa pliku zaczyna się od treści pola „Dotyczy”, np. `Wymiana_rozdzielnicy_Wycena_W-1-2026.pdf`
   (puste „Dotyczy” → `Wycena_W-1-2026.pdf`).

Wyceny są zapisywane w aplikacji (i w kopii zapasowej) – można je edytować, duplikować i generować ponownie.
Menu **⋮** w wycenie: pobierz ponownie pozycje z projektu, duplikuj, usuń.

Folder `libs/` zawiera biblioteki do tworzenia PDF (jsPDF – MIT) i czcionkę z polskimi znakami
(podzbiór Liberation Sans – SIL OFL 1.1), szczegóły w `libs/LICENSES.txt`. **Wgraj go razem z resztą plików.**

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
Regularnie rób kopię: **Ustawienia (⚙) → Udostępnij kopię** (np. na Dysk Google) lub **Zapisz kopię do pliku**.
Na nowym telefonie: **Ustawienia → Wczytaj kopię z pliku**.

## Aktualizacja aplikacji

Po zmianie plików wgraj je ponownie do repozytorium na GitHubie i w pliku `sw.js` podnieś numer
wersji (np. `el_fuszka-v1.1.3` → `el_fuszka-v1.1.4`). Telefon pobierze nową wersję przy następnym uruchomieniu
z dostępem do internetu. Dane nie zostaną usunięte.
