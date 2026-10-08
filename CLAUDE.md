# ekokoza.cz

## Brand positioning & tone of voice
Plné brand positioning je v `brand/brand-positioning.md` — **používej ho pro veškerý copywriting.**

### Claim architektura (v03 FINAL, červenec 2026)
Hlavní claimová dvojice — používat spolu:
- **„S námi víte, co tvoříte."** (postojová věta — homepage, brandové bloky, bannery)
- **„Suroviny, recepty a ověřené postupy."** (čím to značka naplňuje)

Podpůrné aplikační věty (nenahrazují hlavní claim, rozvíjejí ho podle kontextu):
- **„Od suroviny k vlastnímu výrobku."** — recepty, návody, rozcestníky, komunikace krok za krokem
- **„Provedeme vás vlastní výrobou."** — začátečníci, startovací obsah, edukace
- **„Vše pro vlastní výrobu."** — homepage, kategorie, sortimentní sdělení („domácí výrobu“ tam, kde jde primárně o koncové zákazníky, ne malovýrobce)

Starší claimy („Důvod, proč tvořit.“, „Suroviny, recepty a důvod proč.“, „Vědět proč. Vědět jak.“) se už **nepoužívají.**

### Tone of voice (závazné)
- Klidný, věcný, vysvětlující — jako zkušený člověk z praxe („ekologie z praxe, ne z počítače").
- **Vysvětlujeme, netlačíme.** Žádná slevová urgence, odpočty, „poslední kus", CAPS, vykřičníky, agresivní badge.
- Vykáme. „váš" s malým v (velké jen v přímém oslovení).
- Bez superlativů a reklamních frází („nejlepší", „prémiové", „100% čisté") bez faktické opory.
- Emoji nepoužíváme jako běžný prostředek.
- Recept = most mezi surovinou a výsledkem (páteř systému, ne doplněk).
- Věrnost/objem = férová odměna za dlouhodobý vztah, NE slevová hra.

### Vizuál
- Přírodní, tlumená paleta (slonovinová #F6F1E7, jediná tmavě zelená #4C653D dle manuálu, terrakota #D14405 jen pro hlavní konverze). Role každé barvy jsou popsané v `design-system.html` → Barvy → Role barev; nové odstíny nevymýšlet.
- EB Garamond (serif, nadpisy — Medium a Regular) + Work Sans jako základní písmo (SemiBold nadpisy, Medium perexy, Regular/Bold text; náhrada Helvetica). Kulaté rohy 14px. Container 1560 / max 1720px.
- **Breakpointy (závazné, definované na začátku projektu):**
  - XXL: 1560 px a víc
  - XL: 1150–1560 px
  - L: 1000–1150 px
  - M: 820–1000 px
  - S: 550–820 px
  - XS: 420–550 px
  - XXS: 420 px a méně
  - Media queries stavět jen na hranicích 1560 / 1150 / 1000 / 820 / 550 / 420 (např. „na XS/XXS“ = max-width: 549px). Žádné vymyšlené hodnoty (600, 760, 900 apod.).
- Loga v `assets/` (zelené pro světlé pozadí, krémové pro tmavé).
- Realistické fotky produktů a procesu/lidí; žádné „pohádkové bio scény".

## Workflow
- **Každou uzavřenou úpravu zapiš do `upravy.html`** (changelog úprav ze schůzek) — hned po dokončení, s datem.
- `upravy.html` = kompletní historie rozhodnutí. Před novou prací ho přečti (hlavně sekci „Probrat na schůzce“ = otevřené otázky). Nová data přidávej nahoru.
- `ukolovnik.dc.html` = úkolovník.
- Malé úpravy dělej cíleně, ostatního se nedotýkej. Větší redesign = kopie souboru (v1/v2).

## Struktura projektu (stav k 8. 10. 2026)
Projekt je soběstačný, nic neodkazuje na externí design systém. **Zdroj pravdy pro vizuál je `design-system.html`** + komponenty `ui-*.dc.html`.

**Stránky (šablony e-shopu):**
- `index.html` — homepage (hero V1, karusely, rozcestník podle zkušenosti, komunitní dílna, recenze)
- `kategorie.html` — výpis kategorie (filtry, průvodce chipy, produktový banner, podkategorie karusel)
- `vysledky-vyhledavani.html` — výsledky vyhledávání: záložky Produkty / Recepty / Kategorie, filtry jako v kategorii, prázdný stav `?empty=1` (vede na Ekokozího AI asistenta), AI bloky žlutý gradient #FBF2E1→#FBD870
- `produkt.html` (obecný detail), `produkt-material.html` (původní šablona suroviny), `produkt-obal.html` (obal s výběrem uzávěru)
- `receptar.dc.html`, `recept.dc.html`, `slovnicek.dc.html`, `mate-doma.dc.html`
- `kosik.dc.html` (kroky 1–3, přepínač Host/Přihlášen, uložené košíky jen pro přihlášené), `objednavka.html`
- Účet: `muj-ucet.html`, `ucet.html`, `objednavky.html`, `faktury.html`, `oblibene.html`
- `vernostni-program.html` (+ v1), `o-nas.html` (+ v1)

**Komponenty:** `ui-*.dc.html` (Header, Footer, MegaMenu MM3 = výchozí, SearchOverlay, ProductCard/V2, RecipeCard, FilterPanel, CartOverlay, CartAdded, Stock, Badge, Button…). Hlavička a patička se importují do všech stránek — změny dělej v komponentě, ne na stránce.

**Assety:** `assets/` (plné), `assets-lite/` (zmenšené pro rychlé načítání), `uploads/` (podklady od klienta vč. Hugeicons sad — ikony používáme z nich), `brand/brand-positioning.md`.

## Klíčová rozhodnutí (výběr, detail v upravy.html)
- **Vyhledávání V2:** pole přímo v hlavičce na všech breakpointech vč. M a S; hamburger od M; na S bez textu „Menu“. Našeptávač ve dvou sloupcích: 2/3 produkty, 1/3 recepty (jako karty). Věrnostní program v zelené horní liště s ikonou (jen V2).
- **Kategorie ve výsledcích:** hierarchie „Kosmetika \ Pomůcky \ Formy“, dva sloupce, zvýrazněný hledaný výraz.
- **Scrollbar ve filtrech:** 10 px, 6 px od pravé hrany, kulaté konce, béžová, tmavě zelená při hoveru.
- **Dostupnost:** stav skladovosti vždy bez chipu; „Očekáváme“ / „Na cestě k nám“ oranžovo-žlutě; ikona „i“ s nápovědou.
- **Hodnocení receptů** zatím skryté / jen vizuál.
- Nadpisy sekcí ve výsledcích v EB Garamond.

## Otevřené body
- Kam vede CTA tlačítko AI asistenta.
- Vizuálně ověřit hlavičku kolem 1150–1180 px (těsné místo).
- Finální maskot (zatím provizorní fotky), obsah horní lišty, složitost hlaviček kategorií — viz „Probrat na schůzce“ v upravy.html.
