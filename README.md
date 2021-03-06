# misekonyv-spec
A Digitális Misekönyv (és további liturgikus alkalmazások) specifikációja

A digitális misekönyv egy saját hardverrel és szoftverrel rendelkező e-ink kijelzős kütyü ami római katolikus papoknak, diakónusnak és igeliturgiákat végzőnek segít abban, hogy a kütyün kívül semmilyen más liturgikus könyvet ne kelljen magukkal vinniük, valamint a liturgia helyszínén már ne kelljen lapozgatni, hanem az előzetes beállítások alapján egybe megmutatja a liturgia teljes menetét (ha kell akkor a hivatalos megjegyzésekkel és opciókkal). Ez 10-12 db 300-800 oldalas könyv kiváltását jelenti. Lásd még: http://misekonyv.hu

Tartalmaz mindenféle szentmisét, keresztelés, házasság, és temetési liturgiákat. (Későbbiekben még bérmálás, papirendek, stb. stb. Lásd: [choose liturgy type](views/chooseLiturgyType.md) Az alkalmazás hasonlít az [*iMassal*hoz ](http://www.imissal.com/)abban, hogy a szentmise minden szövege benne van és akár más imák is. Viszont inkább úgy működik mint a [*zsolozsma* ](https://lh.kbs.sk/hu/default.htm)alkalmazás: egészen offline és az adott napi beállítások alapján egyetlen képernyőre vágja össze az aktuális liturgia minden részét. Illetve nem egyetlen app, hanem egy launcher + meghatározott alkalmazások gyűjteménye, melyek között kiemelkedő maga a misekönyv alkalmazás. 

- [Célközönség](target.md)
- [Szóhasználat definíciói](definitions.md)
- [Az ajánlatkérés scope-ja](inquiry.md)

Programozandó részek
- [A Launcher](theLauncher.md)

# Nézetek

> TODO: Wireframek készítése még szükséges.

- (current) [dateView](views/date.md) (default / kezdőképernyő)
- [chooseLiturgyTypeView](views/chooseLiturgyType.md)
- [liturgyView](views/liturgy.md)
- [liturgyOverviewView](views/liturgyOverview.md)
- [weekView](views/week.md)
- [menu](views/menu.md)



# Követelmények

Az alábbiakban sok-sok követelmény hangzik el. A jobb átláthatóság és talán a fejlesztést is segítő módon modulokba van szedve. A végfelhasználónak erről semmit nem kell tudnia. A modulok nem kapcsolhatóak külön ki vagy be, nem is kell kódban sem szétválniuk, bár talán érdemes.


## Szíve lelke
- Naptár: [m/calendar](modules/calendar.md) ([must](definitions.md#priorities))
- Liturgikus naptár: [m/liturgicalCalendar](modules/liturgicalCalendar.md) ([must](definitions.md#priorities))
## Liturgikus modulok
- Szentmise: [m/mass](modules/mass.md)

  Ebben vannak a szentmise részei is részletezve.

  Valamint a rengeteg extra miseféle (rituális misék, votív misék, különleges alkalmakra, gyászmise)

- Húsvét: [m/easter](modules/easter.md)

- Igeliturgia: [m/celebrationOfTheWord](modules/celebrationOfTheWord.md)

- Házasság: [m/matrimony](modules/matrimony.md)

- Keresztség: [m/baptism](modules/baptism.md)

- Elsőáldozás: [m/firstCommunion](modules/firstCommunion.md)

- Bérmálás: [m/confirmation](modules/confirmation.md)

- Betegek kenete: [m/anointingOfTheSick](modules/anointingOfTheSick.md)

- Temetés: [m/funeral](modules/funeral.md)

- Gyászmise: [m/funeralMass](modules/funeralMass.md)

- Szent Rendek: [m/holyOrders](modules/holyOrders.md)

- Templomszentelés: [m/consecrationOfChurch](modules/consecrationOfChurch.md)

- Preorátor: [m/praeorator](modules/praeorator.md)
## Egyéb modulok
- N. szűrő: [m/nFilter](modules/nFilter.md) ([should](definitions.md#priorities))
- Homília/Prédikáció: [m/homily](modules/homily.md)
- Export: [m/export](modules/export.md) ([should](definitions.md#priorities))
- Google Naptár Szinkronizáció: [m/googleCalendarSync](modules/googleCalendarSync.md)  ([should](definitions.md#priorities))
- Kották: [m/melodies](modules/melodies.md) ([could](definitions.md#priorities))
- Minialklamazások: [m/widgets](modules/widgets.md) ([could](definitions.md#priorities))
- Képernyőkímélő: [m/screenSaver](modules/screenSaver.md) ([should / won't](definitions.md#priorities))
- Énekrend: [m/musicListing](modules/musicListing.md) ([won't](definitions.md#priorities))
- Hírdetések: [m/announcements](modules/announcements.md) ([won't](definitions.md#priorities))
- Hívek könyörgése: [m/prayersOfTheFaithful](modules/prayersOfTheFaithful.md) ([won't](definitions.md#priorities))
- Többnyelvűség: [m/i18n](modules/i18n.md) ([must](definitions.md#priorities))

## [További nem funkcionális követelmények](nonFunctionalRequirements.md)

- Fejlesztői környezet, 
- Támogatott eszközök és kompatibilitás, 
- Telepítés és telepíthetőség, 
- Frissíthetőség és frissítés, 
- Analitikai eszközök, 
- Dokumentáció, 
- Felhasználói kézikönyv, 
- Support igény



# Adatformátumok és adatforrások

Pár ezer oldalnyi szöveg kerül bele ebbe az alkalmazásban.

- Javaslat: JSON vagy XML, könyvek/fejezetek mappa rendszerben sok külön fájlban.
- Javaslat: a struktúra minél inkább kövesse a nyomtatott könyveket. Ez segíti az átláthatóságot.

Megbeszélendő: hatalmas munka a szövegek pdf/txt/word formátumból megfelelő formátumú fájlokra alakítása. Ezt akár mi - megrendelő - is ki tudjuk szervezni harmadik félnek, ha készül megfelelően definiált formátum azonosítókkal.

Segíthet a szövegek előkészítésében, hogy a https://igenaptar.katolikus.hu/ egyféle adatbázisból már dologzik ezen. Tőlük el lehet kérni, ha már minden jogi akadályunk elhárult.

> Todo: hívekkönyörgése, mise, stb (?) deifniálása ide az olvasmányokhoz hasonlóan

- Olvasmányok: [d/readings](dataschemas/readings.md) 
- Hívek könyörgése: [d/prayersOfTheFaithful](dataschemas/prayersOfTheFaithful.md)
- Mise általános
- *stb?*

> TODO: mik vannak még?

# Egyéb 


[Sok minden amit még át kell gondolni és meg kell tervezni.](inProgress.md)

