# Lawtech v1 — landing checklisty bezpieczeństwa AI

Statyczny prototyp landing page kierowanego do kancelarii prawnych. Pokazuje prezentację bezpłatnej checklisty o korzystaniu z AI oraz ścieżkę zapisu: formularz, walidację i ekran potwierdzenia.

To projekt interfejsu. Nie implementuje modelu AI, analizy dokumentów ani dostarczania checklisty.

## Co zawiera

- Responsywny układ z prezentacją materiału, opisem korzyści, FAQ i końcowym CTA.
- Główny formularz imienia, e-maila i zgody oraz uproszczony formularz w popupie.
- Własną walidację JavaScript: niepuste imię, format e-maila i zaznaczona zgoda; oba formularze mają `novalidate`.
- Symulację powodzenia po walidacji, bez wysyłki danych.
- Popup przy próbie opuszczenia strony, wyświetlany raz na sesję dzięki `sessionStorage`.
- Natywne sekcje FAQ `details`/`summary`, animacje `IntersectionObserver` i przewijanie do formularza.

## Uruchomienie

Wymagania: współczesna przeglądarka; Python 3 dla poniższego lokalnego serwera.

```bash
git clone https://github.com/dzwoniar/v1-lawtech.git
cd v1-lawtech
python -m http.server 8000 --bind 127.0.0.1
```

Otwórz [http://localhost:8000](http://localhost:8000). Na Windows można użyć polecenia `py` zamiast `python`. `Ctrl+C` kończy pracę serwera. Nie ma zależności npm ani kroku kompilacji.

## Kod i architektura

```text
.
├── index.html   # kompletna strona, CSS i JavaScript
└── README.md
```

[index.html](index.html) zawiera cały projekt. HTML przechowuje treść oferty i formularze, osadzony CSS definiuje wygląd oraz responsywność, a skrypt na końcu obsługuje walidację, popup i animacje. Stos to HTML5, CSS i JavaScript bez frameworka.

`handleForm()` przechwytuje `submit`, sprawdza pola i przełącza widok na potwierdzenie. Nie wywołuje endpointu sieciowego. `sessionStorage` przechowuje jedynie flagę `exitPopupShown`. Fonty Fraunces i Plus Jakarta Sans są ładowane z Google Fonts; dekoracyjna tekstura jest osadzona jako SVG w CSS.

## Zakres prototypu

- Formularze nie zapisują kontaktów, nie wysyłają e-maili i nie udostępniają pliku PDF. Komunikat powodzenia pokazuje wyłącznie stan interfejsu.
- Link polityki prywatności prowadzi do `#`.
- Deklaracje dotyczące usług AI, bezpieczeństwa danych, opinii i liczby pobrań są treścią makiety. Nie potwierdzają istnienia integracji, wyników wdrożeń ani zgodności usługi.
- Repozytorium nie zawiera backendu, kluczy API, bazy danych, zestawu testów ani konfiguracji wdrożenia.

## Kolejny wariant

[Lawtech v2](https://github.com/dzwoniar/v2-lawtech) rozwija stronę o kalkulator kosztu pracy i prezentację oferty automatyzacji pism.
