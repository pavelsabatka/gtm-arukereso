# Konverziós mérés az Arukereso.hu számára

[HU](https://github.com/pavelsabatka/gtm-arukereso/blob/master/README.md) | [EN](https://github.com/pavelsabatka/gtm-arukereso/blob/master/README-EN.md) | [CZ](https://github.com/pavelsabatka/gtm-arukereso/blob/master/README.md) | [Changelog](https://github.com/pavelsabatka/gtm-arukereso/blob/master/CHANGELOG.md)

Google Tag Manager sablon az Arukereso.hu konverziókövetéshez.
Konverziók mérése [Arukereso.hu](https://www.arukereso.hu/static/conversion-measurement.html)


# Konfiguráció
A megfelelő méréshez 2 kódot kell implementálni:
1. kód a termék részletező oldalán
2. konverziós kód a köszönöm oldalra

Mindkét kódban helyesen kell beállítani az országot, ahol a Arukereso.hu fiókod van.

## Termék részletei
A beállításhoz csak állítsa be az országot és a kód típusát "Tétel részlete".

![GTM sablon beállítása a Arukereso.hu termék részlet kódhoz](https://github.com/pavelsabatka/gtm-arukereso/blob/main/img/arukereso-product-detail-page.png)

## Konverziós kód
A sablonban be kell állítanod, hogy
* **Key** - a tároló mérésének kulcsa. Ezt a Arukereso.hu adminisztrációban kaphatja meg.
* **Order** - objektum [Tranzakciók GA4 formátumban](https://developers.google.com/analytics/devguides/collection/ga4/set-up-ecommerce) (vagy Universal Analytics - `ecommerce.purchase`).
* **Order Id** - a megrendelés egyedi azonosítója.
* **Pénznem** - háromjegyű pénznemkód az ISO 4217 szabvány szerint. Pl. CZK, EUR, USD
* ** **Termékek** - termékmező (objektum). Minden terméknek rendelkeznie kell az `id` (vagy `item_id`), `name` (vagy `item_name`), `price` és `quantity` attribútumokkal.
* **Kiegészítő tételek** (opcionális) - a mezőben további tételek adhatók meg, amelyek befolyásolják a megrendelés teljes árát. Például szállítás, fizetés, utalványok vagy kedvezmények.

Ha egy tranzakciós objektum kerül beillesztésre, akkor a lehető legtöbb adat töltődik be belőle - rendelés azonosító, teljes ár, termékek, kiegészítő tételek.

### Példák
1. Letöltés változókból
![GTM sablonok konfigurálása Arukereso.hu konverziós kódhoz](https://github.com/pavelsabatka/gtm-arukereso/blob/main/img/arukereso-purchase-rows.png)

2. A Tranzakció objektum használata
Az adatok [GA4 vásárlási formátumban](https://developers.google.com/analytics/devguides/collection/ga4/set-up-ecommerce)
![GTM sablon konfigurálása Arukereso.hu konverziós kódhoz - objektum](https://github.com/pavelsabatka/gtm-arukereso/blob/main/img/arukereso-purchase-object.png)

3. További költségek megadása
![GTM sablon konfiguráció a Arukereso.hu konverziós kódhoz - további költségek](https://github.com/pavelsabatka/gtm-arukereso/blob/main/img/arukereso-purchase-additiona-items.png)


### Hibakeresés
A GTM hibakeresési módban keresse meg azt az eseményt, ahol a Arukereso mérési tag kiváltásra kerül. Ezután az összes átadott paramétert megtekintheti a konzolon.
Amikor az adatok elküldésre kerültek a Arukereso felé, a végén meg kell adni a `siker` állapotot.
![GTM sablon hibakeresés a Arukereso.hu számára](https://github.com/pavelsabatka/gtm-arukereso/blob/main/img/arukereso-debug.png)


## Hozzájárulás
A sablon nem kezeli a hozzájárulás állapotát.
A Arukereso azt állítja [a dokumentációban](https://www.arukereso.hu/static/conversion-measurement.html), hogy a kódokat hozzájárulás nélkül kell futtatni - a Arukereso oldalán megadott hozzájárulást követi. Ezzel a megoldással kapcsolatban azonban konzultáljon a jogászokkal, nem vállalok felelősséget a helyességéért.

# Other

## Kizáró nyilatkozatok
A sablont a szabadidőmben fejlesztem, hogy időt és munkát takarítsak meg neked. Nem vállalok felelősséget a használatáért vagy a használatából eredő károkért.
A sablon egy harmadik féltől (Arukereso.hu) tölt le szkripteket, a Arukereso.hu által kiadott dokumentációnak megfelelően. Nem vagyok felelős a GDPR szempontjából felmerülő hiányosságokért.

## Konzultáció
Ha problémái vannak a sablon telepítésével kapcsolatban, akkor [lépjen kapcsolatba velem](https://www.sabatka.net/kontakt) egy fizetős konzultációért.