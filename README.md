# Frylabs Userscript (frylabs-v1.js)

Egyszerű segédscript Moodle/Elearning/KMOOC környezethez.

- Bal alsó vezérlőablak (menü) az állapotokhoz és bejelentkezéshez
- Billentyűparancsok (testreszabhatók):
  - Alt+T: bal alsó ablak ki/be
  - Alt+Q: felső szövegdoboz ki/be (utolsó üzenet visszaállítása bekapcsoláskor)
- Felső üzenetdoboz „csak szöveg” módban (keret- és háttérmentes), automatikus kontraszt (mix-blend-mode: difference)
- Az alsó ablak X gombja a teljes böngésző session idejére zárva tartja az ablakot (frissítésnél/új lapon sem nyílik meg magától), de Alt+T-vel visszahozható

## Telepítés

1. Telepíts egy userscript-kezelőt (ajánlott: Tampermonkey): https://www.tampermonkey.net/
2. Hozzáadás: Tampermonkey → Create a new script → töröld az alap tartalmat → illeszd be a `frylabs-v1.js` teljes tartalmát → Mentsd el.
   - Alternatívaként használhatod a repo nyers fájlját (Raw) forrásként.

A script `@match` bejegyzései több magyar/ER felületet lefednek (Obuda/Unideb/Semmelweis/BME stb.).

## Használat

- Alt+T: bal alsó ablak megjelenítése/elrejtése
- Alt+Q: felső üzenetdoboz megjelenítése/elrejtése
  - Kikapcsolva semmilyen felső üzenet nem jelenik meg.
  - Visszakapcsoláskor az utolsó üzenet automatikusan visszatér.
- Billentyűk testreszabása: bal alsó ablak → „Billentyűparancsok”
  - „Módosítás”: nyomd meg az új kombinációt (pl. Ctrl+Alt+X)
  - „Alapértelmezett”: visszaállítja az Alt+T / Alt+Q beállítást

## Funkciók és finomhangolás

- Felső üzenetdoboz
  - Keret, háttér nélkül jelenik meg (csak szöveg)
  - Automatikus kontraszt: `mix-blend-mode: difference`, így világos/sötét hátteren is jól látszik
- Bal alsó ablak
  - Kontrasztosabb megjelenítés (sötét háttér, világos szöveg, sárga kiemelések)
  - X gomb: session alatt végleges bezárás (nem nyílik újra magától)

## Tartósság

- Beállítások (GM_setValue):
  - `frylabs.shortcuts.v1`: a gyorsbillentyűk (toggleMenu, toggleTop)
  - `frylabs.topbox.enabled`: felső szövegdoboz globálisan engedélyezve
  - `frylabs.menu.enabled`: alsó ablak globálisan engedélyezve
- Session (sessionStorage):
  - `scriptMenuVisible`: ha `false`, az alsó ablak a session végéig nem jelenik meg automatikusan

## Fejlesztés

- A projekt egyetlen userscript fájlból áll: `frylabs-v1.js`
- Nem igényel buildet; szerkesztés után másold be Tampermonkey-ba és mentsd el.
- Git: a fájl neve a repóban `frylabs-v1.js` (a korábbi `frylabs-og.js` átnevezve lett).

## Hibakeresés

- Ha nem működik a gyorsbillentyű: győződj meg róla, hogy nem input/textarea fókuszban vagy.
- Ha az alsó ablak nem jelenik meg: nézd meg, nem zártad-e be sessionre (Alt+T-vel visszahozható).
- Ha a felső szöveg nem látszik jól speciális hátteren: jelezd; opcionálisan adható enyhe `text-shadow` is a jobb olvashatóság érdekében.

## Licenc

GNU GPL v3 vagy újabb.
