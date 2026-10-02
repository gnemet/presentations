# Kéréstől a termékig — a KMTR tudástár esete — speaker notes

> Generated from request-to-product-kmtr.deck.md by DOC-deck_build — do not edit.

## 1. Kéréstől a termékig (#s1)

⏱ 1:00 — Az ígéret: fél óra múlva látni fogod, hogyan lesz egy e-mailből működő termék úgy, hogy a
munka nagy részét egy gép végzi, de minden döntés és minden kapu emberi. A KMTR-eset azért jó példa,
mert kicsi, valódi, és minden lépése megtörtént.

## 2. A kérés (#s2)

⏱ 2:30 — Mondd ki, hogy a kérés tökéletes: van benne mi, miért, és van benne kérdés. Az első dolog,
amit egy platformgazda ilyenkor NEM tesz: ígér. Az első dolog, amit tesz: mér.

## 3. Mi az a tudástár? (#s3)

⏱ 4:00 — Egy mondat minden dobozra. A lényeg a jogosultság-export webhook: nem mi találjuk ki, ki
mit láthat — az admin rendszere exportálja, mi csak alkalmazzuk.

## 4. Első lépés: mérés, nem ígéret (#s4)

⏱ 6:00 — Ez a dia a módszer szíve: a mérés olcsó, az ígéret drága. A táblázat negyedik sorát emeld ki:
a kérés ürügyén derült ki egy régi, néma hiba. Ebből lett a nap második munkaága (riasztás).

## 5. A jegy: ki · mit · miért · ki fogadja el (#s5)

⏱ 8:00 — A jegy nem bürokrácia: az egyetlen hely, ahol a hét felelős egyszerre látja, mi vár rá.
Figyeld meg: az utolsó sor a kérőé. Az elfogadás nem a platformé.

## 6. Döntés: együtt vagy külön? (#s6)

⏱ 11:00 — Itt lassíts. Ez a nap egyetlen valódi tervezési döntése, és nem a platform hozta meg egyedül:
a kérők tették fel a jó kérdést. Mondd ki: a döntés után az egész napi specifikációt átírtuk — ez nem
kudarc, ez a módszer. A spec azért van, hogy olcsó legyen átírni.

## 7. Spec előbb, mint kód (#s7)

⏱ 13:00 — (ha van idő) Egy mondat fájlonként. A lényeg a sorrend: a mappa commitja megelőzi az első
kódsort. Ez a szabály, nem szokás — a gép sem írhat kódot spec nélkül.

## 8. EARS — három példa a KMTR-követelményekből (#s8)

⏱ 14:30 — (ha van idő) Olvass fel egyet, és mutasd meg, hogyan lesz belőle teszt: „hibát dob és
megáll" → egy teszt, ami beír egy KMTR-oldalt a sor nélkül, és elvárja a hibát.

## 9. Tesztek előbb — pirosan, aztán zölden (#s9)

⏱ 16:30 — (ha van idő) A második kártya a nap legjobb példája: nem a tervezés, hanem egy piros teszt
mutatta meg, hogy a „két tenant" döntés eltör egy meglévő függvényt. A negyedik a második nap tanulsága:
a zöld próba sem bizonyíték, ha nem az éles alakot méri — a hibát az első éles alkalmazás találta meg,
és a javítás először egy új piros teszt volt, aztán a migráció.

## 10. A mechanizmus: adat, nem kód (#s10)

⏱ 19:00 — Zöld = adat, lila = motor. A közönség számára a tanulság: a második projekt nem fejlesztés,
hanem sorok és másolatok. Ezért mertük megígérni, hogy a harmadik projekt már csak egy ellenőrző lista.

## 11. A webhook és a riasztás (#s11)

⏱ 21:30 — A két riasztási szint a lényeg: az azonnali a hibára, a reggeli a hiányra. Külön mondd ki:
a néma hiba nem a webhook hibája volt, hanem az, hogy nem futott semmi, ami hibázhatott volna.

## 12. Gépi ellenőrzés és emberi kapu (#s12)

⏱ 23:30 — A közönség fele kérő, fele kolléga: mindkettő megtalálja itt a saját kapuját. A validáció
soha nem a platformé — ezért a kérőé az utolsó szó.

## 13. A kapuk sorban (#s13)

⏱ 25:00 — Hat kapu, hat ember vagy csapat. Mondd ki: öt kapu mögöttünk van — összefésülés, migráció,
admin-jogok (a SharePoint-olvasással együtt), telepítés és az első éles futás a 3. nap reggelére lezajlott.
Egy kapu maradt: a kérőé.

## 14. Ki mit ad hozzá (#s14)

⏱ 26:00 — Egy mondat: a platform nem talál ki jogosultságot. Az admin exportálja, a platform alkalmazza.

## 15. Aki jogosult, az látja — hogyan? (#s15)

⏱ 27:00 — Három réteg, három kérdés: melyik fiók, melyik útvonal, melyik ember.

## 16. Wiki csak KMTR-forrásból — és a tenant-választó (#s16)

⏱ 28:00 — A választó ötlete a kérőktől jött, egy másik termékünk mintájára. Két tengely: mit lát (tenant)
és hogyan viselkedik (kalap).

## 17. Ha valami elromlik (#s17)

⏱ 29:00 — (ha van idő) A négy kártya egy mondat: a rendszer inkább áll meg, mint hogy rosszat mondjon.

## 18. A második nap többlete (#s17b)

⏱ 29:00 — Egy mondat kártyánként. A közönségnek az első kártya szól (ezt látják); a kollégáknak a többi:
minden kártya egy olyan hiba vagy hiány, amit a kérés tett láthatóvá — és mind tesztet kapott.

## 19. A harmadik nap: az első éjszaka és ami kiderült (#s17c)

⏱ 29:20 — A harmadik nap kártyái. A közönségnek az első kettő (a korpusz és a harminc szócikk); a kollégáknak
a többi: minden kártya egy éjszaka által megmutatott hiba vagy hiány — és mind tesztet kapott, mielőtt javítottuk.

## 20. Hol tartunk, mi következik (#s18)

⏱ 29:45 — Rövid. A bal oszlop három napot mond: a mechanizmus egy este, a kapuk egy délelőtt, a többlet egy délután,
a termék egy éjszaka. A jobb oszlop a lényeg: minden kapu zárva, egy maradt — a kérő szava, és az első visszajelzések.

## 21. Mit fogadunk el? (#s19)

⏱ 30:00 — Ez a négy mondat a kérő aláírásának tárgya. Kérdések.

## 22. Köszönöm (#s20)

⏱ 30:00 — Zárás. Ha kérdés jön a „mikor" felől: a jobb oszlop a 18. dián.
