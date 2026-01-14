# Historia Zmian - Gdzie się ukryć PL

Aplikacja PWA do lokalizacji Punktów Schronienia w Polsce.

**Aktualna wersja:** 1.3.48

---

## Styczeń 2026

### 🔒 Bezpieczeństwo
- 14.01.2026 - Dodano rate limiting dla admin endpoints (max 5 req/min) - ochrona przed atakami brute-force
- 14.01.2026 - Poprawiono type safety w sync-weather.ts - zastąpiono Promise<any> przez Promise<unknown>

### 🐛 Naprawy błędów
- 14.01.2026 - Naprawiono type casting w monitoringu pogody - dodano timestamp do WeatherMetrics interface
- 14.01.2026 - Dodano TTL (7 dni) dla emergency cache schronisk - zapobiega pokazywaniu stale danych po długim czasie
- 14.01.2026 - Poprawiono error handling w useWakeLock - dodano identyfikację błędów DOMException
- 14.01.2026 - Usunięto TODO comment bez ticket reference z transformers.ts

### ✨ Nowe funkcje
- 14.01.2026 - Zwiększono częstotliwość synchronizacji schronisk (codziennie zamiast co tydzień) - nowsze dane będą widoczne następnego dnia
- 14.01.2026 - Dodano automatyczne odświeżanie cache pogody (co 15 minut dla 20 głównych miast Polski)
- 14.01.2026 - Dodano endpoint monitoringu aplikacji (GET /api/health) sprawdzający status bazy danych, Redis, pamięci i uptime
- 14.01.2026 - Dodano endpoint metryk cache (GET /api/admin/cache/metrics) z informacjami o hit rate i wydajności
- 13.01.2026 - Dodano przyciski kopiowania koordynatów i adresy w szczegółach schroniska
- 13.01.2026 - Dodano automatyczne łamanie długich tekstów w etykietach szczegółów
- 13.01.2026 - Dodano warunkowe zachowanie przycisku zgłaszania (mobile vs desktop)
- 13.01.2026 - Dodano bezpośrednie przekierowanie dla przycisku zgłaszania schroniska
- 12.01.2026 - Dodano przełącznik układu desktop/mobile w nawigacji
- 12.01.2026 - Dodano widget pogody z danymi hydrologicznymi na pulpicie
- 12.01.2026 - Dodano dedykowaną zakładkę pogody w lewym panelu desktop
- 12.01.2026 - Dodano narzędzia pomiarowe i przełączanie warstw mapy
- 12.01.2026 - Dodano wskaźnik ładowania dla ostrzeżeń hydrologicznych
- 12.01.2026 - Dodano pełną funkcjonalność mobilną do układu desktop
- 12.01.2026 - Dodano automatyczną detekcję urządzenia dla routingu desktop/mobile
- 09.01.2026 - Dodano integrację z czujnikami jakości powietrza ESA NASK (~1600 szkół)
- 08.01.2026 - Dodano walidację odległości 100km dla danych jakości powietrza
- 08.01.2026 - Dodano kompletne etykiety ARIA dla komponentów jakości powietrza
- 08.01.2026 - Dodano integrację jakości powietrza GIOŚ z obliczaniem indeksu zastępczego
- 08.01.2026 - Dodano rotacyjne batche dla pełnego pokrycia stacji pomiarowych
- 07.01.2026 - Dodano integrację pogodową IMGW z ulepszonym UI
- 07.01.2026 - Dodano obsługę przypadków brzegowych i testy dla modułu pogodowego
- 07.01.2026 - Dodano zakładkę pogody do nawigacji
- 07.01.2026 - Dodano planowanie układu desktop z motywem rządowym
- 03.01.2026 - Dodano śledzenie rozmiaru pobierania map offline w czasie rzeczywistym
- 03.01.2026 - Dodano wizualne wskaźniki postępu dla pobierania offline
- 02.01.2026 - Dodano wsparcie service workera w trybie deweloperskim

### 🐛 Poprawki błędów
- 14.01.2026 - Naprawiono przejścia między zakładkami (dodano brakujący tab 'uwaga' do indeksu)
- 13.01.2026 - Naprawiono wyświetlanie ostrzeżeń hydrologicznych (desktop)
- 13.01.2026 - Zmieniono układ etykiet na pionowy w karcie szczegółów
- 13.01.2026 - Ukryto przycisk przełącznika układu na urządzeniach mobilnych
- 12.01.2026 - Naprawiono pozycję kotwicy pinezki pomiarowej
- 12.01.2026 - Zapobiegano duplikacji pinezek pomiarowych
- 12.01.2026 - Przeniesiono useProgressiveShelters przed wywołania zwrotne
- 09.01.2026 - Zaktualizowano parsowanie indeksu GIOŚ API v1
- 08.01.2026 - Przesunięto useMemo przed wcześniejsze zwroty (React hooks)
- 08.01.2026 - Użyto odległości Haversine w wyszukiwaniu cache jakości powietrza
- 08.01.2026 - Zastąpiono pętlę O(n) zapytaniem przestrzennym PostGIS
- 07.01.2026 - Naprawiono błędy TypeScript w cache pogodowym i trasach
- 03.01.2026 - Naprawiono błędy pobierania kafli mapy offline
- 03.01.2026 - Naprawiono obsługę żądań range i plików audio przez service worker
- 03.01.2026 - Zapobiegano timeout service workera podczas długich pobierań
- 02.01.2026 - Naprawiono rozwiązywanie asynchronicznej konfiguracji Vite


### ⚡ Wydajność
- 14.01.2026 - Zoptymalizowano zużycie baterii GPS (adaptive accuracy: niska dokładność podczas chodzenia <1m/s, wysoka podczas jazdy >5m/s)
- 14.01.2026 - Ulepszono wydajność pobierania danych pogodowych (cache warming w tle dla głównych miast)
- 13.01.2026 - Zapobiegano niepotrzebnemu przeładowaniu schronisk przy przesuwaniu pinezki lokalizacji
- 12.01.2026 - Zoptymalizowano układ desktop dla kompleksowego wyświetlania schronisk

### ♻️ Refaktoryzacja
- 12.01.2026 - Usunięto przycisk Pomocy z panelu Quick Actions (desktop)
- 12.01.2026 - Usunięto przycisk Ustawień z górnego paska nawigacji (desktop)
- 12.01.2026 - Przeprojektowano lewy panel desktop z zakładkami i breadcrumbs
- 08.01.2026 - Dodano dexie, usunięto nieużywany @tailwindcss/vite
- 07.01.2026 - Usunięto funkcję historii/trendów pogodowych
- 06.01.2026 - Połączono zakładkę Ulubione z zakładką Lista (segmented control)

### 🔧 Konfiguracja
- 08.01.2026 - Dodano rate limiting do usługi synchronizacji GIOŚ API
- 07.01.2026 - Dodano narzędzia PostGIS i skrypty tabel PRG
- 06.01.2026 - Dodano uprawnienie "gh pr list" do ustawień
- 03.01.2026 - Dodano komendy npx do listy auto-zatwierdzania
- 03.01.2026 - Ulepszono formatowanie tsconfig.json
- 02.01.2026 - Uaktualniono wersję do 1.3.18

### 🎨 UI/UX
- 12.01.2026 - Ulepszone UI/UX desktop z gradientowymi nagłówkami i animacjami
- 12.01.2026 - Otwieranie zakładki Ulubione bezpośrednio po kliknięciu przycisku
- 08.01.2026 - Dostosowano padding w kartach ostrzeżeń pogodowych
- 07.01.2026 - Zintegrowano zakładkę pogody do nawigacji i zaktualizowano konfigurację
- 07.01.2026 - Usunięto poziomy padding z kart ostrzeżeń pogodowych
- 07.01.2026 - Ulepszono doświadczenie startowe aplikacji

### 🧪 Testy
- 08.01.2026 - Dodano kompleksowe testy jednostkowe dla calculateFallbackIndex
- 08.01.2026 - Dodano notyfikacje o błędach IndexedDB i graceful degradation
- 08.01.2026 - Filtrowano wartości NULL w zapytaniu pomiarów jakości powietrza
- 07.01.2026 - Dodano testy komponentów dla kart pogodowych
- 07.01.2026 - Dodano narzędzia seedowania bazy danych dla historii pogody

---

## Grudzień 2025

### ✨ Nowe funkcje
- 31.12.2025 - Dodano poprawioną obsługę komentarzy wielolinijkowych w service worker
- 31.12.2025 - Usunięto pozostałości uszkodzonych komentarzy JSDoc z service workera
- 30.12.2025 - Naprawiono kąt stożka kierunku w trybie mapy heading-up
- 30.12.2025 - Ulepszono niezawodność mechanizmu aktualizacji PWA
- 30.12.2025 - Przerwano nieskończoną pętlę aktualizacji PWA z fallbackiem hard refresh
- 30.12.2025 - Dodano fallback reload dla mechanizmu aktualizacji PWA
- 30.12.2025 - Naprawiono krytyczne i wysokie problemy bezpieczeństwa z przeglądu kodu
- 30.12.2025 - Dodano ekran ładowania z logo i paskiem postępu
- 30.12.2025 - Naprawiono luki bezpieczeństwa w zależnościach produkcyjnych
- 30.12.2025 - Usunięto nieużywany komponent access-code-screen
- 30.12.2025 - Zastąpiono pełnoekranowy splash ładowania subtelnym paskiem postępu
- 30.12.2025 - Dodano wsparcie safe-area dla notcha iPhone X+
- 30.12.2025 - Dodano persystencję poziomu zoomu mapy między sesjami
- 30.12.2025 - Zapobiegano resetowaniu ustawień przy powiadomieniach toast
- 29.12.2025 - Dodano wake lock i ulepszenia z przeglądu kodu
- 29.12.2025 - Dodano rotację mapy heading-up z przyciskiem kompasu
- 29.12.2025 - Ulepszono obsługę uprawnień GPS dla iOS Safari PWA
- 29.12.2025 - Ulepszono wiadomości strony offline dla lepszego UX
- 29.12.2025 - Scalono oczyszczanie i usuwanie rozwlekłych komentarzy
- 29.12.2025 - Usunięto rozwlekłe komentarze w stylu AI z kodu produkcyjnego
- 28.12.2025 - Zoptymalizowano wyszukiwanie cache w navigation handler
- 28.12.2025 - Zagwarantowano niestandardową stronę offline zamiast błędu Safari
- 28.12.2025 - Użyto wzorca fire-and-forget dla cache.put w navigation handler
- 28.12.2025 - Ulepszono obsługę offline dla iOS PWA cold start
- 28.12.2025 - Dodano fallback offline cold start dla iOS PWA
- 28.12.2025 - Zaimplementowano kompleksowe wsparcie trybu offline
- 27.12.2025 - Dodano auto-centrowanie GPS w czasie rzeczywistym dla mapy (jak Google Maps)
- 27.12.2025 - Naprawiono pętle przeładowywania przy starcie ("hiccup" problem)
- 26.12.2025 - Dodano wskaźnik ładowania do aplikacji przy starcie
- 26.12.2025 - Ulepszono wygląd strony internetowej przez inline critical styles
- 26.12.2025 - Zapobiegano wielokrotnej inicjalizacji aplikacji i migotaniu motywu
- 24.12.2025 - Ukryto pasek ładowania na ekranie tytułowym overlay
- 24.12.2025 - Uproszczono do Google Consent Mode v2 Basic Mode
- 24.12.2025 - Zaimplementowano Google Consent Mode v2 dla analityki
- 24.12.2025 - Naprawiono rozciąganie pasków ładowania na pełną szerokość desktop
- 24.12.2025 - Ulepszono jakość kodu: śledzenie GPS, typy, obsługa błędów
- 23.12.2025 - Ulepszono funkcjonalność offline z kompleksową stroną fallback
- 23.12.2025 - Zaktualizowano stronę offline aby użyć designu aplikacji
- 23.12.2025 - Dodano wyjaśnienie dlaczego aplikacja jest offline po zamknięciu
- 23.12.2025 - Zaktualizowano stronę offline aby poprawić styling i ładowanie danych
- 23.12.2025 - Ulepszono wskaźnik offline aby był mniej nachalni i szybciej znikał
- 23.12.2025 - Usunięto bramkę kodu dostępu z opisu aplikacji
- 23.12.2025 - Dodano pobieranie kafli mapy offline i synchronizację ulubionych
- 23.12.2025 - Priorytet GPS dla dokładności lokalizacji, fallback na IP lub cache
- 23.12.2025 - Zaktualizowano styl przycisku na jasnozielone tło
- 23.12.2025 - Dodano przycisk zgłaszania nowych schronisk w drawerze
- 23.12.2025 - Ulepszono komunikaty błędów lokalizacji z instrukcjami dla iOS Safari
- 23.12.2025 - Zaktualizowano ustawienia bezpieczeństwa aby zezwolić na skrypty analityczne
- 23.12.2025 - Ulepszono komunikaty błędów GPS z pomocnymi instrukcjami
- 23.12.2025 - Zaktualizowano wyszukiwanie adresu aby priorytetyzować relevancję nad odległością
- 23.12.2025 - Priorytetyzowano wyszukiwania miast przez ulepszenie logiki parsowania adresu
- 23.12.2025 - Ulepszono wydajność aplikacji i skalowalność dla wysokiego ruchu
- 23.12.2025 - Priorytetyzowano lokalną bazę danych nad zewnętrznym API dla wyszukiwań schronisk
- 23.12.2025 - Poprawnie konwertowano jednostki odległości dla szybszego ładowania mapy
- 23.12.2025 - Zaktualizowano wyszukiwanie schronisk aby użyć lokalnego endpointu bazy
- 23.12.2025 - Zmieniono synchronizację danych na cotygodniową w poniedziałki o 1:00
- 23.12.2025 - Użyto lokalnej bazy danych dla wyświetlania schronisk i POI
- 23.12.2025 - Dodano instrukcje instalacji i przycisk w ustawieniach
- 23.12.2025 - Dodano przycisk resetowania uprawnień GPS i odświeżania stanu lokalizacji
- 23.12.2025 - Ulepszono szybkość ładowania aplikacji i UX przez optymalizację wyszukiwania schronisk
- 23.12.2025 - Ulepszono stabilność aplikacji przez rozwiązanie ostrzeżeń konsoli
- 23.12.2025 - Wyłączono automatyczny banner instalacji PWA dla płynniejszego UX
- 23.12.2025 - Zaktualizowano politykę bezpieczeństwa aby zezwolić na style mapy i skrypty analityczne
- 23.12.2025 - Ulepszono szybkość ładowania schronisk przez zwiększenie promienia wyszukiwania
- 23.12.2025 - Zaktualizowano wskaźnik ładowania na pasek postępu
- 23.12.2025 - Zapewniono że kontrolki mapy są zawsze widoczne nad warstwami mapy
- 23.12.2025 - Skrócono publiczne ID schronisk do wyświetlania tylko pierwszych 10 znaków
- 23.12.2025 - Usunięto prompt otwierania aplikacji w Safari na iOS
- 23.12.2025 - Zatrzymano wielokrotne przeładowania aplikacji podczas developmentu
- 23.12.2025 - Dodano ustawienie trust proxy dla kompatybilności z reverse proxy
- 23.12.2025 - Zaktualizowano etykiety dostępności schronisk dla lepszego zrozumienia
- 23.12.2025 - Dodano automatyczną synchronizację danych i bezpieczny trigger ręczny
- 23.12.2025 - Zaplanowano codzienną synchronizację danych schronisk z ręcznym triggerem
- 23.12.2025 - Priorytetyzowano lokalną bazę danych dla pobierania danych schronisk
- 23.12.2025 - Dodano lokalną kopię zapasową bazy danych dla informacji o schroniskach
- 23.12.2025 - Dodano fallback do lokalnej bazy dla schronisk i poprawiono obliczenia odległości
- 23.12.2025 - Dodano lokalną kopię zapasową i fallback dla pobliskich schronisk
- 23.12.2025 - Dodano skrypt importu danych schronisk z pliku JSON
- 23.12.2025 - Dodano lokalną kopię zapasową bazy danych dla danych schronisk
- 22.12.2025 - Usunięto fallback API schronienia.replit.app
- 22.12.2025 - Zaktualizowano hook auto-bump wersji aby używał shared/version.ts
- 22.12.2025 - Dodano zieloną kolorystykę dla dostępności 24h w kartach schronisk
- 22.12.2025 - Dodano zielony zarys dla markerów schronisk dostępnych 24h
- 22.12.2025 - Zmieniono grubość zarysu markera 24h na 2px
- 22.12.2025 - Dodano czerwoną poświatę dla markerów schronisk dostępnych 24h
- 22.12.2025 - Dodano przyciski kopiowania dla adresu i koordynatów w szczegółach schroniska
- 22.12.2025 - Usunięto obcinanie tekstu w wynikach wyszukiwania adresu
- 22.12.2025 - Dodano MaxMind GeoIP2 jako starting position przy ładowaniu aplikacji
- 22.12.2025 - Dodano testy endpointu MaxMind GeoIP
- 22.12.2025 - Dodano MaxMind GeoIP2 jako fallback geolokalizacji
- 21.12.2025 - Zapobiegano nieskończonej pętli re-render powodującej odświeżanie co 0.5s
- 21.12.2025 - Zachowano stan paska wyszukiwania przy przełączaniu zakładek
- 21.12.2025 - Dodano bottom sheet przewodnika instalacji w ustawieniach
- 21.12.2025 - Usunięto funkcjonalność navigateToInstallGuide
- 21.12.2025 - Zapewniono że zakładka mapy jest aktywna po akceptacji zgody na cookies
- 21.12.2025 - Opóźniono prompty PWA i iOS Safari aby nie przerywać przepływu startowego
- 21.12.2025 - Wykluczono endpointy route i geocoding z rate limitingu
- 21.12.2025 - Ulepszono przepływ startowy aplikacji aby uniknąć wielokrotnych promptów
- 21.12.2025 - Ominięto cache Cloudflare CDN dla dynamicznych endpointów API
- 21.12.2025 - Ulepszono UX panelu wyszukiwania i ustawiono domyślną zakładkę na mapę
- 21.12.2025 - Dodano retry logic i ulepszono obsługę błędów dla obliczeń trasy
- 21.12.2025 - Pokazano pasek wyszukiwania adresu rozwinięty domyślnie na zakładce mapy
- 21.12.2025 - Zredukowano wysokość sheetu polityki prywatności do 75vh
- 21.12.2025 - Ulepszono scroll polityki prywatności i widoczność na mobile
- 21.12.2025 - Dodano ilustrację alarmu do artykułu sygnały alarmowe
- 21.12.2025 - Dodano przewodnik instalacji PWA ze screenshotami
- 21.12.2025 - Dodano cache na poziomie modułu do loadCategories()
- 21.12.2025 - Ograniczono szerokość tytułu aby wymusić truncation po 2-3 słowach
- 21.12.2025 - Wymuszone ograniczenia szerokości dla truncation tytułu
- 21.12.2025 - Naprawiono truncation tytułu z ellipsis
- 21.12.2025 - Poprawnie obcięto długie tytuły w widoku zagnieżdżonym
- 21.12.2025 - Dodano styling tabel z obsługą overflow
- 21.12.2025 - Włączono renderowanie markdown w liście kategorii
- 21.12.2025 - Dodano wsparcie markdown i linki pobierania w meta kategorii
- 21.12.2025 - Wyłączono flagę featured dla dwóch artykułów
- 21.12.2025 - Dodano wsparcie odtwarzania audio dla sygnałów alarmowych
- 21.12.2025 - Zmieniono ikony sekcji na zielone w zakładce pomocy
- 21.12.2025 - Zmieniono banner hero na zielony motyw w zakładce pomocy
- 21.12.2025 - Ulepszono wizualną hierarchię sekcji w zakładce pomocy
- 21.12.2025 - Zmieniono tytuł karty schroniska na "Dane szczegółowe:"
- 21.12.2025 - Zmieniono tytuł sheetu schroniska na "Dane szczegółowe:"
- 21.12.2025 - Dodano mechanizm retry dla PERMISSION_DENIED po aktualizacji SW
- 21.12.2025 - Dodano padding safe-area dla notcha/Dynamic Island iPhone
- 21.12.2025 - Zaktualizowano tekst ekranu tytułowego na "PUNKTY SCHRONIENIA"
- 21.12.2025 - Zaktualizowano terminologię z MTU na PS (Punkt Schronienia)
- 21.12.2025 - Dodano ikonę artykułu/kategorii do navbaru w widokach zagnieżdżonych
- 20.12.2025 - Dodano instrukcje uprawnień GPS specyficzne dla platformy
- 20.12.2025 - Zredukowano szerokość kontenera desktop do 800px i ukryto przycisk kompasu
- 20.12.2025 - Dodano favicon.ico dla wyników wyszukiwania Google
- 20.12.2025 - Zachowano stary cache gdy serwer zwraca błędy (403, 500)
- 20.12.2025 - Dodano splash screeny iOS, Navigation Preload i poprawione fallbacki offline
- 20.12.2025 - Zapobiegano agresywnemu czyszczeniu cache które psuje tryb offline
- 20.12.2025 - Dodano prompt dla użytkowników iOS aby otworzyć app w Safari
- 20.12.2025 - Zastosowano best practices cachowania PWA
- 20.12.2025 - Włączono assety poziomu root do precache SW
- 20.12.2025 - Cache zewnętrznych zasobów CDN dla pełnego offline UI
- 20.12.2025 - Naprawiono uruchamianie PWA offline z skrótu home screen
- 20.12.2025 - Dodano auto-detekcję zmiany wersji i force aktualizacji SW
- 20.12.2025 - Ulepszono niezawodność precache SW dla uruchamiania offline
- 20.12.2025 - Włączono pełne wsparcie offline PWA
- 19.12.2025 - Ulepszono handlery trybu offline i stabilność aplikacji
- 19.12.2025 - Ujednolicono komponenty do Konsta UI w ustawieniach
- 19.12.2025 - Usunięto duplikujący się safe-area-inset-bottom
- 19.12.2025 - Ograniczono szerokość aplikacji na desktop do 1440px
- 19.12.2025 - Poprawiono wyświetlanie dialogu GPS gdy Permissions API kłamie
- 19.12.2025 - Zmieniono terminologię MTU na PS (Punkty Schronienia)
- 18.12.2025 - Dodano auto bump wersji przy commicie
- 18.12.2025 - Krytyczne poprawki bezpieczeństwa i stabilności
- 18.12.2025 - Wyeksportowano helpery i typy wyszukiwania adresu
- 17.12.2025 - Poprawiono UX z przeglądu kodu dla wyszukiwania adresu
- 17.12.2025 - Ulepszenia UX średniego wysiłku (sekcja 4.2)
- 17.12.2025 - Dodano nawigację klawiaturową dla wyszukiwania adresu (Quick Win 3)
- 17.12.2025 - Dodano ostatnie destynacje nawigacji (Quick Win 2)
- 17.12.2025 - Dodano historię wyszukiwania (Quick Win 1 z analizy UX)
- 17.12.2025 - Dodano safe area inset dla notcha/Dynamic Island na iOS
- 16.12.2025 - Ulepszono wydajność geokodowania z Photon API i lepszym UX
- 16.12.2025 - Ulepszono UX wyszukiwania adresu według best practices
- 16.12.2025 - Dodano dynamiczne precache assetów poradników przez Vite plugin
- 16.12.2025 - Dodano obrazy poradników do precache SW dla wsparcia offline
- 16.12.2025 - Naprawiono scroll pozycję artykułu pomocy - użyto specyficznego atrybutu data
- 15.12.2025 - Lepsza responsywność navbaru i tabbaru dla ekranów 385px
- 15.12.2025 - Ulepszono responsywność mobile dla ekranów 385-400px
- 15.12.2025 - Responsive ulepszenia UI dla małych ekranów (<380px)
- 15.12.2025 - Przeprojektowanie zakładki Ustawienia z zakładką Pomoc i aktualizacjami treści poradników
- 13.12.2025 - Dodano animacje slide dla przejść między zakładkami
- 12.12.2025 - Dodano auto-detekcję aktualizacji PWA i auto-reload
- 12.12.2025 - Naprawiono renderowanie zakładek mobile pokazujące biały ekran
- 12.12.2025 - Zwiększono rate limit do 120 req/min dla wsparcia śledzenia GPS
- 12.12.2025 - Poprawki przeglądu kodu: bezpieczeństwo, wydajność i jakość kodu
- 12.12.2025 - Ulepszono offline i wydajność według przeglądu kodu
- 12.12.2025 - Dodano możliwość pobierania danych mapy dla użytku offline
- 12.12.2025 - Ulepszono stabilność wyświetlania schronisk podczas przełączania zakładek
- 11.12.2025 - Naprawiono problemy renderowania zakładek PWA (Lista/Ulubione pusty ekran)
- 11.12.2025 - Ulepszono centrowanie mapy przy wyborze adresu
- 11.12.2025 - Ulepszono centrowanie mapy dla wyboru adresu
- 11.12.2025 - Dodano okrąg dokładności do markera lokalizacji użytkownika
- 11.12.2025 - Ulepszono responsywność śledzenia lokalizacji przez obniżenie progu ruchu
- 10.12.2025 - Zezwolono na swobodny ruch mapy po wycentrowaniu na schronisku
- 10.12.2025 - Zapewniono że nawigacja zawsze działa czyniąc lokalizację użytkownika opcjonalną
- 10.12.2025 - Zezwolono na zoomowanie mapy gdy geolokalizacja jest włączona
- 10.12.2025 - Zaktualizowano marker lokalizacji użytkownika aby przypominał styl Google Maps
- 10.12.2025 - Przywrócono domyślną szybkość animacji dla przejść sheet
- 10.12.2025 - Spowolniono animację przesuwania dla ekranu kompasu
- 10.12.2025 - Dodano wskaźnik kierunku do markera lokalizacji użytkownika
- 10.12.2025 - Dodano detekcję zbliżania z feedback wizualnym do kompasu
- 09.12.2025 - Dodano animacje slide dla przejść między zakładkami
- 05.12.2025 - Naprawiono cache offline: pokazuj wszystkie cached schroniska posortowane po odległości
- 05.12.2025 - Dodano ADR-009 dla ulepszeń UX kontrolek mapy
- 05.12.2025 - Revert pan mapy w dół przy wyborze markera
- 05.12.2025 - Pan mapy w dół przy wyborze markera aby pokazać pełny popup
- 05.12.2025 - Toast notyfikacje zamykalne na kliknięcie
- 05.12.2025 - Przesunięto przycisk lokalizacji obok paska wyszukiwania
- 05.12.2025 - Skrócono pasek wyszukiwania aby zrobić miejsce dla przycisku lokalizacji
- 05.12.2025 - Przesunięto przycisk lokalizacji do górnego prawego rogu
- 05.12.2025 - Ulepszono ikonę przycisku lokalizacji i styling kontrolek zoomu
- 05.12.2025 - Przesunięto kontrolki zoomu mapy do dolnego prawego rogu i dodano czerwoną ikonę lokalizacji
- 05.12.2025 - Zreorganizowano kontrolki mapy aby zapobiec nakładaniu
- 05.12.2025 - Dodano pływający przycisk lokalizacji w górnym prawym rogu mapy
- 05.12.2025 - Przeprojektowano kontrolki mapy z pływającym UI i center-on-user
- 05.12.2025 - Navbar layout - logo po lewej, tytuł po prawej z konsekwentnym białym tekstem
- 05.12.2025 - Migrowano pozostałe użycia Z_INDEX do zmiennych CSS
- 05.12.2025 - Zaimplementowano architekturę CSS Grid Shell dla mobile layout
- 05.12.2025 - Naprawiono problemy mobile layout - z-index, viewport height, positioning tabbaru
- 05.12.2025 - Poprawki przeglądu kodu dla implementacji Konsta UI
- 05.12.2025 - Zaimplementowano Konsta UI dla mobile-first native look
- 05.12.2025 - Naprawiono nakładanie się Leaflet attribution na dolną nawigację
- 05.12.2025 - Ulepszono mobile UX: przycisk zamknięcia popup i pozycjonowanie legendy
- 05.12.2025 - Dodano dialog wyboru aplikacji nawigacji dla użytkowników iOS
- 05.12.2025 - Zaimplementowano ulepszenia RMD i UX/UI według przeglądu kodu
- 02.12.2025 - Ulepszono funkcjonalność offline przez cachowanie danych schronisk i aktualizację UI

### 🐛 Poprawki błędów
- 29.12.2025 - Usunięto rozwlekłe komentarze z komponentów GPS i mapy
- 29.12.2025 - Poprawiono obsługę GPS iOS według przeglądu kodu
- 29.12.2025 - Ulepszono UX strony offline według przeglądu kodu
- 28.12.2025 - Usunięto redundantną funkcję findCachedAppShell
- 28.12.2025 - Użyto Promise.all dla spójności migracji cache
- 28.12.2025 - Ulepszono obsługę offline iOS PWA według przeglądu kodu
- 27.12.2025 - Zresetowano lastAutoCenterPosRef gdy auto-centrowanie ponownie włączone
- 27.12.2025 - Poprawiono problemy z przeglądu kodu w GPS auto-centrowanie
- 27.12.2025 - Usunięto martwy kod z MapView
- 26.12.2025 - Naprawiono pętle przeładowywania przy starcie aplikacji
- 25.12.2025 - Naprawiono typ place_id NominatimResult aby pasował do odpowiedzi API
- 25.12.2025 - Usunięto konfliktujące no-store z cache przeglądarki w CDN-Cache-Control
- 24.12.2025 - Naprawiono testy aby pasowały do obecnej implementacji
- 24.12.2025 - Naprawiono typ place_id w NominatimResult
- 18.12.2025 - Naprawiono mapowanie etykiet accessibility dla "Określone godziny"
- 17.12.2025 - Naprawiono poprawki z przeglądu kodu dla UX wyszukiwania adresu
- 16.12.2025 - Naprawiono przegląd kodu: bezpieczeństwo, wydajność, jakość
- 15.12.2025 - Naprawiono responsywność mobile navbaru dla ekranów 400px
- 12.12.2025 - Naprawiono błąd TypeScript i asercję testu
- 11.12.2025 - Naprawiono rendering zakładek w trybie offline
- 05.12.2025 - Naprawiono błędy w obsłudze offline i pobieraniu schronisk


### ⚡ Wydajność
- 30.12.2025 - Zapisywano zoom tylko gdy faktycznie się zmienia
- 27.12.2025 - Zoptymalizowano auto-centrowanie GPS mapy
- 22.12.2025 - Zoptymalizowano wgrywanie punktów schronienia na mapę
- 21.12.2025 - Dodano auto-increment minor gdy patch osiągnie 100
- 12.12.2025 - Ulepszono wydajność i offline według przeglądu kodu
- 09.12.2025 - Ulepszono pozycjonowanie toastów i kontrolek mapy

### ♻️ Refaktoryzacja
- 30.12.2025 - Ulepszono architekturę CSS ekranu ładowania
- 30.12.2025 - Używano Vite mode dla warunkowego drop konsoli
- 30.12.2025 - Stripowano komentarze i console.log z produkcji
- 19.12.2025 - Ustawienia jako pełny ekran zamiast wysuwanego panelu
- 19.12.2025 - Ustawienia pod główną belką z logo
- 19.12.2025 - Ustawienia i Polityka Prywatności - spójny design
- 05.12.2025 - Migrowano stare wartości Z_INDEX do zmiennych CSS

### 🔧 Konfiguracja
- 21.12.2025 - Dodano uprawnienie "gh pr create" do Claude Code
- 20.12.2025 - Zmieniono grubość zarysu markera 24h (thicker 2px, potem green)
- 05.12.2025 - Dodano Konsta UI do projektu

### 🎨 UI/UX
- 20.12.2025 - Dodano klikalne ostrzeżenie GPS otwierające ustawienia
- 20.12.2025 - GPS error zwijany z instrukcjami przeglądarki
- 19.12.2025 - Naprawiono styling i ładowanie danych strony offline

### 🚀 Publikacja
- Regularne publikacje aplikacji (łącznie ~170 publikacji w grudniu 2025)

---

## Listopad 2025

_(Brak commitów w listopadzie)_

---

## Październik 2025

### ✨ Nowe funkcje
- 29.10.2025 - Dodano bramkę kodu dostępu dla celów demo z weryfikacją kodu
- 29.10.2025 - Dodano ekran kodu dostępu aby chronić aplikację kodem
- 28.10.2025 - Zaktualizowano rozmiar czcionki nagłówka mobile
- 28.10.2025 - Resetowano widok mapy i trasę gdy lokalizacja użytkownika jest aktualizowana
- 28.10.2025 - Ulepszono interakcje z mapą i wyświetlanie ładowania
- 27.10.2025 - Ulepszono kompatybilność przeglądarki przez precomputing wartości kolorów OKLCH
- 27.10.2025 - Dodano definicje kolorów dla obramowań
- 27.10.2025 - Pokazano postęp ładowania podczas inicjalizacji mapy i pobierania danych
- 27.10.2025 - Dodano wizualny wskaźnik postępu ładowania mapy i etapów
- 27.10.2025 - Ulepszono animację paska postępu z płynniejszymi przejściami
- 27.10.2025 - Ulepszono wyszukiwanie adresu aby rozpoznawać popularne skróty ulic
- 27.10.2025 - Dodano możliwość pokazywania tras pieszych przez klikanie na markery mapy
- 27.10.2025 - Dodano przycisk czyszczenia trasy na widoku mapy
- 27.10.2025 - Dodano funkcjonalność wyświetlania tras do schronisk bezpośrednio z mapy
- 27.10.2025 - Dodano możliwość wyświetlania trasy na mapie po kliknięciu markera schroniska
- 27.10.2025 - Dodano sposób bezpiecznego logowania użytkowników
- 27.10.2025 - Dodano początkowe assety dla aplikacji webowej shelter finder
- 27.10.2025 - Dodano opcję dodawania skrótu aplikacji do pulpitu telefonu lub komputera
- 27.10.2025 - Dodano funkcjonalność instalacji aplikacji na ekranie głównym
- 27.10.2025 - Ustawiono nazwę i ikonę aplikacji dla lepszego brandingu
- 27.10.2025 - Zaktualizowano nazwę aplikacji i ikonę na "Gdzie się ukryć PL"
- 27.10.2025 - Ulepszono przepływ żądania uprawnień GPS w zakładce "Więcej"
- 27.10.2025 - Dodano zarządzanie uprawnieniami GPS w zakładce ustawień
- 27.10.2025 - Ulepszono dostęp do lokalizacji GPS i obsługę błędów na mobile
- 27.10.2025 - Dodano nowy sposób bezpiecznego logowania użytkowników
- 27.10.2025 - Ulepszono legendę mapy aby zapewnić dostępność z minimalną wysokością
- 27.10.2025 - Dodano zwijalną legendę mapy z ulepszonymi elementami wizualnymi
- 27.10.2025 - Podniesiono dolny pasek nawigacji aby pojawiał się nad elementami mapy
- 26.10.2025 - Ulepszono funkcjonalność wyszukiwania adresu z zaawansowanym parsowaniem
- 26.10.2025 - Dostosowano ranking wyników wyszukiwania według zaufania parsowania adresu
- 26.10.2025 - Ulepszono wyszukiwanie adresu aby obsługiwać brakujące wartości confidence score
- 26.10.2025 - Ulepszono wyświetlanie wyników wyszukiwania z kodowanymi kolorami poziomami zaufania
- 26.10.2025 - Ulepszono parsowanie adresu dla skrzyżowań i dodano fallback zapytania
- 26.10.2025 - Ulepszono dokładność wyszukiwania adresu i geokodowania z zaawansowanym parsowaniem
- 26.10.2025 - Ulepszono wyszukiwanie adresu przez obsługę różnych formatów wejściowych
- 26.10.2025 - Ulepszono mobile layout i spacing dla lepszego UX
- 26.10.2025 - Dostosowano layout aplikacji aby zapobiec blokowaniu mapy na mobile
- 26.10.2025 - Umożliwiono stałą widoczność dolnego menu dla użytkowników
- 26.10.2025 - Zaktualizowano aplikację jako PWA z designem mobile-first inspirowanym rządem
- 26.10.2025 - Dodano polskie tłumaczenia dla elementów UI i nawigacji
- 26.10.2025 - Dostosowano aplikację do użytku mobilnego z funkcjami PWA i motywem rządowym
- 26.10.2025 - Dodano sposób wyświetlania informacji o konkretnych schroniskach MTU na mapie
- 26.10.2025 - Ulepszono obsługę błędów nawigacji i logikę wyświetlania na stronie głównej
- 26.10.2025 - Ulepszono nawigację do schronisk używając lokalizacji podanej przez użytkownika
- 26.10.2025 - Zaktualizowano aplikację aby pokazać schroniska na mapie
- 26.10.2025 - Dodano możliwość wyświetlania wyników wyszukiwania na mapie
- 26.10.2025 - Zaktualizowano promień wyszukiwania i włączono klikanie mapy aby ustawić lokalizację
- 26.10.2025 - Zaktualizowano ścieżki ikon aby używać wewnętrznych lokalizacji assetów
- 26.10.2025 - Dodano ikony reprezentujące różne typy schronisk na mapie
- 26.10.2025 - Dodano kolorowe ikony aby różnicować typy schronisk na mapie
- 26.10.2025 - Dodano unikalne ikony dla różnych typów schronisk na mapie
- 26.10.2025 - Dodano ikony dla różnych typów schronisk i POI
- 26.10.2025 - Ulepszono interakcję z mapą i wyświetlanie markerów dla pobliskich schronisk
- 26.10.2025 - Ulepszono pobieranie lokalizacji przez użycie cached data
- 26.10.2025 - Ulepszono dokładność lokalizacji dla nawigacji i wyświetlania
- 26.10.2025 - Dodano ikony dla elementów interfejsu użytkownika i brandingu aplikacji
- 26.10.2025 - Ulepszono nawigację przez dokładne przekazywanie szczegółów lokalizacji do Google Maps
- 26.10.2025 - Naprawiono problem z niepoprawnym uruchamianiem nawigacji po kliknięciu przycisku nawigacji
- 26.10.2025 - Ulepszono nawigację do schronisk przez uwzględnienie obecnej lokalizacji użytkownika
- 26.10.2025 - Dostosowano strukturę danych aby pasowała do oczekiwanego schematu aplikacji
- 26.10.2025 - Dodano wsparcie języka ukraińskiego dla interfejsu aplikacji
- 26.10.2025 - Dodano dostęp offline i ulepszono UX z service workers
- 26.10.2025 - Dodano możliwość zaznaczania i odznaczania schronisk jako ulubione
- 26.10.2025 - Dodano możliwość wyświetlania tras pieszych do schronisk na mapie
- 26.10.2025 - Dodano możliwość wyszukiwania konkretnych adresów używając integracji mapy
- 26.10.2025 - Dodano możliwości filtrowania schronisk w aplikacji
- 26.10.2025 - Dodano podstawowe komponenty i strukturę layoutu dla aplikacji shelter finder
- 26.10.2025 - Commit początkowy

### 🐛 Poprawki błędów
- 29.10.2025 - Zaktualizowano nazwę systemu na ekranie kodu dostępu na MTU testing
- 28.10.2025 - Naprawiono problemy z renderowaniem mapy i początkową lokalizacją
- 27.10.2025 - Ulepszono obsługę lokalizacji i ładowanie mapy na mobile
- 27.10.2025 - Usunięto skróty ulic z wyszukiwania adresu w polskim

### 🚀 Publikacja
- Regularne publikacje aplikacji (łącznie ~10 publikacji w październiku 2025)

---

**Ostatnia aktualizacja:** 13.01.2026

**Łączna liczba zmian:** 876 commitów

---

## Legenda Kategorii

- ✨ **Nowe funkcje** - Nowa funkcjonalność dodana do aplikacji
- 🐛 **Poprawki błędów** - Naprawa istniejących problemów
- 📝 **Dokumentacja** - Zmiany w dokumentacji projektu
- 🎨 **UI/UX** - Ulepszenia interfejsu użytkownika i doświadczenia
- ⚡ **Wydajność** - Optymalizacje i ulepszenia wydajności
- ♻️ **Refaktoryzacja** - Zmiany strukturalne kodu bez wpływu na funkcjonalność
- 🔧 **Konfiguracja** - Zmiany w plikach konfiguracyjnych
- 🌐 **Tłumaczenia** - Zmiany językowe i i18n
- 📦 **Zależności** - Aktualizacje bibliotek i pakietów
- 🚀 **Publikacja** - Publikacje wersji produkcyjnych
- 🧪 **Testy** - Dodanie lub modyfikacja testów

---

## Kluczowe Kamienie Milowe

### 2025
- **Październik 2025**: Pierwsze publiczne wydanie aplikacji PWA
- **Grudzień 2025**: Integracja Konsta UI, PWA offline, architektura CSS Grid

### 2026
- **Styczeń 2026**: Integracja IMGW pogoda, GIOŚ jakość powietrza, układ desktop
