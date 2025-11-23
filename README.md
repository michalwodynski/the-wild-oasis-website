# The Wild Oasis — Aplikacja rezerwacji domków

## 🚀 Opis

The Wild Oasis to nowoczesna aplikacja webowa do rezerwacji domków, zbudowana przy użyciu Next.js i Tailwind CSS. Umożliwia wygodne przeglądanie domków, wybór dat rezerwacji, logowanie przez dostawców OAuth oraz zarządzanie rezerwacjami. Główne funkcje:

- Przeglądanie i filtrowanie dostępnych domków
- Tworzenie, podgląd, edycja i usuwanie rezerwacji
- Uwierzytelnianie przez NextAuth (OAuth) oraz integracja z Supabase dla użytkowników i sesji
- Responsywny interfejs i szybka nawigacja dzięki Next.js App Router

Repozytorium zawiera frontend oraz bezserwerowe (serverless) trasy API używane przez aplikację.

## 🛠️ Stos technologiczny

- **Framework:** Next.js (App Router)
- **Język:** JavaScript / React
- **Stylowanie:** Tailwind CSS, PostCSS
- **Uwierzytelnianie:** NextAuth.js (trasy API w `api/auth/[...nextauth]`)
- **Backend / DB:** Supabase (klient i helpery w `app/_lib/supabase.js` i `data-service.js`)
- **Stan i akcje:** Komponenty klienckie i helpery w `app/_lib/actions.js` oraz `ReservationContext` w `app/_components`
- **Środowisko uruchomieniowe:** Node.js (narzędzia deweloperskie i budowanie)
- **Wdrożenie:** Vercel lub każda platforma wspierająca serverless dla Next.js

Wyróżnione katalogi i pliki:

- `app/` — Strony i podstrony Next.js (App Router), w tym trasy `api`
- `app/_components/` — Wspólne komponenty React (formularze rezerwacji, lista domków, nagłówek itp.)
- `app/_lib/` — Moduły pomocnicze (inicjalizacja Supabase, narzędzia auth, data service, akcje)
- `public/` — Zasoby statyczne
- `tailwind.config.js`, `postcss.config.js` — Konfiguracja stylów
- `next.config.mjs` — Konfiguracja Next.js

## ⚙️ Konfiguracja (.env)

Aplikacja oczekuje typowych zmiennych środowiskowych używanych przez Next.js, NextAuth i Supabase. Utwórz lokalny plik środowiskowy (np. `.env.local`) i uzupełnij poniższe wartości. Nie umieszczaj prawdziwych poświadczeń w repozytorium.

Wymagane zmienne (nazwy używane w projekcie):

- `NEXTAUTH_URL` — Główny URL aplikacji (np. `http://localhost:3000`)
- `NEXTAUTH_SECRET` — Sekretny klucz do szyfrowania sesji NextAuth
- `SUPABASE_URL` — URL projektu Supabase
- `SUPABASE_KEY` — Klucz API
- `AUTH_GOOGLE_ID` — ID klienta Google
- `AUTH_GOOGLE_SECRET` — Sekret klienta Google

Przykład pliku `.env.example` (tylko wartości zastępcze):

```.env.example
# Next.js / NextAuth
NEXTAUTH_URL=your_nextauth_url
NEXTAUTH_SECRET=your_nextauth_secret

# Supabase
SUPABASE_URL=https://your-supabase-project.supabase.co
SUPABASE_KEY=key-placeholder

# Google Provider
AUTH_GOOGLE_ID="[TWÓJ_GOOGLE_CLIENT_ID].apps.googleusercontent.com"
AUTH_GOOGLE_SECRET="[TWÓJ_GOOGLE_CLIENT_SECRET]"

```

Wskazówki:

- Używaj `.env.local` do ustawień deweloperskich i nie dodawaj go do kontroli wersji.
- Przy wdrożeniu na Vercel ustaw te same zmienne w panelu projektu (Environment Variables).

## Szybki start

1. Zainstaluj zależności:

```bash
npm install
```

2. Skopiuj `.env.example` do `.env.local` i uzupełnij wartości.

3. Uruchom serwer deweloperski:

```bash
npm run dev
```

4. Otwórz `http://localhost:3000` w przeglądarce.

## Kontekst Projektu

Ten projekt został stworzony jako część kursu **"Ultimate React Course"** prowadzonego przez **Jonasa Schmedtmanna**.

## Gdzie szukać w repozytorium

- `app/page.js` — Strona główna
- `app/cabins/` — Lista domków i strony pojedynczych domków
- `app/_components/ReservationForm.js` — Formularz tworzenia rezerwacji
- `app/_lib/supabase.js` — Inicjalizacja klienta Supabase
- `app/api/auth/[...nextauth]/route.js` — Konfiguracja NextAuth
