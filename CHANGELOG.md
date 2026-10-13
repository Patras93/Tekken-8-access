# Changelog

W tym pliku opisano najważniejsze zmiany w projekcie **Tekken8Access**. Układ jest oparty na formacie [Keep a Changelog](https://keepachangelog.com/pl/1.1.0/). Projekt używa numeracji wersji zgodnej z dotychczasowymi wydaniami moda; starsze wpisy bez dat zachowują informacje zapisane w źródłowym changelogu.

## [1.8.95-preview] — 2026-10-13

### Naprawiono

- Odczyt „Stwórz sesję” i „Wyszukaj sesje” podczas przesuwania kursora. Działanie obu opcji potwierdzono w grze z NVDA.
- Przy wyborze tych dwóch pozycji używany jest indeks lokalny grupy. Poprzedni odczyt błędnie dodawał przesunięcie wizualne 3, szukając nieistniejących pozycji 3/4 zamiast 0/1.
- Zdarzenia innych poziomów menu nie kasują już oczekującej nazwy zaznaczonej opcji. Wewnętrzne ekrany sesji pozostają bez zmian.
- Zachowano tekst zaznaczonej opcji w osobnej kolejce, obsługując szybki ruch kursora, natywne zatrzymanie mowy i zwolnienie danych przez grę.
- Uwzględniono lokalną wersję 1.8.93: osobny odczyt zaznaczonych ustawień i ich podmenu oraz ochronę przed nadpisaniem przez komunikaty pomocy.

### Weryfikacja i ograniczenia

- Kompilacja x64, testy tekstu i regresja wyboru sesji przeszły bez błędów. Regresja obejmuje rzeczywisty callback wyboru grupy z dwoma wpisami i przesunięciem 3, obie pary kluczy etykiet oraz callbacki innych poziomów.
- Wersje 1.8.93–1.8.94 były lokalnymi etapami napraw; 1.8.94 nie rozwiązała odczytu tych dwóch opcji. Wydanie 1.8.95 zawiera skuteczną poprawkę potwierdzoną przez użytkownika.
- Mod nadal ma częściowe pokrycie ekranów. Obsługiwany build: Polaris 3.02.02.

## [1.8.92-preview] — 2026-10-13

### Naprawiono

- W rankingach odczytywany jest właściwy nick gracza zamiast długiego identyfikatora konta. Pozycja i liczba wyników pozostają w komunikacie, np. „1 of 10000”.
- Zachowano prawdziwe nicki liczbowe i dosłowny tekst nazw. Brak nicku nie powoduje odczytu identyfikatora konta.
- Zachowano odczyt przy ruchu kursora, zmianie strony i późnym nadejściu danych; nazwa jest kopiowana przed zwolnieniem bufora gry.
- Uwzględniono poprawki z lokalnych wersji 1.8.88–1.8.91: właściwe zdarzenie tekstu wyboru regionu, odczyt zaznaczonego salonu, nazwy sesji i gospodarza na liście „Wyszukaj sesję” oraz odczyt ustawień po natywnym przerwaniu mowy.

### Weryfikacja i ograniczenia

- Kompilacja x64, testy tekstu i testy rankingów przeszły bez błędów. Testy rozróżniają nick od identyfikatorów, obejmują strony, późne dane, przerwanie mowy i zwolnienie bufora.
- Odczyt nicków w tej wersji wymaga jeszcze potwierdzenia podczas gry z NVDA. Mod nadal nie zapewnia kompletnej dostępności wszystkich ekranów; obsługiwany build: Polaris 3.02.02.
- Wcześniejszy opis wydania 1.8.87 przedwcześnie uznawał odczyt regionów za potwierdzony. Późniejsze zgłoszenia wykazały brak odczytu; poprawiono go w lokalnej wersji 1.8.89, zawartej w tej paczce.

## [1.8.87-preview] — 2026-10-12

### Dodano i naprawiono od wersji 1.8.80

- Odczyt regionu zaznaczonego kursorem w oknie „Wybierz region”, również podczas nawigacji klawiaturą lub padem. Działanie potwierdzono w grze.
- Odczyt pozycji list rankingowych podczas ruchu kursora oraz kategorii i wartości filtrów. Dodano obsługę osobnego panelu wyboru postaci.
- Odczyt opcji profilu gracza, w tym „Pobierz ducha”, oraz nazwy i postaci zaznaczonego ducha udostępnionego przez gracza. Działanie profilu i listy duchów potwierdzono w grze.
- Poprawiono kolejność odczytu menu „Stwórz sesję” / „Wyszukaj”, aby natywna obsługa zaznaczenia nie kasowała nowego komunikatu.
- Dodano odczyt zakładek znajomych, rywali i śledzących, zaznaczonego gracza, dostępnej nazwy salonu oraz komunikatów pustej listy i ładowania.
- Poprawiono późne nadejście etykiet, ponowne otwieranie okien, powrót z dialogów wewnętrznych oraz czyszczenie starych nazw po odświeżeniu.
- Zwiększono pojemność list wartości dialogów z 32 do 128 i przeniesiono odczyt po natywnych wywołaniach, które mogą przerywać mowę.

### Weryfikacja i ograniczenia

- Kompilacja x64, testy tekstu, rankingów, profilu, list duchów, salonów i regionów przeszły. Testy obejmują przekazywanie argumentów gry oraz wykonanie kodu przekaźników.
- Wersje 1.8.81–1.8.86 były lokalnymi etapami napraw. Wydanie 1.8.87 zawiera te zmiany.
- Mod nadal nie zapewnia pełnej dostępności całej gry. Część ekranów wymaga dalszych testów; zgodność zweryfikowano dla Polaris 3.02.02.

## [1.8.80-preview] — 2026-10-11

### Naprawiono

- Odczyt nazw zaznaczonych duchów w Super walka duchów → Walcz przeciwko pobranym duchom. Działanie potwierdzono podczas nawigacji w grze z czytnikiem ekranu.
- Rozpoznawanie właściwego ekranu Blueprint i jego zdarzenia OnButtonSelect; wcześniejsze wywołania dotyczyły innego selektora.
- Konflikt podwójnego przejmowania Online ID, błędne sygnatury rekordów i SetGhostList oraz kopiowanie tekstu przed zwolnieniem bufora przez grę.
- Odczyt po powrocie na ekran i kolejkę komunikatów podczas StopSpeaking.

### Dodano

- Czytnik zakładek serii i nazw utworów Jukeboxa.
- Testy rozpoznawania zaznaczenia, czasu życia tekstu i wykonania relay z zachowaniem rejestrów oraz argumentów gry.

Wersje 1.8.78 i 1.8.79 były lokalnymi etapami diagnostyki. Pozostałe ograniczenia dostępności gry nadal obowiązują.

## [1.8.77-preview]

### Dodano

- Dodano sześć semantycznie potwierdzonych zdarzeń walki: rozpoczęcie rundy, KO, Double KO, Time Up oraz aktywację Heat i Rage.
- Combo Challenge korzysta teraz z czterech dokładnych wywołań `SetComboChallengeCommand` i trzech `CurrentCommand`, które przekazują ten sam natywny indeks.
- Bieżący krok Combo Challenge jest bezpośrednio łączony z dokładną komendą i opisem dostarczonym przez grę.

### Zabezpieczenia

- Nieopisane parametry zdarzeń walki nie są interpretowane jako numer rundy ani strona gracza.
- Siedem wywołań Combo Challenge ma weryfikację instrukcji i celu, wycofanie zmian po błędzie oraz deduplikację komunikatów.
- Numeracja kroków nie jest zgadywana; mod używa wspólnego natywnego indeksu Polarisa.
- Zachowano wszystkie kanały dostępności z wersji 1.8.76 i wcześniejszych.

## [1.8.76-preview]

### Dodano

- Przeprowadzono trzy równoległe audyty obejmujące menu i tryby offline, ekrany online oraz walkę, fabułę i personalizację.
- Dodano 11 dokładnie zweryfikowanych wywołań dla ekranów online: nazwy gospodarza i graczy, reguły sesji, warunki pokoju, profile społeczności oraz tekst rangi drugiej postaci.
- Dodano 15 dokładnie zweryfikowanych wywołań personalizacji postaci: etykiety Menu2 i nazwy przedmiotów Menu3.
- Dodano trzy wywołania bieżącego kroku Combo Challenge. Indeks jest łączony wyłącznie z dokładną sekwencją komend dostarczoną przez grę.

### Zabezpieczenia

- Teksty są kopiowane przed wykonaniem wrapperów, które zwalniają rekordy wejściowe.
- Każdy nowy moduł sprawdza bajty instrukcji i cel `rel32` przed instalacją oraz wycofuje własne zmiany po błędzie.
- Nierozwiązane identyfikatory `TEXT_*` pozostają ciche, zamiast być odczytywane jako techniczne nazwy.
- Zachowano wszystkie kanały dostępności z wcześniejszych wersji.

## [1.8.75-preview]

### Dodano

- Dodano pięć potwierdzonych wywołań przekazujących dokładny tekst gry dla zdarzeń `CancelSkip`, dwóch wariantów `Confirm`, `Skip` oraz `WaitConfirm`.
- Czytnik odczytuje komunikaty potwierdzenia, pomijania sceny, anulowania pomijania i oczekiwania na potwierdzenie.

### Zabezpieczenia

- Każda ścieżka ma potwierdzone ABI `self + FString` oraz weryfikację instrukcji `CALL` dla Polaris 3.02.02.
- Oryginalne zdarzenia gry są wykonywane przed obsługą dostępności.
- Mod przekazuje tekst gry bez nadawania własnych nazw i bez interpretowania nieopisanych pól.
- Powtórzenie identycznego tekstu podczas odświeżania interfejsu w ciągu 600 ms jest pomijane.

## [1.8.74-preview]

### Dodano

- Rankingi odczytują pozycję, całkowitą liczbę miejsc oraz nazwę widocznego gracza, na przykład „1 of 100. NazwaGracza”.
- Przejęto dwa dokładne wywołania przekazujące widoczne rekordy rankingu. Potwierdzony rekord ma rozmiar `0x88`, a pierwszy `FString` z nazwą gracza znajduje się pod `+0x18`.
- Jeśli zdarzenie kursora nadejdzie przed zbudowaniem rekordów, aktywna pozycja jest ponownie ogłaszana po ich dostarczeniu.

### Zabezpieczenia

- Mod nie interpretuje nieopisanych pól liczbowych ani ikon postaci, platform i rang.
- Zachowano poprawki listy pobranych duchów oraz kolejności mowy z wcześniejszych wersji.

## [1.8.73-preview]

### Dodano

- Dodano odczyt wejścia na ekran „Pobrane duchy”: tytułu, opisu i liczby pozycji po `SetGhostList`.
- Dodano odczyt dokładnego tekstu zaznaczonego ducha po `SetPlayerInfo`.
- Tytuł i opis są pobierane z kluczy lokalizacji gry `TEXT_000_UI_GHOST_002` oraz `TEXT_000_UI_GHOST_006`, a liczba pozycji z natywnego `TArray`.

### Zmieniono

- Komunikaty są opóźniane o 140 ms, emitowane po blokadzie `StopSpeaking` i deduplikowane.
- Wykorzystano istniejące hooki; nie dodano nowych punktów patchowania gry.
- Dane wewnętrzne obiektów listy nie są odczytywane ani zgadywane.

## [1.8.72-preview]

### Naprawiono

- Naprawiono utratę nowego tekstu, gdy gra wywoływała `StopSpeaking`, a przed kolejnym cyklem czytnika przekazywała nowe zaznaczenie lub `Speak`.
- `StopSpeaking` usuwa tylko wypowiedzi utworzone przed tym zdarzeniem. Tekst z bieżącej generacji pozostaje w kolejce.
- Identyczna treść występująca po `StopSpeaking` jest traktowana jako nowe zdarzenie.

### Zabezpieczenia

- Poprawka obejmuje główną kolejkę ekranową oraz opóźniony globalny `Speak`.
- Przekaźnik `StopSpeaking` zachowuje ABI: używa wyłącznie ulotnych rejestrów `R10` i `RAX`, atomowo zwiększa licznik generacji i przechodzi do oryginalnej funkcji.
- Nie dodano nowych punktów patchowania Polaris.

## [1.8.71-preview]

### Naprawiono

- Naprawiono ciszę na pozycji „Pobierz ducha” w `UPolarisUMGCommunityMenu`.
- Gdy pierwszy rekord Community Menu nie zawiera użytecznego tekstu, cache korzysta z dokładnego klucza lokalizacji gry `TEXT_000_UI_LOBBY_COMMNUNITY_MENU_001`.
- Obsługiwane teksty lokalizacji to „Pobierz ducha” po polsku i „Download Ghost” jako angielski fallback.

### Zabezpieczenia

- Nie dodano nowych hooków. Poprawka korzysta z istniejących kanałów `AddButtonData` i `SetCursorIndex` z wersji 1.8.29.
- Tekst dostarczony przez grę zawsze ma pierwszeństwo. Fallback dotyczy wyłącznie pustego pierwszego rekordu i nie zmienia pozostałych pozycji Community Menu.
- Zachowano mechanizm Global Speech Arbitration z wersji 1.8.70 oraz wszystkie wcześniejsze moduły.

## [1.8.70-preview]

### Zmieniono

- Dokładne kanały ekranowe otrzymały 180 ms priorytetu nad generycznym `Speak`, aby krótszy fallback z tego samego odświeżenia nie zastępował bogatszego komunikatu.
- Po natywnym `StopSpeaking` działa 90 ms blokady, która usuwa stare kolejki modułów i oczekujący fallback.

## [1.8.69-preview]

### Dodano

- Dodano dokładną synchronizację z natywnym `StopSpeaking` i anulowanie bieżącej mowy NVDA.
- Host single-DLL przekazuje `nvdaController_cancelSpeech` do czytnika interfejsu.

## [1.8.68-preview]

### Dodano

- Dodano globalny, natywny `Speak(FString*)` jako fallback dla tekstów bez bardziej szczegółowego kanału ekranowego.
- Fallback czeka 60 ms, jest anulowany przez dokładniejszy komunikat i deduplikuje identyczny tekst przez 750 ms.

## [1.8.64-preview]–[1.8.67-preview]

### Dodano

- Odczyt uruchamianych aktualności w menu głównym.
- Odczyt nagłówków Command List.
- Odczyt informacji o wersji w Battle HUD.
- Uzupełniono tekst wersji i XID w panelach Fight Lounge.

## [1.8.60-preview]–[1.8.63-preview]

### Dodano

- Uzupełniono tekst ostatnich komend listy TAM w Arcade Quest.
- Dodano etykiety zakładek Combo Challenge.
- Dodano etykiety Menu2 personalizacji postaci.
- Dialogi odczytują tekst główny oraz dokładne etykiety przycisków zgody i odmowy.

## [1.8.54-preview]–[1.8.59-preview]

### Dodano

- Rozszerzono informacje o zdarzeniach walki w treningu.
- Dodano odczyt Combo Challenge, jego postępu oraz pomocy i wskazówek Command List.
- Dodano odczyt bieżącego ruchu w Command List.
- Uzupełniono ostrzeżenia o wyłączności przedmiotów w sklepie.

## [1.8.45]–[1.8.53-preview]

### Dodano

- Rozbudowano dostępność Arcade Quest: rozmowy TAM, zadania i ich listę, trzeci panel, licznik czasu oraz pełny dokładny tekst listy komend.
- Teksty komend zależne od kontekstu są wypowiadane tylko po potwierdzonym zdarzeniu aktywnego elementu.

## [1.8.36]–[1.8.44]

### Dodano

- Rozbudowano tryb fabularny: wybór rozdziału, trudność, rozpoczęcie rozdziału, komunikaty i powiadomienia, napisy filmowe, zdarzenia STE/QTE, ekran po walce oraz turnieje.
- Przeprowadzono audyt przepływu fabuły i uzupełniono potwierdzone teksty przed walką oraz w HUD.

## [1.8.24-preview]–[1.8.35]

### Dodano

- Uzupełniono tryby online, powtórki i wskazówki, galerię, sklep, tryby offline, Fight Lounge i Community.
- Dodano obsługę rankingów, wyników po walce, tekstów personalizacji, Photo Mode, Tekken Ball oraz Ghost Battle.

## [1.8.7]–[1.8.20]

### Dodano

- Rozbudowano Practice Menu oraz informacje o graczu i danych gry.
- Etapami uzupełniono Options: nazwy i wartości, podokna, dostępność, mapowanie przycisków, ustawienia kontrolera, język, obszar, stany HUD i Player ID.
- Dodano globalny Information Bar oraz teksty dialogów, błędów, ogłoszeń i nazw zaznaczonych elementów.

## [1.8.0]–[1.8.6]

### Dodano

- Dodano dokładne zdarzenia głównego menu Polaris.
- Character Select odczytuje natywne nazwy grywalnych postaci i filtruje wymuszone odświeżenia oraz fałszywy odczyt po zatwierdzeniu.
- Stage Select odczytuje nazwę podświetlonej areny.

## [1.7]–[1.7.9]

### Zmieniono

- Połączono bridge i czytnik w jeden plik `dinput8.dll` z przekazywaniem wywołań do systemowej biblioteki DirectInput.
- Osadzono dane wymagane przez mod i dodano obsługę późno tworzonych widżetów.
- Dostosowano obsługę do Tekken 8 / Polaris 3.02.02 oraz rozwijano dokładny kanał interfejsu i zdarzenia głównego menu.
- Zachowano sprawdzoną integrację NVDA/Tolk oraz weryfikację obsługiwanego buildu gry.

