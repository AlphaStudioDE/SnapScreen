# SNAPSCREEN XL 1.0.8
Darmowa wersja konkursowa / Budowa samego panelu
22 listopada 2026 - publiczne wydanie 1.0.8 / instalacja z sieci lub SD

## 1 / Zakres i części

Budujesz samodzielny, 7-calowy panel ESP32-P4 do obsługi i monitorowania kompatybilnej drukarki przez sieć lokalną. Nie wymaga Raspberry Pi do działania panelu. SnapScreen jest niezależnym programem; określenie „KlipperScreen na sterydach” opisuje pomysł. Demonstracja konkursowa dotyczy Snapmaker U1. Inne drukarki wymagają dostępnego, zgodnego API Klipper/Moonraker i osobnego sprawdzenia.

SnapScreen jest darmowy: bez opłaty aktywacyjnej, zamówienia i biletu. Części kupuje budujący. Darmowa dystrybucja nie oznacza licencji open source. Funkcje zmieniarek są widoczne jako wyszarzone i blokowane również w kodzie wykonawczym. Po dotknięciu pojawia się informacja o PrismFlow. Wybór natywnych narzędzi drukarki pozostaje dostępny.

Wymagane: 1 kompletny panel GUITION JC1060P470C_I_W_Y / JC1060P470 XL M3/ETH, 1024 x 600, dotyk pojemnościowy, ESP32-P4 + C6, flash 16 MiB i PSRAM 32 MiB. Nie dowolna płytka P4. Instalator obsługuje starszą rodzinę oraz P4 v3.2. Wykrywa rewizję procesora, a nie dowolny model LCD. Przed instalacją sfotografuj oznaczenia i sprawdź fabryczne demo oraz dotyk.

Wymagane: przewód USB z transmisją danych do złącza programowania P4, komputer Windows x64 do pierwszej instalacji oraz stabilne, regulowane zasilanie 5 V zgodne z instrukcją konkretnej płytki. Specyfikacja producenta podaje około 600 mA; uwzględnij zapas i straty przewodu. Nie podawaj 24 V na wejście 5 V/USB i nie łącz dwóch źródeł zasilania bez potwierdzenia zgodności. Przy prawidłowym zasilaniu USB nie potrzeba przetwornicy ani gniazda DC w obudowie. Komputer nie musi być później podłączony.

Do instalacji offline wymagana, a przy instalacji sieciowej opcjonalna: karta microSD 512 MB-4 GB, czytelny FAT/FAT32, oraz czytnik, jeśli komputer go nie ma. Zabezpiecz własne dane; narzędzie nie formatuje karty. Potrzebna jest kompatybilna drukarka i sieć lokalna, najlepiej na początek wspólna Wi-Fi/LAN bez izolacji klientów. Instalacja z dołączonej karty nie wymaga Internetu ani zmiany firmware drukarki.

Opcjonalne: drukowana obudowa/podstawka, izolowane mocowanie, dystanse, śruby i inserty dobrane do otworów oraz obudowy. Finalne pliki obudowy i dokładna specyfikacja mocowań są osobnym materiałem mechanicznym; tej paczce nie towarzyszy gotowy STL. Podstawowy panel zasilany przez USB nie wymaga lutowania. Opcjonalny kabel Ethernet łączy RJ45 panelu z routerem. Hub/adapter Ethernet po stronie drukarki dotyczy osobno sprawdzanego wariantu przewodowego, nie zwykłego Wi-Fi.

Nie kupuj do tego wariantu CFS, modułów CAN, przewodów zmieniarek, zasilacza 24 V, PTFE, rozdzielaczy, łożysk ani przewijaków. Nie wgrywaj mostka CAN do C6. Zachowaj działające fabryczne oprogramowanie sieciowe C6. Lista nie zawiera bieżących cen zakupowych.

## 2 / Złożenie i sprawdzenie plików

Przy odłączonym zasilaniu sprawdź płytkę i taśmy. Zostaw fabryczne połączenia LCD i dotyku, umieść panel na nieprzewodzącym podłożu albo w dopasowanej obudowie. Nie dociskaj śrubami ekranu ani elementów PCB. Nie podłączaj GPIO, CAN ani okablowania głowicy. Połączenia logiczne: zasilanie 5 V do przewidzianego wejścia panelu, komputer do USB P4 na czas programowania, panel przez sieć lokalną do drukarki.

Najpierw sprawdź działające fabryczne demo. Rozpakuj cały ZIP i uruchom 00-CHECK-FILES.cmd. Sprawdza pliki obu rewizji i podpisane paczki SD bez otwierania portu urządzenia. Nie kontynuuj po błędzie sum. Python i esptool 4.14.0 są w paczce. Przed programowaniem zamknij monitory portu, wyjmij SD i upewnij się, że używasz portu P4, nie C6. Procedurę BOOT/RESET sprawdzaj w instrukcji konkretnej płytki; nie zwieraj przypadkowych pinów.

## 3 / Wgranie miniinstalatora

Dla zgodnego, istniejącego układu SnapScreen uruchom 01-FLASH-P4.cmd, wybierz sprawdzony port COM i potwierdź FLASH. Instalator sam dobiera rodzinę: v0.1-v1.99 -> p4-v1, v3.1-v3.99 -> p4-v3. Nieznane rewizje, zabezpieczenia lub układy pamięci zatrzymują operację. Przed pierwszym zapisem tworzy pełny backup 16 MiB i porównuje go osobnym odczytem. Po zapisie osobno sprawdza obrazy i zachowanie NVS, a dopiero potem resetuje. Zgodna tożsamość i istniejące bilety zostają zachowane.

Dla świeżej płytki z obsługiwanym fabrycznym demo użyj 01b-MIGRATE-FACTORY-P4.cmd. Wymaga potwierdzeń FLASH oraz MIGRATE FACTORY. Akceptuje tylko dokładnie rozpoznany układ producenta, w tym sprawdzony zajęty prefiks V3.8, i puste docelowe NVS. Fabryczne NVS pozostaje w prywatnej kopii; powstaje nowa tożsamość SnapScreen. Nie używaj migracji do omijania uszkodzonej lub aktywowanej instalacji. Nieznany układ zgłoś do sprawdzenia, zamiast go kasować.

Logi i kopie: %LOCALAPPDATA%/SnapScreen/backups/tester-installer/. Pełny dump może zawierać prywatne dane. Zachowaj go lokalnie, do pomocy wysyłaj flash.log i obserwacje. Narzędzie nie kasuje całej pamięci, nie zmienia eFuse ani zabezpieczeń sprzętowych i nie programuje C6.

## 4 / Darmowa aplikacja z sieci lub karty SD

Dla instalacji offline skopiuj oba niezmienione pliki z 03-Installer/SD-OPTIONAL do katalogu głównego karty: snapscreen-free.ssota i snapscreen-free-p4v3.ssota. Nie kopiuj ZIP, surowych BIN, installer.ssota ani biletu. Bezpiecznie odłącz kartę od komputera i włóż do panelu.

Wybierz na ekranie „Install SnapScreen - Free”, następnie „Continue”, aby otworzyć wbudowany instalator. Nie składaj zamówienia i nie kupuj aktywacji. W instalatorze wybierz Network i połącz się z Wi-Fi lub Ethernet, aby pobrać darmowy firmware, albo wybierz instalację z SD z przygotowaną kartą. Dobór pliku do procesora jest automatyczny. Podpis, cel, rewizja i obraz są sprawdzane przed wyborem nowego slotu. Nie odłączaj zasilania. Po starcie sprawdź nazwę SnapScreen i wersję 1.0.8.

Publiczne wydanie SnapScreen 1.0.8 zawiera oba darmowe obrazy sieciowe i metadane dla obu rodzin P4. Instalator sam dobiera nazwę pliku. Instalacja sieciowa wymaga Internetu i prawidłowego czasu sieciowego; dołączone pliki SD pozwalają instalować offline. Sam miniinstalator otwiera się z obrazu wbudowanego. Obie darmowe ścieżki działają bez zamówienia, opłaty i biletu.

## 5 / Połączenie i pierwszy test

W kreatorze wybierz język i sieć, następnie Auto-Detect albo ręcznie IP drukarki. Sprawdź tożsamość i stan przed wysyłaniem poleceń. Przy braku połączenia sprawdź adres, izolację Wi-Fi i dostępność API. Nie wystawiaj API drukarki do Internetu tylko po to, żeby uruchomić panel.

Zacznij od obserwacji: stabilny obraz, dotyk, temperatury i status, pliki, podgląd i kamera, jeśli jest dostępna. Pusty pulpit pokazuje „Touch and hold to add widgets”. Przytrzymaj wolne miejsce, dodaj widget i zapisz układ. Zmieniarki pozostają zablokowane; nie podłączaj CAN i nie wykonuj ich kalibracji. Ruch, grzanie, makra i drukowanie sterują prawdziwą drukarką, więc testuj je świadomie przy bezpiecznym stanie urządzenia.

## 6 / Błędy i zakres weryfikacji

Brak pliku instalacyjnego na serwerze, problem połączenia, serwera albo weryfikacji pokazuje okno z zaleceniem ponowienia później lub użycia SD. Błąd nie wybiera nowego obrazu startowego ani nie wykonuje aktywacji. Restart następuje dopiero po OK. Zachowaj dokładną treść komunikatu. Nie używaj --force, erase_flash, kopii innej płytki ani aktualizacji C6 do naprawy czarnego ekranu P4.

Przy braku obrazu zachowaj log, wersję/hash paczki, zdjęcia PCB/LCD i obserwacje podświetlenia oraz USB. Dalsze kroki i ewentualne odtworzenie własnej zweryfikowanej kopii wymagają sprawdzenia konkretnego przypadku. Nie ma automatycznego przycisku kasowania/odtwarzania.

Obie rodziny są przebudowane jako 1.0.8, ze swoim SDK i profilem LCD: starsza ESP-IDF 5.3.5, nowa ESP-IDF 6.1 z poprawionym zegarem DSI. Poprzednie paczki pozostają niezmienione. Dodano komunikat błędu instalacji sieciowej i wskazówkę pustego pulpitu. Działanie ekranu, dotyku i instalacji sieciowej wcześniejszego 1.0.7 na nowym P4 potwierdzono w relacji testera. Dokładne darmowe obrazy 1.0.8 wymagają jeszcze fizycznego testu na obu rewizjach; kompilacja, podpis i symulowany zapis tego nie zastępują.
