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


