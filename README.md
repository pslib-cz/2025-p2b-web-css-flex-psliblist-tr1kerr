# CSS Flexbox - Zpravodajství

live demo: https://pslib-studium.github.io/CSSFlexPSLIBList/

## Cíl cvičení

Cílem tohoto cvičení je procvičit práci s **CSS Flexbox** pro vytvoření responzivního seznamu článků. Naučíte se, jak pomocí flexboxu:
- Uspořádat elementy horizontálně
- Ovládat pořadí elementů pomocí `order`
- Pracovat s růstem a smrštěním flexbox položek
- Kombinovat flexbox s dalšími CSS vlastnostmi

## Důležité omezení

- **Modifikujte pouze soubor `styles/style.css`**
- Změny v HTML nejsou povoleny
- Soubor `styles/noedit.css` neupravujte
- Přesto že se jedná o cvičení na flexbox, není účelem dávat `display: flex` i tam, kam přirozeně patří `display: block` nebo `text-align`

## Zadání

### 1. Responzivní obrázky
Obrázky v článcích musí být responzivní a správně se přizpůsobit kontejneru.

**Úkol:** Vytvořte CSS třídu `.img-responsive` s následujícími vlastnostmi:
- Obrázek musí být **responzivní** - šířka a výška se přizpůsobí kontejneru
- Použijte vlastnost `object-fit` pro zachování poměru stran obrázku
- Obrázek se zobrazí jako **inline-block** element

**Poznámka:** Kontejner odkazu `.news-item__image-link` má aspect-ratio 4/3 a výšku 90px, což je již nastaveno v `noedit.css`.

### 2. Kontejner stránky
Vytvořte responzivní kontejner s těmito vlastnostmi:
- **Maximální šířka**: 1200px
- **Minimální šířka**: 600px
- Kontejner musí být **horizontálně vycentrovaný**

### 3. Položka článku (News Item)
Každá zpravodajská položka se skládá ze tří částí:
1. **Datum** (`.news-item__date`)
2. **Barevná tečka** (vizuální separátor)
3. **Článek** (`.news-item__article`)

**Úkol:** Uspořádejte tyto tři části horizontálně vedle sebe pomocí flexboxu.

### 4. Box s datem
Datum se zobrazuje ve čtverci o hraně **116px** a obsahuje měsíc a den (rozměry jsou již nastaveny v `noedit.css`).

**Požadavky:**
- Text musí být **vystředěn** (horizontálně)
- Box používá **flexbox** s vertikálním směrem (`flex-direction: column`)
- Mezi měsícem a dnem je **růžová linka** (bottom border, 2px, barva `--color-bg-pink`)
- Pod dnem je **akcentová linka** (bottom border, 6px, barva `--category-accent`)
- Den **roste** do volného prostoru (`flex-grow`)
- Box nesmí být deformován při změně šířky stránky (`flex-shrink`)
- Datum se zobrazuje jako **první** v pořadí

### 5. Barevná tečka (Separator)
Mezi datumem a článkem je vizuální separator.

**Specifikace:**
- Tečka průměr **8px** (barva `--category-accent`)
- Růžový okraj (border) **3px** (barva `--color-bg-pink`)
- Kulatý tvar (border-radius 50%)
- Tečka je **vertikálně vycentrovaná** vzhledem k celé výšce položky
- Zobrazuje se jako **druhá** v pořadí
- Překrývá se středem s okrajem datumu a článku (negativní margin -3px)
- Musí být nad ostatními elementy (`z-index: 1`)

**Nápověda:** Použijte pseudoelement `::before` na `.news-item`

### 6. Box s článkem
Box obsahuje obrázek (volitelný), nadpis, text a patičku.

**Požadavky:**
- Všechny boxy s perexem článku jsou **stejně široké** (rostou do volného prostoru)
- Box je zobrazený jako **třetí** v pořadí
- Obsah boxu (obrázek a text) je uspořádán horizontálně pomocí flexboxu
- Obrázek nesmí být deformován (`flex-shrink`)
- Mezera mezi obrázkem a textem: **1rem**
- Pravé vnitřní odsazení perexu (padding-right): **2.5rem** - aby se červená šipka nepřekrývala s textem

### 7. Odkaz "více" (More Link)
Bílá šipka v gradientním kroužku slouží jako odkaz na celý článek.

**Požadavky:**
- Text "více" je **neviditelný** (použijte `font-size: 0`)
- Bílá šipka "->" je viditelná díky `::after` pseudoelementu (stylováno v `noedit.css`)
- Po **najetí myší** se barva rámečku změní na **vínovou** (`border-color: --color-accent1`)

### 8. Interaktivita odkazů
**Všechny odkazy** musí vizuálně reagovat na přejetí myší:

- **Odkaz v nadpisu** (`.news-item__title-link`):
  - Při hover: barva textu se změní na `--color-hover-title`
  
- **Odkaz v kategorii** (`.news-item__category-link`):
  - Při hover: přidá se podtržení (`text-decoration: underline`)

- **Odkaz "více"** (`.news-item__more-link`):
  - Při hover: barva rámečku kolem šipky se změní na `--color-accent1`

### 9. Modifikátory kategorií
Různé kategorie článků mají různé barevné schéma. Barvy se mění pomocí CSS proměnných.

**Požadavky:**  
Vytvořte modifikátory pro tři kategorie:

- `.news-item--school` - barva `--color-accent2`
- `.news-item--engineering` - barva `--color-accent3`  
- `.news-item--success` - barva `--color-accent4`

Každý modifikátor přepisuje proměnné `--category-text` a `--category-accent` na odpovídající barvu

## CSS Custom Properties (proměnné)

Pro snadnější práci s barvami jsou v `noedit.css` definovány CSS proměnné:

```css
--color-white           /* bílá */
--color-hover-title     /* barva nadpisu při hover */
--color-shadow          /* barva stínu (RGB hodnoty) */
--color-text            /* hlavní barva textu */
--color-text1           /* růžová pro nadpis h1 */
--color-text2           /* fialová pro nadpisy článků */
--color-text3           /* tmavě fialová pro datum */
--color-text4           /* šedá pro patičku */
--color-bg-pink         /* růžové pozadí */
--color-accent1         /* vínová (hover rámeček) */
--color-accent2         /* tmavě růžová (výchozí kategorie) */
--color-accent3         /* modrá (strojírenství) */
--color-accent4         /* zelená (úspěchy) */
--color-gradient        /* gradient pro šipku */

/* Proměnné pro kategorie (přepisovatelné modifikátory) */
--category-text         /* barva textu kategorie */
--category-bg           /* pozadí kategorie */
--category-accent       /* akcentová barva kategorie */
```

## BEM metodika

Projekt využívá **BEM** (Block Element Modifier) metodiku pro pojmenování CSS tříd:

### Block: `news-item`
Hlavní sémantický blok reprezentující jednu zpravodajskou položku.

### Elementy:
- `news-item__date` - box s datem
- `news-item__date-part` - měsíc nebo den
- `news-item__article` - box s obsahem článku
- `news-item__image-link` - odkaz s obrázkem
- `news-item__title` - nadpis článku
- `news-item__title-link` - odkaz v nadpisu
- `news-item__content` - textový obsah
- `news-item__excerpt` - perex článku
- `news-item__more-link` - odkaz "více"
- `news-item__footer` - patička s metadaty
- `news-item__category` - kategorie článku
- `news-item__category-link` - odkaz na kategorii
- `news-item__author` - jméno autora

### Modifikátory:
- `news-item__date-part--month` - modifikátor pro měsíc
- `news-item__date-part--day` - modifikátor pro den
- `news-item--school` - modifikátor pro kategorii "O škole"
- `news-item--engineering` - modifikátor pro kategorii "Strojírenství"
- `news-item--success` - modifikátor pro kategorii "Úspěchy"

## Tipy a nápovědy

### Flexbox vlastnosti, které budete potřebovat:
- `display: flex` - zapne flexbox režim
- `flex-direction` - směr hlavní osy (row, column)
- `order` - určuje pořadí zobrazení flex položek
- `flex-shrink` - určuje, zda se položka může zmenšit
- `flex-grow` - určuje, zda položka může růst do volného prostoru
- `align-self` - vertikální zarovnání konkrétní položky
- `gap` - mezera mezi flex položkami

### Další užitečné vlastnosti:
- `text-align` - horizontální zarovnání textu
- `border-bottom` - spodní ohraničení
- `border-color` - barva ohraničení
- `margin` - vnější okraje (může být i záporný!)
- `padding` - vnitřní odsazení
- `z-index` - vrstvení elementů

### CSS proměnné:
- `var(--nazev-promenne)` - použití CSS proměnné
- Přepsání proměnné v selektoru: `--category-accent: var(--color-accent3);`

### Responzivní obrázky:
- `width` a `height` - šířka a výška (v %, px, rem, atd.)
- `object-fit` - způsob přizpůsobení obrázku do kontejneru (cover, contain, fill)
- `display` - typ zobrazení elementu (block, inline, inline-block)

### Pseudoelementy:
- `::before` - vložení obsahu před element
- `::after` - vložení obsahu za element

### Pseudotřídy:
- `:hover` - stav při najetí myši
