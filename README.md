# Skarby Ziemi: Minerały i Skamieniałości Dolnego Śląska

Edukacyjna, interaktywna baza wiedzy oraz katalog okazów geologicznych stworzony z myślą o uczniach szkoły podstawowej (klasy 4–6, ok. 10 lat) do prezentacji na tablicach interaktywnych podczas lekcji przyrody i geografii.

## 🎯 Cel Projektu

Projekt powstał, aby w przystępny, wizualny i angażujący sposób zaprezentować dzieciom autentyczne znaleziska geologiczne pochodzące z polskiej części Dolnego Śląska.

Aplikacja została zaprojektowana specjalnie z myślą o czytelności na szkolnych **tablicach interaktywnych** i wsparciu dzieci ze specjalnymi potrzebami edukacyjnymi. Zawiera cztery motywy: domyślny **Ziemia i Drewno (drzewo)**, **Wysoki Kontrast**, **Spokojna Szałwia** oraz dodatkowy **Motyw AI**.

## 🗺️ Pochodzenie Okazów (Lokalizacje na Dolnym Śląsku)

Wszystkie eksponaty ujęte w bazie zostały znalezione w następujących rejonach:
1. **Dawna Kopalnia Chryzoprazu w Szklarach** (koło Ząbkowic Śląskich) – chryzopraz, kwarc niklowy.
2. **Kraina Wygasłych Wulkanów** (Pogórze Kaczawskie) – agaty, chalcedony, geody.
3. **Okolice Wałbrzycha** – kwarce, szczotki krystaliczne, brekcje, otoczaki z plaży.
4. **Hałdy po kopalniach węgla kamiennego w Wałbrzychu** – skamieniałości roślin karbońskich (paprocie, kory pra-drzew sprzed 300 mln lat).

## 💧 Złota Zasada Młodego Geologa
> **Skały i minerały najlepiej badać po zmyciu pyłu wodą!** Gdy kamień jest lekko wilgotny, woda wypełnia mikroskopijne nierówności powierzchni, co drastycznie zwiększa nasycenie barw i pozwala dostrzec blask kryształów.

## 💻 Struktura i Wdrożenie
Projekt jest statyczną aplikacją typu **Single-Page Application (SPA)** napisaną w HTML, CSS (Tailwind) i JavaScript. Stworzony przy wsparciu sztucznej inteligencji **Gemini**.

- [index.html](index.html) zawiera układ strony, style motywów i kod renderowania.
- [okazy.js](okazy.js) zawiera dane kategorii i okazów; zdjęcia są w katalogu [zdjecia/](zdjecia/).
- Wygląd wspólny dla kart używa zmiennych CSS, dzięki czemu zmiana motywu nie wymaga edycji każdego elementu.

### Dodawanie okazów i kategorii

1. Umieść plik JPG w `zdjecia/`.
2. Dopisz okaz do `specimens` właściwej kategorii w `okazy.js`, podając `number`, nazwę pliku (`image`), `title` i `description`.
3. Nową kategorię dodaj jako kolejny obiekt w `MINERAL_CATEGORIES`, kopiując strukturę istniejącej. Nawigacja i karty wygenerują się automatycznie.

Opisy i nazwy zdjęć są wstawiane jako tekst, a nazwa pliku zdjęcia musi być zwykłą nazwą JPG (bez ścieżek). Nie dodawaj HTML ani skryptów do danych okazów.

### Dodawanie motywu

Dodaj blok `html[data-theme="id"]` z wartościami zmiennych CSS w `index.html` oraz przycisk z `data-theme-choice="id"` w sekcji przełączania motywów. Motyw **Ziemia i Drewno** (`tree`) jest domyślny; motyw wybierany jest na stronie bez zapisywania ustawień po jej zamknięciu.

### Ocena architektury i bezpieczeństwa

To mała, statyczna strona, a nie pełna architektura SOLID: rozdzielenie danych okazów od widoku upraszcza rozwój, ale HTML nadal odpowiada za układ i logikę renderowania. Dodawanie okazów i kategorii jest teraz niezależne od powielania kart HTML; dodanie motywu wymaga zmiany palety CSS i dodania przycisku.

Strona nie ma backendu, logowania ani formularzy, więc nie przetwarza danych użytkowników. Katalog jest statyczny, a treści okazów trafiają do DOM przez `textContent`, nie przez interpretację HTML. Nie oznacza to pełnej gwarancji bezpieczeństwa: Tailwind, Google Fonts i Font Awesome są pobierane z zewnętrznych CDN bez SRI, więc wdrożenie zależy od zaufania do tych dostawców i dostępu do sieci. Przy wdrożeniu produkcyjnym warto przypiąć wersje lub hostować zasoby lokalnie.

## 📜 Licencja

Ten projekt jest udostępniany na licencji **Creative Commons Uznanie autorstwa - Użycie niekomercyjne - Na tych samych warunkach 4.0 Międzynarodowe (CC BY-NC-SA 4.0)**.

Szczegółowy tekst licencji znajdziesz w pliku [LICENSE](LICENSE) w tym repozytorium.
