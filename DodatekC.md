## Dodatek C: Kwestie do Rozwiązania (Open Issues)

---

### Cel dodatku
Celem niniejszego dodatku jest zidentyfikowanie **otwartych kwestii decyzyjnych i niejednoznaczności**, 
które pojawiły się w trakcie analizy wymagań systemu **Beautly** i wymagają dalszych ustaleń 
na etapie projektowania architektury, implementacji lub kolejnych iteracji produktu.

Kwestie te **nie blokują realizacji MVP**, jednak mają istotny wpływ na:
- doświadczenie użytkownika (UX),
- niezawodność i spójność procesów,
- zgodność prawną (RODO),
- rozwój systemu w przyszłości.

---

### C.1 Zasady anulowania rezerwacji
- Czy anulowanie wizyty przez klienta jest możliwe bez ograniczeń czasowych, czy obowiązuje określone okno (np. 12 lub 24 godziny przed wizytą)?
- Czy salon może definiować własne zasady anulowania rezerwacji?
- Jak anulowanie wpływa na dostępność slotu czasowego oraz statystyki salonu (np. obłożenie)?

---

### C.2 Obsługa nieobecności klienta (No-show)
- Jak system powinien reagować w sytuacji, gdy klient nie pojawi się na umówionej wizycie?
- Czy przewidywane są mechanizmy ostrzegania, ograniczenia funkcji lub czasowej blokady konta przy częstych nieobecnościach?
- Czy informacje o no-show powinny być widoczne dla salonów i wpływać na ich decyzje operacyjne?

---

### C.3 Transakcyjność funkcji Self-Care Day
- Czy rezerwacje w ramach **Self-Care Day** powinny być realizowane atomowo (wszystko albo nic), czy sekwencyjnie?
- Jak system powinien zachować się w przypadku, gdy jeden z elementów planu nie może zostać zarezerwowany?
- Czy użytkownik powinien mieć możliwość ręcznego zatwierdzania poszczególnych rezerwacji w planie dnia?

---

### C.4 Definicja i zarządzanie slotami czasowymi
- Jak dokładnie definiowany jest slot czasowy (czas trwania usługi, przerwy techniczne, przerwy logistyczne)?
- Czy system powinien uwzględniać czas przejścia lub dojazdu między salonami przy planowaniu **Self-Care Day**?
- Czy sloty mogą być dynamicznie modyfikowane przez salon (np. wydłużenie, skrócenie, blokada)?

---

### C.5 Zakres funkcjonalny panelu salonu w MVP
- Które funkcje panelu salonu są **niezbędne** w wersji MVP, a które mogą zostać odłożone na kolejne iteracje?
- Czy raporty i statystyki (np. obłożenie, liczba rezerwacji) są wymagane już w MVP, czy dopiero w późniejszych wersjach?

---

### C.6 Powiadomienia użytkowników
- Jakie kanały powiadomień będą dostępne w MVP (e-mail, push, SMS)?
- Czy powiadomienia będą konfigurowalne przez użytkownika lub salon?
- Jakie zdarzenia generują powiadomienia (np. rezerwacja, anulowanie, przypomnienie o wizycie)?

---

### C.7 Moderacja opinii i treści
- Jakie są kryteria usuwania lub ukrywania opinii użytkowników?
- Czy salon ma możliwość odpowiedzi na opinię klienta?
- Jak wygląda proces zgłaszania, weryfikacji i eskalacji nadużyć?

---

### C.8 Weryfikacja salonów
- Czy każdy użytkownik może założyć konto salonu bez weryfikacji?
- Czy w kolejnych wersjach systemu wymagane będą dodatkowe dane (np. NIP, REGON)?
- Jakie ryzyko dla jakości platformy niosą fałszywe lub niskiej jakości oferty?

---

### C.9 Retencja i usuwanie danych (RODO)
- Jak długo przechowywana jest historia rezerwacji po usunięciu konta użytkownika?
- W jaki sposób system realizuje prawo do bycia zapomnianym oraz prawo do eksportu danych?
- Jakie dane muszą zostać zachowane ze względów prawnych lub statystycznych?

---

### C.10 Model rekomendacji i personalizacji
- Na jakich danych opierają się rekomendacje w MVP (np. historia wizyt, ulubione, lokalizacja)?
- Czy personalizacja w MVP jest regułowa (rule-based), czy oparta na prostych algorytmach?

---

**Koniec Dodatku C**
