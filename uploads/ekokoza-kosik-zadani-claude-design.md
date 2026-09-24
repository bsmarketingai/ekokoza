# Ekokoza.cz – Košík (kroky 1–3) – zadání pro Claude Design

## Cíl

Převést stávající třikrokový košík ekokoza.cz **1:1 do nového designu** (Ekokoza design system).
Jde o **vizuální kopii**, ne o UX redesign.

### Pravidla (závazná)

- **Zachovat rozložení**: pořadí sekcí, rozdělení do sloupců, umístění prvků i sticky spodní lištu.
- **Nepřidávat žádné funkce, prvky ani texty**, které na stránce nejsou (žádné progress bary k dopravě zdarma, trust badge, odhady doručení, upsell, souhrn v postranním panelu navíc apod.).
- **Nic neodebírat.** Všechny prvky ze screenshotů musí zůstat, a to i ty, které se zdají zbytečné.
- **Texty přebírat doslova** (včetně velkých/malých písmen). Nepřepisovat copy.
- Měnit se smí jen **vizuální vrstva**: barvy, typografie, zaoblení, rozestupy, ikony, stavy prvků (hover/focus/checked/error), jednotný vzhled formulářových prvků.
- Formulářové prvky (inputy, selecty, checkboxy, radio) sjednotit podle design systému. Dnes jsou nativní a nekonzistentní.

### Podklady (screenshoty celé stránky, desktop)

| Soubor | Obsah |
|---|---|
| `ekokoza-kosik-krok1-doprava-platba.png` | Krok 1 – vybraná doprava PPL na adresu + platba kartou |
| `ekokoza-kosik-krok2-kontaktni-udaje.png` | Krok 2 – **všechna rozbalovací pole otevřená** (nový účet, nákup na firmu, jiná dodací adresa) |
| `ekokoza-kosik-krok3-souhrn.png` | Krok 3 – souhrn s testovacími údaji |

Ve screenshotech jsou i vývojářské prvky (`XXL (1440,9999)`, verze buildu vpravo dole). **Ty nejsou součástí designu, nekreslit.**

---

## Společné prvky všech kroků

### Hlavička (beze změny struktury)

- Horní úzká lišta: vlevo `eshop@ekokoza.cz` s ikonou, vpravo odkazy `KONTAKTY · O EKOKOZE · FAQ · VĚRNOSTNÍ PROGRAM · Přihlášení` a vlajky CZ / SK.
- Hlavní řádek: logo Ekokoza (zelený štítek s kozou), menu v zaobleném rámečku `VÝROBA · PRODUKTY · OBALY · RECEPTÁŘ · DÁRKOVÉ POUKAZY`, vyhledávání (`Zadejte hledaný výraz...` + ikona lupy), vpravo ikona košíku (oranžový odznak).
- Pod hlavičkou je krémové pozadí s papírovou texturou a vlnitým spodním okrajem. Obsah košíku začíná v této zóně.

### Stepper (3 kroky, vycentrovaný)

- Kroky `1 Doprava a platba` · `2 Kontaktní údaje` · `3 Souhrn objednávky`, spojené linkou.
- Stavy: **aktivní/hotový** = plný zelený kruh s bílým číslem, **budoucí** = bílý kruh se zeleným obrysem.
- Popisek pod kruhem.

### Sticky spodní lišta (kroky 1 a 2)

Drží se u spodního okraje viewportu, šířka obsahu:

- vlevo tlačítko `Zpět` (světle zelená pilulka)
- `Poštovné a balné:` + částka (zeleně, tučně)
- `Konečná cena s DPH:` + částka (oranžově, větší, tučně)
- vpravo primární CTA `Pokračovat` (oranžová pilulka)

V kroku 3 lišta vypadá jinak (viz Krok 3).

### Plovoucí prvky třetích stran (ponechat, neredesignovat)

- Vlevo svislý žlutý štítek „Ověřeno zákazníky“ (Heureka).
- Vpravo dole kulaté tlačítko chatu a odznak hodnocení („Store rating by Google · 5.0 ★“ / „5.0 ★“).

---

## Krok 1 – Doprava a platba

URL: `/objednat-krok1/`. Prvky shora dolů:

1. **Nadpis** `Obsah košíku`.
2. **Tabulka položek** (levý sloupec, cca 3/4 šířky):
   - Záhlaví sloupců: `Množství` · `Cena s DPH (m. j.)` · `Cena celkem s DPH`.
   - Řádek položky (karta s rámečkem): miniatura produktu, název jako podtržený odkaz (`Arganový olej, lis za studena, 190 ml`), pod ním `ID produktu: 5030` a zelený stav skladu s ikonou `Ihned k odeslání`.
   - Množství: tlačítka `−` / `+` kolem pole `1 ks`.
   - Cena za kus (`499 Kč`), cena celkem (oranžově, `499 Kč`), ikona `×` pro odebrání.
3. **Boxík podpory** (pravý sloupec, vedle tabulky): ikona obálky, text `Nevíte si rady s výběrem produktu? Napište nám na: eshop@ekokoza.cz`, tlačítko `Poslat e-mail` (světle zelená pilulka).
4. **Lišta dopravy zdarma** (celá šířka, světle zelené pozadí): ikona dodávky + `Pokud nakoupíte ještě za **1 501 Kč**, budete mít **dopravné zdarma**`.
5. **Doporučujeme** (vycentrovaný nadpis) + **4 produktové karty v řadě**. Každá karta obsahuje:
   - obrázek
   - srdíčko (oblíbené) vpravo nahoře
   - hvězdičky + počet hodnocení v závorce (u produktu bez hodnocení chybí)
   - název (max. 2 řádky)
   - cenu
   - oranžové tlačítko `Koupit`
6. **Přednostní odeslání** (celá šířka, béžové pozadí): checkbox, ikona dodávky, text `Přednostní odeslání`, vpravo `50 Kč` a ikona `i` (info).
7. **Kupón** (řádek s rámečkem): label `Mám slevový/dárkový kupón a chci ho uplatnit:` + input s placeholderem `Kód kupónu` + tlačítko `Uplatnit` (tmavě zelené).
8. **Nadpis** `Přidat k objednávce` s ikonou `i`. Pod ním řádek s rámečkem: `Zde zadejte číslo objednávky, ke které chcete udělat doobjednávku:` + input `Číslo objednávky` + tlačítko `Přidat` (tmavě zelené).
9. **Dva sloupce vedle sebe (50/50):**
   - **Doprava** (nadpis + box). Radio seznam, každá položka má radio, logo/ikonu dopravce, název a cenu vpravo:
     - `PPL na adresu` (logo PPL): 100 Kč
     - `PPL Parcelshop` (logo PPL): 60 Kč
     - `Zásilkovna` (logo Zásilkovny): 90 Kč
     - `Osobní odběr (Fryčovice 297)` (ikona pin → chodec): 0 Kč
   - **Způsob platby** (nadpis + box). Radio seznam:
     - `Kartou on-line` (loga VISA + Mastercard): 0 Kč
     - `Bankovním převodem` (ikona dokument → banka): 0 Kč + ikona `i`
     - `Dobírka` (ikona balík + bankovka): `(od 15 Kč)`, po výběru dopravy konkrétní částka (např. `20 Kč`), + ikona `i`
10. **Sticky spodní lišta** (viz společné prvky).

Stavy k navržení: radio vybrané / nevybrané, hover řádku dopravy a platby, checkbox přednostního odeslání.

---

## Krok 2 – Kontaktní údaje

URL: `/objednat-krok2/`. Rozložení je **dvousloupcové**: vlevo formulář (cca 2/3), vpravo úzký souhrn.

### Levý sloupec

1. **Malý nadpis** `Přihlášení a registrace`. Pod ním **dvě karty vedle sebe**:
   - **Jsem nový zákazník**: tenká ikona osoby s plusem, nadpis, checkbox `Vytvořit nový účet`.
     - Po zaškrtnutí se v kartě rozbalí pole `Heslo` a `Potvrzení hesla` (labely nad inputy).
   - **Mám zde svůj účet**: tenká ikona klíče, nadpis, tlačítko `Přihlásit se` (světle zelená pilulka).
2. Oddělovací linka.
3. **Malý nadpis** `Fakturační údaje`.
4. Checkbox `Nákup na firmu`. Po zaškrtnutí se **nad osobními údaji** zobrazí box:
   - `Společnost` (input)
   - `IČ` (input) + malé zelené tlačítko `Načíst z ARESu`
   - `DIČ` (input, placeholder `CZ12345678`)
   - checkbox `Plátce DPH` (výchozí zaškrtnutý)
5. **Box osobních údajů** (grid 2 sloupce, label vlevo od inputu):
   - `Jméno` | `Příjmení`
   - `E-mail` | `Telefon`
   - `Ulice, čp.` | `PSČ`
   - `Město` | `Země` (select, výchozí `Česko`)
   - `Poznámka` (textarea přes celou šířku)
6. Checkbox `Adresa dodání je jiná než adresa fakturační`. Po zaškrtnutí se zobrazí box dodací adresy (grid 2 sloupce):
   - `Firma`
   - `Jméno` | `Příjmení`
   - `Ulice, čp.` | `Město`
   - `PSČ` | `Země` (select `Česko`)
   - `Telefon`
7. **Souhlasy** (3 checkboxy pod sebou, výchozí stav):
   - ☐ `Nesouhlasím se zasláním dotazníku spokojenosti v rámci programu Heureka Ověřeno zákazníky, který pomáhá zlepšovat naše služby`
   - ☑ `Mám zájem o zasílání novinek a akcí`
   - ☑ `Nesouhlasím s předáním údajů o objednávce Zboží.cz za účelem nezávislého hodnocení nákupu.`

### Pravý sloupec

1. **Malý nadpis** `Obsah košíku`. Pod ním box s položkami: miniatura, název jako odkaz, cena vpravo, pod ní `1 ks`.
2. Ve stejném boxu pod oddělovačem: `Doprava: PPL na adresu` → `100 Kč` a `Platba: Kartou on-line` → `0 Kč`.
3. Samostatný **boxík podpory** (stejný jako v kroku 1: obálka, text, `Poslat e-mail`).

Pak následuje **sticky spodní lišta** (viz společné prvky).

Stavy k navržení:

- výchozí formulář se sbalenými sekcemi
- formulář s rozbalenými sekcemi (nový účet, firma, jiná dodací adresa)
- input: prázdný, focus, vyplněný, chybový (jen vzhled; texty chyb nevymýšlet)
- checkbox: zaškrtnutý / nezaškrtnutý

---

## Krok 3 – Souhrn objednávky

URL: `/objednat-krok3/`. **Jednosloupcové** rozložení přes celou šířku obsahu. Stepper má všechny 3 kroky aktivní.

1. **Nadpis** `Kontaktní údaje` + box s tabulkou „label: hodnota“ (label tučně, zarovnaný vpravo):
   `Jméno:` · `Ulice, čp.:` · `PSČ, Město:` · `Země:` · `E-mail:` · `Telefon:`
   (Pokud je vyplněná firma nebo jiná dodací adresa, zobrazí se tu analogicky. V tomto stavu to nebylo ověřeno, takže nové řádky nevymýšlet.)
2. Oddělovací linka.
3. **Nadpis** `Obsah košíku` + záhlaví `Množství` · `Cena s DPH (m. j.)` · `Cena celkem s DPH`.
   - Řádek položky je stejný jako v kroku 1, ale **bez úprav množství a bez odebrání**. Množství je jen text `1 ks`.
4. **Box souhrnu** (2 části vedle sebe):
   - vlevo `Doprava: PPL na adresu` → `100 Kč` a `Platba: Kartou on-line` → `0 Kč`
   - vpravo `Cena celkem bez DPH` → `528 Kč` a `Cena celkem s DPH` → `599 Kč` (oranžově, velké)
5. **Lišta dopravy zdarma** (stejná jako v kroku 1).
6. **Spodní akční řádek** (není sticky, je součástí obsahu):
   - vlevo `Zpět` (světle zelená pilulka)
   - uprostřed box se souhlasem: checkbox + `Souhlasím s obchodními podmínkami a beru na vědomí zpracování osobních údajů. Odesláním objednávky se zavazuji k její úhradě.` Části `obchodními podmínkami` a `zpracování osobních údajů` jsou podtržené odkazy.
   - vpravo velké oranžové CTA `Zaplatit` s ikonou štítu. Screenshot je pořízený při platbě kartou. Popisek pro jiné platby nebyl ověřen, takže nic nevymýšlet.

Stavy k navržení: souhlas nezaškrtnutý / zaškrtnutý, CTA `Zaplatit` normální / hover.

---

## Současné vizuální hodnoty (jen pro orientaci, nahradit tokeny z DS)

| Použití | Hodnota dnes |
|---|---|
| Font | Work Sans (základ 14 px) |
| Text / nadpisy / tmavé tlačítka | #4C653D |
| Primární CTA (`Pokračovat`, `Koupit`, `Zaplatit`, celková cena) | #FD5308 |
| Sekundární tlačítko (`Zpět`, `Poslat e-mail`, `Přihlásit se`) | #C8D8A4 |
| Lišta dopravy zdarma | #D9F3C9 |
| Přednostní odeslání | #F7F3DF |
| Zaoblení tlačítek | 18–24 px (pilulky) |

V novém designu použij barvy, typografii a komponenty z **Ekokoza design systému** (primární CTA dle manuálu, krémové pozadí, zaoblené rohy, jemný řemeslný motiv).
Tón zůstává klidný, bez urgence a agresivních prvků. **Rozložení a obsah ale zůstávají přesně podle screenshotů.**

## Výstup

- Desktop verze kroků 1, 2 a 3 (šířka obsahu jako dnes, vycentrováno).
- Krok 2 ve dvou variantách: sbalené a rozbalené sekce.
- Mobil zatím neřešit.
