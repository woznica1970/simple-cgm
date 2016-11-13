#Simple CGM 2009
Copyright (c) 2016 <a href="mailto:simple.cgm.2009@gmail.com" title="Mariusz Woźnica">Mariusz Woźnica</a>

![logo](/Images/scanner-os.png)

>**Dedykacja**
 
>_**[Teresa Woźnica]**, grupa Facebook **[Cukrzyca typ 1 - odzyskajmy kolory zycia :)]**, za sformułowanie bardzo praktycznych oczekiwań funkcjonalnych w stosunku do  **Simple CGM 2009**, która powstała tylko dzięki Twojej inicjatywie i uporowi, przyjmij w tym miejscu gorące podziękowania za pomoc, inspirację oraz okazaną cierpliwość._
>
>_Twoje merytoryczne uwagi poparte zdrowym rozsądkiem, z perspektywy **Mamy** opiekującej się dzieckiem z CT1 w wieku szkolnym, pozwoliły zbudować napawdę proste i użyteczne narzędzie._


# Wstęp

**_Simple CGM 2009_**, to **_responsywna aplikacja webowa_** służąca do wizualizacji pomiarów glikemii na ekranach różnych urządzeń z dostępem do Internetu np. smartfonach. Wartości glikemii  pochodzą z sensora *[FreeStyle Libre]*, a odczytywane są przez aplikację *[Glimp]*, lub aplikację *[Libre Alarm]* połączoną z aplikacją *[xDrip+]*. To ostatnie rozwiązanie jest testowane przez **[Timi Koza]**. Wartości pomiarów poziomu glikemii są zapisywane następnie przez wybraną aplikację w ekosystemie *[Nightscout]* oraz usłudze *[Dropbox]*.

>Fakt, że **_Simple CGM 2009_** może odczytwać pomiary glikemii z ekosystemu **_[Nightscout]_** sprawia, że będzie można również za pomocą tej aplikacji wizualizować dane pochodzące z innych urządzeń i programów współpracujących z ekosystemem *[Nightscout]*.

W naszym przypadku, dziecko może skanować się zarówno za pomocą zegarka [Sony SmartWatch 3 SWR50], jak i za pomocą smartfonu [Sony Xperia E5]. Podczas pobytu w szkole, smartfon schowany jest do teczki, a dziecko skanuje się tylko zegarkiem. Nauczyciel natomiast, widzi pomiar glikemii na swoim prywatnym smartfonie za pomocą aplikacji **_[Simple CGM 2009 Edycja Szkolna]_**. Aplikacja *[Glimp]*, zainstalowana jednocześnie na obu powyższych urządzeniach, przesyła pomiar glikemii z zegarka, za pomocą smartfonu do ekosystemu *[Nightscout]* działającego w serwisie *[Azure]*. Sam ekosystem *[Nightscout]* przechowuje natomiast pomiary glikemii w bazie danych działającej w usłudze *[mLab]*. Równolegle aplikacja *[Glimp]* przesyła pomiar glikemii do pliku w formacie *_CSV_* zapisywanego w serwisie *[Dropbox]*.

>**Uwaga**
>
>**_Simple CGM 2009_** nie jest dostępna w serwisie [Google Play] lub [iTunes Store], i nie wymaga tradycyjnej instalacji na urządzeniu mobilnym. Opis jak uruchomić aplikację na smartfonie znajdziesz poniżej w cześci *[Instalacja]*.
>Na poniższym schemacie pragnę przedstawić relacje pomiędzy poszczególnymi elementami wchodzącymi w skład całego rozwiązania.
>
>**[Szymona Czapla]** i **[Timi Koza]**, serdecznie podziękowania dla Was za pomoc w opracowaniu poniższego schematu:

![schemat](/Images/Demo/schemat.jpg)

**Opis schematu**

**_Simple CGM 2009_** instaluje się w serwisie *[Azure]* jako tzw. **_[Aplikacja Sieci Web]_**, równolegle do ekosystemu  *[Nightscout]*. Aplikację można również zainstalować na dowolnym innym serwerze web typu **_[IIS  Windows® Server]_**. Aplikacja może prezentować pomiary glikemii, korzystając z poniższych wariantów odczytu danych:
 - czytając dane **jednocześnie** z bazy *[mLab]* w formacie [MongoDB] oraz z pliku w formacie *_CSV_* zapisywanego w serwisie *[Dropbox]*, tzw. opcja bezpieczna
 - czytając dane **tylko** z bazy *[mLab]* w formacie [MongoDB], tzw. opcja uniwersalna
 - czytając dane  **tylko** z pliku w formacie *_CSV_* zapisywanego w serwisie *[Dropbox]*, tzw. opcja szybka

>Dzięki opcji odczytu danych od dwóch niezależnych dostawców jednocześnie, zyskujesz większą gwarancję niezawodności działania systemu, ponieważ na wypadek awarii jednego ze źródeł danych, możesz w dalszym ciągu odczytać na odległość pomiar glikemii na swoim smartfonie ze źródła rezerwowego.

#Kompatybilność

**_Simple CGM 2009_**, to **_responsywna aplikacja webowa_**, którą możesz uruchamiać na dowolnym urządzeniu obsługującym przeglądarkę internetową z włączoną obsługą *JavaScript*, takim jak **komputer, tablet, smartfon**.
Działanie **_Simple CGM 2009_** przetestowałem w popularnych przeglądarkach **Chrome, Safari, Firefox, Opera, IE,** oraz w systemach operacyjnych **Android, iOS, Windows Phone**. Aplikacja działa prawidłowo na wszytkich współczesnych smartfonach popularnych producentów. Wydajność aplikacji zależy oczywiście od specyfikacji technicznej konkretnego smartfona oraz jakości połączenia do Internetu.

>Zachęcam użytkowników smartfonów **iPhone** do utworzenia skrótu do **_Simple CGM 2009_** na pulpicie za pomocą funkcji menu **_Dodaj do ekranu początkowego_** z przeglądarki Safari . Pozwoli to na uruchamianie aplikacji w **_trybie pełnoekranowym_**. Proszę tylko pamiętać, że aplikacja uruchomiona w trybie pełnoekranowym wymaga ponownego wpisania **Secret Key**. Podobna funkcjonalność jest również dostępna dla użytkowników smartfonów z systemem Android.

**_Simple CGM 2009_** wymaga do uruchomienia i pracy, abyś wcześniej posiadał poprawnie zainstalowane i skonfigurowane, poniższe aplikacje i serwisy:

- dla opcji bezpiecznej:
 - aplikację *[Glimp]*
 - ekosystem *[Nightscout]*
 - konto w serwisie *[Dropbox]*
- dla opcji uniwersalnej:
 - aplikację *[Libre Alarm]* wraz z aplikacją *[xDrip+]* 
 - ekosystem *[Nightscout]*
- dla opcji szybkiej:
 - aplikację *[Glimp]*
 - konto w serwisie *[Dropbox]*

>**Uwaga**
>
>Instalacja poszczególnych aplikacji i serwisów zależą tylko od Twoich specyficznych potrzeb i preferencji. Po instalacji i uruchomieniu **_Simple CGM 2009_** wystarczy bowiem wskazać, w jakiej opcji aplikacja ma pracować, oraz z których źródeł danych ma korzystać. Definiujesz te ustawienia za pomocą odpowiednich wartości kluczy **_Data.Source.Default_**, **_Data.Source.Switchable_** oraz **_Data.Model.Auto_** opisanych w dalszej części tego dokumentu.

>Pamiętaj, aby w aplikacji *[Glimp]* zdefiniować w menu **_Options\Remote glucose monitoring_** dwa konta *[Dropbox]* oraz *[Nightscout]*, jeżeli chcesz, aby aplikacja pracowała w tzw. opcji bezpiecznej.
> 

**_Simple CGM 2009_** uruchamiasz wpisując do przeglądarki internetowej **adres url**, zdefinowany przez Ciebie dla aplikacji podczas procesu instalacji w serwisie *[Azure]*. 

**_Simple CGM 2009_** nie jest aplikacją oficjalnie zatwierdzoną przez firmę [Abbott] i nie daje żadnej gwarancji co do poprawności odczytu wartości glikemii z z sensora *[FreeStyle Libre]* oraz nie jest przeznaczona jako substytut lekarza diabetologa. W przypadku jakichkolwiek pytań lub wątpliwości musisz skontaktować się ze swoim lekarzem specjalistą.

Instalując i uruchamiając aplikację **_Simple CGM 2009_** wyrażasz zgodę na jej używanie wyłącznie na własne ryzyko oraz akceptujesz warunki <a href="LICENSE.md">Licencji</a>.

W razie problemów z działaniem aplikacji lub pytań, proszę o wysłanie mi wiadomości email na adres:
><a href="mailto:simple.cgm.2009@gmail.com" title="simple.cgm.2009@gmail.com">simple.cgm.2009@gmail.com</a>.

Serdecznie dziękuję za wszystkie sugestie oraz uwagi związane z działaniem i zakresem funkcjonalnym  **_Simple CGM 2009_**.


# Wygląd i funkcjonalność

![monitor](Images/Demo/monitor.jpg)
![slupki](Images/Demo/slupki.jpg)
![monitor](Images/Demo/historia.jpg)
![poziomo](Images/Demo/poziomo.jpg)


Tak jak już wspominałem, **_Simple CGM 2009_** może zawsze pobierać wartość ostatniego pomiaru glikemii **równocześnie z dwóch źródeł** tzn. serwisu *[Dropbox]* oraz serwisu *[Azure]* w tzw. opcji bezpiecznej, a następnie aplikacja wyświetla ostatni pomiar glikemii ze źródła, które udostępnia w danej chwili bardzej bieżący wynik.
Zaobserwowałem, że źródło *[Dropbox]* odświeża się szybciej, niż źródło *[Azure]*. Czasami na wynik pomiaru glikemii ze źródła *[Azure]* trzeba czekać kilka minut. Dlatego taka funkcjonalność jest bardzo pomocna, jeżeli zależy nam na szybkim odczytaniu wartości ostatniego pomiaru glikemii, bez względu na źródło.

>Możesz oczywiście ustawić własny preferowany wariant źródła danych.

####Widok *Monitor* pokazuje:####

- centralnie u góry, jako dużą cyfrę, ostatni pomiar glikemii ze strzałkami trendów, jeżeli trendy są dostępne;</br>
- po lewej stronie, czas wyświetlanego pomiaru np. 85 min temu, oraz zmianę w stosunku do poprzedniego wyniku;</br>
- po prawej stronie, poziom hemoglobiny glikowanej wyliczany na podstawie średniej wartości glikemii dla wybranego zakresu czasu;</br>
- w ramce poniżej 3 wartości glikemii (minimalną, średnią, maksymalną) dla wybranego zakresu czasu;</br>
- wykres liniowy za wybrany okres czasu z dodatkowymi liniami. Linie czerwone dla oznaczenia wartości hipo/hiper oraz linie zielone dla oznaczenia granic (min/max) normalnego poziomu glikemii;</br>
- po dwukrotnym kliknięciu na wykres liniowy, zostanie wyświetlony wykres słupkowy, oraz zostanie odblokowane dodatkowe menu wyboru zakresu czasu w dniach, które jest dostępne tylko dla wykresu słupkowego;</br>
- u dołu ekrany, znajdziesz menu wyboru zakresu czasu w godzinach **3/6/12/24/48** lub dniach **7/14/30/60/90** oraz główne menu nawigacyjne;</br>

####Widok *Historia* pokazuje:####

- listę poszczególnych pomiarów zarejestrowanych przez sensor dla wybranego zakresu czasu;
- na liście moża odczytać również tzw. wartość RAW glikemii, na podstawie której, oblicza się wartość ostateczną glikemii.
- listę można sortować za pomocą przycisku *Sortuj*;
- przycisk *Góra* pozwala przewinąć listę automatycznie do góry;
- listę można filtrować wpisując do pola szukania np. **g100**, aby wyświetlić tylko pomiary glikemii o wartości równej 100, lub **12:30**, aby wyświetlić tylko pomiary z godz. 12:30;

Nad przyciskiem **_Odśwież_** widać w czerwonym polu ilość pomiarów glikemii zarejestrowanych przez sensor, dla wybranego zakresu czasu.

**_Widok poziomy_** pokazuje wykres powiększony do szerokości ekranu i jest dostępny, jeżeli urządzenie, na którym uruchomiona jest aplikacja ma włączony tryb autorotacji ekranu.

**_Simple CGM 2009_** udostępnia również 4 widoki dzienne , oraz 4 widoki nocne, które można wybrać w menu **_Ustawienia_** jako opcje **A/B/C/D** (barwy jasne) oraz **E/F/G/H** (barwy ciemne).

![skins](Images/Demo/skins.jpg)
![skins](Images/Demo/skinsL.jpg)

**_Simple CGM 2009_** pozwala również wybrać w menu **_Ustawienia_**, z którego źródło danych ma korzystać do odczytywania pomiarów glikemii. Masz do wybou trzy warianty, o których już wspominałem:

- **Tandem**, tzw. opcja bezpieczna, gdzie aplikacja czyta pomiary zarówno z usługi *[Dropbox]* oraz ekosystemu *[Azure]* z bazą *[mLab]*, dostępna tylko jeżeli używasz aplikacji [Glimp].
- **Dropbox**, tzw. opcja szybka, dostępna tylko jeżel używasz aplikacji [Glimp] oraz usługi [Dropbox].
- **Azure**, tzw. opcja uniwersalna, jeżeli używasz aplikacji [Glimp] lub [Libre Alarm] z [xDrip+] oraz ekosystemu *[Azure]* z bazą *[mLab]*.

>Możesz ustawić w **_Ustawieniach aplikacji_** w kluczu **Data.Source.Default** jaki wariant źródła danych chcesz zastosować:
- wartość klucza: **0** oznacza wariant **Tandem**
- wartość klucza: **1** oznacza wariant **Dropbox**
- wartość klucza: **2** oznacza wariant **Azure**

>Dodatkowo możesz ustawić w kluczu **Data.Source.Switchable** czy zmiana wariantu źródła danych jest możliwa dynamicznie z poziomu aplikacji:
- wartość klucza: **0** oznacza, że funkacja jest **Zablokowana**
- wartość klucza: **1** oznacza, że funkcja jest **Aktywna**

>Klucz **Data.Model.Auto** pozwala natomiast określić automatycznie z jakiej aplikacja pochodzą dane odczytywane ze źródła [Azure] / [mLab].
Pomiary pochodzące z aplikacji [Glimp] zawierają dodatkowo tzw.wartość RAW glikemii, czyli wartość glikemii zarejestrowanej przez sensor i nieprzetworzonej przez algorytmy korygujące aplikacji czytającej sensor.

W menu **_Ustawieniach_** widać również wartości kluczy zdefiniowane w sekcji *Ustawienia aplikacji* usługi **Azure** dla poszczególnych progów glikemii:

- dolnej normy glikemii, odpowiada kluczowi **Norm.Min**
- górnej normy glikemii, odpowiada kluczowi **Norm.Max**
- hipoglikemii, odpowiada kluczowi **Alert.Hipo**
- hiperglikemii, odpowiada kluczowi **Alert.Hiper**

Powyższe wartości służą do sterowania komunikatami wyświetlanymi w widoku **Monitor**.

Opis wszystkich kluczy stosowanych do konfiguracji aplikacji znajdziesz w dalszej części intrukcji w rodziale **_[Konfiguracja Usługi Azure]_**.

>**Bezpieczeństwo**
>
>Dostęp do odczytu pomiarów glikemii zabezpieczony jest za pomocą hasła dostępu tzw. **_Secret Key_**. Bez znajomości tego hasła nie moża odczytać danych z api aplikacji. Pozwala to zabezpieczyć pomiary gilkemii przed nieuprawnionym dostępem ze strony innych użytkowników Internetu, pod warunkiem używania w adresie url prefixu **HTTPS** zamiast **HTTP**, czyli inaczej mówiąc tzw. protokołu **SSL**. Taki bezpieczny tryb pracy jest automatycznie ustawiony tyllko dla aplikacji uruchamianej w usłudze [Azure]. Jeżeli uruchamiasz aplikację na innym serwerze, musi samemu zatroszczyć się o ten rodzaj zabezpieczenia. Pamiętaj, aby regularnie zmieniać twój **_Secret Key_** oraz chronić go przed osobami postronnymi.
>
>Pierwszy raz ustawiasz  *Secret Key* w konfiguracji usługi [Azure] w wartości klucza **Secret.Key**, natomiast drugi raz wpisujesz to samo hasło w aplikacji na Twoim urządzeniu. Hasło zapisuje się w aplikacji po naciśnięciu przycisku **_Zapisz_**.

```
Przycisk 'Reset' służy do przywrócenia ustawień domyślnych aplikacji.
Po użyciu przycisku 'Reset' należ jeszcze raz wpisać 'Secret Key'.
```
# Instalacja - Wstęp

Poniżej znajdziesz informacje jak zainstalować, skonfigurować i uruchomić **_Simple CGM 2009_** oraz wszystkie potrzebne usługi dodatkowe. Informacje te są natury technicznej i w związku z tym, mogą być trudne do zrozumienia dla osób bez doświadczenia informatycznego. Jeżeli masz problem z ich interpretacją lub wdrożeniem, najlepiej zwrócić się o pomoc do zaprzyjaźnionego i zaufanego informatyka, zwłaszcza, że podczas konfiguracji usługi **_[Azure]_** zostaniesz poproszony o podanie i zapisanie danych z Twojej karty kredytowej.

1. [Instrukcja](http://nightscout.pl/freestyle-libre/glimp/) instalacji aplikacji **_[Glimp]_**, służącej do skanowania sensora *[FreeStyle Libre]* za pomocą smartfonu lub smartwatcha w trybie ręcznym bez ciągłego monitoringu tzn. smartwatch jest noszony normalnie na nadgarstku. 
2. Instalacja aplikacji **_[Libre Alarm]_** służącej do skanowania sensora [FreeStyle Libre] za pomocą smartwatcha w trybie automatycznym CGM tzn. smartwatch jest przymocowany do sensora na ramieniu.
3. Instalacja aplikacji **_[xDrip+]_**, służącej do zapisywania wyniku pomiaru glikemii do ekosystemu [Azure] / [mLab], po wcześniejszym jego odczytaniu z sensora *[FreeStyle Libre]* przez **_[Libre Alarm]_** lub pośredniczący transmiter z innego rodzaju sensora.
4. Instalacja ekosystemu **_[Nightscout]_**, służącego do przechowywania i udostępniania pomiaru glikemii przez Internet:
 1. [Instrukcja](http://nightscout.pl/instalacja/github-konfiguracja/) instalacja konta **_[GitHub]_**, służącego do udostępniania kopii kodu źródłowego *[Nightscout]* oraz kopii kodu źrółowego **_Simple CGM 2009_** dla usługi *[Azure]*.
 2. [Instrukcja](http://nightscout.pl/instalacja/mlab-konfiguracja/) instalacja konta **_[mLab]_**, służącego do zapisywania, przechowywania i udostępniania pomiaru glikemii.
 3. [Instrukcja](http://nightscout.pl/instalacja/azure-konfiguracja/) instalacja usługi **_[Azure]_**, służącej do instalacji i uruchamiania ekosystemu *[Nightscout]* oraz **_Simple CGM 2009_**.
3. [Zakładanie](https://www.dropbox.com/login) konta **_[Dropbox]_**, służącego do **równoległego** lub **szybkiego** zapisywania, przechowywania i udostępniani pomiary glikemii.

>Zamiast konta w usłudze **_[GitHub]_** możesz użyć kont innych popularnych usług dostępnych w Internecie w celu przekopiowania kodu źródłowego **_Simple CGM 2009_** do serwisu **_[Azure]_**, takich jak:
>- [OneDrive](https://onedrive.live.com/about/pl-pl/)
>- [Dropbox]
>- [Bitbucket](https://bitbucket.org/)

>W taki przypadku musisz najpierw przekopiować [kod źródłowy] **_Simple CGM 2009_** do wybranego serwisu za pomocą dostępnych funkcji.

# Instalacja - Simple CGM 2009 #

### Konfiguracja konta *Dropbox* ###

####1. Sprawdzenie czy *[Glimp](http://nightscout.pl/freestyle-libre/glimp/)* zapisuje wyniki skanowania na koncie *[Dropbox](https://www.dropbox.com/login)*####

 1. Zainstaluj i skonfiguruj aplikację *[Glimp](http://nightscout.pl/freestyle-libre/glimp/)* według podanych powyżej instrukcji na smartfonie z włączonym czytnikiem NFC.
 2. Zeskanuj działający sensor *[FreeStyle Libre](http://www.freestylelibre.pl/)* za pomocą smartfonu z  włączoną aplikacją *[Glimp](http://nightscout.pl/freestyle-libre/glimp/)* i aktywnym połączeniem do Internetu.
 3. Zaloguj się do konta *[Dropbox](https://www.dropbox.com/login)* i sprawdź, czy widzisz katalog: ***/home/Aplikacje/Glimp***, oraz czy znajduje się w nim plik: ***GlicemiaNightscout.csv***.
 4. Jeżeli NIE widzisz danych z *[Glimp](http://nightscout.pl/freestyle-libre/glimp/)*, to sprawdź, czy konfiguracja *[Glimp](http://nightscout.pl/freestyle-libre/glimp/)* na smartfonie jest prawidłowa, a smartfon ma aktywne połączenie z Internetem.

Uwaga, czasami *[Dropbox](https://www.dropbox.com/login)* zapisuje pliki z aplikacji *[Glimp](http://nightscout.pl/freestyle-libre/glimp/)* w katalogu **Apps** zamiast w katalogu **Aplikacje**.

```
https://www.dropbox.com/home/aplikacje/glimp/GlicemiaNightscout.csv
lub
https://www.dropbox.com/home/apps/glimp/GlicemiaNightscout.csv
```

![dropbox1](Images/Demo/dropbox1.jpg)


####2. Pobranie *Dropbox Access Token* do późniejszego użycia w serwisie *[Azure](https://azure.microsoft.com/pl-pl/free/)*####

1. Przejdź do strony [Dropbox API Explorer download](https://dropbox.github.io/dropbox-api-v2-explorer/#files_download).
2. Kliknij przycik ***Get Token*** - token zostanie utworzony i pokazany w polu *Access Token*.
3. Wpisz do pola **_path_** ścieżkę dostępu do pliku *GlicemiaNightscout.csv* (zobacz przykład w ramce poniżej).
4. Naciśnij przycisk ***Submit Call*** i potwierdź chęć nadania uprawnień dostępu do żądanego katalogu i pliku.
5. *[Dropbox](https://www.dropbox.com/login)* powinien wyświetlić poniższy widok z klawiszem ***Download GlicemiaNightscout.csv***.

![dropbox2](Images/Demo/dropbox2.jpg)

Oznacza to, że wygenerowany token działa prawidłowo. Możesz teraz zapisać **_Dropbox Access Token_** znajdujący się w polu **_Access Token_**, tak abyś mógł potem użyć go podczas konfiguracji parametrów połączeń aplikacji w usłudze *[Azure](https://azure.microsoft.com/pl-pl/free/)*. 

Jeżeli **nie widzisz** powyższego ekranu, sprawdź czy prawidłowo wpisałeś ścieżkę dostępu w polu *path* oraz czy plik *GlicemiaNightscout.csv* znajduje się w podanym katalogu.

```
/aplikacje/glimp/GlicemiaNightscout.csv
lub
/apps/glimp/GlicemiaNightscout.csv
```

### Konfiguracja konta *[GitHub](https://github.com/)* ###

1. Zaloguj się na swoje konto [GitHub](https://github.com/).
2. Utwórz nowy **_Fork_** do repozytorium [https://github.com/woznica1970/simple-cgm-school](https://github.com/woznica1970/simple-cgm-school), postępując według [instrukcji](http://nightscout.pl/instalacja/github-konfiguracja/), punkt od 7 do 10, używając ***woznica1970/simple-cgm-school*** zamiast ***nightscout/cgm-remote-monitor***.

### Konfiguracja usługi *[Azure](https://portal.azure.com/)* ###

#### 1. Tworzenie nowej *Aplikacji Sieci Web* ####

1. Zaloguj się na swoje konto do usługi [Azure](https://portal.azure.com/).
2. Utwórz nową **_Aplikację Sieci Web_**, analogicznie jak przy tworzeniu *Aplikacji Sieci Web* dla *Nightscout* według [instrukcji](http://nightscout.pl/instalacja/azure-konfiguracja/), punkt 11. 
3. Użyj tej samej **_Subskrypcji_** co w przypadku aplikacji *Nightscout*, oraz 
4. Ten sam **_Plan/lokalizacji usługi App Service_**.
5. Nadajesz tylko nową **_Nazwę aplikacji_** oraz tworzysz nową **_Grupę zasobów_**. 
6. Możesz też przypiąć aplikację do pulpitu. 
7. Osobiście ustawiam **_App Insights_** jako wyłączone. 

Usługa *[Azure](https://portal.azure.com/)* na podstawie pola **_Nazwa aplikacji_** utworzy nowy adres **url** dla aplikacji **_Simple CGM 2009_**, który będziesz używał do uruchomiania aplikacji na smartfonie np. **_https://mojanazwaaplikacji.azurewebsites.net_**.

#### 2. Tworzenie kluczy w sekcji *Ustawienia aplikacji* ####

Utwórz poniższe klucze i ustaw odpowiednie wartości kluczy zgodnie z własnymi preferencjami, postępując według [instrukcji](http://nightscout.pl/instalacja/azure-konfiguracja/), punkt 22.

```
Norm.Min
Norm.Max
Alert.Hipo
Alert.Hiper
Time.Zone
Secret.Key
Data.Source.Default
Data.Source.Switchable
Data.Model.Auto
```

<span>![azureUstawienia](Images/Demo/azureUstawienia.jpg)</span>

#### 3. Konfiguracja trybu pracy aplikacji####

####_Data.Source.Default_####

- ustawiasz opcje czytania źródeł danych
- aby czytać dwa źródła danych, tzw. **opcja bezpieczna**, ustawiasz wartość klucza *Data.Source.Default* na **0**
- aby czytać tylko źródło **_[Dropbox]_**, tzw. **opcja szybka**, ustawiasz wartość klucza *Data.Source.Default* na **1**
- aby czytać tylko źródło **_[Azure]_**, tzw. **opcja uniwersalna**, ustawiasz wartość klucza *Data.Source.Default* na **2**

####_Data.Source.Switchable_####

- ustawiasz czy można zmieniać dynamicznie źródła danych z poziomu aplikacji
- aby **zablokować** dynamiczą zmianę źródeł danych ustawiasz wartość klucza *Data.Source.Default* na **0** 
- aby **aktywować** dynamiczą zmianę źródeł dwnanych ustawiasz wartość klucza *Data.Source.Default* na **1** 

####_Data.Model.Auto_####

- ustawiasz czy aplikacja ma **automatycznie** rozpoznawać, z jakiej aplikacji pochodzą dane np. [Glimp], czy też [xDrip+]
- aby **wyłączyć** rozpoznawanie, ustawiasz wartość klucza *Data.Model.Auto* na **false** 
- aby **aktywować** rozpoznawanie, ustawiasz wartość klucza *Data.Model.Auto* na **true**

#### 4. Tworzenie kluczy w sekcji *Parametry połączeń* ####

Utwórz poniższe klucze i ustaw odpowiednie wartości kluczy zgodnie z danymi z konta *[mLab]* oraz konta [DropBox].

```
Mongo.Connection.String
Mongo.Database
Mongo.Collection
Dropbox.Access.Token
Dropbox.File.Path
```

<span>![azurePolaczenia](Images/Demo/azurePolaczenia.jpg)</span>

Przykładowe wartości kluczy:

```
Mongo.Connection.String : mongodb://użytkownik:hasło@ds046939.mlab.com:46573/mojabazadanych
Mongo.Database : mojabazadanych
Mongo.Collection : mojakolekcja
Dropbox.Access.Token : QY-8ABIbye4JKJADUAyziFqDMVBHpE2S2Jb793PoM0mz287sdaiuashd&Iy0jMSRT2
Dropbox.File.Path : /aplikacje/Glimp/GlicemiaNightscout.csv
```

#### 5. Konfiguracja *Opcji wdrożenia* ####

1. Postępuj zgodnie z [instrukcją](http://nightscout.pl/instalacja/azure-konfiguracja/), punkt od 30 do 40.
2. Pamiętaj, aby podać swoje dane logowania do konta **_GitHub_** oraz wybrać odpowiedni *Projekt*: **simple-cgm-school** oraz *Rozgałęzienie*: **Master**

### Uruchomienie *Simple CGM 2009* na smartfonie ###

1. Wpisz **adres url** np. **_https://mojanazwaaplikacji.azurewebsites.net_**  w dowolnej przeglądarce internetowej zainstalowanej na Twoim urządzeniu.
2. Adres url znajdziesz na swoim koncie w usłudze *[Azure](https://portal.azure.com/)*.
3. Jeżeli aplikacja **_Simple CGM 2009_** została prawidłowo zainstalowana w usłudze *[Azure](https://portal.azure.com/)* to teraz powinna zostać wyświetlona strona startowa.
4. Kliknij u dołu ekranu na menu **_Ustawienia_**.
4. Wpisz w polu **_Secret Key_** to samo hasło, które ustawiłeś w wartości klucza *Secret.Key* w sekcji *Ustawienia aplikacji* podczas instalacji i konfiguracji **_Simple CGM 2009_** w usłudze *[Azure](https://portal.azure.com/)*  .
5. Następnie kliknij kolejno przyciski **_Zapisz_**, **_Monitor_**.

![ustawienia1](Images/Demo/ustawienia1.jpg)
![monitor](Images/Demo/monitor.jpg)

Jeżeli proces instalacji przebiegł prawidłowo, to powinieneś teraz zobaczyć na ekranie wartość glikemii z ostatniego skanowania oraz wykres liniowy. Jeżeli coś poszło nie tak, aplikacja wyświetli odpowiedni komunikat błędu.

W ramce poniżej znajdują się możliwe komunikaty błędów. W przypadku ich wystąpienia należy sprawdzić klucze i ich wartości w sekcji **Parametry połączeń** oraz w sekcji **Ustawienia aplikacji** usługi *[Azure](https://portal.azure.com/)*:

```
(MongoDB) Brak parametru połączenia -> brak jednego z kluczy Mongo.*, lub błąd w nazwie klucza
(MongoDB) Brak danych w kolekcji -> błędna wartość klucza Mongo.Collection
(MongoDB) Nieudane połączenie z bazą -> błędna wartość klucza Mongo.Connection.String
(MongoDB) Błędna nazwa serwera -> błędna wartość klucza Mongo.Connection.String
(MongoDB) Błędna nazwa bazy danych -> błędna wartość klucza Mongo.Connection.String lub Mongo.Database
(MongoDB) Niepoprawny format danych -> problem z bazą mLab. Napisz do mnie wiadomość email
(MongoDB) Niepoprawny secret key -> porównaj wartość klucza Secret.Key z hasłem użytym na smartfonie

(Dropbox) Brak parametru połączenia -> brak jednego z kluczy Dropbox.*, lub błąd w nazwie klucza
(Dropbox) Unieważniony access token -> błędna wartość klucza Dropbox.Access.Token
(Dropbox) Nie znaleziono pliku danych -> zobacz punktu 'Przejdź do strony Dropbox API Explorer download'
(Dropbox) Błędne żądanie -> napisz do mnie wiadomość email 
(Dropbox) Wystąpił nieznany błąd -> napisz do mnie wiadomość email 
(Dropbox) Niepoprawny access token -> błędna wartość klucza Dropbox.Access.Token
(Dropbox) Niepoprawny secret key -> porównaj wartość klucza Secret.Key z hasłem użytym na smartfonie
```

####Jednoczesne używanie wersji [Simple CGM 2009](https://github.com/woznica1970/simple-cgm) oraz wersji [Simple CGM 2009 Edycja Szkolna](https://github.com/woznica1970/simple-cgm-school)####

- wystarczy skonfigurować jedno wspólne konto dla obu aplikacji w usłudze *[Dropbox]*,
- należy skonfigurować dwie osobne aplikacje w usłudze *[Azure](https://azure.microsoft.com/pl-pl/free/)*,
- obie aplikacje mogą za to używać tych samych wartości dla kluczy:
 - **_Mongo.Connection.String_**
 - **_Mongo.Database_**
 - **_Mongo.Collection_**
 - **_Dropbox.Access.Token_**
 - **_Dropbox.File.Path_**
- zalecam ustawienie w obu aplikacjach różnych wartości dla klucza **_Secret.Key_**

Jeżeli znajdziesz w powyższym opisie jakieś błędy lub nieścisłości, dziękuję za przesłanie wiadomości na <a href="mailto:simple.cgm.2009@gmail.com" title="Mariusz Woźnica">ten adres email</a>.

Dziękuję i pozdrawiam,</br>
<a href="mailto:simple.cgm.2009@gmail.com" title="Mariusz Woźnica">Mariusz Woźnica</a>

>Dodatkowo zobacz aplikację mobilną **_[Simple CGM 2009 Edycja Szkolna]_** dla nauczycieli, w celu monitorowania glikemii u dziecka, z zachowaniem zasad ochrony prywatności tzn. aplikacja udostępnia tylko ostatni pomiar glikemii w określonych dniach i godzinach np. w czasie pobytu dziecka w szkole.


[Simple CGM 2009 Edycja Szkolna]: <https://github.com/woznica1970/simple-cgm-school#simple-cgm-2009-edycja-szkolna>
[Simple CGM 2009]: <https://github.com/woznica1970/simple-cgm#simple-cgm-2009>
[kod źródłowy]: <https://github.com/woznica1970/simple-cgm-school>
[Teresa Woźnica]: <http://www.facebook.com/teresa.woznica.58>
[Teresie]: <http://www.facebook.com/teresa.woznica.58)>
[Cukrzyca typ 1 - odzyskajmy kolory zycia :)]: <https://www.facebook.com/groups/140046209720733/>
[Szymona Czapla]: <https://www.facebook.com/szymon.czapla.75>
[Timi Koza]: <https://www.facebook.com/timi.koza>
[FreeStyle Libre]: <http://www.freestylelibre.pl/>
[Abbott]: <http://xidoneo.pl/> 
[Sony SmartWatch 3 SWR50]: <http://www.sonymobile.com/pl/products/smart-products/smartwatch-3-swr50/#yellow>
[Sony Xperia E5]: <http://www.sonymobile.com/pl/products/phones/xperia-e5/>
[Glimp]: <http://nightscout.pl/freestyle-libre/glimp/>
[Libre Alarm]: <https://play.google.com/store/apps/details?id=com.pimpimmobile.librealarm&hl=pl>
[xDrip+]: <http://nightscout.pl/freestyle-libre/xdrip/>
[Dropbox]: <https://www.dropbox.com/pl/>
[GitHub]: <https://github.com/>
[Nightscout]: <http://nightscout.pl/instalacja/>
[Azure]: <https://portal.azure.com/>
[mLab]: <Https://mlab.com/welcome/>
[MongoDB]: <https://docs.mongodb.com/>
[Google Play]: <https://play.google.com/store/apps?hl=pl>
[iTunes Store]: <http://www.apple.com/pl/itunes/charts/free-apps/>
[Instalacja]: <#instalacja---simple-cgm-2009>
[Konfiguracja Usługi Azure]: <#konfiguracja-usługi-azure>
[Aplikacja Sieci Web]: <https://azure.microsoft.com/pl-pl/services/app-service/web/>
[IIS  Windows® Server]: <https://www.iis.net/>