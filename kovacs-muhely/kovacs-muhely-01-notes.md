# kovacs-muhely — speaker notes

> Generated from kovacs-muhely-01.deck.md by DOC-deck_build — do not edit.

## 1. kovacs-muhely

_(no notes)_

## 2. Két oldal, egy adatbázis — ki mit tesz? (#s2)

⏱ 1:30 — A legfontosabb mondat: a kovacs-muhely tölt, az iier-tudastar olvas, és a kettő között
egyetlen adatbázis van tenantonként. A végfelhasználó semmit nem telepít a saját gépére a
Claude-on kívül: a tool-ok a távoli pf-mcpd tenant-útvonalain élnek.

## 3. Mi van a dobozban? (#s3)

⏱ 3:00 — Három dolog számít: a bundle-olt pf (a host nem fordít), a pipeline-ok mint dokumentumok,
és hogy a repo teljesen Python-mentes — minden lépés pf-adapter.

## 4. Tenantok — kik élnek ma? (#s4)

⏱ 4:30 — A kmtr a iier2 másolata: ugyanaz a séma, ugyanazok a pipeline-ok, más scope. Ez a
multi-tenancy bizonyítéka — a második tenant nem kért egyetlen sor új kódot sem.

## 5. Egy tenant pipeline-jai — iier2 / kmtr (#s5)

⏱ 6:30 — Balról jobbra a forrásoktól a származtatott rétegig: előbb a jogosultság (LDAP), aztán a
három forrás, aztán ami ezekből épül (klaszter, élek), végül a kereső és a wiki.

## 6. Hozzáférés — a jog a sorban él, nem az alkalmazásban (#s6)

⏱ 8:30 — A jog nem az alkalmazás kódjában van, hanem minden sorban. Ugyanaz a lekérdezés két
felhasználónak két eredményt ad — és ezt az adatbázis dönti el, nem a kliens.

## 7. SharePoint v2 — registry-vezérelt crawl, táblák mint adat (#s7)

⏱ 10:30 — A táblázat nem szövegként vész el: sorai adatként tárolódnak, és a keresőből pontos
értékre is rá lehet kérdezni. A crawl külön idősávja mérési tanulság, nem preferencia.

## 8. Ütemezés — a pf-worker kezeli (#s8)

⏱ 12:00 — A sorrend logikus: előbb a jog (ACL), aztán a SharePoint külön, aztán a fő embed, végül a
reggeli összesítő és a watchdog — ami nem futott, az reggel már látszik.

## 9. Embedding és keresés (#s9)

⏱ 13:30 — Egy modell, egy forrás a modell nevéhez: így nem fordulhat elő, hogy két pipeline más
modellel embedel ugyanabba a gyűjteménybe.

## 10. Mindennapi munka (#s10)

⏱ 15:00 — A napi munka nagy része nem futtatás, hanem ellenőrzés: a reggeli összesítő és a
watchdog megmondja, mit kell kézzel újrafuttatni.

## 11. Végfelhasználói kérés — egy forrástól a találatig (#s11)

⏱ 16:30 — Senki nem szerkeszt pipeline-t egy új forrásért. A forráslista adat, a jog az admin
exportjából jön, a következő éjszaka végzi a munkát.

## 12. Új tenant — adat és másolat, nem kód (#s12)

⏱ 18:00 — Hat lépés, egyik sem kód: egy migráció, egy mappamásolat, kulcsok, menetrend, útvonal,
manifest. Ez a „generikus motor, logika a specben” elv egy tenant szintjén.

## 13. Számok — a kmtr az első héten (#s13)

⏱ 19:00 — Valódi, dátummal rögzített számok a bevezetés naplójából. A 30 wiki-cikk AI-vázlat:
ember hagyja jóvá, mielőtt véglegesnek számít.

## 14. Telepítés és migráció (#s14)

⏱ 20:30 — A telepítés sem kézi lépéssor: a manifest mondja meg, mi megy ki, a pipeline végzi, és
előtte-utána egy-egy ellenőrzés fut.

## 15. Mit ad a builder-oldali toolkit? (#s15)

⏱ 22:00 — Négy mondat, amit érdemes hazavinni: dokumentum a lépés, adat a jog, másolat a tenant,
és a csend nem siker — a watchdog reggel szól.
