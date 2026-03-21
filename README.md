Hra jde spustit zde -> https://dbrvsk-git.github.io/space-invaders/

Skóre na tomto odkazu nefunguje globálně.

--------------------------------------------------------------------------

# 🚀 Space Invaders — Instrukce pro online nasazení

## Co dostáváš

Jednoduchá HTML hra ve stylu Space Invaders, jeden soubor `space_invaders.html`.
Skóre se dá uložit dvěma způsoby:
- **Lokálně** (localStorage) — funguje hned, ale jen v daném prohlížeči
- **Online** (JSONBin.io) — sdílená databáze skóre přístupná odkudkoli

---

## KROK 1 — Nastav databázi skóre (JSONBin.io — zdarma)

JSONBin.io je jednoduché REST API úložiště. Zdarma, bez serveru.

### 1.1 Vytvoř účet
Jdi na **https://jsonbin.io** → Sign Up (zdarma).

### 1.2 Vytvoř nový "bin" (databázi)
1. Po přihlášení klikni na **"+ New Bin"**
2. Vlož tento JSON jako obsah:
   ```json
   { "scores": [] }
   ```
3. Klikni **Create** (nech bin jako **Private**)
4. **Zkopíruj BIN ID** — je to číslo v URL, např. `6642abc123def456789012`

### 1.3 Získej přístupový klíč
1. Klikni na **Account → API Keys**
2. Vytvoř nový klíč (nebo zkopíruj existující)
3. **Zkopíruj Access Key** — vypadá jako `$2a$10$xxxxx...`

### 1.4 Nakonfiguruj hru
Otevři soubor `space_invaders.html` v textovém editoru a najdi tento řádek (kolem řádku 185):

```javascript
const JSONBIN_URL = 'https://api.jsonbin.io/v3/b/6642000000000000000000';
const JSONBIN_KEY = '$2a$10$PLACEHOLDER';
```

Nahraď hodnotami ze svého účtu:
```javascript
const JSONBIN_URL = 'https://api.jsonbin.io/v3/b/TVOJE_BIN_ID';
const JSONBIN_KEY = 'TVUJ_ACCESS_KEY';
```

**Nebo** — po nasazení hry online otevři v prohlížeči konzoli (F12) a spusť:
```javascript
setupJsonBin('TVOJE_BIN_ID', 'TVUJ_ACCESS_KEY');
```
Klíče se uloží do localStorage prohlížeče.

---

## KROK 2 — Nasaď hru online (3 možnosti)

### Možnost A — GitHub Pages (doporučeno, zdarma)

1. Vytvoř si účet na **https://github.com** (pokud nemáš)
2. Klikni **"+ New repository"** → pojmenuj ho např. `space-invaders`
3. Zaškrtni **"Add a README file"** → Create repository
4. Klikni **"Add file" → "Upload files"** a nahraj `space_invaders.html`
   - Přejmenuj soubor na `index.html` (pro lepší URL)
5. Jdi do **Settings → Pages**
6. Pod "Source" vyber **"Deploy from a branch"** → větev `main` → `/root`
7. Klikni **Save**

Za ~2 minuty bude hra dostupná na:
```
https://TVOJE_UZIVATELSKE_JMENO.github.io/space-invaders/
```

---

### Možnost B — Netlify (drag & drop, zdarma)

1. Jdi na **https://app.netlify.com**
2. Přihlas se (lze přes GitHub)
3. Na dashboardu přetáhni soubor `space_invaders.html` (přejmenovaný na `index.html`) do zóny **"Deploy manually"**
4. Hotovo! Dostaneš URL ve tvaru `https://random-name-123.netlify.app`

Vlastní doménu lze nastavit zdarma.

---

### Možnost C — Vercel (zdarma)

1. Jdi na **https://vercel.com** → Sign Up
2. Klikni **"Add New → Project"**
3. Vyber **"Browse"** a nahraj složku s `index.html`
4. Deploy → dostaneš URL `https://project-name.vercel.app`

---

## KROK 3 — Ověření funkčnosti

Po nasazení:
1. Otevři hru v prohlížeči
2. Zahraj si partii, zadej jméno → klikni "Uložit skóre"
3. Klikni "Žebříček" — skóre by se mělo zobrazit
4. Otevři hru v jiném prohlížeči / na telefonu — žebříček by měl být sdílený

Pokud se skóre neuloží online, zkontroluj:
- Správné BIN ID a Access Key v kódu
- Bin na JSONBin.io není smazaný
- Prohlížeč neblokuje požadavky (CORS — JSONBin.io CORS podporuje)

---

## Rychlý přehled

| Krok | Čas | Cena |
|------|-----|------|
| JSONBin účet + bin | ~5 min | Zdarma |
| GitHub Pages hosting | ~10 min | Zdarma |
| Vlastní doména (volitelné) | ~30 min | ~200 Kč/rok |

---

## Struktura souborů

```
space_invaders.html   ← celá hra v jednom souboru (HTML + CSS + JS)
```

Vše je v jednom souboru — žádný build, žádné závislosti, žádný server.

---

*Hru stačí otevřít v prohlížeči — funguje i offline (jen skóre se uloží jen lokálně).*
