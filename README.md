[README_Edennium_Platby.md](https://github.com/user-attachments/files/32028123/README_Edennium_Platby.md)
# Platby Edennium

Interní webová aplikace Edennium, z.s. pro evidenci a potvrzování plateb a vzdálené podepisování dokladů.

## Funkce

### Administrace
- přihlášení přes Supabase Authentication
- vytvoření platebního dokladu
- evidence čísla dokladu
- příjemce, účel a částka
- stav platby:
  - hotově – vyplaceno
  - bankovním převodem – k vyplacení
  - bankovním převodem – vyplaceno
- podpis osoby jednající za Edennium
- vytvoření unikátního podpisového odkazu
- přehled vytvořených dokladů

### Vzdálený podpis
Příjemce obdrží unikátní odkaz, prostřednictvím kterého:

- vidí předem vytvořený doklad,
- nemůže změnit jeho údaje,
- může připojit svůj podpis,
- podpisem dokument definitivně potvrdí.

Po podpisu se dokument v databázi uzamkne.

## Technické řešení

Frontend:
- HTML / CSS / JavaScript

Backend:
- Supabase
- PostgreSQL
- Supabase Authentication
- Row Level Security
- PostgreSQL RPC funkce

Hosting:
- GitHub Pages

## Bezpečnost

Aplikace nepoužívá service role ani secret key ve frontendu.

Ve frontendové aplikaci je použit pouze Supabase Project URL a publishable key.

Administrativní operace jsou kontrolovány databázovými funkcemi podle přihlášeného uživatele.

Příjemce může dokument načíst a podepsat pouze prostřednictvím unikátního signing tokenu.

Po podpisu příjemcem je dokument označen jako podepsaný a uzamčený.

## Struktura projektu

- `index.html` – hlavní aplikace
- `manifest.webmanifest` – metadata aplikace
- `sw.js` – základní service worker
- `README.md` – dokumentace projektu

## Provoz

Aplikace je určena pro interní použití Edennium, z.s.

Před produkčním použitím je doporučeno otestovat:

1. přihlášení administrátora,
2. vytvoření testovacího dokladu,
3. otevření podpisového odkazu v anonymním okně,
4. podpis příjemcem,
5. uzamčení dokumentu po podpisu,
6. zobrazení dokončeného dokumentu,
7. vytvoření PDF.

## Poznámka

Tento projekt slouží jako interní nástroj pro organizační a účetní evidenci. Konkrétní účetní a daňové posouzení jednotlivých plateb je vhodné konzultovat s účetní nebo daňovým poradcem Edennium, z.s.

---

Edennium, z.s.
IČO: 08142408
