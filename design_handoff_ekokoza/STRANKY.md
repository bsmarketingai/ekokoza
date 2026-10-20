# Stránky (šablony e-shopu)

Všechny soubory jsou v `design/`. Otevřete je v prohlížeči přímo ze složky (fonty se načítají z Google Fonts). Dole na některých stránkách je **ovládací lišta ukázky** (Host/Přihlášen, Dostupný/Nedostupný…). Slouží jen pro prezentaci stavů a v e-shopu se neimplementuje.

Každá stránka obsahuje `ui-Header` a `ui-Footer`, horní lištu `ui-InfoBar` a globální `ui-CartAdded`.

## Homepage — `index.html`
1. **Hero V1:** mozaika 4 karet, výška 460 px, mezera 16 px. První velká karta má video na pozadí (`assets/hero/hero-loop.mp4`, muted, loop, playsinline, poster, vypnuté při `prefers-reduced-motion`) a tlačítko „Přehrát video“, které otevře lightbox. Hero V2 (jeden banner) je v souboru zachovaný, klient si varianty přepíná v administraci.
2. **USP V2:** redakční mřížka benefitů.
3. **Co chcete vyrábět?** (`#blok3`): od 1150 px 6 sloupců, pod 1150 px rovnou karusel 260 px. Mezikrok 3 sloupce se nepoužívá.
4. **Suroviny dle kategorie:** `ui-IngredientGrid` s layoutem `carousel` (4 sloupce, pod 1150 px karusel).
5. Karusely produktů a receptů, rozcestník podle zkušenosti, komunitní dílna, recenze.
6. **Newsletter:** nadpis, pole e-mailu s ikonou `mail-01` (pill, rám #E4DAC6) a CTA „Odebírat“, pod tím „Odhlásíte se kdykoli jedním klikem.“ Bez výběru témat.

## Kategorie — `kategorie.html`
- **Výpis V1:** filtry v panelu (drawer), obsah 1280 px.
- **Šablona:** edukativní (úvod, článek, video, mini kurz, srovnání).
- **Hlavička A:** průvodce vpravo, srovnání pod textem.
- **Karta:** `ui-ProductCardV2`.
- Řádek filtrů (facety) je na úzkých šířkách vodorovně posuvný. Následují průvodce chipy, produktový banner po 6. položce a karusel podkategorií.

## Výsledky vyhledávání — `vysledky-vyhledavani.html`
- Záložky Produkty / Recepty / Kategorie a filtry jako v kategorii.
- Kategorie se zobrazují s hierarchií „Kosmetika \ Pomůcky \ Formy“ ve dvou sloupcích, hledaný výraz je zvýrazněný.
- Nadpisy sekcí v EB Garamond.
- Prázdný stav (`?empty=1`) vede na Ekokozího AI asistenta. AI bloky mají přechod #FBF2E1 → #FBD870. **Cíl CTA asistenta zatím není rozhodnutý.**

## Detail produktu — `produkt.html`, `produkt-material.html` (surovina), `produkt-obal.html` (obal)
- Galerie G1 (náhledy po straně) a výběr varianty `ui-VariantPicker`.
- Stepper, CTA Do košíku, nebo místo něj hlídací pes u nedostupného zboží.
- Parametry `ui-ParamStrip`, sekce obsahu jako akordeon, FAQ a dotazy. U odpovědí je zelený znak Ekokozy.
- Buy bar se ukáže při scrollu.
- Recepty v panelu ve variantě R2 (surovina).
- **Obal navíc:**
  - **Výběr barvy:** kulaté vzorky 44 px. Vybraný má zelený rám a uprostřed zatržítko `tick-01` 20 px, bílé na tmavé barvě a #4C653D na světlé. Při najetí se ukáže náhled fotky 100×100 px, na dotyku na 1,8 s.
  - **Kompatibilní uzávěry:** po kliknutí se otevře detail. Volba „Po kusech“ / „Balení 100 ks“ (štítek s úsporou) má radio jako `ui-VariantPicker`. Při volbě balení skočí stepper na 100 a dál přidává po 100. Modal ukazuje součet a „Přidat do košíku“. **Ceny balení jsou zatím pracovní (42 % kusové ceny).**

## Receptář a obsah
- `receptar.dc.html`: kategorie jako řádkové dlaždice s ikonou (V1), filtry Obtížnost / Čas / Co vyrábíte, režim „Co máte doma“. **Hodnocení receptů zatím skryté / jen vizuál.**
- `recept.dc.html` (detail receptu s videem), `slovnicek.dc.html`, `mate-doma.dc.html`.

## Nákup
- `kosik.dc.html`: kroky 1–3, přepínač Host/Přihlášen (jen ukázka). Uložené košíky jen pro přihlášené.
- `objednavka.html`: potvrzení objednávky.

## Účet
`muj-ucet.html`, `ucet.html`, `objednavky.html` (stavy `ui-OrderStatus`), `faktury.html`, `oblibene.html` (i s prázdným stavem). Navigace účtu je v `ui-AccountNav`.

## Ostatní
`vernostni-program.html`, `o-nas.html`.
