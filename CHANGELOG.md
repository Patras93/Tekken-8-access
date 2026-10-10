# Changelog

W tym pliku opisano najważniejsze zmiany w projekcie **Tekken8Access**. Układ jest oparty na formacie [Keep a Changelog](https://keepachangelog.com/pl/1.1.0/). Projekt używa numeracji wersji zgodnej z dotychczasowymi wydaniami moda; wpisy nie zawierają dat, ponieważ nie zostały one zapisane w źródłowym changelogu.

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


