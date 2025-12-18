# Instrukcja deploymentu na Vercel

## Przygotowanie projektu

Projekt został już przygotowany do deploymentu na Vercel. Zmiany obejmują:

- ✅ Dodano `vercel.json` z konfiguracją
- ✅ Zmodyfikowano `server.ts` aby eksportować aplikację
- ✅ Utworzono `api/index.ts` jako punkt wejścia dla Vercel
- ✅ Zaktualizowano `package.json`

## Kroki deploymentu

### 1. Zainstaluj Vercel CLI (opcjonalnie)

```bash
npm install -g vercel
```

### 2. Deployment przez Vercel CLI

W katalogu projektu uruchom:

```bash
vercel
```

Lub od razu na produkcję:

```bash
vercel --prod
```

### 3. Deployment przez Vercel Dashboard

1. Wejdź na [vercel.com](https://vercel.com)
2. Zaloguj się lub utwórz konto
3. Kliknij "Add New Project"
4. Zaimportuj swoje repozytorium GitHub (lub prześlij projekt bezpośrednio)
5. Vercel automatycznie wykryje ustawienia

### 4. Ustawienie zmiennych środowiskowych

**WAŻNE:** Musisz ustawić zmienną środowiskową w Vercel Dashboard:

1. Przejdź do ustawień projektu na Vercel
2. Zakładka "Environment Variables"
3. Dodaj:
   - **Nazwa:** `API_KEY`
   - **Wartość:** Twój klucz API z FACEIT
   - **Środowisko:** Production, Preview, Development (zaznacz wszystkie)

## Testowanie

Po deploymencie, Twoje API będzie dostępne pod adresem:
```
https://twoj-projekt.vercel.app
```

Endpointy:
- `/` - Strona główna z instrukcją
- `/stats/[nick]` - Statystyki gracza
- `/last/[nick]` - Ostatnia gra
- `/live/[nick]` - Live stats
- `/avg/[nick]` - Średnie statystyki

Przykład:
```
https://twoj-projekt.vercel.app/stats/donk666
```

## Rozwój lokalny

Projekt nadal działa lokalnie jak wcześniej:

```bash
# Instalacja zależności
npm install
# lub
pnpm install

# Uruchomienie w trybie deweloperskim
npm run dev
```

Pamiętaj o pliku `.env` z `API_KEY` do testów lokalnych.

## Dodatkowe informacje

- Vercel automatycznie używa środowiska Node.js
- Każdy push do głównej gałęzi (main/master) automatycznie wdroży nową wersję
- Preview deployments są tworzone dla każdego pull requesta
- Logi są dostępne w Vercel Dashboard
