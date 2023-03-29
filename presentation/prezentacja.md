# Prezentacja dyplomowa

## Temat pracy

Tematem pracy jest projekt, implementacja i zautomatyzowane wdrożenie systemu do wizualizacji danych w chmurze Azure.

## Agenda

Plan prezentacji. Zacznę od wstępu i przedstawienia celu projektu, następnie omówię podstawowe pojęcia i organizacje, później zaś przedstawię infrastrukturę rozwiązania, oraz narzędzia używane przy automatycznych wdrożeniach. Po tym zaprezentuję witrynę internetową i omówię jej konstrukcję, a wtedy przejdę do wizualizacji danych. Na końcu przedstawię podsumowanie.

## Cel prezentacji

Niniejsza praca opisuje tworzenie strony internetowej w chmurze. Witryna ma za zadanie wizualizację danych.

Projekt miał na celu zbadanie technologii przy tworzeniu rozwiązań w chmurze.

## Pojęcia

Chmura obliczeniowa to model świadczenia usług przetwarzania danych przez Internet. Usługi chmurowe pozwalają na hostowanie aplikacji i przechowywanie danych, dostarczając niezbędnych zasobów wedle potrzeby, na żądanie, w krótkim czasie. Azure jest platformą chmury obliczeniowej firmy Microsoft, zawierającą ponad 200 różnych usług, od serwisów aplikacji, maszyn wirtualnych i przechowywania danych, aż po sztuczną inteligencję, Internet rzeczy i komunikację ze stacjami naziemnymi do wysyłania i odbierania danych z satelit.

Bank Światowy jest międzynarodową instytucją finansową, udzielającą pożyczek krajom rozwijającym się w celu redukcji ubóstwa. W mojej pracy wykorzystywałem dane udostępniane przez usługę World Bank Open Data, zawierające informacje na temat rozwoju.

## Infrastruktura

Zostały zaplanowane usługi i relacje między nimi, w celu uzyskania działającej witryny. Na infrastrukturę składały się usługi Azure SQL, Azure App Service, Azure Active Directory oraz Power BI. Postanowiłem wykorzystać rozwiązania typu Platform as a Service w celu uniknięcia konieczności zarządzania maszynami wirtualnymi. 

## Automatyczne wdrożenie

We współczesnych rozwiązaniach biznesowych poza przygotowaniem samej aplikacji, zalecaną praktyką jest również automatyzacja wdrożeń, w celu szybkiej reakcji na zmiany. Przygotowałem zestaw skryptów w PowerShell i Terraform, umożliwiając powtarzalne wdrożenia.

Terraform pozwala zastąpić skomplikowany zestaw instrukcji prostą listą deklaracji określającą zasoby w chmurze i relacje między nimi.

Program wdrożeń został podzielony na osiem osobnych skryptów, w celu zapewnienia większej przejrzystości i wygody w powtarzaniu operacji. Skrypty były odpowiedzialne za tworzenie infrastruktury chmury, ładowanie kopii zapasowej bazy danych, ładowanie raportu, oraz umieszczanie aplikacji na serwerze.

## Witryna

Stronę internetową napisałem w języku C#, z użyciem frameworka ASP.NET Core MVC, korzystając również z biblioteki Entity Framework Core do komunikacji z bazą danych. Witryna została umieszczona na serwerze Azure App Service.

< otworzyć stronę >

Witryna składa się z czterech elementów - ankiety, prezentacji wyników, prezentacji danych, oraz panelu administracyjnego. 

Ankieta jest dostępna dla wszystkich użytkowników strony. Podczas udzielania odpowiedzi na pytania, wpisy są automatycznie dodawane do bazy danych. Po zakończeniu ankiety, użytkownik otrzymuje komentarz do swoich odpowiedzi.

Prezentacja wyników wyświetla dotychczasowe statystyki ankiet - jakie odpowiedzi padały najczęściej i które były poprawne.

Prezentacja danych jest przedstawiona w postaci wykresów z Power BI App, osadzonych na stronie internetowej. Slajdy są interaktywne, co pozwala na eksplorację danych przez użytkownika.

Panel administracyjny jest dostępny tylko dla administratora strony, który musi się zalogować przy użyciu konta Azure Active Directory. Weryfikacja jest prosta, użytkownik musi być częścią grupy dzierżawy, która jest zdefiniowana w konfiguracji aplikacji. Panel administracyjny pozwala na dodawanie, edycję i usuwanie pytań oraz opisów wykresów. Dane są przechowywane w bazie w usłudze Azure SQL.

## Wizualizacja danych

Utworzyłem wizualizacje z użyciem następujących wskaźników:

- Współczynnik śmiertelności niemowląt. Została zaprezentowana animacja pokazująca zmiany w tych wskaźnikach dla różnych krajów na przestrzeni lat 1960-2020, porównanie wskaźników z lat 1980 i 2020 dla wybranych oraz dla wszystkich krajów świata, z możliwością filtrowania według grup dochodowych i regionów geograficznych.
- Współczynnik dzietności. Zostały przedstawione zmiany dla krajów świata w średniej liczbie dzieci na kobietę w latach 1960-2020.
- Zmiany w oczekiwanej długości życia. W ciagu ostatnich sześćdziesięciu lat, oczekiwana długość życia wzrosła dla wszystkich krajów świata, niekiedy nawet dwukrotnie. 
- Zmiana współczynnika skrajnego ubóstwa w latach 1980-2020. Skrajne ubóstwo jest definiowane przez Bank Światowy jako życie poniżej 2.15 dolara dziennie, z uwzględnieniem inflacji. W ciągu ostatnich czterdziestu lat, procent ludzi żyjących w skrajnym ubóstwie zmalał z 40% do 10%.

Wykresy zostały wykonane w celu uzyskania przejrzystej i interaktywnej prezentacji danych, z możliwością eksploracji przez użytkownika.

## Podsumowanie

W niniejszej pracy przedstawiłem wdrożenie przykładowej witryny internetowej w środowisku chmury Azure. Projekt pozwolił mi na rozeznanie się w technologiach używanych w procesach związanych z chmurą obliczeniową. Został zbadany potencjał narzędzia Terraform jako programu do automatycznego tworzenia infrastruktury chmurowej, PowerShell jako narzędzie do automatyzacji zadań, oraz usługi takie jak Azure App Service do aplikacji oraz Azure SQL do baz danych. Został również zbadany potencjał Power BI jako narzędzia do prezentacji danych.

Praca ta może służyć jako punkt wyjścia do bardziej zaawansowanych projektów w przyszłości.