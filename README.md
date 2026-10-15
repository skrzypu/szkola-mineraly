# Skarby Ziemi: Minerały i Skamieniałości Dolnego Śląska

Edukacyjna, interaktywna baza wiedzy oraz katalog okazów geologicznych stworzony z myślą o uczniach szkoły podstawowej (klasy 4–6, ok. 10 lat) do prezentacji na tablicach interaktywnych podczas lekcji przyrody i geografii.

**Otwórz stronę:** [skrzypu.github.io/szkola-mineraly](https://skrzypu.github.io/szkola-mineraly/)

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
Projekt jest statyczną aplikacją typu **Single-Page Application (SPA)** napisaną w HTML, CSS i JavaScript. Nie wymaga instalowania zależności ani budowania. Nie korzysta z zewnętrznych bibliotek, czcionek ani ikon — wszystkie potrzebne pliki znajdują się w repozytorium.

- [index.html](index.html) zawiera układ strony, style motywów i kod renderowania.
- [style.css](style.css) zawiera lokalne style strony.
- [okazy.js](okazy.js) zawiera dane kategorii i okazów; zdjęcia są w katalogu [zdjecia/](zdjecia/).
- Wygląd wspólny dla kart używa zmiennych CSS, dzięki czemu zmiana motywu nie wymaga edycji każdego elementu.

### Uruchamianie offline

Pobierz lub skopiuj cały folder projektu, zachowując jego strukturę, a następnie otwórz `index.html` w przeglądarce. Strona, style, skrypt z danymi i zdjęcia są lokalne — do działania katalogu nie jest potrzebne połączenie z internetem. Internet jest potrzebny tylko do otwarcia strony bezpośrednio z adresu GitHub Pages; lokalnie pobrana kopia działa offline.

### Dodawanie okazów i kategorii

1. Umieść plik JPG w `zdjecia/`.
2. Dopisz okaz do `specimens` właściwej kategorii w `okazy.js`, podając `number`, nazwę pliku (`image`), `title`, `description` i krótką ciekawostkę dla dzieci (`funFact`).
3. Nową kategorię dodaj jako kolejny obiekt w `MINERAL_CATEGORIES`, kopiując strukturę istniejącej. Podaj też `placeDescription` i `placeFact`, by krótko przedstawić miejsce oraz ciekawostkę o nim. Nawigacja i karty wygenerują się automatycznie.

Opisy, ciekawostki i nazwy zdjęć są wstawiane jako tekst, a nazwa pliku zdjęcia musi być zwykłą nazwą JPG (bez ścieżek). Nie dodawaj HTML ani skryptów do danych okazów.

### Dodawanie motywu

Dodaj blok `html[data-theme="id"]` z wartościami zmiennych CSS w `index.html` oraz przycisk z `data-theme-choice="id"` w sekcji przełączania motywów. Motyw **Ziemia i Drewno** (`tree`) jest domyślny; motyw wybierany jest na stronie bez zapisywania ustawień po jej zamknięciu.

### Ocena architektury i bezpieczeństwa

To mała, statyczna strona, a nie pełna architektura SOLID: rozdzielenie danych okazów od widoku upraszcza rozwój, ale HTML nadal odpowiada za układ i logikę renderowania. Dodawanie okazów i kategorii jest teraz niezależne od powielania kart HTML; dodanie motywu wymaga zmiany palety CSS i dodania przycisku.

Strona nie ma backendu, logowania ani formularzy i nie zbiera danych użytkowników. Opisy okazów są wstawiane do strony jako tekst (`textContent`), a nie interpretowane jako HTML. Strona nie pobiera kodu, czcionek ani ikon z zewnętrznych serwisów, więc po skopiowaniu całego folderu działa również bez internetu. Jak przy każdej stronie otwieranej lokalnie, należy używać zaufanych plików projektu.

## 📜 Licencja

Ten projekt, w tym zdjęcia okazów będące własnością autora projektu, jest udostępniany na licencji **Creative Commons Uznanie autorstwa - Użycie niekomercyjne - Na tych samych warunkach 4.0 Międzynarodowe (CC BY-NC-SA 4.0)**. Przy wykorzystaniu należy podać autorstwo i zachować warunki tej licencji.

Szczegółowy tekst licencji znajdziesz w pliku [LICENSE](LICENSE) w tym repozytorium.
