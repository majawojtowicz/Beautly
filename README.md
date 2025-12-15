# SRS – Beautly (Specyfikacja Wymagań Oprogramowania)
Produkt: Beautly – inteligentna platforma rezerwacji usług beauty i wellness z modulem Self Care Day
Wersja produktu (docelowa dla SRS): MVP 1.0
Wersja dokumentu: 1.0
Autor: Maja Wojtowicz

1. Wstęp
1.1 Cel
Celem dokumentu jest zdefiniowanie jednoznacznych wymagań dla systemu Beautly (MVP 1.0), aby umożliwić:
planowanie prac projektowych i implementacji,


przygotowanie testów (akceptacyjnych / systemowych),


wspólne rozumienie zakresu między klientem a zespołem.


Beautly to platforma rezerwacji usług beauty/wellness z modułem Self-Care Day, który układa pełny dzień zabiegów na podstawie preferencji i dostępności terminów .

1.2 Wizja, zakres i cele produktu
Wizja:
Beautly łączy wygodę technologii z ideą dbania o siebie - pozwala planować wizyty w wielu salonach i zamienia self-care w łatwy nawyk .
Zakres:
konto użytkownika (rejestracja/logowanie, profil),


przegląd salonów i usług + filtry (kategoria, cena, lokalizacja),


rezerwacje i zarządzanie terminami dla klientów i salonów,


panel salonu: usługi, grafik, rezerwacje, dostępność,


Self-Care Day: automatyczne układanie planu zabiegów na jeden dzień z różnych salonów, z dopasowaniem slotów czasowych ,


opinie, ulubione, podstawowe rekomendacje
.


Cele biznesowe + KPI :
KPI-1: min. 100 aktywnych użytkowników w ciągu 2 miesięcy od uruchomienia


KPI-2 : min. 40% nowych użytkowników wróci w ciągu 30 dni


KPI-3: rejestracja trwa max 30 sekund i max 3 kroki


Poza zakresem :
płatności online i rozliczenia (np. BLIK, Apple Pay) – później,


czat klient–salon,


wideokonsultacje,


program lojalnościowy i subskrypcje,


dynamiczne ceny i promocje w czasie rzeczywistym.


1.3 Definicje, akronimy i skróty
SRS – Software Requirements Specification


MVP – Minimum Viable Product


Self-Care Day (SCD) – moduł układający cały dzień zabiegów na podstawie preferencji i dostępności


Slot – przedział czasowy dostępny do rezerwacji


Usługodawca / Salon – podmiot oferujący usługi beauty/wellness


Klient – użytkownik rezerwujący usługi


1.4 Przegląd dokumentu
Rozdział 2 opisuje system ogólnie (funkcje, role, ograniczenia, założenia). Rozdział 3 zawiera wymagania funkcjonalne w formacie user story + Given/When/Then. Rozdział 4 opisuje wymagania jakościowe (mierzalne) oraz kompromisy. Rozdział 5 – analiza porównawcza rynku. Dodatki: diagram przypadków użycia, persony, lista otwartych kwestii.

2. Opis ogólny
2.1 Główne funkcje produktu
Konta i profile (Klient, Salon, Administrator)


Katalog salonów i usług (wyszukiwanie, filtry)


Rezerwacje i kalendarz (dla klientów + salonów)


Self-Care Day (planowanie pakietu zabiegów z różnych salonów)


Opinie, ulubione, rekomendacje


Panel salonu (usługi, grafik, rezerwacje)


2.2 Klasy użytkowników
A) Klient (osoba rezerwująca)
cele: szybka rezerwacja, wygodne planowanie dnia, minimalna liczba kroków, brak „ręcznego dopasowywania” terminów


B) Salon / usługodawca
cele: zarządzanie grafikiem, usługami i rezerwacjami, minimalizacja pustych okienek, porządek w kalendarzu
C) Administrator / Moderator
cele: utrzymanie jakości i bezpieczeństwa platformy, moderacja treści (opinie, salony), obsługa zgłoszeń nadużyć oraz realizacja obowiązków RODO (eksport i usuwanie danych), zapewnienie zgodności działania systemu z regulaminem i przepisami prawa.

2.3 Ograniczenia projektowe
Ograniczenie technologiczne
Ograniczenie: System Beautly musi być zrealizowany jako aplikacja webowa z backendem w Python (Django) oraz frontendem w React / React Native.


Źródło: Wcześniejsze decyzje projektowe zespołu oraz kompetencje technologiczne członków zespołu.


Wpływ na architekturę:


Wymusza projektowanie architektury zgodnej z frameworkiem Django (np. MVC/MVT) oraz REST API jako warstwy komunikacyjnej.


Narzuca konieczność zaprojektowania czytelnego podziału odpowiedzialności pomiędzy frontendem a backendem oraz integracji z aplikacją mobilną.


Ograniczenie biznesowe
Ograniczenie: Zakres funkcjonalny wersji MVP musi być ograniczony do kluczowych funkcji rezerwacji oraz modułu Self-Care Day, bez obsługi płatności online.


Źródło: Ograniczony czas realizacji projektu oraz potrzeba szybkiej walidacji pomysłu produktowego.


Wpływ na architekturę:


Wyklucza integrację z zewnętrznymi systemami płatności (np. BLIK, Stripe, PayPal) w wersji MVP.


Wymusza projektowanie procesu rezerwacji bez transakcji finansowych, opierając się wyłącznie na zarządzaniu terminami.


Pozwala uprościć architekturę systemu i skupić się na stabilności oraz użyteczności kluczowych funkcji.



Ograniczenie prawne
Ograniczenie: System musi być zgodny z Rozporządzeniem o Ochronie Danych Osobowych (RODO), a dane osobowe użytkowników (klientów i salonów) muszą być przetwarzane zgodnie z obowiązującymi przepisami prawa UE.


Źródło: Prawo Unii Europejskiej (RODO).


Wpływ na architekturę:


Wymusza implementację mechanizmów realizacji praw użytkownika, takich jak prawo do usunięcia danych oraz prawo do ich eksportu.


Narzuca konieczność ograniczenia dostępu do danych osobowych wyłącznie do uprawnionych ról (np. administrator).


Wymaga logowania i audytowania operacji na danych wrażliwych oraz odpowiedniego zabezpieczenia bazy danych i komunikacji (np. szyfrowanie).


Ograniczenie organizacyjne
Ograniczenie: Projekt realizowany jest przez niewielki zespół studencki, pracujący w niepełnym wymiarze czasu.


Źródło: Charakter projektu akademickiego.


Wpływ na architekturę:


Wymusza prostą i czytelną architekturę systemu, łatwą do zrozumienia i utrzymania.


Ogranicza liczbę zaawansowanych komponentów infrastrukturalnych w wersji MVP.


Skłania do stosowania sprawdzonych rozwiązań i frameworków zamiast eksperymentalnych technologii.

2.4 Założenia projektowe
Założenie techniczne
Założenie: Zakładamy, że algorytm dopasowywania terminów w module Self-Care Day będzie w stanie wygenerować poprawny plan dnia dla użytkownika w czasie krótszym niż 5 sekund przy typowym obciążeniu systemu.


Ryzyko: Jeśli algorytm okaże się zbyt wolny lub nieefektywny, użytkownicy będą rezygnować z korzystania z funkcji Self-Care Day, co bezpośrednio wpłynie na kluczowy wyróżnik produktu i obniży retencję użytkowników.


Plan walidacji:


Co: Testy wydajności modułu Self-Care Day.


Jak: Uruchomienie algorytmu na zestawie danych testowych (wiele salonów, usług i slotów czasowych) oraz pomiar czasu generowania planu.


Kiedy: W drugim sprincie, przed pełną integracją modułu Self-Care Day z interfejsem użytkownika.


Kto: Backend developer.
Założenie dotyczące użytkownika lub biznesu
Założenie: Zakładamy, że użytkownicy końcowi będą skłonni zaplanować kompletny Self-Care Day w czasie nie dłuższym niż 2 minuty i przy użyciu maksymalnie kilku prostych kroków.


Ryzyko: Jeśli proces planowania okaże się zbyt złożony lub czasochłonny, użytkownicy będą porzucać funkcję Self-Care Day, co spowoduje niskie wykorzystanie kluczowej funkcjonalności i obniżenie wskaźników retencji.


Plan walidacji:


Co: Testy użyteczności procesu planowania Self-Care Day.


Jak: Przygotowanie klikalnego prototypu (np. w Figma) i przeprowadzenie testów z udziałem 5–7 użytkowników, mierząc czas wykonania zadania i liczbę błędów.


Kiedy: Przed rozpoczęciem implementacji finalnego interfejsu użytkownika dla modułu Self-Care Day.


Kto: Product Owner lub UX Designer.



Założenie organizacyjne
Założenie: Zakładamy, że zespół projektowy będzie w stanie regularnie dostarczać działające przyrosty funkcjonalności w iteracjach sprintowych trwających 2–3 tygodnie.


Ryzyko: Jeśli tempo pracy zespołu okaże się niestabilne, część zaplanowanych funkcji MVP może nie zostać dostarczona na czas, co ograniczy możliwość pełnej walidacji produktu.


Plan walidacji:


Co: Monitorowanie realizacji sprintów i wskaźnika ukończonych zadań.


Jak: Analiza tablicy zadań (np. Trello/Jira) oraz retrospektywy sprintów.


Kiedy: Po zakończeniu każdego sprintu.


Kto: Scrum Master lub lider zespołu.


Tytuł: Rejestracja konta użytkownika
Opis:
 Umożliwia nowym użytkownikom utworzenie konta w systemie Beautly.


Historyjka Użytkownika:


Jako nowy użytkownik,


chcę móc zarejestrować konto w systemie,


abym mógł korzystać z funkcji rezerwacji usług i planowania Self-Care Day.


Cel Biznesowy:
 Obniżenie bariery wejścia do systemu oraz realizacja celu szybkiego onboardingu użytkowników.


Warunki Wstępne:
 Użytkownik nie posiada jeszcze konta w systemie Beautly.


Warunki Końcowe:
 Konto użytkownika zostaje utworzone i użytkownik jest zalogowany w systemie.


Kryteria Akceptacji:



WF-AUTH-01: Pomyślna rejestracja użytkownika (Scenariusz Główny)


Opis: Użytkownik poprawnie zakłada konto.


Kryteria Akceptacji:


Given: Nie posiadam konta w systemie Beautly.


When: Podaję wymagane dane rejestracyjne (np. adres e-mail oraz hasło) i zatwierdzam formularz.


Then: Konto zostaje utworzone w systemie.


And: Zostaję automatycznie zalogowany do aplikacji.



WF-AUTH-02: Rejestracja z użyciem istniejącego adresu e-mail (Scenariusz Alternatywny)


Opis: System blokuje próbę rejestracji na istniejący adres e-mail.


Kryteria Akceptacji:


Given: Podaję adres e-mail, który jest już przypisany do innego konta.


When: Próbuję zakończyć proces rejestracji.


Then: System wyświetla komunikat o istniejącym koncie.


And: System proponuje przejście do logowania lub resetu hasła.



WF-AUTH-03: Niepoprawne dane rejestracyjne (Scenariusz Wyjątkowy)


Opis: System waliduje poprawność danych wejściowych.


Kryteria Akceptacji:


Given: Wprowadzam niepoprawne lub niekompletne dane rejestracyjne.


When: Próbuję zatwierdzić formularz.


Then: System wyświetla komunikat walidacyjny.


And: Konto nie zostaje utworzone.



Tytuł: Logowanie użytkownika
Opis:
 Umożliwia zarejestrowanym użytkownikom dostęp do systemu Beautly.


Historyjka Użytkownika:


Jako zarejestrowany użytkownik,


chcę móc zalogować się do systemu,


abym miał dostęp do swoich rezerwacji i funkcji personalizowanych.


Cel Biznesowy:
 Zapewnienie bezpiecznego dostępu do konta użytkownika oraz utrzymanie ciągłości korzystania z systemu.


Warunki Wstępne:
 Użytkownik posiada aktywne konto w systemie Beautly.


Warunki Końcowe:
 Użytkownik zostaje poprawnie zalogowany do systemu.


Kryteria Akceptacji:



WF-LOGIN-01: Pomyślne logowanie użytkownika (Scenariusz Główny)


Opis: Użytkownik loguje się przy użyciu poprawnych danych.


Kryteria Akceptacji:


Given: Posiadam aktywne konto w systemie Beautly.


When: Podaję poprawny adres e-mail i hasło.


Then: Zostaję zalogowany do systemu.


And: Uzyskuję dostęp do funkcji wymagających autoryzacji.



WF-LOGIN-02: Logowanie z niepoprawnym hasłem (Scenariusz Alternatywny)


Opis: System odrzuca niepoprawne dane logowania.


Kryteria Akceptacji:


Given: Posiadam konto w systemie Beautly.


When: Podaję niepoprawne hasło.


Then: System wyświetla komunikat o błędnych danych logowania.


And: Użytkownik pozostaje niezalogowany.



WF-LOGIN-03: Próba dostępu do funkcji bez logowania (Scenariusz Wyjątkowy)


Opis: System wymusza autoryzację dla funkcji wymagających konta.


Kryteria Akceptacji:


Given: Nie jestem zalogowany w systemie.


When: Próbuję uzyskać dostęp do funkcji wymagającej konta (np. rezerwacji).


Then: System przekierowuje mnie do ekranu logowania lub rejestracji.


Tytuł: Rezerwacja usługi beauty/wellness
Opis:
 Umożliwia klientom rezerwację wybranej usługi w salonie na konkretny termin.


Historyjka Użytkownika:


Jako klient,


chcę móc zarezerwować wybraną usługę w salonie,


abym miał potwierdzony termin wizyty bez konieczności kontaktu telefonicznego.


Cel Biznesowy:
 Uproszczenie procesu umawiania wizyt oraz zwiększenie liczby rezerwacji realizowanych przez platformę Beautly.


Warunki Wstępne:
 Użytkownik jest zalogowany w systemie jako klient.


Warunki Końcowe:
 Rezerwacja zostaje zapisana w systemie i jest widoczna zarówno dla klienta, jak i dla salonu.


Kryteria Akceptacji:



WF-REZ-01: Pomyślna rezerwacja usługi (Scenariusz Główny)


Opis: Klient rezerwuje usługę w dostępnym terminie.


Kryteria Akceptacji:


Given: Jestem zalogowanym klientem i przeglądam ofertę salonu.


And: Wybrana usługa posiada dostępne wolne sloty czasowe.


When: Wybiorę usługę, termin wizyty i kliknę przycisk „Rezerwuj”.


Then: Rezerwacja otrzymuje status „Potwierdzona”.


And: Termin zostaje oznaczony jako zajęty w grafiku salonu.


And: Rezerwacja jest widoczna w sekcji „Moje wizyty”.



WF-REZ-02: Rezerwacja zajętego terminu (Scenariusz Alternatywny)


Opis: System blokuje rezerwację terminu, który został zajęty przez innego użytkownika.


Kryteria Akceptacji:


Given: Jestem zalogowanym klientem i wybrałem termin wizyty.


And: Wybrany slot czasowy został zajęty w trakcie rezerwacji.


When: Próbuję potwierdzić rezerwację.


Then: System wyświetla komunikat o braku dostępności terminu.


And: System prosi o wybór innego dostępnego slotu.


And: Rezerwacja nie zostaje zapisana.



WF-REZ-03: Rezerwacja przez niezalogowanego użytkownika (Scenariusz Wyjątkowy)


Opis: System uniemożliwia dokonanie rezerwacji bez zalogowania.


Kryteria Akceptacji:


Given: Nie jestem zalogowany w systemie.


When: Próbuję zarezerwować usługę w wybranym terminie.


Then: System przekierowuje mnie do ekranu logowania lub rejestracji.


And: Rezerwacja nie zostaje utworzona.



Tytuł: Planowanie Self-Care Day
Opis:
 Umożliwia klientom zaplanowanie całego dnia zabiegów beauty/wellness poprzez automatyczne dopasowanie usług i dostępnych terminów.


Historyjka Użytkownika:


Jako klient,


chcę móc zaplanować Self-Care Day obejmujący kilka zabiegów,


abym nie musiał ręcznie dopasowywać terminów i lokalizacji.


Cel Biznesowy:
 Wyróżnienie platformy Beautly na tle konkurencji oraz zwiększenie zaangażowania i retencji użytkowników.


Warunki Wstępne:
 Użytkownik jest zalogowany w systemie jako klient.


Warunki Końcowe:
 System generuje plan dnia obejmujący zestaw zabiegów z przypisanymi terminami, gotowy do potwierdzenia.


Kryteria Akceptacji:



WF-SCD-01: Pomyślne wygenerowanie planu dnia (Scenariusz Główny)


Opis: Klient otrzymuje kompletny plan Self-Care Day.


Kryteria Akceptacji:


Given: Jestem zalogowanym klientem.


And: Wybrałem co najmniej dwa zabiegi oraz preferowany dzień.


When: Kliknę przycisk „Ułóż Self-Care Day”.


Then: System generuje plan dnia z kolejnością zabiegów i proponowanymi slotami czasowymi.


And: Każdy zabieg posiada przypisany salon i godzinę.



WF-SCD-02: Brak możliwości ułożenia pełnego planu (Scenariusz Alternatywny)


Opis: System informuje o braku możliwości pełnego dopasowania planu.


Kryteria Akceptacji:


Given: Jestem zalogowanym klientem i wybrałem zestaw zabiegów.


And: Dostępne terminy nie pozwalają na ułożenie kompletnego planu.


When: Próbuję wygenerować Self-Care Day.


Then: System informuje o problemie z dopasowaniem terminów.


And: System proponuje alternatywy (inny dzień lub zmniejszenie liczby zabiegów).



WF-SCD-03: Próba planowania przez niezalogowanego użytkownika (Scenariusz Wyjątkowy)


Opis: System wymaga zalogowania przed użyciem funkcji Self-Care Day.


Kryteria Akceptacji:


Given: Nie jestem zalogowany w systemie.


When: Próbuję skorzystać z funkcji Self-Care Day.


Then: System przekierowuje mnie do logowania lub rejestracji.


And: Plan dnia nie zostaje wygenerowany.


Tytuł: Zarządzanie grafikiem i rezerwacjami w Panelu Salonu
Opis:
 Umożliwia salonowi zarządzanie dostępnością usług, grafikiem pracy oraz rezerwacjami klientów.


Historyjka Użytkownika:


Jako przedstawiciel salonu,


chcę móc zarządzać grafikiem i rezerwacjami,


abym miał porządek w terminach i mógł efektywnie obsługiwać klientów.


Cel Biznesowy:
 Usprawnienie obsługi rezerwacji po stronie salonu oraz ograniczenie pustych okienek w grafiku.


Warunki Wstępne:
 Użytkownik jest zalogowany w systemie jako salon / usługodawca.


Warunki Końcowe:
 Grafik i rezerwacje salonu są aktualne i widoczne dla klientów w systemie Beautly.


Kryteria Akceptacji:



WF-SALON-01: Pomyślne ustawienie grafiku dostępności (Scenariusz Główny)


Opis: Salon ustawia dostępne dni i godziny pracy.


Kryteria Akceptacji:


Given: Jestem zalogowanym użytkownikiem z rolą salonu.


And: Posiadam zdefiniowane usługi w systemie.


When: Ustawiam godziny pracy oraz dostępność terminów w panelu salonu.


Then: Grafik zostaje zapisany w systemie.


And: Dostępne sloty czasowe są widoczne dla klientów.



WF-SALON-02: Przegląd rezerwacji klientów (Scenariusz Główny)


Opis: Salon przegląda listę nadchodzących rezerwacji.


Kryteria Akceptacji:


Given: Jestem zalogowanym użytkownikiem z rolą salonu.


When: Otwieram sekcję „Rezerwacje” w panelu salonu.


Then: Widzę listę wszystkich nadchodzących wizyt wraz z datą, godziną i usługą.


And: Rezerwacje są uporządkowane chronologicznie.



WF-SALON-03: Anulowanie rezerwacji przez salon (Scenariusz Alternatywny)


Opis: Salon może anulować rezerwację klienta.


Kryteria Akceptacji:


Given: Jestem zalogowanym użytkownikiem z rolą salonu.


And: Istnieje aktywna rezerwacja klienta.


When: Anuluję rezerwację w panelu salonu.


Then: Rezerwacja zmienia status na „Anulowana”.


And: Klient otrzymuje informację o anulowaniu rezerwacji.



WF-SALON-04: Konflikt terminów w grafiku (Scenariusz Wyjątkowy)


Opis: System blokuje możliwość ustawienia konfliktujących terminów.


Kryteria Akceptacji:


Given: Jestem zalogowanym użytkownikiem z rolą salonu.


When: Próbuję ustawić grafik powodujący nakładanie się terminów.


Then: System wyświetla komunikat o konflikcie terminów.


And: Zmiany w grafiku nie zostają zapisane.


