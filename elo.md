# SRS – Beautly (Specyfikacja Wymagań Oprogramowania)

**Produkt:** Beautly – inteligentna platforma rezerwacji usług beauty i wellness z modułem **Self Care Day**  
**Wersja produktu (docelowa dla SRS):** MVP 1.0  
**Wersja dokumentu:** 1.0  
**Autor:** Maja Wojtowicz  

---

## Spis treści
1. [Wstęp](#1-wstęp)  
   1.1 [Cel](#11-cel)  
   1.2 [Wizja, zakres i cele produktu](#12-wizja-zakres-i-cele-produktu)  
   1.3 [Definicje, akronimy i skróty](#13-definicje-akronimy-i-skróty)  
   1.4 [Przegląd dokumentu](#14-przegląd-dokumentu)  
2. [Opis ogólny](#2-opis-ogólny)  
   2.1 [Główne funkcje produktu](#21-główne-funkcje-produktu)  
   2.2 [Klasy użytkowników](#22-klasy-użytkowników)  
   2.3 [Ograniczenia projektowe](#23-ograniczenia-projektowe)  
   2.4 [Założenia projektowe](#24-założenia-projektowe)  
3. [Wymagania funkcjonalne (FR)](#3-wymagania-funkcjonalne-fr)  
   3.1 [Rejestracja konta użytkownika](#31-rejestracja-konta-użytkownika)  
   3.2 [Logowanie użytkownika](#32-logowanie-użytkownika)  
   3.3 [Rezerwacja usługi beauty/wellness](#33-rezerwacja-usługi-beautywellness)  
   3.4 [Planowanie Self-Care Day](#34-planowanie-self-care-day)  
   3.5 [Panel salonu: grafik i rezerwacje](#35-panel-salonu-grafik-i-rezerwacje)  
   3.6 [Priorytetyzacja wymagań dla MVP](#36-priorytetyzacja-wymagań-dla-mvp)  
4. [Atrybuty jakościowe (NFR)](#4-atrybuty-jakościowe-nfr)  
   4.1 [Priorytety atrybutów jakościowych](#41-priorytety-atrybutów-jakościowych)  
   4.2 [Scenariusze jakościowe](#42-scenariusze-jakościowe)  
   4.3 [Analiza kompromisów architektonicznych](#43-analiza-kompromisów-architektonicznych)  
5. [Odkrywanie i analiza wymagań (Analiza porównawcza)](#5-odkrywanie-i-analiza-wymagań-analiza-porównawcza)  
6. [Dodatki](#6-dodatki)  
   6.1 [Persony użytkowników](#61-persony-użytkowników)  

---

## 1. Wstęp

### 1.1 Cel
Celem dokumentu jest zdefiniowanie jednoznacznych wymagań dla systemu **Beautly (MVP 1.0)**, aby umożliwić:
- planowanie prac projektowych i implementacji,
- przygotowanie testów (akceptacyjnych / systemowych),
- wspólne rozumienie zakresu między klientem a zespołem.

Beautly to platforma rezerwacji usług beauty/wellness z modułem **Self-Care Day**, który układa pełny dzień zabiegów na podstawie preferencji i dostępności terminów.

### 1.2 Wizja, zakres i cele produktu

**Wizja**  
Beautly łączy wygodę technologii z ideą dbania o siebie — pozwala planować wizyty w wielu salonach i zamienia self-care w łatwy nawyk.

**Zakres (MVP 1.0)**  
- konto użytkownika (rejestracja/logowanie, profil),
- przegląd salonów i usług + filtry (kategoria, cena, lokalizacja),
- rezerwacje i zarządzanie terminami dla klientów i salonów,
- panel salonu: usługi, grafik, rezerwacje, dostępność,
- **Self-Care Day**: automatyczne układanie planu zabiegów na jeden dzień z różnych salonów, z dopasowaniem slotów czasowych,
- opinie, ulubione, podstawowe rekomendacje.

**Cele biznesowe + KPI**
- **KPI-1:** min. **100 aktywnych użytkowników** w ciągu **2 miesięcy** od uruchomienia.
- **KPI-2:** min. **40%** nowych użytkowników wróci w ciągu **30 dni**.
- **KPI-3:** rejestracja trwa max **30 sekund** i max **3 kroki**.

**Poza zakresem (kolejne wersje)**
- płatności online i rozliczenia (np. BLIK, Apple Pay),
- czat klient–salon,
- wideokonsultacje,
- program lojalnościowy i subskrypcje,
- dynamiczne ceny i promocje w czasie rzeczywistym.

### 1.3 Definicje, akronimy i skróty
- **SRS** – Software Requirements Specification  
- **MVP** – Minimum Viable Product  
- **Self-Care Day (SCD)** – moduł układający cały dzień zabiegów na podstawie preferencji i dostępności  
- **Slot** – przedział czasowy dostępny do rezerwacji  
- **Usługodawca / Salon** – podmiot oferujący usługi beauty/wellness  
- **Klient** – użytkownik rezerwujący usługi  

### 1.4 Przegląd dokumentu
- Rozdział 2 opisuje system ogólnie (funkcje, role, ograniczenia, założenia).  
- Rozdział 3 zawiera wymagania funkcjonalne w formacie *user story* + kryteria akceptacji **Given/When/Then**.  
- Rozdział 4 opisuje wymagania jakościowe (mierzalne) oraz kompromisy.  
- Rozdział 5 – analiza porównawcza rynku.  
- Dodatki: persony użytkowników.

---

## 2. Opis ogólny

### 2.1 Główne funkcje produktu
- Konta i profile (Klient, Salon, Administrator)
- Katalog salonów i usług (wyszukiwanie, filtry)
- Rezerwacje i kalendarz (dla klientów + salonów)
- Self-Care Day (planowanie pakietu zabiegów z różnych salonów)
- Opinie, ulubione, rekomendacje
- Panel salonu (usługi, grafik, rezerwacje)

### 2.2 Klasy użytkowników

**A) Klient (osoba rezerwująca)**  
- **Cele:** szybka rezerwacja, wygodne planowanie dnia, minimalna liczba kroków, brak ręcznego dopasowywania terminów.

**B) Salon / usługodawca**  
- **Cele:** zarządzanie grafikiem, usługami i rezerwacjami, minimalizacja pustych okienek, porządek w kalendarzu.

**C) Administrator / Moderator**  
- **Cele:** utrzymanie jakości i bezpieczeństwa platformy, moderacja treści (opinie, salony), obsługa zgłoszeń nadużyć, realizacja obowiązków RODO (eksport i usuwanie danych), zgodność działania z regulaminem i przepisami prawa.

### 2.3 Ograniczenia projektowe

#### Ograniczenie technologiczne
- **Ograniczenie:** system musi być aplikacją webową z backendem w **Python (Django)** oraz frontendem w **React / React Native**.  
- **Źródło:** wcześniejsze decyzje projektowe zespołu i kompetencje technologiczne.  
- **Wpływ na architekturę:**
  - architektura zgodna z Django (MVC/MVT) oraz **REST API** jako warstwa komunikacyjna,
  - czytelny podział odpowiedzialności frontend/backend oraz integracja z aplikacją mobilną.

#### Ograniczenie biznesowe
- **Ograniczenie:** w MVP zakres ograniczony do rezerwacji oraz SCD, **bez płatności online**.  
- **Źródło:** ograniczony czas realizacji i potrzeba szybkiej walidacji pomysłu.  
- **Wpływ na architekturę:**
  - brak integracji z systemami płatności w MVP,
  - proces rezerwacji bez transakcji finansowych,
  - uproszczenie architektury i skupienie na stabilności procesów krytycznych.

#### Ograniczenie prawne
- **Ograniczenie:** zgodność z **RODO** (UE) – przetwarzanie danych osobowych zgodnie z prawem.  
- **Źródło:** przepisy UE (RODO).  
- **Wpływ na architekturę:**
  - mechanizmy realizacji praw użytkownika (eksport/usunięcie danych),
  - kontrola dostępu do danych wg ról,
  - logowanie i audyt operacji na danych wrażliwych + zabezpieczenie bazy i komunikacji (np. szyfrowanie).

#### Ograniczenie organizacyjne
- **Ograniczenie:** mały zespół studencki, praca w niepełnym wymiarze.  
- **Źródło:** charakter projektu akademickiego.  
- **Wpływ na architekturę:**
  - prosta, czytelna architektura, łatwa w utrzymaniu,
  - ograniczenie liczby zaawansowanych komponentów infrastrukturalnych w MVP,
  - preferencja dla sprawdzonych frameworków/rozwiązań.

### 2.4 Założenia projektowe

#### Założenie techniczne
- **Założenie:** algorytm dopasowywania terminów w SCD generuje plan w czasie **< 5 s** przy typowym obciążeniu.  
- **Ryzyko:** zbyt wolne działanie obniży użycie kluczowej funkcji i retencję.  
- **Plan walidacji:**
  - **Co:** testy wydajności SCD  
  - **Jak:** uruchomienie na danych testowych (wiele salonów/usług/slotów) i pomiar czasu  
  - **Kiedy:** sprint 2 (przed pełną integracją UI)  
  - **Kto:** backend developer

#### Założenie użytkownika / biznesu
- **Założenie:** użytkownicy ułożą Self-Care Day w czasie **≤ 2 min** i w kilku prostych krokach.  
- **Ryzyko:** złożoność procesu → porzucenia i niskie wykorzystanie SCD.  
- **Plan walidacji:**
  - **Co:** testy użyteczności procesu SCD  
  - **Jak:** klikalny prototyp (np. Figma) + testy 5–7 osób, pomiar czasu i błędów  
  - **Kiedy:** przed implementacją finalnego UI SCD  
  - **Kto:** Product Owner / UX Designer

#### Założenie organizacyjne
- **Założenie:** zespół dostarcza działające przyrosty w sprintach **2–3 tygodnie**.  
- **Ryzyko:** niestabilne tempo → niedostarczenie części funkcji MVP.  
- **Plan walidacji:**
  - **Co:** monitorowanie realizacji sprintów  
  - **Jak:** analiza tablicy zadań (Trello/Jira) + retrospektywy  
  - **Kiedy:** po każdym sprincie  
  - **Kto:** Scrum Master / lider zespołu

---

## 3. Wymagania funkcjonalne (FR)


### 3.1 Rejestracja konta użytkownika

**Opis:** Umożliwia nowym użytkownikom utworzenie konta w systemie Beautly.  

**User story**  
Jako **nowy użytkownik**, chcę móc **zarejestrować konto**, abym mógł korzystać z rezerwacji usług i planowania Self-Care Day.

**Cel biznesowy:** obniżenie bariery wejścia i szybki onboarding.  
**Warunki wstępne:** użytkownik nie posiada konta.  
**Warunki końcowe:** konto utworzone, użytkownik zalogowany.

**Kryteria akceptacji**
- **WF-AUTH-01 (Scenariusz główny): Pomyślna rejestracja**  
  - **Given:** nie posiadam konta w Beautly  
  - **When:** podaję wymagane dane (np. e-mail, hasło) i zatwierdzam formularz  
  - **Then:** konto zostaje utworzone  
  - **And:** zostaję automatycznie zalogowany

- **WF-AUTH-02 (Alternatywny): Rejestracja na istniejący e-mail**  
  - **Given:** podaję e-mail przypisany do innego konta  
  - **When:** próbuję zakończyć rejestrację  
  - **Then:** system wyświetla komunikat o istniejącym koncie  
  - **And:** proponuje logowanie lub reset hasła

- **WF-AUTH-03 (Wyjątkowy): Niepoprawne dane**  
  - **Given:** wprowadzam niepoprawne lub niekompletne dane  
  - **When:** zatwierdzam formularz  
  - **Then:** system wyświetla komunikat walidacyjny  
  - **And:** konto nie zostaje utworzone

### 3.2 Logowanie użytkownika

**Opis:** Umożliwia zarejestrowanym użytkownikom bezpieczny dostęp do systemu.  

**User story**  
Jako **zarejestrowany użytkownik**, chcę móc **zalogować się**, abym miał dostęp do rezerwacji i funkcji personalizowanych.

**Cel biznesowy:** bezpieczny dostęp i ciągłość korzystania.  
**Warunki wstępne:** użytkownik posiada aktywne konto.  
**Warunki końcowe:** użytkownik zalogowany.

**Kryteria akceptacji**
- **WF-LOGIN-01 (Główny): Pomyślne logowanie**  
  - **Given:** posiadam aktywne konto  
  - **When:** podaję poprawny e-mail i hasło  
  - **Then:** zostaję zalogowany  
  - **And:** mam dostęp do funkcji wymagających autoryzacji

- **WF-LOGIN-02 (Alternatywny): Błędne hasło**  
  - **Given:** posiadam konto  
  - **When:** podaję niepoprawne hasło  
  - **Then:** system wyświetla komunikat o błędnych danych  
  - **And:** pozostaję niezalogowany

- **WF-LOGIN-03 (Wyjątkowy): Dostęp bez logowania**  
  - **Given:** nie jestem zalogowany  
  - **When:** próbuję wejść do funkcji wymagającej konta (np. rezerwacji)  
  - **Then:** system przekierowuje do logowania/rejestracji

### 3.3 Rezerwacja usługi beauty/wellness

**Opis:** Umożliwia klientom rezerwację wybranej usługi na konkretny termin.  

**User story**  
Jako **klient**, chcę móc **zarezerwować usługę**, abym miał potwierdzony termin bez kontaktu telefonicznego.

**Cel biznesowy:** uproszczenie umawiania wizyt i wzrost rezerwacji z platformy.  
**Warunki wstępne:** użytkownik jest zalogowany jako klient.  
**Warunki końcowe:** rezerwacja zapisana i widoczna dla klienta i salonu.

**Kryteria akceptacji**
- **WF-REZ-01 (Główny): Pomyślna rezerwacja**  
  - **Given:** jestem zalogowanym klientem i przeglądam ofertę salonu  
  - **And:** usługa ma wolne sloty  
  - **When:** wybieram usługę, termin i klikam „Rezerwuj”  
  - **Then:** rezerwacja ma status „Potwierdzona”  
  - **And:** termin oznaczony jako zajęty w grafiku salonu  
  - **And:** rezerwacja widoczna w „Moje wizyty”

- **WF-REZ-02 (Alternatywny): Slot zajęty w trakcie rezerwacji**  
  - **Given:** wybrałem termin  
  - **And:** slot został zajęty w trakcie procesu  
  - **When:** próbuję potwierdzić rezerwację  
  - **Then:** system informuje o braku dostępności  
  - **And:** prosi o wybór innego slotu  
  - **And:** rezerwacja nie zostaje zapisana

- **WF-REZ-03 (Wyjątkowy): Rezerwacja bez logowania**  
  - **Given:** nie jestem zalogowany  
  - **When:** próbuję zarezerwować usługę  
  - **Then:** system przekierowuje do logowania/rejestracji  
  - **And:** rezerwacja nie zostaje utworzona

### 3.4 Planowanie Self-Care Day

**Opis:** Umożliwia klientom zaplanowanie dnia zabiegów poprzez automatyczne dopasowanie usług i terminów.  

**User story**  
Jako **klient**, chcę zaplanować **Self-Care Day** obejmujący kilka zabiegów, abym nie musiał ręcznie dopasowywać terminów i lokalizacji.

**Cel biznesowy:** wyróżnik produktu + wzrost zaangażowania i retencji.  
**Warunki wstępne:** użytkownik zalogowany jako klient.  
**Warunki końcowe:** system generuje plan dnia do potwierdzenia.

**Kryteria akceptacji**
- **WF-SCD-01 (Główny): Wygenerowanie planu**  
  - **Given:** jestem zalogowany  
  - **And:** wybrałem min. 2 zabiegi i preferowany dzień  
  - **When:** klikam „Ułóż Self-Care Day”  
  - **Then:** system generuje plan z kolejnością i slotami  
  - **And:** każdy zabieg ma przypisany salon i godzinę

- **WF-SCD-02 (Alternatywny): Brak pełnego dopasowania**  
  - **Given:** wybrałem zestaw zabiegów  
  - **And:** dostępne terminy nie pozwalają na pełny plan  
  - **When:** próbuję wygenerować plan  
  - **Then:** system informuje o problemie dopasowania  
  - **And:** proponuje alternatywy (inny dzień / mniej zabiegów)

- **WF-SCD-03 (Wyjątkowy): SCD bez logowania**  
  - **Given:** nie jestem zalogowany  
  - **When:** próbuję użyć SCD  
  - **Then:** system przekierowuje do logowania/rejestracji  
  - **And:** plan nie zostaje wygenerowany

### 3.5 Panel salonu: grafik i rezerwacje

**Opis:** Umożliwia salonowi zarządzanie dostępnością, grafikiem oraz rezerwacjami.  

**User story**  
Jako **przedstawiciel salonu**, chcę zarządzać grafikiem i rezerwacjami, abym miał porządek w terminach i efektywnie obsługiwał klientów.

**Cel biznesowy:** usprawnienie obsługi po stronie salonu i redukcja pustych okienek.  
**Warunki wstępne:** użytkownik zalogowany jako salon/usługodawca.  
**Warunki końcowe:** grafik i rezerwacje aktualne i widoczne dla klientów.

**Kryteria akceptacji**
- **WF-SALON-01 (Główny): Ustawienie grafiku**  
  - **Given:** jestem zalogowany jako salon  
  - **And:** mam zdefiniowane usługi  
  - **When:** ustawiam godziny pracy i dostępność  
  - **Then:** grafik zapisuje się w systemie  
  - **And:** sloty są widoczne dla klientów

- **WF-SALON-02 (Główny): Przegląd rezerwacji**  
  - **Given:** jestem zalogowany jako salon  
  - **When:** otwieram „Rezerwacje”  
  - **Then:** widzę listę nadchodzących wizyt (data, godzina, usługa)  
  - **And:** lista jest uporządkowana chronologicznie

- **WF-SALON-03 (Alternatywny): Anulowanie rezerwacji przez salon**  
  - **Given:** jestem zalogowany jako salon  
  - **And:** istnieje aktywna rezerwacja  
  - **When:** anuluję rezerwację  
  - **Then:** status zmienia się na „Anulowana”  
  - **And:** klient otrzymuje informację o anulowaniu

- **WF-SALON-04 (Wyjątkowy): Konflikt terminów w grafiku**  
  - **Given:** jestem zalogowany jako salon  
  - **When:** ustawiam grafik powodujący nakładanie terminów  
  - **Then:** system zgłasza konflikt  
  - **And:** zmiany nie są zapisane

### 3.6 Priorytetyzacja wymagań dla MVP

**Wzór priorytetu:**  
`Priorytet = (Korzyść + Kara) / (Koszt + Ryzyko)`

**Tabela priorytetyzacji funkcji**
| Funkcja (kandydat do MVP) | Korzyść | Kara | Koszt | Ryzyko | Priorytet |
|---|---:|---:|---:|---:|---:|
| Rejestracja konta | 13 | 21 | 5 | 3 | 4.25 |
| Logowanie | 8 | 13 | 3 | 2 | 4.20 |
| Rezerwacja usługi | 21 | 21 | 8 | 8 | 2.63 |
| Self-Care Day (MVP) | 21 | 21 | 8 | 8 | 2.63 |
| Przegląd salonów i filtrowanie | 13 | 21 | 8 | 5 | 2.62 |
| Panel salonu: grafik + rezerwacje | 21 | 21 | 13 | 8 | 2.00 |
| Powiadomienia o rezerwacji (e-mail/push) | 13 | 13 | 8 | 5 | 2.00 |
| Ulubione + opinie | 8 | 8 | 5 | 5 | 1.60 |
| Self-Care Day (pełna wersja) | 21 | 13 | 13 | 13 | 1.31 |

**Uwaga do definicji SCD**
- **Self-Care Day (MVP Lite):** generowanie planu + propozycje slotów (bez: dojazdu, pełnej optymalizacji wielu wariantów, rezerwacji wszystkiego „naraz”).  
- **Self-Care Day (pełna wersja):** rozbudowany algorytm, więcej ograniczeń i wariantów, wyższe ryzyko techniczne.

**Wybór zakresu MVP (na podstawie priorytetu)**
- Rejestracja konta
- Logowanie
- Przegląd salonów i filtrowanie
- Rezerwacja usługi
- Panel salonu: grafik + rezerwacje
- Powiadomienia o rezerwacji
- Self-Care Day (MVP) — jako wyróżnik w ograniczonym zakresie

**Poza MVP (kolejna iteracja)**
- Ulubione + opinie
- Self-Care Day (pełna wersja)

**Krótkie uzasadnienie**
- Rejestracja i logowanie są niezbędne dla procesów kluczowych (rezerwacje, historia wizyt).  
- Rezerwacja + panel salonu to rdzeń biznesowy platformy.  
- Self-Care Day jest wyróżnikiem, ale pełna wersja ma wysoki koszt/ryzyko — dlatego w MVP dostarczana jest wersja ograniczona.

---

## 4. Atrybuty jakościowe (NFR)

### 4.1 Priorytety atrybutów jakościowych
- **Użyteczność (Usability):** szybki onboarding, mało kroków, intuicyjny proces rezerwacji i SCD.  
- **Niezawodność (Reliability):** brak podwójnych rezerwacji, spójność danych, odporność na częściowe awarie.  
- **Wydajność (Performance):** szybkie wyszukiwanie i generowanie planu SCD.  
- **Bezpieczeństwo (Security):** ochrona danych osobowych i informacji o wizytach, zgodność z RODO.  
- **Dostępność (Availability):** możliwość rezerwacji 24/7.  
- **Skalowalność (Scalability):** obsługa wzrostu liczby użytkowników/salonów/rezerwacji bez spadku jakości.  
- **Modyfikowalność (Modifiability):** łatwy rozwój (MVP → kolejne wersje: płatności, lojalność itp.).

### 4.2 Scenariusze jakościowe

#### A) Użyteczność (Onboarding)
| Element | Opis |
|---|---|
| Źródło bodźca | Nowy użytkownik |
| Bodziec | Rozpoczęcie rejestracji |
| Artefakt | Moduł rejestracji |
| Środowisko | Typowe obciążenie |
| Reakcja | Użytkownik kończy rejestrację bez błędów |
| Miara reakcji | **≤ 30 s**, **≤ 3 kroki** dla **95%** przypadków; dropout **< 20%** |

#### B) Niezawodność (Rezerwacje)
| Element | Opis |
|---|---|
| Źródło bodźca | Klient |
| Bodziec | Potwierdzenie rezerwacji slotu |
| Artefakt | Moduł rezerwacji + baza danych |
| Środowisko | 500 równoczesnych użytkowników |
| Reakcja | Spójny zapis, brak podwójnych rezerwacji |
| Miara reakcji | **0** podwójnych rezerwacji / miesiąc; **100%** spójności transakcji |

#### C) Wydajność (Self-Care Day)
| Element | Opis |
|---|---|
| Źródło bodźca | Klient |
| Bodziec | Żądanie wygenerowania planu SCD |
| Artefakt | Moduł SCD + dostępność terminów |
| Środowisko | Szczytowe obciążenie |
| Reakcja | System generuje plan i propozycje |
| Miara reakcji | czas generowania **< 5.0 s** dla **95%** żądań (MVP) |

### 4.3 Analiza kompromisów architektonicznych

#### A) Użyteczność (Onboarding)
- **Cel:** rejestracja ≤ 30 s, ≤ 3 kroki (95%) + dropout < 20%.  
- **Możliwe rozwiązanie:** uproszczona rejestracja (minimum danych) + uzupełnianie profilu później (*progressive profiling*), autouzupełnianie i walidacja po stronie klienta.  
- **Kompromis:**
  - ✅ lepsza użyteczność i większa aktywacja,
  - ❌ potencjalnie niższe bezpieczeństwo (jeśli uprościmy zasady lub weryfikację),
  - ❌ większa złożoność logiki (profil uzupełniany etapami) i ryzyko „pustych profili”.

#### B) Niezawodność (Rezerwacje)
- **Cel:** 0 podwójnych rezerwacji / miesiąc + 100% spójności.  
- **Możliwe rozwiązanie:** transakcje ACID, blokowanie slotu (unikalne ograniczenia / blokady pesymistyczne-optymistyczne), idempotentne API.  
- **Kompromis:**
  - ✅ maksymalna spójność i zaufanie,
  - ❌ spadek wydajności przy dużym obciążeniu (blokady),
  - ❌ większa złożoność implementacji (retry/timeout/konflikty) i potencjalnie niższa skalowalność.

#### C) Wydajność (Self-Care Day)
- **Cel:** generowanie planu < 5.0 s dla 95% żądań.  
- **Możliwe rozwiązanie:** cache wyników częściowych, indeksy DB, ograniczenie przestrzeni poszukiwań (heurystyki MVP), opcjonalnie asynchroniczne generowanie (kolejka zadań).  
- **Kompromis:**
  - ✅ lepsza wydajność i komfort użytkownika,
  - ❌ większa złożoność (cache/invalidacja), koszt operacyjny (cache/worker),
  - ❌ ryzyko nieaktualnych danych (zły refresh cache),
  - ❌ potencjalnie gorsza użyteczność przy podejściu async (czekanie/odświeżanie).

---

## 5. Odkrywanie i analiza wymagań (Analiza porównawcza)

### Krok 1: Identyfikacja konkurencji i wzorców
**Konkurencja bezpośrednia**
- Booksy
- Treatwell

**Konkurencja pośrednia**
- Google Maps + telefon
- Instagram/Facebook (DM)
- Strony salonów z formularzem kontaktowym

**Wzorce funkcjonalne**
- rezerwacje oparte o kalendarze i sloty,
- marketplace usług,
- mechanizmy opinii i ocen budujące zaufanie.

### Krok 2: Kryteria oceny
| Kryterium | Opis |
|---|---|
| Funkcjonalność | zakres (rezerwacje, filtry, panel salonu, planowanie wizyt) |
| User Experience (UX) | intuicyjność, liczba kroków, czytelność procesu |
| Wyróżniki funkcjonalne | unikalne / rzadkie funkcje |
| Model biznesowy | monetyzacja (abonament, prowizja, freemium) |
| Wsparcie dla usługodawców | jakość panelu salonu i narzędzi grafiku |

### Krok 3: Synteza wyników
| System | Mocne strony | Słabe strony | Wnioski dla Beautly |
|---|---|---|---|
| Booksy | duża baza salonów, stabilne rezerwacje, rozpoznawalna marka | złożony interfejs, dużo kroków, brak planowania wielu wizyt | stawiać na prostotę i krótsze ścieżki |
| Treatwell | dobre UX, przejrzyste oferty, silna pozycja w UE | ograniczona elastyczność grafiku, brak personalizacji dnia | inspiracja UX + szansa na wyróżnik SCD |
| Instagram/telefon | bezpośredni kontakt | brak automatyzacji, chaos terminów, ryzyko błędów | uzasadnia potrzebę niezawodnych rezerwacji |
| Strony salonów | kontrola salonu nad ofertą | brak porównywania i agregacji | wartość marketplace i filtrów |

**Wnioski kluczowe**
- Konkurencja dobrze rozwiązuje pojedyncze rezerwacje, ale rzadko wspiera planowanie całego dnia zabiegów.  
- Istnieje luka rynkowa dla kompleksowego planowania **Self-Care Day**.  
- Użyteczność i prostota powinny być priorytetem (konkurencja bywa zbyt rozbudowana).  
- Analiza wspiera decyzję: SCD w MVP (w wersji ograniczonej), a następnie stopniowy rozwój.

**Wpływ analizy na SRS**
- wybór użyteczności, niezawodności i wydajności jako kluczowych NFR,  
- wdrożenie SCD jako wyróżnika (MVP Lite),  
- ograniczenie MVP do funkcji o najwyższej wartości (rezerwacje + panel salonu).

---


**Koniec dokumentu SRS – Beautly (MVP 1.0)**
