# Tekken8Access

Tekken8Access to eksperymentalny mod dostępności dla **Tekken 8**, który przekazuje tekst i wybrane informacje interfejsu do czytnika ekranu. Projekt skupia się przede wszystkim na menu, konfiguracji trybów, listach, dialogach i komunikatach gry.

Aktualna wersja: **1.8.87-preview**.

[Pobierz paczkę 1.8.87](https://github.com/Patras93/Tekken-8-access/releases/download/v1.8.87/Tekken8Access_v1.8.87-preview-release.zip) · [Opis wydania](https://github.com/Patras93/Tekken-8-access/releases/tag/v1.8.87).

Wersja 1.8.87 dodaje odczyt regionu pod kursorem w oknie **Wybierz region**. Odczyt potwierdzono w grze. Zawiera także poprawki nawigacji rankingów, filtrów postaci, opcji profilu gracza, list duchów, menu sesji online oraz list znajomych, rywali i śledzących. Zakres tych ekranów nadal może być częściowy.

> [!IMPORTANT]
> Mod nie zapewnia jeszcze pełnej dostępności całej gry. Obsługa poszczególnych ekranów może być częściowa, a po aktualizacji Tekken 8 wymagane może być dostosowanie punktów integracji.

## Wymagania

- Windows 64-bit;
- Tekken 8 — zweryfikowany build **Polaris 3.02.02**;
- uruchomiony czytnik ekranu **NVDA**;
- zgodna 64-bitowa biblioteka NVDA Controller Client umieszczona obok moda (`nvda64.dll`, `nvdaControllerClient.dll` albo `nvdaControllerClient64.dll`).

Mod potrafi również użyć `Tolk.dll` jako zapasowego mechanizmu mowy. Paczka wydania zawiera `nvdaControllerClient64.dll` i `Tolk.dll` obok `dinput8.dll`.

## Instalacja

1. Zamknij Tekken 8.
2. Otwórz katalog:

   ```text
   ...\SteamLibrary\steamapps\common\TEKKEN 8\Polaris\Binaries\Win64
   ```

3. Jeśli znajduje się tam wcześniejszy `dinput8.dll`, utwórz jego kopię zapasową poza katalogiem gry.
4. Skopiuj `dinput8.dll` z rozpakowanej paczki wydania do powyższego katalogu.
5. Skopiuj do tego samego katalogu dołączone `nvdaControllerClient64.dll` i `Tolk.dll`.
6. Uruchom NVDA, a następnie grę.

Wydanie ma postać pojedynczego pliku moda. Nie wymaga osobnych plików `Tekken8Accessibility.dll`, `Tekken8UIReader.dll`, `Tekken8Accessibility.dat` ani `Tekken8Accessibility.ini`.

### Aktualizacja i usuwanie

Przed aktualizacją zamknij grę, zachowaj działający `dinput8.dll` jako kopię i dopiero wtedy zastąp go nową wersją. Aby wyłączyć mod, zamknij grę i usuń albo przenieś modowy `dinput8.dll`; następnie możesz przywrócić poprzednią kopię.

## Obsługiwane obszary

Zakres obejmuje między innymi:

- menu główne, zakładki, wiadomości i typowe dialogi;
- ustawienia, wartości opcji, sterowanie, HUD i identyfikator gracza;
- wybór postaci i areny;
- tryby offline oraz ekrany wyników;
- dobieranie przeciwnika, warunki sieciowe, sesje, pokoje i część Fight Lounge;
- listy rankingowe, w tym pozycję i nazwę widocznego gracza;
- profile społeczności oraz ekran pobranych duchów;
- listę powtórek, jej filtry, akcje i część informacji odtwarzania;
- historię: wybór rozdziału, poziom trudności, komunikaty, napisy, QTE i część ekranów po walce;
- Arcade Quest, w tym część rozmów, zadań, list komend i liczników;
- trening, listę komend, pomoc do komend i Combo Challenge;
- bieżący krok Combo Challenge z dokładną komendą i opisem;
- potwierdzone komunikaty walki: rozpoczęcie rundy, KO, Double KO, Time Up oraz aktywację Heat i Rage;
- personalizację postaci, część sklepu, galerii i trybu fotograficznego;
- część Tekken Ball oraz Ghost Battle;
- przerwanie poprzedniej wypowiedzi i ograniczanie powtarzających się komunikatów.

Mod używa tekstu przekazywanego przez grę oraz dokładnie zweryfikowanych zdarzeń interfejsu. Nie nadaje znaczenia nieopisanym polom tylko na podstawie przypuszczeń.

## Znane ograniczenia

- Nie każdy ekran i nie każda kontrolka zostały przetestowane podczas rzeczywistej rozgrywki.
- Informacje zależne głównie od grafiki, ikon lub tekstur mogą pozostać nieme.
- Komunikaty rozpoczęcia rundy, KO, Double KO, Time Up oraz aktywacji Heat i Rage są odczytywane, ale mod nie interpretuje nieopisanych argumentów jako numeru rundy ani strony gracza.
- Bieżący stan zdrowia, zegar, licznik rund oraz wizualne paski Heat i Rage nie mają jeszcze kompletnego odczytu.
- Frame Info w treningu oraz niektóre elementy Tekken Ball, Arcade Quest, sklepu i galerii mogą być odczytywane częściowo.
- Niektóre ikony rangi, platformy i nagrody nie mają bezpiecznie potwierdzonego opisu tekstowego.
- Mod jest związany z konkretnym buildem gry. Jeżeli weryfikacja kodu Polaris nie powiedzie się, dany moduł nie zostanie zainstalowany, aby uniknąć patchowania niewłaściwego miejsca.
- Teksty pochodzą z gry, więc ich język zależy od ustawień Tekken 8 i dostępnej tabeli lokalizacji.

Szczegółowe notatki techniczne znajdują się w plikach `*_COVERAGE_*.txt`, `*_STATIC_MAP.txt` oraz w `CHANGELOG_PL.txt`.

## Testowanie i zgłaszanie problemów

Po instalacji sprawdź najpierw menu główne, a następnie ekran, którego dotyczy zmiana. Przy zgłoszeniu podaj:

- wersję Tekken8Access i wersję Tekken 8;
- język gry i wersję NVDA;
- dokładną ścieżkę do ekranu, np. „Online → Mecz rankingowy → Ustaw warunki sieciowe przeciwnika”;
- użyte klawisze lub przyciski oraz oczekiwany tekst;
- informację, czy ekran jest całkowicie niemy, czy brakuje tylko części danych;
- pliki `Tekken8Access_loader.log` i `Tekken8Access_mod.log` utworzone obok `dinput8.dll`.

Przed opublikowaniem logów sprawdź, czy nie zawierają danych, których nie chcesz udostępniać. Raport powinien dotyczyć jednego ekranu lub jednego powtarzalnego problemu — ułatwia to odtworzenie błędu.

## Budowanie ze źródeł

Wymagane są:

- Visual Studio albo Visual Studio Build Tools z zestawem **Desktop development with C++**;
- MSVC dla x64;
- Windows SDK, w tym `rc.exe`.

Uruchom w katalogu projektu:

```bat
BUILD_X64_SINGLE_DLL.bat
```

Skrypt automatycznie wyszukuje narzędzia Visual Studio, kompiluje trzy jednostki produkcyjne, osadza tabelę lokalizacji i sprawdza eksport `DirectInput8Create`. Gotowy plik powstaje jako:

```text
release\dinput8.dll
```

Katalog `release` powinien zawierać dokładnie jeden plik moda.

Testy jednostkowe można uruchomić poleceniem:

```bat
BUILD_TESTS.bat
```

Testy statyczne i jednostkowe nie zastępują sprawdzenia w działającej grze z NVDA. Zmiany punktów wywołań należy weryfikować względem dokładnie obsługiwanego pliku `Polaris-Win64-Shipping.exe`.

## Bezpieczeństwo zmian

Kod sprawdza oczekiwane bajty i cel każdego przechwytywanego wywołania przed zastosowaniem zmiany. Nie używa ogólnego skanowania obiektów Unreal Engine w czasie działania. Mimo tych zabezpieczeń jest to wersja preview: przechowuj kopię ostatniego działającego `dinput8.dll` i po każdej aktualizacji gry sprawdzaj logi przed dalszym testowaniem.
