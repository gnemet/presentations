# Spec-driven Development (SdD) — módszertan, gyakorlati példával (v5) — speaker notes

> Generated from presentation-sdd.deck.md by DOC-deck_build — do not edit.

## 1. Spec-driven Development (SdD) (#s1)

⏱ 0:45 — Mondd ki az ígéretet, ne a tartalomjegyzéket: *„Fél óra múlva tudni fogod, hogyan írunk kódot
úgy, hogy a nagy részét egy gép írja, mégis mi felelünk érte."*

Két mondat a keretezéshez: ez **nem AI-demó**. Ez egy **munkamódszer**, aminek három új
alkatrésze van — a **specifikáció**, a **teszt** és a **git**. Aki BA, annak az első; aki
fejlesztő, annak a második; aki vezető, annak a harmadik lesz a legfontosabb.

**Keret az egész előadáshoz.** A `⏱` érték azt mutatja, hány perc telt el, amikor elhagyod a diát —
ha csúszol, a *(ha van idő)* blokkokat hagyd ki először. A `#talk` cut (a fejléc 🎤 gombja) a
30 perces változat; a teljes, ~45 perces deck referenciaanyag. **Közönség:** tapasztalt
Java-fejlesztők · vezetők · üzleti elemzők. A git ebben a cégben **új** (az SVN most megy ki) —
ezt sose feltételezd ismertnek, de ne is kérj bocsánatot érte.

## 2. Spec-driven Development — ahogy a Vishy család házat épít Verőcén (#s2)

⏱ 2:00 — A hasonlat végigkíséri az egészet, ezért érdemes rá időt szánni. A kulcs: **senki nem kezd
falat húzni tervrajz nélkül**, és a műszaki ellenőr nem azért van, mert nem bízunk a kőművesben.

**A táblázat két utolsó sora a lényeg** — ezt mondd ki, mert erre hivatkozunk még háromszor:
a **műszaki ellenőr** azt nézi, *a terv szerint épült-e meg* (verifikáció); a **család** azt, hogy
*azt a házat kapta-e, amire szüksége volt* (validáció). A brigád saját ellenőrzése (vízszintben
a fal) még nem kapu — az a gépi teszt. És vigyázz: az építész a tervet az építkezés **előtt**
írja alá; az terv-jóváhagyás, nem a kész ház ellenőrzése.

Kérdezz vissza a terembe: *„Ki írt már olyan kódot, amit fél év múlva ő maga sem értett?"* —
általában felmegy a kéz. Ez a dia arról szól, hogy a tervrajz **nem a bürokrácia**, hanem az,
ami miatt hat hónap múlva is meg tudod mondani, hogy **miért** úgy van.

## 3. A probléma — 20 év Linux-infrastruktúra (#s3)

⏱ 3:15 — 20 év Linux-infrastruktúra, dokumentálatlanul. Ez a valódi feladat, amiből az egész példa jön.
Ne menj bele a technikai részletbe — a lényeg, hogy ez **nem laborpélda**: éles rendszer,
éles kockázattal, és van egy határidő.

## 4. Mi a Spec-driven Development? — a lánc TdD-vel és validációval zárva (#s4)

⏱ 5:30 — A nyolc lépéses lánc. **Ne olvasd fel** — mutass rá háromra:

- **02 Specifikáció** — itt dől el minden (ide jövünk vissza a 11. diánál).
- **05–06 · TdD** — *ez az új elem a láncban*. Mondd ki a nevét: **teszt-vezérelt fejlesztés**,
  és a lényege az „05 a 06 **előtt**" sorrend. Jelezd, hogy külön dia lesz róla (13.), itt csak
  annyit rögzíts, hogy a teszt **nem a végén ellenőriz** — hanem elöl **definiál**.
- **07–08 Verifikáció és Validáció** — **két különböző ember, két különböző kérdés**:
  *„jól építettük?"* vs. *„a jót építettük?"* Ez a legfontosabb mondat az egész diasoron
  a vezetőknek.

A jobb oldali „vibe coding vs. spec-driven" kártyapár a kontraszt — a bal oldali oszlopot
mindenki ismeri, ezért működik.

*(ha van idő)* Nyisd meg a `▸ Egy spec a lemezen` drill-downt, és mutasd meg, hogy ez egy
**valódi mappa a repóban**, nem ábra. Elég 20 másodperc.

**Ezt mondd ki itt, szóban — kötelező.** Az axióma-dia (`#s6`), ami ezt leírja, a
30 perces változatban **ki van hagyva**, tehát a teremben csak tőled hangzik el:

> *„Amit itt SdD-nek hívok, nem szabvány és nem iparági előírás. Nálunk ez egy
> **működési modell**: spec-first, teszt-first, kis diff és emberi kapuk. A módszer
> általános — a mi tizenegy axiómánk és a Claude Code már a **mi megvalósításunk**,
> nem a definíció. Az AI a végrehajtást gyorsítja; a döntési felelősséget nem veszi át."*

Enélkül a terem azt viheti haza, hogy az EARS, a Markdown, a git és a Claude Code
**kötelező előírás** — és az első kérdés az lesz, hogy „ki írta elő?".

## 5. LLM + agent — és hogyan olvassa az AI a repót? (#s5)

⏱ 7:30 — A négy alapfogalom (LLM · token · context window · prompt) gyors, de **két dolgot nyomatékosíts**.

**(1) A modell súlyai nem változnak** attól, hogy beszélgetsz vele; és amit az aktuális kontextus
vagy az eszközei nem hoztak be, arra abban a lépésben nem tud támaszkodni. Friss tényhez az
**agent** jut hozzá — fájlt olvas, DB-t kérdez. Innen következik minden más a diasoron.

**(2) Az aranyhal.** A context window kártyáján van a kép, használd ki — ez az a hasonlat, amit
a terem estig megjegyez:

> *(Az aranyhal a **session munkamemóriájának** hasonlata, nem a platform memóriájáé.)*
> Az aranyhal állítólag **tíz másodpercig** emlékszik. A modell pontosan ilyen: amíg együtt
> beszélgettek, mindent tud — a session végén viszont **kiürül a tál**. Nem haragszik,
> nem lusta: *nem emlékszik.*

Egy pontosítást tegyél hozzá rögtön, mert a 16. dián látni fogják a `Memory` sort, és
különben ellentmondásnak tűnik: **nem a tudás vész el, hanem a munkamemória.** A modell
felejt — **a platform nem**. A következő session a repóból, a szabályfájlokból és a
memóriából *újraépíti*, amire szüksége van. Ezért nem baj, hogy felejt: ezért van minden
fájlban.

Két dolgot vezess le belőle, mert a diasor további fele erre épül:

- **A tál véges.** A context window nem végtelen: néhány száz oldalnyi szöveg fér bele, a
  rendszerünk ennek a sokszorosa. Tehát **minden session választ**, mit olvas be — és ez a
  választás mérnöki döntés, nem véletlen. (Erről szól a szabályhierarchia a dia alján.)
- **Amit nem hozott be, arra abban a lépésben nem tud támaszkodni — és amit nem lát, arról
  találgathat.** Ha egy szabály a fejedben van vagy a Confluence-en, a gép nem tud róla, amíg
  valami be nem hozza a kontextusba. *(Az agent tud érte nyúlni — fájlt olvas, DB-t kérdez —,
  de magától nem tudja, hogy létezik.)*
  **Ezt pontosan mondd** — a dia is ezt írja (*„Magabiztosan tud tévedni"*), ne mondj mellé
  mást: nem az van, hogy „nem téved, csak nem látja". A hiányzó kontextus **és** a téves
  következtetés két külön hibamód, és a válasz magabiztossága egyikről sem árul el semmit:
  > *„Amit nem lát, arról találgathat. Ezért nem azt ellenőrizzük, mennyire magabiztos a
  > válasz — beolvassuk a forrást, futtatjuk a tesztet, és elolvassuk a diffet."*
  Ez a mondat a diasor tézise, nem mellékszál: ezért van teszt, review és futó rendszer.

*(Ha valaki bekiabálja, hogy ez városi legenda — igaza van: az aranyhal hónapokig emlékszik.
Nyugtázd, és fordítsd meg: „a halnak jobb a memóriája — a modell session-kontextusa tényleg
kiürül; a platform viszont újraépíti." A poén így erősebb lesz, nem gyengébb.)*

Az agent-ciklus (kérés → terv → eszközhívás → megfigyelés → ismétlés) azért fontos, hogy a
terem értse: ez nem chat. **Fájlt szerkeszt, parancsot futtat, tesztet indít.**

**Az agent négy arca** (a ciklus alatti kártyasor) — egyetlen kérdés választja szét őket:
*ki irányítja a lépéseket?* **Agent:** egy session, egy ciklus. **Agentic workflow:** a
sorrendet az ember rögzíti, az AI a lépéseken belül dolgozik — ez az SdD lánc maga.
**Multi-agent:** több agent szétosztott szerepekkel, párhuzamosan (nálunk a négy reviewer).
**Autonóm agent:** az AI dönti el a lépéseket is. Mondd ki a határt — és **pontosan** mondd,
mert a 18. dián visszajön: nálunk az olvasás **és a megfigyelő írás** (napló, snapshot,
mérés) autonóm lehet a policy keretei között, szűk jogosultsággal, mechanikus kapuk mögött
(RLS, RBAC, hook). Ami a **rendszer állapotát megváltoztatja**, az viszont sosem autonóm:
az emberi kapun (MR) megy át. **Minden írás kapuzott** — a kérdés csak az, hogy a kaput
*ember* nyitja-e vagy *szabály* (A6; pontosan ezt írja az axióma-dia A6 kártyája is).
A buzzword-kérdésre ez a válasz: *„autonóm, de kapuvezérelt"*.

*(Ne mondd, hogy „minden írás emberi kapun megy át" — nem igaz, és a 18. dián te magad
fogod pontosítani. A kapu ott van, ahol a rendszer megváltozik, nem ott, ahol csak
leírjuk, mit láttunk.)*

Zárómondat: *„az aranyhal-memóriájú agentnek a repo a memóriája"* — ez vezet át a következő diára.

## 6. Hol dolgozik az AI? — a development-platform munkaterület (#s5b)

⏱ 9:15 — Itt a Java-fejlesztők kapcsolódnak be. A fa-ábra bal oldalt ismerős: **workspace, egymás melletti
projektek**. A különbség egyetlen mondatban: **a szabályok is a munkaterületen laknak**, nem a
Confluence-en.

A vezetőknek szánt fél mondat: a titkok **vaultban** vannak, a feloldás **emberi kapu** — az
agent önmagának nem tud jogot adni. Ezt itt vesd el, a 18. dián (kapuk) fogod learatni.

A fában szándékosan **céges GitLab-projektek** állnak (`infra-forge`, `jiramntr`,
`admin-knowledge`, `iier-tudastar`) — ismerős nevek a teremnek, és mind a
`hu.admin.knowledge` / `hu.ulyssys.ai` csoportban él. Ha rákérdeznek: bármelyik további projekt
ugyanígy fér el mellettük, a szerkezet nem változik.

*(ha van idő)* A `▸ Amit a Java-világból ismersz` táblázat öt sora pontosan erre a közönségre
készült — ha látod, hogy kapaszkodót keresnek, nyisd ki; ez a leggyorsabb megnyugtatás.

## 7. Miért git? — mert a kis diff az emberi kapu (#s5c)

⏱ 11:30 — **Ne git-tanfolyamot tarts.** Két gondolatot adj át, és a másodikra szánd az idő nagyobb felét.

**(1) A git a kontrollpont, nem a mentés.**

> Vibe codingnál a git csak mentés. Spec-driven fejlesztésnél a git a **kontrollpont**.

A három kártya sorrendje szándékos: *olcsó branch* (mersz kísérletezni) → *a kis diff a review
egysége* → *a history a bizonyíték* (és a 17. dián látni fogják).

Az SVN felől érkezőknek a legfontosabb egyetlen új dolog: **a commit és a push kettéválik.**
Helyben commitolsz tízszer, mielőtt bárki látná. Ettől lesz a történet olvasható.

**(2) A kis diff — ez a dia igazi mondanivalója.**

A tapasztalt fejlesztőknek ez ismerősen hangzik majd („jó commit-kultúra"), ezért mondd ki, hogy
**mi változott**: amíg ember gépelt, a diff *magától* maradt kicsi, mert lassan nőtt. Egy gép
mellett nem nő lassan.

A piros doboz a dia csúcspontja, ezt olvasd fel lassan: **az AI-nak nincs fáradtságjelzése.**
Boldogan ír 2000 sort egy kérésre — és a 2000 soros diffet senki nem nézi át, csak jóváhagyja.
Ilyenkor a kapu **papíron megvan, a valóságban nincs**. Ez a legdrágább hiba, amit egy csapat
AI mellett elkövethet.

A kép, amit érdemes megjegyezniük: **néhány tucat sort elolvasnak, több százat nem.** Nem a
figyelem vész el a kettő között, hanem *a kapu maga*. *(Ha konkrét számpárt mondasz — 40 és 900 —,
tedd hozzá, hogy szemléltetés, nem mért küszöb: nincs mögötte belső mérésünk.)*

Zárd azzal, ami cselekvéssé teszi: **ha nő a diff, nem a review-t kell erősíteni, hanem a
feladatot kettévágni** — vagyis a méret korlátja a **specbe és a taskokba** kerül, nem a review-ra.

*(ha van idő)* Az `▸ A kis diff technikája` drill-down — az öt szabályból az elsőt és a
harmadikat emeld ki: *egy MR = egy önállóan átnézhető viselkedés* (rendszerint egy
EARS-kikötés — de a mérce az átnézhetőség, nem a darabszám), és *semmi alkalmi rendrakás*. Ha vezető van a
teremben, a jobb oldali oszlop második pontja neki szól: kis diff = **kicsi a visszavonás
egysége is**, éles hiba esetén egy döntést vonsz vissza, nem egy hetet.

*(ha van idő)* Az `▸ SVN → git` táblázat — az utolsó sorra menj rá: a **merge requestnek (MR)
nincs SVN-megfelelője**, és pont az az A9 verifikációs kapuja. Használd végig az **MR**
rövidítést: a céges GitLab ezt a szót írja ki, a „PR" a GitHub szóhasználata — ne keverd, mert
a teremben az MR az, amit holnap látni fognak.

## 8. A 11 axióma — a platform alaptörvénye (#s6)

_(no notes)_

## 9. Alaptörvény → fizika → projekt-szabály — és mindet ember írja (#s7)

_(no notes)_

## 10. Miért kontextus-alapú a fejlesztés? — erősítő vs. rövidítés (#s8)

⏱ 13:30 — **Első fele — a tézis.** Erősítő vs. rövidítés. Egy mondat: az AI **nem rövidíti le** a
gondolkodást, hanem **felerősíti** azt, amit beleteszel — jó specből gyorsan lesz jó kód, üres
specből gyorsan lesz sok rossz kód.

**Második fele — „és miért angolul?"** Ezt a kérdést **tedd fel te, mielőtt ők kérdeznék.** Egy
magyar cégben, magyar teremnek, angol nyelvű EARS-kikötéseket mutatni magyarázat nélkül sértő és
gyanús. Magyarázattal viszont az egyik legmeggyőzőbb dia.

A három ok, ebben a sorrendben — az elsőre szánd a legtöbbet, mert az számokkal megfogható:

- **Token.** Itt a *mechanizmust* mondd el, ne a végeredményt: egy **angol szó átlagosan
  ~5 karakter**, egy token nagyjából **4** — vagyis egy angol szó jellemzően egy-másfél token,
  és sokszor egészben szerepel a szótárban. A magyar **toldalékol**: egy szó több ragot hordoz,
  ritkábban van benne egészben, ezért több darabra esik szét. Innen jön, hogy ugyanaz a tartalom
  magyarul több token. Kösd vissza az aranyhalhoz (5. dia): ez nemcsak **drágább**, hanem
  **kiszorítja a kódot a véges ablakból**. *Ez nem nyelvi ízlés, hanem férőhely.*
  **Konkrét szorzót továbbra se mondj** — az modellenként más, és nincs mögötte saját mérésünk.
  A mechanizmus viszont ellenőrizhető, és ennyi elég is az érvhez.
- **Egy nyelv — egy szótár.** A szabály, a spec, a kód és a hibaüzenet ugyanazokat a szavakat
  használja. **Ne mondd, hogy a magyar RAG rosszabb** — a mi beágyazó modellünk (`arctic-embed2`)
  többnyelvű — a teljes változat RAG-diája külön ki is mondja, hogy *erős magyar szemantikus
  keresés*. A valódi
  érv nem a nyelv minősége, hanem a **fogalmi egyezés**: két nyelven ugyanaz a fogalom kétféle
  néven él, és a keresés is, a review is ezen a résen szivárog el. Egy fogalom — egy név (A1).
- **A kód úgyis angol.** Kulcsszó, hibaüzenet, könyvtár-dokumentáció. Magyar spec mellé
  fordítási réteg kerül — és a jelentés ott szivárog el.

**A zárás a legfontosabb, és ez a BA-knak szól** — mondd ki lassan, mert enélkül azt viszik haza,
hogy „mostantól angolul kell dolgozniuk", és az nem igaz:

> Az **infrastruktúra és az orchestráció** beszél angolul. Az **üzleti tartomány marad magyarul**:
> a szakterületi fogalmak, a felhasználói szövegek — és ez a diasor is. A kikötés **váza** angol,
> a szakszó benne **magyar**.

*(Ha jön a kérdés, hogy „nem lehetne mindent magyarul?" — de lehetne, csak drágább, rosszabbul
kereshető, és a kód felé úgyis fordítani kell. Ez mérési kérdés, nem identitás-kérdés.)*

## 11. Négy lépés — a szándéktól a bizonyított kódig (#s8b)

_(no notes)_

## 12. Hogyan fejlődött a terület — és hol áll az infra-forge (#s8c)

_(no notes)_

## 13. Az AI a munka középpontja — az ember a kontroll középpontja (#s9)

⏱ 14:45 — A diasor tézise. A vezetőknek: **nem a fejlesztőt váltjuk ki, hanem a szűk keresztmetszetet
mozdítjuk el** — a szűk keresztmetszet mostantól a **review és az átvétel**, azaz emberi
kapacitás. Ezt a mondatot érdemes szó szerint kimondani.

## 14. Miért dokumentum? Miért Markdown? — egy fájl, három arc (#s10)

⏱ 16:45 — **Ez a diasor leglátványosabb pillanata — élő demó, ne olvasd fel.** A képernyőn egyetlen
valódi fájl van: `pipelines/ops_dep_extract.md`. **Minden éjjel 04:00-kor magától** lefut:
a flotta pillanatképeiből kiszámolja a szolgáltatás-függőségeket, naplóz, átszinkronizálja a
függőségi gráfot — és **nincs mellette kód**.

Kattints a gombra **kétszer**, és mondd hozzá ezt a három mondatot:

1. **RAW** — „Ez egy szövegfájl. Ennyi. Ezt diffeli a git, és ezt olvassa az LLM."
2. **DOC** — „Ugyanez a fájl renderelve: ezt olvassa az ember, aki nem programozó."
3. **PIPELINE** — „És ugyanez a fájl **fut**: öt lépés, két ággal. Lent a valódi tegnap
   éjjeli napló: `steps_run=4` — a hibaág sikeres éjszakán kimarad, és ezt a fájl mondja meg."

Aztán állj meg egy pillanatra, és mondd ki a lényeget:

> **Nem három fájl. Egy.** Nincs külön dokumentáció, ami elavulhatna — mert nincs *külön*.

Innen a táblázat már csak összefoglal: a négy sor pontosan a három nézet (DOC · RAW · RAW ·
PIPELINE). Ne olvasd fel, mutass rá.

A BA-knak szóló félmondat: *ha tudsz Wordben követelményt írni, akkor tudsz Markdownban is —
a különbség annyi, hogy ezt a gép is el tudja olvasni, és a git meg tudja mondani, ki mit
változtatott rajta.*

*(ha van idő — de ez a dia legerősebb fél perce)* A RAW nézetben az első lépés fölött ott a
tanulság: egy elírt tenant-hivatkozás miatt **27 futás volt zöld, és egyetlen élt sem írt** —
két hétig senki nem vette észre. Mondd ki, hogy ez nem szégyen a diában, hanem maga a tézis:
*a hiba oka és a helyes alak bekerült a futtatható fájlba, ott, ahol a következő szerkesztő
— ember vagy AI — biztosan elolvassa.* A TdD-dián (13.) ugyanez az eset a bukó teszt oldaláról
tér vissza: egy „legalább 1 él" teszt az első éjszakán piros lett volna.

*(Ha a demó nem indul — pl. régi böngésző —, ne bűvészkedj: a három nézet nyomtatásban egymás
alatt is megjelenik, és a lényeg egy mondatban elmondható.)*

## 15. Egy igazságforrás + a dokumentum a kód — nem kettő, nem nulla (#s10b)

_(no notes)_

## 16. Felülről lefelé — adatbázis → backend → frontend → AI-felület (#s10c)

_(no notes)_

## 17. SDD + BRD, és az ötrétegű dokumentumtérkép — valós fájlokkal (#s11)

_(no notes)_

## 18. EARS — öt mondatminta, amiből teszt lesz (#s11c)

⏱ 19:00 — **Ez a BA-k dia**ja, és a diasor egyik csúcspontja. Menj végig az öt soron, de gyorsan —
a táblázat magát magyarázza. Amin **lassíts**, az az alsó kártyapár:

- Bal: *„A ház legyen meleg, és ne ázzon be."* — kérdezd meg a termet: **mikor kész ez?**
  Hány fok, milyen hidegben? Nincs válasz. Ezért nem lehet rá próbát csinálni.
- Jobb: ugyanaz EARS-ben, azonosítóval (E1: −15 °C kint, 21 °C bent; X1: a pince — ez a
  mondat tér vissza az esettanulmányban). Most már **eldönthető**.

A táblázatban a ház az elsődleges példa; minden sor alatt egy hétköznapi szoftveres mondat
(jelszó, rendelés, zárolás) mutatja, hogy a fejlesztőnek ugyanaz a minta.

A zárómondat, amit vigyenek haza: *az EARS-kikötés a szerződés szövege* — a BA írja, a fejlesztő
olvassa, az AI implementálja, a teszt bizonyítja.

## 19. Egy követelménytől az átvett funkcióig — nyolc lépés, egy valódi példán (#s11d)

⏱ 21:30 — A leggyakorlatiasabb dia; itt a fejlesztők figyelnek a legjobban. Ne olvasd fel mind a nyolc
sort — vezesd végig **ugyanazt az egy példát** a házon („Télen ne fázzunk" → `E1`), és mutasd,
hogyan alakul mondatból kikötéssé, kikötésből próbává, próbából kivitelezéssé. A kis betűs sorok
a szoftveres megfelelőt adják — a fejlesztőknek elég rájuk mutatni.

Két helyen állj meg:

- **3. lépés (Terv):** *„mekkora hőszivattyú kell?"* — **ez a valódi mérnöki döntés**, és
  most kell vitatkozni róla, nem a beépítés után (a szoftverben: nem a code review-n).
- **Az alsó piros doboz:** az üres spec **nem semleges** — fel van töltve az AI találgatásaival.
  Ez a mondat szokott megmaradni az emberekben.

## 20. TdD — a teszt az EARS-kikötés gépi fele (#s11e)

⏱ 23:30 — Jelezd, hogy ez **új elem** a módszertanunkban. A közönség fele ismeri a TdD-t 15 éve — nekik
azt mondd el, ami **megváltozott**:

1. Régen a TdD a **fejlesztő fegyelmét** pótolta. Most azt a kérdést dönti el, amit egy
   magabiztos géptől másképp nem lehet: *tényleg kész van, vagy csak annak hangzik?*
2. A piros teszt **gépi visszajelzés**, amiből az agent tovább tud dolgozni — enélkül minden
   kör emberi figyelmet igényel.

A piros dobozt **mondd ki hangosan**, ez a dia legfontosabb figyelmeztetése: ha a teszt a kód
után születik, az AI olyan tesztet ír, amit a saját kódja biztosan teljesít — vagy gyengíti a
bukó tesztet. Ezért (1) a teszt előbb kerül commitba, (2) **a review a tesztet is nézi**.

Záró: spec, teszt és kód **ugyanannak az állításnak három alakja**.

## 21. Négy motor, nem egy ötödik — katalógus-vezérelt eszközök (#s15)

_(no notes)_

## 22. Mi a RAG — és miért kell a fejlesztéshez is? (#s16)

_(no notes)_

## 23. Vektor → él → property-graph — a visszakeresés rétegei (#s17)

_(no notes)_

## 24. Tartalom és kontextus — mindkettő kell a jó RAG-sorrendhez (#rag-content-context)

_(no notes)_

## 25. „Ne ázzon be a pince" — egy igény végig a láncon (#s12)

⏱ 24:30 — Visszatérünk a Vishy-házhoz. A 2. dia azt mutatta, **ki** mit csinál; ez a dia **egyetlen igényt** követ
végig — a család mondatától a műszaki ellenőrig. Szoftverismeret nem kell hozzá, ezért mindenki
ugyanazt látja benne.

**A két láb — ezt mondd ki, mert magától nem nyilvánvaló.** Az igénynek két, más szakember által
végzett fele van, és más kérdésre válaszolnak:

- **① Felmérés (talajmechanika, geodézia):** *„mi van a telken?"* — kívülről, csak olvasás.
  **Egy tégla sem mozdul hozzá.**
- **② Kivitelezés (szigetelés, drén, vízzáró beton):** *„mi kerül a falba?"* — a terv szerint.

A mondat, ami összeköti: **„nem tervezhetsz alapot, amíg nem tudod, mi van a talajban."**

**A teszt-kártyánál álljunk meg egy pillanatra:** a nyomáspróba a visszatöltés **előtt** történik,
mert utána a szigetelés már csak bontással ellenőrizhető. Ez a TdD lényege egy mondatban — a mércét
akkor kell rögzíteni, amikor még meg lehet nézni.

Az alsó két kártya a 2. dia két kapuját hívja vissza: a **műszaki ellenőr** a tervet nézi
(verifikáció), a **család** az első eső után azt, hogy erre volt-e szüksége (validáció).

## 26. Négy döntés, ami megformálta a házat (#s13)

⏱ 25:15 — A négy kérdés–válasz pár lényege egyetlen mondatban: **minden döntés emberi döntés volt**, és
mindegyik EARS-kikötésként került a tervre. A brigád — nálunk az AI — egyet sem hozott meg
helyettünk. Ha van idő, a „két szint" kérdésnél mondd ki: *ez a legkisebb diff (A10) a házon.*

## 27. Claude Code mint fejlesztőtárs — a fegyelmező keret (#s19)

⏱ 26:15 — A táblázatból a **hookra** menj rá: *a kapu nem kérés, hanem mechanikus erő.* A házon: amíg az
ellenőr nem vette át a vasszerelést, nem öntenek betont. Nálunk a **szabály-kapu** blokkolja a
szerkesztést, amíg az AI el nem olvasta a réteg szabályfájlját — nem győzködni kell az AI-t.

**Pontosan mondd:** a main-re szerkesztésnél a hook csak *figyelmeztet*, nem blokkol — ez
szándékos (a direkt út megengedett ott, ahol a repó arra jogosult). A blokkoló kapu a szabály-kapu.

Vezetői olvasat: a szabály **kikényszerítve** van, nem remélve.

## 28. Az építési napló — a bizonyíték nem emlékezet, hanem bejegyzés (#s20)

⏱ 27:15 — Itt fizet vissza a 7. dia. A háznál mindenki tudja: vitában **az építési napló dönt**, nem az
emlékezet és nem a kivitelező becslése. A mondat, ami átvisz a számokhoz: *„nálunk a git log
az építési napló"* — minden commit egy dátumozott, névvel jegyzett bejegyzés.
Ezért a lenti számok **nem becslések**: bárki újraszámolhatja a git logból. A dián két sor
van: az első 27 nap (390 commit) — és **ma** (v0.8.951, 2 107 commit, 81 aktív nap; ~36 ezer
sor Go, ~24 ezer sor teszt, ~87 ezer sor Markdown). Az arány a lényeg, nem a szám: *még mindig
több a terv, mint a fal*. A TdD bizonyítéka **nem a sorarány**, hanem a napló: a 2026-09-09-i
mandátum óta született **16 új spec-mappa mind az első napon `tests.md`-vel jött** (24 a 47-ből).
Ha kérdezik: a többi 23 mappa a mandátum előtti, grandfatherelt — mondd ki, ne tagadd.

A zöld sávban a lánc: **megrendelő → BA → architekt → AI → architekt (review) → megrendelő = QA.** A három emberi
kalap egy emberen van — de a verifikáció (review, a műszaki ellenőr) és a validáció (a megrendelő = QA) két külön kapu marad,
pont mint a 2. dián a műszaki ellenőr és a család.

**Amit itt pontosan kell mondani** (a dia kártyája is így szól): a git history **nem
megváltoztathatatlan** — technikailag átírható (`rebase`, `--force`). Ne állítsd az
ellenkezőjét, mert a teremben ülő tapasztalt fejlesztő tudja, és ha egyszer elkapnak egy
túlzáson, a többi állítás is gyanús lesz. A helyes megfogalmazás:
> *„A `main` védett ág: nincs force-push, a beolvasztás MR-en át megy. A történetet nem a
> fizika védi, hanem szabály és jogosultság — vagyis ez is egy kapu, mint a többi."*

Ez **erősebb** érv, nem gyengébb: pont azt mondja, amit a 18. dia — a garanciát nem remélni
kell, hanem kikényszeríteni. Ha rákérdeznek, hogy „akkor mégis átírható?": igen, és éppen
ezért van jogosultsághoz kötve, és ezért látszik, ha valaki megpróbálja.

**A „12–27 emberhónap" a dia leggyengébb pontja — kezeld óvatosan.** A bal oldal ellenőrizhető,
ez nem: belső szakértői becslés, dokumentált módszertan nélkül. Mondd **nagyságrendként**, ne
bizonyítékként. Ha rákérdeznek (*ki becsülte? milyen scope-pal? hány FTE?*), a helyes válasz:
„nincs mögötte dokumentált WBS — ezért mondom nagyságrendnek." Ha nem akarod megvédeni,
**hagyd ki**, és csak a git-számokat mondd; a dia enélkül is működik.

## 29. És mi épült? — az alkalmazás, amit az IT-csoport használ (#s20b)

⏱ 28:00 — **Ez a dia a ház fényképe.** Eddig a tervrajzot, a brigádot és a naplót néztük — itt az, ami
belőle lett. Ha egyetlen mondatot mondasz el róla: *„nem kódot írtunk, alkalmazást építettünk;
a kód ennek csak az anyaga."*

Ne technikai bejárás legyen. A négy kártya egy-egy **felhasználói képesség** (látja a flottát ·
magától frissül · kérdezni lehet tőle · új gépet igényelni), a „hétfő reggel" sor pedig egy
valódi munkamenet. A hallgató azt vigye el, hogy **valaki reggel megnyitja és dolgozik vele** —
nem azt, hogy hány endpoint van mögötte.

**A 4. lépés (KAPU) a kapocs a következő diához:** a beavatkozás és az érzékeny érték feltárása
emberi kapun megy — a 18. dia ezt bontja ki. Ne mondd el itt előre.

**Ha csúszol:** ezt a diát **ne** hagyd ki — inkább a 17. dián a „12–27 emberhónap" kitérőt
hagyd el, az úgyis a leggyengébb pont. Ez a dia válaszolja meg, amit a vezető valójában kérdez:
*„és mi lett belőle?"*

## 30. Három kapu a házon — és a két módszertani kapu (#s21)

⏱ 29:00 — A vezetők diaja. **Négy kapu, mindegyik mögött ember** — a házon három (engedély, kulcs, két
aláírás); az engedély egyben a verifikációs kapu (MR: review, *aztán* merge), a validáció a negyedik. Az AI egyiket sem tudja megnyitni
magának. Ha a teremben van olyan, aki a kockázatért felel, ez az a dia, amit lefényképez.

A három kapu most a házon áll, mert így mindenki ismeri: **építési engedély**, **kulcsátadás
jegyzőkönyvvel**, **két aláírás a hitelfolyósításhoz**. Minden kártya alján egy „Nálunk" sor
mondja meg a szoftveres megfelelőt — azt elég egy mondattal végigvenni.

**Egy pontosítás, amit ne hagyj ki** — Kapu ① nem azt mondja, hogy *minden* írás kapun megy át.
A brigád az **építési naplóba** szabadon ír; engedély a **falhoz** kell. Nálunk ugyanígy: az
állapotváltoztató lépés megy MR-en, a megfigyelő írások (napló, snapshot) saját szűk
jogosultsággal, önállóan futnak. Ez nem kibúvó, hanem a lényeg: **a kapu ott van, ahol a
rendszer megváltozik** — nem ott, ahol csak leírjuk, mit láttunk. Ha ezt nem mondod ki, egy
figyelmes fejlesztő pont ezt fogja megkérdezni, és jogosan.

## 31. Négy döntés, ami a vezetőé — és az első lépés holnap (#s22)

⏱ 29:45 — Ne foglald össze, amit már elmondtál — **négy döntést adj a vezetők kezébe**: hová teszik a
kapacitást (review + átvétel, nem gépelés), hol van a tudás (dokumentumban, nem fejekben), mit
mérnek (átvett követelményt, nem sorokat), és hol a kockázat határa (a kapuknál). A sebesség
szándékosan nincs a listán: az a **következmény**, nem a cél.

A zöld sávot mondd ki szó szerint, ez a hívás cselekvésre: *„egy kicsi, valódi igény, végigvive
— nem pilot-program."* Ha kérdezik, mivel kezdjék: ezzel.

## 32. Hogyan kezdj AI-fejlesztésbe? — útravaló (#s23)

_(no notes)_

## 33. Köszönjük a figyelmet! (#s24)

⏱ 30:30 — Három mondat, aztán kérdések:

1. A specifikáció a szerződés, a dokumentum a kód.
2. Az ember dönt, az AI végrehajt — és **minden állapotváltoztató lépést ember enged át**.
3. Ami új nálad holnaptól: **EARS-ben írd le a követelményt**, és **a teszt legyen előbb, mint a kód**.

---

**Ha kérdés jön — a két leggyakoribb**

**„Elveszi a fejlesztő munkáját?"** — A szűk keresztmetszet mozdul el: kevesebb gépelés, sokkal
több **döntés, review és átvétel**. Ezek egyike sem delegálható gépnek (A6).

**„Honnan tudom, hogy nem hazudik?"** — Nem tudod a szövegéből, ezért nem is abból ellenőrzöd:
zöld teszt, olvasható diff, futó rendszer. A 13. és 18. dia erről szól.

## 34. Források & szabványok — minden technológia hivatkozva (#s25)

_(no notes)_
