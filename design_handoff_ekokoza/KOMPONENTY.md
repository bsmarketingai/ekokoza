# Komponenty

Každá komponenta je samostatný soubor `design/ui-*.dc.html`. Hlavička, patička a overlaye se v e-shopu implementují jednou a vkládají do všech šablon. Seznam props je převzatý z návrhu — v cílovém systému je přizpůsobte datům e-shopu.

## Společná pravidla modálů a popupů

- **Nadpis:** EB Garamond Medium 26 px / 1.1, #2A2A24 (pod 1000 px 25 px / 1.2).
- **Tlačítko Zavřít:** kruh 40 px, pozadí #F6F1E7, rám 1 px #E4DAC6, ikona cancel-01 #4C653D, hover pozadí #EFE7D6.
- **Karta popupu:** bílá, rám 1 px #E4DAC6, rádius 14 px, stín 0 34px 64px -30px rgba(45,58,46,.55).
- **Mobil:** košík a přihlášení přes celou obrazovku pod 1000 px, hamburger menu a vyhledávání pod 550 px. Respektovat `env(safe-area-inset-*)`.
- Zavírání: křížek, klik na podklad, klávesa Esc.

## ui-Header

Hlavička na všech stránkách. Zelená horní lišta (věrnostní program s ikonou), řádek s logem, vyhledávacím polem (vždy V2 — pole přímo v hlavičce), ikonami účtu/oblíbených/košíku a hlavní navigací. Od M (<1000 px) hamburger, na S bez textu „Menu“. Megamenu vždy MM3. Hamburger menu: nad 550 px boční panel 84 % / max 360 px zprava; pod 550 px přes celou obrazovku (bílé pozadí, safe-area). Ověřit těsné místo kolem 1150–1180 px.

Props: `loggedIn: boolean = false`, `customerName: string = "Anežka Drtinová"`, `priceGroup: string = "Registrovaný zákazník"`, `topbarText: string = "Doprava zdarma od 2000 Kč · Ověřené rec`, `homeHref: string = "#"`, `cartCount: number = 2`, `menuTree: MenuNode[]`, `active`, `aboutHref`, `loyaltyHref`, `topbarVariant`, `searchVariant`

## ui-MegaMenu

Varianta MM3 (jediná): kategorie s max. 5 podkategoriemi a odkazem „Zobrazit vše“, vpravo doporučený produkt (ui-MegaProductCard). Otevírá se najetím na položku navigace.

Props: `title: string = "Co chcete vyrábět?"`, `allHref: string = "#"`, `links: {name:string,href:string}[]`, `onClose: () =&gt; void`, `prodName: string = "Levandulové máslo, 100 g"`, `prodPrice: string = "189 Kč"`, `prodImg: string = "assets/products/levandulove-maslo-100-g`, `prodRating: number = 4.8`, `prodRatingCount: number = 214`, `prodCtaVariant: koupit|varianta = "koupit"`, `variant`, `groups`

## ui-SearchOverlay

Našeptávač. Desktop: pod polem v hlavičce, dva sloupce (2/3 produkty, 1/3 recepty jako karty), rádius 14, stín popup. S (550–819): přilepený pod hlavičkou na celou šířku, bez rádiusu, jeden sloupec. XS/XXS (<550): overlay přes celý displej; nahoře pole 52 px (rám #D9D0BC 1,5 px, focus zelený + prstenec), vlevo šedá lupa 22 px, vpravo v poli kulaté oranžové tlačítko 42 px s bílou lupou, vedle pole tlačítko Zavřít 40 px. Boční odsazení položek na XS 16 px.

Props: `active: boolean = true`, `query: string = "mýdla"`, `allLabel: string = "Zobrazit všech 24 produktů"`, `topRecipeName: string = "Mýdlo z bambuckého másla"`, `topRecipeCat: string = "Topovaný recept"`, `topRecipeLevel: Začátečník|Pokročilý|Zkušený = "Začátečník"`, `topRecipeTime: string = "60 min"`, `topRecipeImg: string = "assets/recipes/pasta-na-holeni.jpg"`, `products: {name:string,price:string,av:string,img:string}[]`, `recipes: string[]`, `onInput: (e)=&gt;void`, `onClose: ()=&gt;void`, `submit: (e)=&gt;void`, `inputRef: ref`, `recipeItems`, `recipesAllLabel`, `hideForm`

## ui-CartOverlay

Popup košíku pod ikonou košíku. Hlavička: ikona + „Košík“ EB Garamond 26/1.1 + počet (Work Sans 15/600 #7C7A6A), tlačítko Zavřít. Položky s fotkou, názvem, skladovostí, „n ks × cena“, cenou a odebráním. Patička: Celkem, zbývá do dopravy zdarma, CTA „Přejít do košíku“. Pod 1000 px přes celou obrazovku.

Props: `items: {name:string,price:number,qty:number,av:string,img:string}[]`, `checkoutHref: string = "#"`, `freeShippingFrom: number = 2000`, `onClose: ()=&gt;void`, `onRemove: (i:number,item)=&gt;void`, `onMouseLeave: ()=&gt;void`

## ui-LoginOverlay

Popup přihlášení: nadpis „Přihlaste se“ 26 px, e-mail + heslo s ikonami, „Nevíte heslo?“, Registrace / Přihlásit se, „Přihlásit trvale“, Facebook. Pod 1000 px přes celou obrazovku.

Props: `forgotHref: string = "#"`, `registerHref: string = "#"`, `facebookHref: string = "#"`, `onClose: ()=&gt;void`, `onSubmit: (e)=&gt;void`

## ui-CartAdded

Modal po přidání do košíku: ikona ✓, nadpis „1 kus přidán do košíku“ 26 px, podtitul, karta zboží, pruh „do dopravy zdarma zbývá…“, stav věrnostního programu, patička „Přidané zboží“ + Zpět do obchodu / Přejít do košíku. Poslouchá globální událost přidání do košíku.

Props: `open: boolean = true`, `items: {title:string,variant?:string,qty:number,price:number,noVat?:number,img?:string,state?:string,date?:string}[]`, `cartItems: {title:string,qty?:number,price:number,img?:string}[]`, `cartTotal: number = 0`, `cartCount: number = 0`, `turnover: number = 12400`, `ctaLabel: string = "Přejít do košíku"`, `onClose: ()=&gt;void`, `listen`

## ui-AccountMenu

Menu účtu po přihlášení (jméno, cenová skupina, věrnost, odkazy, odhlášení).

Props: `name: string = "Anežka Drtinová"`, `turnover: number = 12400`, `priceGroup: string = "Registrovaný zákazník"`, `floating: boolean = false`, `logoutHref: string = "#"`, `onClose: () =&gt; void = null`

## ui-Footer

Patička na všech stránkách — tmavě zelená, krémový text, sloupce odkazů, kontakty, odznaky důvěry (Heureka, Google…), dopravci.

Props: `loggedIn: boolean = false`, `loyaltyTier: number = 0`, `company: string = "Ekokoza s.r.o."`, `address: string = "Tvořivá 12, 110 00 Praha"`, `email: string = "info@ekokoza.cz"`, `phone: string = "+420 601 365 245"`, `homeHref: string = "#"`, `copyright: string = "© 2026 Ekokoza s.r.o. — S námi víte, co`, `colAccount: string[]`, `colInfo: string[]`, `colCoop: string[]`, `carriers: string[]`, `colHelp`, `colDiscover`, `colLegal`, `mapHref`, `trustBadges`

## ui-ProductCardV2

Výchozí produktová karta ve výpisech (kategorie, vyhledávání, karusely): výběr balení, množství (ui-QtyStepper), věrnostní cena pro přihlášené, skladovost, oblíbené, badge. Hover: posun −4 px + stín cardHover.

Props: `title: string = "Levandulové máslo"`, `price: string = "189 Kč"`, `pack: string = "100 g"`, `img: string = "assets/products/levandulove-maslo-100-g`, `href: string = "produkt-material.html"`, `variants: object[]`, `ctaVariant: koupit|varianta = "varianta"`, `loggedIn: boolean = false`, `loyaltyTier: number = 10`, `stockState: ready|packing|expected|onway|toorder|longterm|ended = "ready"`, `stockDate: string = "28. 8. 2026"`, `badge: |bestseller|novinka|doporucujeme|prirodni|bio|sada = ""`, `rating: number = 4.6`, `ratingCount: number = 84`, `fav: boolean = false`, `priceNum`, `badgeLabel`, `watchHref`

## ui-ProductCard

Základní karta — zůstává jen tam, kde není výběr balení (část karuselů / výsledků). Výpis kategorie používá výhradně V2.

Props: `fav: boolean = false`, `title: string = "Levandulové máslo, 100 g"`, `price: string = "189 Kč"`, `stockState: ready|packing|expected = "ready"`, `stockDate: string = "28. 8. 2026"`, `img: string = "assets/products/levandulove-maslo-100-g`, `href: string = "#"`, `ctaVariant: koupit|varianta = "koupit"`, `badge: |bestseller|novinka|doporucujeme|akce|sleva|prirodni|bio|sada = "bestseller"`, `badgeLabel: string = ""`, `rating: number = 4.6`, `ratingCount: number = 84`, `stock`, `loggedIn`, `loyaltyTier`, `watchHref`

## ui-VariantPicker

Výběr varianty na detailu produktu. Řádky: radio (vybraná = ikona checkmark-circle-01 24 px #4C653D, nevybraná = kroužek 24 px rám 1,5 px #D8CDB4), štítek, skladovost, cena, jednotková cena. Vybraný řádek: rám #4C653D, pozadí #F4F7EA, prstenec 0 0 0 2px rgba(76,101,61,.16). Nejlevnější varianta: „Nejvýhodnější cena za {jednotka}: {cena}“ — jednotka z jednotkové ceny (ks, l, kg…).

Props: `variants: {label:string, price:string, state?:string, date?:string}[]`, `selected: number = 0`, `heading: string = "Vyberte variantu"`, `maxVisible: number = 4`, `onSelect: (i:number, v:object)=&gt;void`, `mode: select|qty = "select"`, `onQtyChange: (all:object, i:number, qty:number, v:object)=&gt;void`, `resetKey`, `layout`

## ui-QtyStepper

Stepper množství. Prop step: u balení po 100 ks skáče po 100 (první klik na balení nastaví 100).

Props: `value: number = 1`, `min: number = 1`, `max: number = 99`, `onChange: (q:number)=&gt;void`, `height: number = 48`, `step`

## ui-Stock

Skladovost — vždy bez chipu, ikona + text v barvě stavu, volitelně ikona „i“ s nápovědou. 8 stavů, viz tabulka v README.

Props: `state: digital|ready|packing|expected|incoming|toorder|longterm|ended = "ready"`, `variant: inline|pill = "inline"`, `withNote: boolean = false`, `date: string = "28. 8. 2026"`, `size: number = 13`, `noteFocusable`

## ui-Rating

Hodnocení — 5 hvězd s procentní výplní (#B8860B). Zápis „4,75 · 128 hodnocení“. Bez hodnocení se řádek skryje, místo zůstává. U receptů zatím jen vizuál / skryté.

Props: `value: number = 4.75`, `count: number = 128`, `showValue: boolean = true`, `showCount: boolean = true`, `countLabel: boolean = true`, `compact: boolean = false`, `size: number = 14`, `color: #B8860B|#F5C63C = "#B8860B"`, `textColor: string = null`, `trackColor: string = null`

## ui-Badge

Štítek v rohu fotky: bestseller, novinka, doporucujeme, akce, sleva, prirodni, bio, sada. Work Sans 600 11 px, pill, padding 5×10.

Props: `variant: bestseller|novinka|doporucujeme|akce|sleva|prirodni|bio|sada = "bestseller"`, `label: string = ""`

## ui-Button

Referenční tlačítka (na stránkách bývají vložená přímo). Varianty: main (terrakota #D14405, hover #B23803), primary (zelená), secondary (obrys), ghost, onDark (krémová na tmavé zeleni). Velikosti sm 9×16/13.5, md 13×28/15, lg 15×30/16. Vždy pill, Work Sans 600, ikona šipky.

Props: `variant: main|primary|secondary|ghost|onDark = "main"`, `size: sm|md|lg = "md"`, `label: string = "Začněte tady"`, `href: string = "#"`, `showArrow: boolean = true`

## ui-Gallery

Galerie produktu, vždy layout „side“ (G1 — náhledy po straně). Podporuje video a badge.

Props: `layout: side|below = "side"`, `productName: string = "Kyselina citronová"`, `images: {src:string, alt?:string}[]`, `video: {src:string, poster?:string}`, `note: string = "Obrázek je pouze ilustrační."`, `badges: (string|{variant:string,label?:string})[]`

## ui-IngredientGrid

Mřížka kategorií surovin. Layout „carousel“: ≥1150 px mřížka (4 sloupce), pod 1150 px rovnou horizontální karusel (karta 260 px, scroll-snap, posuvník, šipky). Mezikrok 3 sloupce se nepoužívá.

Props: `title: string = "Suroviny dle kategorie"`, `kicker: string = ""`, `subtitle: string = ""`, `allLabel: string = "Všechny suroviny"`, `allHref: string = ""`, `layout: grid|carousel = "grid"`, `columns: number = 4`, `items: {name:string, img?:string, icon?:string, desc?:string, href?:string}[]`, `variant`, `ratio`

## ui-USP

Blok benefitů — finální varianta V2 (redakční mřížka s linkami). Na XS/XXS kompaktní řádky: ikona vlevo, nadpis a popis vpravo.

Props: `media: photo|icon|none = "none"`, `withPhoto: boolean = true`, `photo: string = "assets/maskot-lezici.png"`, `variant: card|plain = "card"`, `tone: light|dark = "light"`, `layout: stack|row = "stack"`, `columns: number = 6`, `iconSize: number = 64`, `title: string = ""`, `kicker: string = ""`, `items: {title:string, desc?:string, img?:string, icon?:string, href?:string}[]`

## ui-FilterPanel

Filtry v panelu (drawer) — výpis kategorie V1. Scrollbar 10 px, 6 px od pravé hrany, kulaté konce, béžový, při hoveru tmavě zelený.

Props: `variant: drawer|sidebar = "sidebar"`, `groups: object[]`, `priceMin: string = ""`, `priceMax: string = ""`, `applyLabel: string = "Zobrazit produkty"`, `onPriceMin`, `onPriceMax`, `onClear`, `onClose`

## ui-WatchDog

Hlídací pes (upozornění na naskladnění) — u stavů toorder / longterm místo tlačítka Do košíku.

Props: `productName: string = "Kyselina citronová monohydrát"`, `variantLabel: string = "25 kg"`, `loggedIn: boolean = false`, `accountEmail: string = "anezka.drtinova@email.cz"`, `boxed: boolean = true`, `onClose: () =&gt; void = null`, `onSubmit: (email: string) =&gt; void = null`

## ui-AccountNav

Props: `active: objednavky|faktury|oblibene|ucet = "objednavky"`, `name: string = "Anežka Drtinová"`, `turnover: number = 12400`, `priceGroup: string = "Registrovaný zákazník"`

## ui-AddToCart

Props: `label: string = "Do košíku"`, `qty: number = 1`, `max: number = 99`, `height: number = 54`, `icon: string = "shopping-cart-check-in-01"`, `onAdd: (qty:number)=&gt;void`, `onQtyChange: (qty:number)=&gt;void`

## ui-Breadcrumb

Props: `items: {label:string, href?:string}[]`, `homeIcon: boolean = true`

## ui-BuyBar

Props: `title: string = "Kyselina citronová"`, `variantLabel: string = "1 kg"`, `variants: object[]`, `selected: number = 0`, `onSelect: (i:number,v:object)=&gt;void`, `price: string = "110 Kč"`, `note: string = "110 Kč / kg"`, `img: string = "assets/products/kyselina-citronova-1-kg`, `buyable: boolean = true`, `needsVariant: boolean = false`, `max: number = 99`, `watch: string = "#ek-buy-cta"`, `pickTarget: string = "#ek-buy-cta"`, `onAdd: (qty:number)=&gt;void`, `onQtyChange: (qty:number)=&gt;void`, `qty`, `stockState`, `stockDate`

## ui-Carousel

Props: `title: string = "Nepotřebujete dokoupit i toto?"`, `subtitle: string = "Suroviny a pomůcky, které se k tomuto p`, `items: object[]`, `loggedIn`, `loyaltyTier`

## ui-CategoryTile

Props: `name: string = "Kosmetika"`, `desc: string = "Krémy, másla a balzámy pro každodenní p`, `hoverLabel: string = "Zobrazit suroviny"`, `img: string = "assets/make/kosmetika.png"`, `imgPosition: string = "center"`, `href: string = "#"`, `tone`, `variant`, `icon`, `title`

## ui-FAQ

Props: `items: {q:string,a:string,icon?:string}[]`, `multiOpen: boolean = true`

## ui-InfoBar

Props: `emoji: string = "🫒"`, `visible: boolean = true`, `text: string = "Připravili jsme pro vás neodolatelnou n`, `linkLabel: string = "Prohlédnout"`, `href: string = "kategorie.html"`

## ui-IngredientTile

Props: `name: string = "Oleje"`, `icon: string = ""`, `img: string = "assets/categories/oleje.png"`, `desc: string = ""`, `href: string = "#"`, `variant: row|lifestyle = "row"`, `ratio: 4/3|1/1|3/2|16/9 = "4/3"`, `iconColor`, `title`

## ui-LoyaltyStatus

Props: `turnover: number = 12400`, `variant: full|compact = "full"`, `onDark: boolean = false`, `showScale: boolean = true`, `showLink: boolean = true`, `href: string = "vernostni-program.html"`

## ui-MegaProductCard

Props: `kicker: string = "Topovaný produkt"`, `title: string = "Levandulové máslo, 100 g"`, `price: string = "189 Kč"`, `rating: number = 4.8`, `ratingCount: number = 214`, `ctaVariant: koupit|varianta = "koupit"`, `img: string = "assets/products/levandulove-maslo-100-g`, `href: string = "#"`, `onNavigate: () =&gt; void`

## ui-OrderStatus

Props: `state: prijato|zpracovano|ceka_platba|pripraveno_expedice|pripraveno_odber|castecne_expedovano|castecne_vyzvednuto|expedovano|vyzvednuto|stornovano = "expedovano"`, `size: number = 13`, `plain: boolean = false`

## ui-ParamStrip

Props: `items: {k:string, v:string, icon?:string}[]`, `iconSize: number = 26`, `iconColor: #4F6E2A|#4C653D|#D14405 = "#4F6E2A"`, `tone`

## ui-ProductBanner

Props: `kicker: string = "Recepty"`, `title: string = "Vlastní parfém z přírodních silic"`, `desc: string = "Jak poskládat hlavu, srdce a základ vůn`, `cta: string = "Zobrazit recept"`, `href: string = "recept.dc.html"`, `img: string = "assets/banners/parfemy.png"`, `imgPosition: string = "center 40%"`

## ui-RecipeCard

Props: `title: string = "Krém na paty a ztvrdlá místa"`, `desc: string = "Vyživující krém, který změkčí ztvrdlou `, `category: string = "Kosmetika"`, `type: string = ""`, `level: Začátečník|Pokročilý|Zkušený = "Začátečník"`, `time: string = "30 min"`, `rating: number = 4.8`, `ratingCount: number = 34`, `fav: boolean = false`, `coverage: string = ""`, `complete: boolean = false`, `cta: string = ""`, `img: string = "assets/recipes/krem-na-paty.jpg"`, `href: string = "#"`, `ingredients: string[]`, `missing: string[]`, `onAddMissing: (m:string[])=&gt;void`, `showRating`

