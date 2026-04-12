# DeepDual: Manuál vizuální identity značky

_Verze 1.0, 11. dubna 2026_

Tento dokument popisuje vizuální identitu značky DeepDual podle aktuálního webu, jeho obsahu, loga, typografie, barevných tokenů, komponent a způsobu, jakým značka komunikuje téma AI Reliability Engineering. Slouží jako praktický manuál pro konzistentní tvorbu webových stránek, prezentací, technických dokumentů, sociálních náhledů, ikon a dalších materiálů značky.

## 1. Podstata značky

DeepDual je technicky orientovaná konzultační značka pro týmy, které posouvají AI a LLM systémy z prototypů do produkce. Značka nestaví na obecném nadšení z AI, ale na otázce, zda systém obstojí pod reálnou zátěží, proti bezpečnostním rizikům, regresím, nákladům a driftu.

Primární pozice značky:

> AI reliability engineering pro týmy, které nasazují LLM systémy do produkce.

Vizuální identita má působit:

- technicky, přesně a inženýrsky
- sebevědomě, ale bez agresivního prodeje
- tmavě, kontrastně a soustředěně
- systematicky, s důrazem na data, metriky a kontrolní mechanismy
- produkčně, ne experimentálně
- moderně, ale ne módně nebo dekorativně

Hlavní vizuální metafora je **systém, který drží v produkci**. Tomu odpovídá tmavé prostředí, jemná technická mřížka, hranaté komponenty, monospace metadata, měřitelné metriky a přesný tyrkysový signál.

## 2. Strategická myšlenka

### Hlavní sdělení

Klíčové sdělení homepage zní:

> Your AI works in demo. Does it hold in prod?

Tato věta definuje tón celé identity. Je přímá, technická a lehce konfrontační. Neprodává abstraktní „AI transformaci“, ale upozorňuje na konkrétní produkční riziko.

### Pilíře značky

- **Reliability**: AI systém musí být měřitelně stabilní, ne pouze působivý v demu.
- **Security**: LLM aplikace mají specifické útokové plochy, které vyžadují architektonickou obranu.
- **Performance**: Latence, jednotkové náklady a propustnost jsou součástí spolehlivosti.
- **Evidence**: Rozhodování má stát na evalech, baselinech, metrikách a regresních branách.
- **Production discipline**: Každý vizuální i obsahový prvek má podporovat dojem produkční připravenosti.

## 3. Logo

### Základní podoba

Logo DeepDual je čtvercový monogram založený na písmenu **D**. Symbol pracuje se dvěma propojenými tvary:

- vnější robustní tmavé **D**
- vnitřní negativní/tyrkysové **D**, které vytváří dojem duality, vrstvení a technického průchodu systémem

Symbol je umístěn na tyrkysovém čtvercovém poli. Tmavý monogram používá stejný vizuální jazyk jako web: silný ink odstín, jednoduchou geometrii, přesnost a minimální dekorativnost.

### Dostupné logo assety

Používejte existující rastrové soubory:

| Soubor | Velikost | Doporučené použití |
| --- | --- | --- |
| `static/icons/logo-mobile.png` | 120 x 120 px | malé UI použití, navigace |
| `static/icons/logo-mobile@2x.png` | 240 x 240 px | retina varianta pro navigaci |
| `static/icons/logo-desktop.png` | 240 x 240 px | větší digitální plochy |
| `static/icons/logo-desktop@2x.png` | 480 x 480 px | retina varianta pro větší plochy |
| `static/icons/favicon-16x16.png` | 16 x 16 px | favicon |
| `static/icons/favicon-32x32.png` | 32 x 32 px | favicon |
| `static/icons/apple-touch-icon.png` | 180 x 180 px | Apple touch icon |
| `static/icons/android-chrome-192x192.png` | 192 x 192 px | PWA a social fallback |
| `static/icons/android-chrome-512x512.png` | 512 x 512 px | Open Graph / PWA fallback |
| `static/icons/mstile-150x150.png` | 150 x 150 px | Microsoft tile |

### Samostatný symbol

Samostatný symbol používejte pro:

- favicony
- mobilní UI
- sociální avatary
- malé značkové signatury
- místa, kde je název DeepDual už přítomný v okolním textu

Symbol musí vždy zůstat čtvercový. Nedeformujte ho, neořezávejte ho, neumisťujte ho do dalších dekorativních rámečků a neměňte jeho vnitřní barvy.

### Kombinovaná lockup varianta

Na webu se používá horizontální lockup:

- čtvercový symbol vlevo
- textový nápis **DeepDual** vpravo
- mezera mezi symbolem a textem: 10 px
- symbol v hlavní navigaci: 36 x 36 px
- symbol ve footeru: 28 x 28 px
- radius symbolu v navigaci: 4 px
- radius symbolu ve footeru: 3 px
- text DeepDual: Syne, váha 800, barva `#e2e8f5`

Toto je hlavní webová varianta loga. Pro další digitální materiály ji používejte tam, kde má symbol minimálně 28 px a nápis DeepDual zůstává čitelný.

### Minimální velikosti

- Favicon: 16 x 16 px, pouze symbol
- Malá UI ikona: 24 x 24 px, pouze symbol
- Navigace: 36 x 36 px symbol + text
- Footer: 28 x 28 px symbol + text
- Sociální avatar: 192 x 192 px nebo více, pouze symbol
- Titulní slide prezentace: symbol alespoň 64 x 64 px, ideálně 96 x 96 px nebo více

### Ochranná zóna

Ochranná zóna kolem samostatného symbolu má být minimálně **25 % šířky symbolu** na všechny strany. U horizontální lockup varianty zachovejte interní mezeru 10 px mezi symbolem a textem. Vnější ochranná zóna celé lockup varianty má být minimálně 8-12 px v malém UI a úměrně větší ve větších formátech.

### Umístění loga

Primární umístění:

- vlevo nahoře ve sticky navigaci
- vlevo ve footeru jako součást brand bloku
- v prezentacích vlevo nahoře nebo vpravo dole, podle typu slidu
- u sociálních avatarů samostatně a centrovaně

Logo nepoužívejte jako dekorativní pattern, watermark přes obsah nebo pozadí sekcí. Má být orientační bod, ne dekorace.

### Zakázané úpravy loga

- neměnit tyrkysové pozadí symbolu
- nepřebarvovat tmavý monogram
- nenatahovat symbol mimo poměr 1:1
- nepřidávat stíny, glow efekty, gradientní orby ani rámečky
- nepoužívat symbol na podobně tyrkysovém pozadí bez jasného kontrastu
- nenahrazovat text DeepDual jiným fontem v lockup variantě
- nepoužívat logo jako opakovaný dekorativní motiv

## 4. Barevný systém

Barvy jsou definované primárně v CSS proměnných v `templates/base.html`. Tailwind konfigurace obsahuje starší amber paletu, ale aktuální identita webu používá tyrkysový akcent `#00A4A6`. Pro značkové materiály je proto rozhodující tokenový systém z aktuálního webu.

### Primární paleta

| Token | HEX | Role |
| --- | --- | --- |
| Ink | `#101820` | hlavní pozadí, základní tmavá plocha, text v primárních tlačítkách |
| Surface 0 | `#141f2a` | sekundární sekce, footer, karty |
| Surface 1 | `#1a2838` | aktivnější plochy, hover stavy, inputy |
| Surface 2 | `#202f42` | hlubší vrstvení, rezervní tmavá plocha |
| Border | `#243850` | standardní linky, děliče, okraje karet |
| Border Hi | `#2e4868` | hover okraje, silnější dělení, aktivní okraje |
| Text 1 | `#e2e8f5` | primární text, nadpisy, logo text |
| Text 2 | `#7b8faa` | běžný body text a popisy |
| Text 3 | `#3d5070` | metadata, sekundární popisky, low-emphasis text |
| Accent | `#00A4A6` | primární tyrkysový akcent, CTA, metriky, štítky, linky |
| Accent High | `#00c8ca` | hover stav akcentu a silnější call-to-action |

### Podpůrné barvy

| Token | Hodnota | Role |
| --- | --- | --- |
| Accent Low | `rgba(0,164,166,0.12)` | jemné pozadí tagů a akcentních prvků |
| Success | `#22c55e` | success/outcome signalizace |
| Success Low | `rgba(34,197,94,0.08)` | pozadí outcome badge |
| Success Text | `#86efac` | text ve success stavech |
| Error Text | `#fca5a5` | error flash message |

### Role barev

Tyrkysová nesmí převzít celou obrazovku. Má fungovat jako přesný signál pro:

- CTA tlačítka
- štítky a kategorie
- metriky
- linky a šipky
- akcentní dělicí linky
- focus stavy
- aktivní okraje
- favicon/theme-color

Tmavé plochy vytvářejí hierarchii. `Ink` je základ, `Surface 0` zvedá sekce, `Surface 1` zvedá interaktivní prvky a `Border` odděluje informace. Nepoužívejte velké světlé plochy; značka stojí na tmavém technickém prostředí.

### Doporučené kombinace

- Hlavní pozadí: `#101820`
- Sekundární sekce: `#141f2a`
- Karty: `#141f2a` s okrajem `#243850`
- Hover karta: `#1a2838` s okrajem `#2e4868`
- Primární nadpis: `#e2e8f5`
- Body text: `#7b8faa`
- Metadata: `#3d5070`
- CTA pozadí: `#00A4A6` s textem `#101820`
- CTA hover: `#00c8ca` s textem `#101820`

### Zakázané barevné použití

- Nepoužívejte žlutou/oranžovou amber paletu z Tailwind konfigurace jako aktuální brand akcent.
- Nepoužívejte fialové, modro-fialové, béžové nebo oranžovo-hnědé dominantní palety.
- Nepoužívejte tyrkysovou jako velké celoplošné pozadí mimo logo a vybrané systémové ikony.
- Nepoužívejte čistě bílý text `#ffffff` jako výchozí styl; značkový světlý odstín je `#e2e8f5`.
- Nepoužívejte neutrální šedou bez modrého podtónu; neutraly mají být navázané na tmavý ink systém.

## 5. Typografie

Typografický systém je založený na trojici Google Fonts:

- **Syne** pro display nadpisy a brand text
- **Outfit** pro hlavní text, tlačítka a formuláře
- **JetBrains Mono** pro labely, metadata, kód, čísla a technické značky

### Syne

Použití:

- H1, H2 a H3 nadpisy
- textový nápis DeepDual v logo lockupu
- velké metriky
- titulní slidy a hero sdělení

Váhy:

- 700 pro běžné nadpisy
- 800 pro hero, logo text a metriky

Webové vzory:

- Hero H1: `clamp(2.8rem, 7vw, 5.5rem)`, line-height `1.05`, weight `800`, letter-spacing `-0.025em`
- Stránkový H1: `clamp(2.2rem, 5.5vw, 3.8rem)`, line-height `1.08`, weight `800`, letter-spacing `-0.02em`
- H2: `clamp(1.8rem, 4vw, 2.5rem)`, line-height `1.12-1.15`, weight `700`
- Karty H3/H4: `0.95rem-1.2rem`, weight `700`

Syne používejte pro krátké, silné fráze. Není určený pro dlouhé odstavce.

### Outfit

Použití:

- body text
- navigace
- tlačítka
- formuláře
- popisy služeb
- vysvětlující odstavce

Váhy:

- 400 pro body text
- 500 pro sekundární interaktivní prvky
- 600 pro primární CTA

Webové vzory:

- Body text: `0.875rem-1rem`, line-height `1.65-1.8`
- Hero paragraph: `1.15rem`, line-height `1.75`, max-width cca `520px`
- Tlačítka: `0.9rem`, weight `500-600`
- Form input: `0.9rem`

Outfit vyvažuje výraznější Syne a drží technické texty čitelné.

### JetBrains Mono

Použití:

- labely typu „AI Reliability Engineering“, „The Problem“, „What We Do“
- čísla problémů a practice kódy
- metadata v blogu a case studies
- kategorie/tagy
- tabulkové hlavičky
- kódové ukázky
- footer claims

Webové vzory:

- Label: `0.68rem`, uppercase, letter-spacing `0.14em`, barva `#00A4A6`
- Form label: `0.65rem`, uppercase, letter-spacing `0.12em`, barva `#3d5070`
- Metadata: `0.65rem-0.72rem`, letter-spacing `0.03em-0.14em`

Monospace text používejte pro systémové značky a metadata, ne pro dlouhé odstavce.

## 6. Layout a kompozice

### Kontejner

Hlavní obsah webu používá:

- max-width: `72rem`
- horizontální padding: `1.5rem`
- centrování: `margin: 0 auto`

Tento kontejner je základní jednotkou pro homepage, services page, blog, case studies i kontaktní bloky.

### Sekční odsazení

Typické hodnoty:

- Hero: `6rem 0 5rem`
- Page header: `5rem 0 4rem`
- Službové sekce: `5rem 0`
- Service cards blok: `6rem 0`
- Contact sekce: `6rem 0`
- Social proof strip: `3.5rem 0`

Sekce jsou oddělené linkami `1px solid #243850` a střídají základní `Ink` pozadí se `Surface 0`.

### Vrstvení

DeepDual nepoužívá těžké stíny ani glassmorphism. Vrstvení se vytváří pomocí:

- tmavších a světlejších surface hodnot
- tenkých okrajů
- jemných hover změn
- malých posunů o 2 px
- horizontálních dělicích linek

### Pozadí

Základní body pozadí kombinuje:

- barvu `#101820`
- jemný radialní tečkový pattern
- barvu bodů `rgba(36,56,80,0.55)`
- velikost bodu `1px`
- rozestup `26px 26px`

Pattern má působit jako jemná technická textura. Nemá být dominantní grafický motiv.

### Horní akcentní linka

Hero a stránkové hlavičky používají 2px horizontální gradient:

```css
linear-gradient(90deg, transparent, #00A4A6 40%, transparent)
```

Tato linka je signatura pro začátek hlavní obsahové oblasti. Používejte ji na důležitých stránkách, ne na každé malé sekci.

## 7. Komponenty

### Navigace

Navigace je sticky:

- výška: 60 px
- pozadí: `rgba(16,24,32,0.9)`
- backdrop blur: 14 px
- spodní okraj: `1px solid #243850`
- logo vlevo
- desktop odkazy vpravo
- CTA „Get in Touch“ jako primární tlačítko

Navigace má být klidná a funkční. Nepoužívejte velké menu bloky, dekorativní animace ani barevně silná pozadí.

### Navigační odkazy

Nav link:

- default barva: `#7b8faa`
- hover barva: `#e2e8f5`
- hover underline: `1px` tyrkysová linka
- transition: `0.18s`

Podtržení se animuje z nulové šířky na 100 %. Tento detail podporuje přesný technický charakter.

### Primární tlačítko

Primární CTA:

- pozadí: `#00A4A6`
- text: `#101820`
- font: Outfit, weight 600
- velikost: `0.9rem`
- padding: `0.6rem 1.5rem`
- radius: 3 px
- hover pozadí: `#00c8ca`
- active: scale `0.98`

Použití:

- hlavní konverzní akce
- odeslání kontaktního formuláře
- sekční „Start with ...“ CTA

Primární tlačítko musí být výrazné, ale ne kulaté, lesklé nebo hravé. Zachovejte hranatý technický charakter.

### Sekundární tlačítko

Outline CTA:

- transparentní pozadí
- text: `#e2e8f5`
- okraj: `1px solid #2e4868`
- radius: 3 px
- hover: okraj a text `#00A4A6`
- font: Outfit, weight 500

Použití:

- „View Services“
- „Read Case Studies“
- sekundární navigační akce

### Karty

Karta:

- pozadí: `#141f2a`
- okraj: `1px solid #243850`
- radius: 4 px
- hover pozadí: `#1a2838`
- hover okraj: `#2e4868`
- hover transform: `translateY(-2px)`

Vhodné použití:

- služby
- case studies
- feature bloky
- technické checklisty

Karty jsou informační jednotky, ne dekorativní kontejnery. Nevkládejte kartu do karty a nepoužívejte velké radiusy, drop shadow nebo glassmorphism.

### Tagy a labely

Tagy a labely:

- JetBrains Mono
- uppercase
- letter-spacing `0.1em-0.16em`
- tyrkysový text
- u tagů jemné pozadí `rgba(0,164,166,0.12)`
- radius 2 px

Mají působit jako metadata, ne jako výrazné marketingové pill chips.


### H1 struktura

Aktuální vzor:

```text
Your AI works
in demo.
Does it hold
in prod?
```

První část je `#e2e8f5`, druhá část je `#00A4A6`. Tento kontrast je důležitý: základní konstatování proti produkční otázce.

### Metriky

Metriky mají být:

- velké, Syne, weight 800
- tyrkysové
- doplněné malým JetBrains Mono popisem
- oddělené horním borderem

Používejte konkrétní čísla, ne obecné claims:

- `73%`
- `< 4h`
- `100%`
- `3x`

Metriky musí být obhajitelné. Pokud nejsou doložené, nepoužívejte je jako brand prvek.

## 9. Obsahové stránky a prose

Markdown/prose obsah má samostatný styl:

- H1-H4 v Syne
- body text v `#7b8faa`
- odkazy v tyrkysové
- inline code na `Surface 1` s `#00c8ca`
- code bloky na `Surface 1`, `1px` border a `3px` levý tyrkysový border
- tabulky s monospace hlavičkami a tyrkysovou spodní linkou
- unordered list používá pomlčku `—` jako tyrkysový marker
- blockquote má levý tyrkysový border

Prose má být technická, strukturovaná a čitelná. Kódové ukázky jsou legitimní součást značky, protože podporují inženýrskou důvěryhodnost.

## 10. Ikonografie a grafické prvky

Ikony na webu jsou minimální, line-based a funkční:

- šipky v odkazech
- checkmark v outcome badge
- hamburger/close pro mobilní navigaci

Používejte:

- jednoduché SVG linie
- stroke okolo `1.5-2px`
- `currentColor`, kde je to možné
- tyrkysovou pro aktivní/link směr
- zelenou pouze pro výsledek nebo success stav

Nepoužívejte ilustrační icon packy, 3D ikony ani emoji jako hlavní vizuální jazyk.

### Dělicí linky

Brand pracuje s linkami:

- `1px` okraje karet
- `1px` border mezi sekcemi
- `2px` tyrkysová/gradientní linka nad hero a page header
- krátké `2rem-2.5rem` tyrkysové linky u practice sekcí

Linky jsou důležitou součástí identity. Strukturovaně oddělují obsah bez vizuálního šumu.

## 11. Motion a interakce

Motion je subtilní:

- page entrance `fadeUp`
- duration `0.5s`
- posun z `translateY(14px)` do `0`
- opacity z `0` do `1`
- stagger delay `0.1s`, `0.2s`, `0.3s`, `0.45s`

Hover efekty:

- link underline do 100 %
- karta `translateY(-2px)`
- CTA hover změna na `#00c8ca`
- CTA active scale `0.98`

Motion nesmí působit hravě nebo dekorativně. Jeho role je signalizovat stav, ne bavit.

## 12. Obrazový styl

Aktuální web nepoužívá fotografie ani ilustrace. Identita stojí na typografii, barvě, logu, linkách a struktuře.

Pokud bude potřeba přidat obrazový doprovod, měl by být:

- technický a realistický
- spojený s produkční infrastrukturou, evaly, monitoringem nebo inženýrskou prací
- tmavý nebo snadno integrovatelný do tmavé palety
- bez generických AI robotů, humanoidů, abstraktních mozků a neonových datových tunelů

Doporučený směr:

- detail observability dashboardu
- pipeline schémata
- architektonické grafy
- technické diagramy datového toku
- makro detail infrastruktury bez stock-photo teatrálnosti

Nepoužívejte gradientní orby, bokeh, generické „AI brain“ ilustrace ani dekorativní matrix efekty.

## 13. Tón vizuální komunikace

Vizuální styl má podporovat obsahový tón:

- konkrétní produkční problémy
- technické termíny bez zbytečného vysvětlování
- jasné metriky
- krátké confident headlines
- žádné přehnané prodejní sliby
- „no pitch, no hard sell“ přístup

Vhodná slova a fráze:

- production reliability
- evaluation gates
- behavioral regressions
- prompt injection defense
- latency profiling
- cost modeling
- rollback triggers
- production baselines
- built to hold

Nevhodná slova a fráze:

- magical AI transformation
- unlock your potential
- supercharge everything
- next-gen AI revolution
- beautiful AI experiences
- effortless innovation

## 14. Sociální a externí použití

### Social avatar

Používejte samostatný symbol v čtvercovém formátu. Doporučený export:

- 512 x 512 px pro univerzální avatar
- 192 x 192 px pro PWA/social fallback

Do avataru nevkládejte text DeepDual, pokud platforma zobrazuje ikonu menší než 96 px.

### Open Graph

Aktuální web používá `android-chrome-512x512.png` jako social image fallback. Pro lepší sdílení lze v budoucnu vytvořit OG šablonu:

- pozadí `#101820` s jemným dot patternem
- symbol vlevo nahoře nebo vpravo dole
- headline v Syne
- krátký label v JetBrains Mono
- tyrkysový akcentní pruh
- maximálně jedna metrika nebo jeden statement

### Prezentace

Pro prezentace používejte:

- tmavé pozadí `#101820`
- nadpisy v Syne
- body text v Outfit
- metadata/kódy v JetBrains Mono
- tyrkysový akcent pouze pro hlavní signály
- střídmé linky a mřížkové rozložení

Titulní slide může použít symbol 96 x 96 px, velký H1 a krátký monospace label.

## 15. Přístupnost

### Kontrast

- Nadpisy `#e2e8f5` na `#101820` nebo `#141f2a` jsou vhodné pro primární obsah.
- Body text `#7b8faa` na tmavém pozadí je sekundární, ale má zůstat čitelný.
- `#3d5070` používejte pouze pro metadata a low-emphasis text, ne pro kritické instrukce.
- Tyrkysová `#00A4A6` je vhodná pro akcenty, ale dlouhý text v tyrkysové nepoužívejte.

### Focus stavy

Interaktivní prvky musí mít viditelný focus:

- input focus: tyrkysový okraj + jemný tyrkysový ring
- link hover/focus: změna barvy nebo underline
- tlačítka: zachovat kontrast textu vůči pozadí

### Mobilní použití

Mobilní navigace přechází na hamburger. Zachovejte:

- symbol + DeepDual text vlevo
- hamburger jako hranaté tlačítko s borderem
- menu na `Surface 0`
- vertikální gap 1rem
- CTA jako samostatné centrované tlačítko

Hero na mobilu musí stále ukazovat hierarchii: label, H1, paragraph, CTA a metriky. Nepřebarvujte hero na světlou variantu.

## 16. Praktický systém pro nové materiály

### Nová webová sekce

Checklist:

- kontejner `max-width: 72rem`, padding `0 1.5rem`
- nadpis v Syne
- body text v Outfit
- label v JetBrains Mono, uppercase, tyrkysový
- pozadí buď `#101820`, nebo `#141f2a`
- oddělení přes `1px` border, ne přes velké stíny
- tyrkysový akcent jen na jeden dominantní signál v bloku
- radius 2-4 px
- žádný glassmorphism, orby, velké gradienty ani kulatá CTA

### Nová karta

Struktura:

1. Monospace kód nebo label v tyrkysové
2. Krátká tyrkysová linka
3. Nadpis v Syne
4. Popis v Outfit, `#7b8faa` nebo `#3d5070`
5. Volitelný link se šipkou v tyrkysové

### Nový technický článek

Použijte:

- přesný titulek
- krátký excerpt
- tagy v lowercase technických termínech
- tabulky pro metriky
- kódové bloky, pokud pomáhají vysvětlit princip
- závěr s jasnými takeaways

## 17. Kontaktní informace o DeepDual.ai
- Kontaktní osoba: Ing. Stanislav Bajer
- Email: stanislav@deepdual.ai
- Webové stránky: deepdual.ai

## 18. Do / Don't

### Do

- Používejte tmavý ink systém a tyrkysový akcent.
- Zachovejte Syne / Outfit / JetBrains Mono jako jedinou typografickou trojici.
- Pracujte s metrikami, čísly, practice kódy a technickými labely.
- Používejte malé radiusy a přesné okraje.
- Nechte obsah dýchat přes velké sekční odsazení.
- Pište vizuálně i obsahově ve stylu „evidence before confidence“.
- Používejte logo jako orientační bod, ne jako dekoraci.

### Don't

- Nepoužívejte amber/žlutou jako hlavní brand barvu.
- Nepoužívejte generické AI ilustrace, roboty nebo neonové mozky.
- Nepoužívejte velké zaoblené SaaS karty.
- Nepoužívejte světlé pozadí jako hlavní brand plochu.
- Nepřehlcujte layout ikonami.
- Nepoužívejte dlouhé nadpisy s marketingovými superlativy.
- Nepoužívejte tyrkysovou na všechno; musí zůstat signální.
