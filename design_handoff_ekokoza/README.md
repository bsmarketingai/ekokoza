# Handoff: ekokoza.cz — e-shop (design systém, šablony, komponenty)

## Přehled
Redesign e-shopu ekokoza.cz: suroviny, obaly a recepty pro domácí a malovýrobu kosmetiky, mýdel a svíček. Balíček obsahuje finální návrh všech šablon e-shopu, komponenty, design tokeny, ikony a brandové podklady.

**Claim:** „S námi víte, co tvoříte.“ + „Suroviny, recepty a ověřené postupy.“ Tón: klidný, věcný, vysvětlující. Žádná slevová urgence, odpočty, CAPS ani vykřičníky. Podrobně v `brand/brand-positioning.md`.

## O souborech návrhu
Soubory v `design/` jsou **referenční návrhy v HTML**: prototypy, které ukazují vzhled a chování. **Nejsou to produkční kód ke zkopírování.** Úkolem je převést je do prostředí e-shopu (šablonovací systém platformy, existující CSS/JS) podle jeho zavedených postupů. Komponenty (`ui-*.dc.html`) mají inline styly kvůli nástroji, ve kterém vznikly. V produkci je převeďte na třídy a tokeny (`tokens/tokens.css`).

Jak otevřít: soubory jdou spustit v prohlížeči přímo ze složky `design/`. Potřebují internet kvůli Google Fonts. Stránka načte runtime `support.js` a ten si dotahuje komponenty `ui-*.dc.html` ze stejné složky. Pokud prohlížeč z `file://` blokuje načítání, pusťte složku přes jednoduchý lokální server (např. `npx serve design`).

## Věrnost návrhu
**High-fidelity.** Barvy, typografie, rozestupy, stavy i responzivní chování jsou finální. Implementovat pixel-perfect. Zdrojem pravdy pro vizuál je `design/design-system.html` (je v něm jen to, co se ve finále používá) spolu s komponentami.

## Obsah balíčku
```
README.md            tento soubor — pravidla, tokeny, breakpointy, chování
KOMPONENTY.md        popis všech komponent, jejich stavů a props
STRANKY.md           popis všech šablon e-shopu
tokens/tokens.css    CSS proměnné (barvy, písma, rádiusy, stíny, layout)
tokens/tokens.json   totéž jako JSON
icons/               152 SVG ikon (Hugeicons), jen ty, které design používá + README s rozdělením do skupin
brand/               loga, znak, nápis, textura pozadí, maskot, brand positioning
ui-assets/           ilustrace USP, odznaky důvěry, loga dopravců, vlajky
images/              všechny obrázky a video použité na webu (bez ikon), ve stejné struktuře jako v návrhu
design/              HTML návrhy všech stránek + komponenty + assety (assets/)
```

## Design tokeny (výtah, kompletně v tokens/)

### Barvy a jejich role
| Role | Hex | Použití |
|---|---|---|
| Tmavá zeleň (jediná) | `#4C653D` | Nadpisy, ikony, ceny, sekundární tlačítka, aktivní stavy, plocha horní lišty a patičky |
| Terrakota CTA | `#D14405` → hover `#B23803` | **Jen hlavní nákupní akce** (Do košíku, Přejít do košíku, Dokončit). Max. 1× na obrazovku. Ne na tmavé zeleni |
| Kicker | `#D8763B` | Uppercase kickery, drobné zvýraznění (jen velký text) |
| Slonovinová | `#FFFDF6` | Pozadí stránky + textura `brand/background-textura.png` |
| Krémová | `#F6F1E7` | Plochy sekcí, dlaždice, tlačítko Zavřít; text na tmavé zeleni |
| Krémová tmavší | `#EFE7D6` | Sekundární plochy, hover ghost |
| Rámy | `#ECE3D2` karty · `#E4DAC6` popupy a inputy · `#D9D0BC` formulářová pole | 1 px (pole 1,5 px) |
| Vybraný stav | pozadí `#F4F7EA` + rám `#4C653D` + prstenec `0 0 0 2px rgba(76,101,61,.16)` | Varianty, balení, karty výběru |
| Text | `#2A2A24` silný · `#4A4A42` běžný · `#6B6B5E` doplňkový · `#8A8776` labely | |
| Hvězdy | `#B8860B` | Jen hodnocení |

Nové odstíny nevymýšlet. Když barva není v `design-system.html` → Barvy → Role barev, nepoužívá se.

### Typografie
- **EB Garamond** (Medium 500, Regular 400): nadpisy, ceny, názvy produktů v kartách.
- **Work Sans** (400 / 500 / 600 / 700): základní písmo a UI. Náhrada: Helvetica.

| Styl | Specifikace |
|---|---|
| H1 hero | EB Garamond 500, 60 / 1.02 (pod 1150 px 44, pod 550 px 34) |
| H2 sekce | EB Garamond 500, 40 / 1.05, #4C653D (pod 1000 px 30) |
| Nadpis modálu | EB Garamond 500, 26 / 1.1, #2A2A24 |
| Název v kartě | EB Garamond 500, 18 / 1.25 |
| Cena | EB Garamond 500, 17–18, #4C653D |
| Kicker | Work Sans 600, 12–13, letter-spacing .12–.16em, uppercase |
| Text | Work Sans 400, 16–17 / 1.6 |
| UI / odkaz | Work Sans 600, 15 |
| Malý text | Work Sans 400, 12,5–13,5 |

Minimum na mobilu: text 13 px, hit target 44 px.

### Tvary a stíny
Rádius 14 px (karty, obrázky, popupy) · 12 px (pole, varianty) · 999 px (tlačítka, vyhledávání, chipy). Stíny: karta při hoveru `0 18px 40px -22px rgba(45,58,46,.45)` + posun −4 px; popup `0 34px 64px -30px rgba(45,58,46,.55)`; focus prstenec `0 0 0 3px rgba(76,101,61,.14)`.

### Layout
Container 1560 px, maximální šířka 1720 px. Boční odsazení stránky 32 px (pod 1000 px 20 px). Mezi sekcemi ~64 px.

## Breakpointy (závazné)
| Název | Šířka |
|---|---|
| XXL | ≥ 1560 px |
| XL | 1150–1559 |
| L | 1000–1149 |
| M | 820–999 |
| S | 550–819 |
| XS | 420–549 |
| XXS | < 420 |

Media queries stavět **jen** na hranicích 1560 / 1150 / 1000 / 820 / 550 / 420 (`max-width: 1559px`, `1149px`, `999px`, `819px`, `549px`, `419px`). Žádné jiné hodnoty.

V návrhu jsou místy ještě starší hranice 900 / 600 / 1180 px. Při implementaci je zarovnejte na nejbližší závaznou hranici.

## Tlačítka
Všechna jsou pill (rádius 999), Work Sans 600, rám 1,5 px; velikosti sm 9×16 px / 13,5 · md 13×28 / 15 · lg 15×30 / 16.
| Varianta | Plocha / text / rám | Kde |
|---|---|---|
| Main | #D14405 / #FFF / #D14405, hover #B23803 | Hlavní nákup — jen světlé podklady a fotografie |
| Primární | #4C653D / #F6F1E7 | Přihlásit, Uložit, Odeslat |
| Sekundární | průhledná / #4C653D / #4C653D | Zobrazit více, Všechny recepty |
| Ghost | průhledná / #4C653D / bez rámu, hover #EFE7D6 | Registrace, doplňkové akce |
| Ghost — zrušení | průhledná / #B23803 | Zrušit všechny filtry |
| Ghost — tlumený | průhledná / #6B6B5E | Zrušit upozornění |
| On dark | #F6F1E7 / #4C653D | Hlavní akce na tmavé zeleni |
| Obrys na tmavé | průhledná / #F6F1E7 / rgba(246,241,231,.5) | Doprovodná akce na tmavé zeleni |
| Na fotografii | rgba(246,241,231,.12) / #F6F1E7 / rgba(246,241,231,.42) | Přehrát video v hero |
| Facebook | #4267B2 / #FFF, hover #375593 | Jen přihlášení |

Ikonová: Zavřít 40 px (#F6F1E7 + rám #E4DAC6), šipky karuselu 38 px (bílá, rám 1,5 px #4C653D, hover zelená výplň), Hledat 42 px (terrakota, bílá lupa), Oblíbené 40 px. Vždy s `aria-label`. Přehled podle podkladu je v `design-system.html` → Tlačítka.

## Klíčové chování
- **Hlavička:** vyhledávací pole přímo v hlavičce na všech breakpointech, na XS/XXS ikona s overlayem. Hamburger od M (<1000), na S bez textu „Menu“. Zelená horní lišta s věrnostním programem a ikonou. Megamenu MM3.
- **Našeptávač:** desktop dva sloupce (2/3 produkty, 1/3 recepty), S na celou šířku pod hlavičkou, XS/XXS přes celý displej. Detail v KOMPONENTY.md.
- **Mobilní overlaye:** košík a přihlášení přes celou obrazovku pod 1000 px. Hamburger menu a vyhledávání pod 550 px.
- **Karusely** (Co chcete vyrábět, Suroviny dle kategorie): nad 1150 px mřížka, pod 1150 px karusel (karta 260 px, scroll-snap, skrytý scrollbar, vlastní posuvník 3 px, šipky 38 px, maska slábnoucí doprava 52 px). Mezikrok 3 sloupce se nepoužívá.
- **Množství u balení:** stepper s krokem podle balení (např. po 100 ks).
- **Video na pozadí:** muted, loop, playsinline, poster, vypnout při `prefers-reduced-motion`.
- **Tooltipy:** bílá bublina, rám #E4DAC6, rádius 12, zobáček 10 px, max. 268 px. Otevírá se po ~600 ms najetí, na dotyku klikem. `pointer-events: none`.
- **Formuláře:** pole 48 px (filtry 46), rám #CFC4AA, rádius 12, popisek nad polem 13 px SemiBold. Focus = zelený rám + prstenec. Chyba = text s ikonou pod polem.
- **Scrollbar ve filtrech:** 10 px, 6 px od pravé hrany, kulaté konce, béžový, při hoveru tmavě zelený.

## Skladovost (`ui-Stock`)
Vždy bez chipu: ikona + text v barvě stavu, u vybraných stavů ikona „i“ s nápovědou.

| Úroveň | state | Text | Barva | Koupit |
|---|---|---|---|---|
| 1 | `digital` | Zasílání elektronicky | #3F7F2C | ano |
| 2 | `ready` | Ihned k odeslání | #3F7F2C | ano |
| 3 | `packing` | Nabalíme po objednání | #57712D | ano |
| 4 | `expected` | Očekáváme + datum | #9E6B00 | ano |
| 5 | `incoming` | Na cestě k nám | #9E6B00 | ano |
| 6 | `toorder` | (na objednávku) | #A33203 | ne → hlídací pes |
| 7 | `longterm` | (dlouhodobě nedostupné) | #8A2412 | ne → hlídací pes |
| 8 | `ended` | (ukončeno) | #8A2412 | ne → náhrada |

Přesné texty a nápovědy jsou v `design/ui-Stock.dc.html` (`static STATES`).

## Stavy objednávky (`ui-OrderStatus`)
`prijato`, `zpracovano`, `ceka_platba`, `pripraveno_expedice`, `pripraveno_odber`, `castecne_expedovano`, `castecne_vyzvednuto`, `expedovano`, `vyzvednuto`, `stornovano`. Varianta a = přepravce, b = osobní odběr. Stav vždy nese ikonu + text, nikdy jen barvu.

## Assety
- **Ikony:** `icons/` (Hugeicons outline 1,5 px). Barví se maskou nebo `currentColor`.
- **Loga:** `brand/ekokoza-logo-green.png` na světlé podklady, `ekokoza-logo-cream.png` na tmavé. V hlavičce na desktopu visačka = `ekokoza-znak-cream.png` + `ekokoza-napis-cream.png`.
- **Maskot:** fotky v `brand/` jsou zatím provizorní. Finální maskot se ještě řeší.
- **Obrázky webu:** `images/` obsahuje přesně ty soubory, které stránky používají (101 souborů): hero a video, dlaždice Co vyrábět a kategorií, ilustrace USP, rozcestníky, receptář, obaly, o nás, komunita, odznaky, dopravci, vlajky, logo a textura. Podsložky odpovídají cestám `assets/…` v návrhu.
- **Fotografie produktů, receptů, kategorií:** slouží jen jako ilustrace. V e-shopu přicházejí z katalogu / CMS. Zmenšené verze jsou v projektu ve složce `assets-lite/`.
- **Fonty:** Google Fonts, licence OFL: EB Garamond 400/500, Work Sans 400/500/600/700.

## Otevřené body (k rozhodnutí)
- Kam vede CTA AI asistenta ve vyhledávání.
- Skutečné ceny balení uzávěrů (teď pracovní data).
- Hodnocení receptů: kdo hodnotí, jakou službou. Zatím jen vizuál.
- Finální maskot, obsah horní lišty, složitost hlaviček kategorií.
- Ověřit hlavičku kolem 1150–1180 px (těsné místo).

## Soubory
Viz **STRANKY.md** (šablony) a **KOMPONENTY.md** (komponenty a props). Historie všech rozhodnutí je v projektu v `upravy.html`.
