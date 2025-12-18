# StreamElements - Gotowe komendy

API URL: **https://obsfcapi.vercel.app**

## Jak dodać komendy:

1. Wejdź na [streamelements.com](https://streamelements.com)
2. Zaloguj się i wybierz swój kanał
3. **Chatbot** → **Commands** → **Custom** → **+ Add New Command**
4. Skopiuj poniższe konfiguracje

---

## Komenda `!stats` - Pełne statystyki

### Konfiguracja:
- **Command:** `!stats`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1} - LVL: $lvl | ELO: $elo | Dzisiaj: $wins W / $losses L ($diff ELO)}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!stats donk666
```
**Zwróci:** `donk666 - LVL: 10 | ELO: 4401 | Dzisiaj: 5 W / 2 L (+127 ELO)`

---

## Komenda `!elo` - Tylko poziom i ELO

### Konfiguracja:
- **Command:** `!elo`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1}: Poziom $lvl ($elo ELO)}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!elo donk666
```
**Zwróci:** `donk666: Poziom 10 (4401 ELO)`

---

## Komenda `!wl` - Wygrane/Przegrane (24h)

### Konfiguracja:
- **Command:** `!wl`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1} dzisiaj: $wins W - $losses L (Bilans: $diff ELO)}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!wl donk666
```
**Zwróci:** `donk666 dzisiaj: 5 W - 2 L (Bilans: +127 ELO)`

---

## Komenda `!rank` - Prosty rank

### Konfiguracja:
- **Command:** `!rank`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1} jest na poziomie $lvl z $elo ELO}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!rank donk666
```
**Zwróci:** `donk666 jest na poziomie 10 z 4401 ELO`

---

## Komenda `!last` - Ostatnia gra

### Konfiguracja:
- **Command:** `!last`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/last/${1}}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!last donk666
```

---

## Komenda `!live` - Live stats

### Konfiguracja:
- **Command:** `!live`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/live/${1}}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!live donk666
```

---

## Komenda `!avg` - Średnie statystyki

### Konfiguracja:
- **Command:** `!avg`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/avg/${1}}
```
- **Cooldown:** 5 sekund
- **User Level:** Everyone
- **Enabled:** ✅

### Użycie:
```
!avg donk666
```

---

## Komenda `!faceit` - Dla streamera (bez argumentu)

Jeśli chcesz, żeby komenda działała bez podawania nicku (np. dla Twojego nicka):

### Konfiguracja:
- **Command:** `!faceit`
- **Response:**
```
${customapi.https://obsfcapi.vercel.app/stats/TWOJ_NICK?format=TWOJ_NICK - LVL: $lvl | ELO: $elo | Dzisiaj: $wins W / $losses L ($diff)}
```
- **Cooldown:** 10 sekund
- **User Level:** Everyone
- **Enabled:** ✅

**Zamień `TWOJ_NICK` na swój nick FACEIT!**

---

## Dostępne zmienne w `?format=`:

- **`$lvl`** - Poziom gracza (1-10)
- **`$elo`** - Punkty ELO
- **`$diff`** - Różnica ELO (ostatnie 24h, max 100 gier)
- **`$wins`** - Wygrane (ostatnie 24h, max 100 gier)
- **`$losses`** - Przegrane (ostatnie 24h, max 100 gier)
- **`${1}`** - Nick podany w komendzie (np. `!stats donk666` → `${1}` = `donk666`)
- **`${user}`** - Nick użytkownika który użył komendy

---

## Przykłady custom formatów:

### Format 1: Emoji style
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=🎮 ${1} | 📊 LVL $lvl | ⭐ $elo ELO | 📈 $diff}
```

### Format 2: Krótki
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=$lvl lvl, $elo elo}
```

### Format 3: Pełny z użytkownikiem
```
${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${user} sprawdza: ${1} ma $lvl lvl ($elo ELO) - Dzisiaj: $wins/$losses ($diff)}
```

---

## Testowanie komend:

Możesz przetestować API bezpośrednio w przeglądarce:

- https://obsfcapi.vercel.app/stats/donk666
- https://obsfcapi.vercel.app/stats/donk666?format=LVL: $lvl, ELO: $elo
- https://obsfcapi.vercel.app/last/donk666
- https://obsfcapi.vercel.app/live/donk666
- https://obsfcapi.vercel.app/avg/donk666

---

## Wskazówki:

1. **Cooldown:** Ustaw cooldown (5-10 sekund) żeby uniknąć spamu
2. **User Level:** Możesz ustawić poziom dostępu (Everyone, Regular, Subscriber, Moderator)
3. **Aliases:** Możesz dodać aliasy, np. `!rank` i `!lvl` dla tej samej komendy
4. **Custom format:** Zmień `?format=` aby dostosować wygląd wiadomości

---

## Gotowe zestawy komend do skopiowania:

### Zestaw podstawowy (3 komendy):
```
!stats → ${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1}: LVL $lvl | $elo ELO | $wins W / $losses L ($diff)}
!elo → ${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1}: $lvl lvl, $elo elo}
!last → ${customapi.https://obsfcapi.vercel.app/last/${1}}
```

### Zestaw pełny (6 komend):
```
!stats → ${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1}: LVL $lvl | $elo ELO | $wins W / $losses L ($diff)}
!elo → ${customapi.https://obsfcapi.vercel.app/stats/${1}?format=${1}: $lvl lvl, $elo elo}
!wl → ${customapi.https://obsfcapi.vercel.app/stats/${1}?format=$wins W - $losses L ($diff)}
!last → ${customapi.https://obsfcapi.vercel.app/last/${1}}
!live → ${customapi.https://obsfcapi.vercel.app/live/${1}}
!avg → ${customapi.https://obsfcapi.vercel.app/avg/${1}}
```
