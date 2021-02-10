# intro
bevezeto feladat

# Immutable

## Ellenőrző kérdések

* Hogyan kell egy attribútum változását megakadályozni?
* A final tagot csak korlátozottan lehet módosítani. Hol lehetnek `final` attribútumot módosító kódok?

## Bolygók felfedezése

A fő feladat az `Astronomer` osztály elkészítése, de annak vannak előfeltételei, függőségei. Olvasd el az egészet, majd haladj szépen sorban. Ha mindenzeket megcsináltad, lefodul, de nem fog csinálni semmit!

Hozz létre egy `Planet` nevű osztályt, amelynek állapota nem változhat! Most csak olyan attribútumok vannak,
amelyek nem változnak. A Bolygót, amikor felfedezik, akkor meghatározzák az átmérőjét, és 
el is nevezik (tároljuk azeket a radius, name attribútumokba). (A bolygó életében ezek az adatok nem fognak változni.)
Hozz létre egy konstruktort, amelyben az objektum megkapja a két adatot kívülről, és rendre beállítja azokat!
Hozz létre getter metódusokat az addatogokra!

Szükség van még egy `EquatorialCoordinate` osztályra is, amely azt tárolja, hogy hol látjuk a bolygót (relatív adat). 
Két `long` típusú attribútummal rendelkezik: `longitude`, `azimuth`.
(Ezek az adatok sem változnak egy rögzített origójú rendszerben. Ha a megfigyelt entitás változik, pl. bolygó
kering a nap körül, akkor nem a koordinátájának az értéke változik, hanem egy másik koordinátára kerül.) Legyen
ezért a két attribútuma `final`! Hozzunk létre egy konstruktort, amely megkap két `long` típust, és beállítja az attribútumok 
értékét! Hozzunk létre getter metódusokat az attribútumokra!

Hozz létre egy interfészt `PlanetCalculator`, amely segít meghatározni egy adott helyen levő bolygó átmérőjét!
Egy long `getPlanetRadiusInPosition(Point point)` metódust tartalmaz! Ennek az implementációját majd megadják a 
felhasználás során (a valóságban is más megvalósítása volt 300 éve és más most), neked csak használni kell.

Hozz létre egy osztály amely tárolja a bolygó abszolút koordinátáit (`Point`). A bolygó abszolút helyzetét írja le.
Ennek az osztálynak három attribútuma van,  `x`, `y`, `z`. 
Hozzunk létre egy konstruktort, amely megkap három `long` típust, és beállítja az attribútumok értékét! 
Hozzunk létre getter metódusokat az attribútumokra!

Hozz létre egy interfészt, amely a nemzetközi csillagász szövetség szolgáltatásait definiálja `InternationalActronomicalUnion` néven, 
amelyek legyenek a következök:

```java
boolean isThePlanetDiscovered(Date noticeDate, EquatorialCoordinate equatorialCoordinate)
```

Visszaadja, hogy az adott pillanatban adott helyen látszó bolygót felfedezték e már (igaz, ha már ismert)

```java
Point getRealPosition(Date noticeDate, EquatorialCoordinate equatorialCoordinate)
```

Visszaadja az abszolút koordinátát a viszonylagos koordináta függvényében.

```java
boolean register(Planet planet, Point position)
```

Beregisztrálja az új bolygót. Hamissal tér vissza, ha a regisztrációt nem sikerült. (Már felfedezték, vagy egyéb akadálya van.)
(Az implementációt, majd megadják később.)

Végül hozzunk létre egy központi csillagász osztályt (`Astronomer`), amely az előzőeket használja! Minden csillagásznak van neve, 
nyilvántartja hogy milyen bolygókat fedezett fel (`List<Planet>` típusú). 
Működéséhez szükség van továbbá két külső entitásra: a már létező `InternationalActronomicalUnion` és a `PlanetCalculator` 
egy egy példányára (4 attribútum). 
Szükség van egy konstruktorra, amellyel az attribútumok beállíthatóak (név + két függőség). 
Szükség van egy getterre, amely visszaadja a felfedezett bolygókat (`getDiscoveredPLanets`).

A csillagász figyeli az égboltot. Adott pillanatban, adott helyet figyeli, amelyet a következő metódus szimulál:

```java
public boolean observeTheSky(Date date, EquatorialCoordinate equatorialCoordinate)`
```

Ez a metódus lekérdezi a nemzetközi szövetséget, hogy az adott helyen látszó valamit felfedezték-e már (`isThePlanetDiscovered`).
Ha még nem, akkor lekérdezi a szövetségtől a valódi abszolút koordinátát (`getRealPosition`), majd kiszámíttatja az adott 
koordinátán levő égitest átmérőjét (`getPlanetRadiusInPosition`). 
Az új adatok birtokában beregisztrálja az új égitestet, használva a saját nevét (magáról nevezi el).

Ha a regisztráció sikeres volt, akkor eltárolja az új bolygót a saját listáján.

Hamissal tér vissza, ha új bolygót sikerült felfedeznie, de a nemzetközi regisztráció sikertelen volt (minden más eset sikeres).

## Bónusz feladat 1.

Hozz létre egy Naprendszer (`SolarSystem`) nevű osztályt, amelyben négy bolygót tárolsz el (Mercury, Venus, Earth, Mars). 
Ezen értékei nem változhatnak.

## Bónusz feladat 2.

Hozz létre egy factory-t a bolygók létrehozására, amely `create` metódusa megkapja a
bolygó nevét, és visszatér az adott bolygó példányával.



## Ellenőrző kérdések

* Miért kell az osztály modosítását tiltani (miután kész van)?
* A specifikációt milyen kérdésekkel érdemes kiegészíteni?
* Milyen a rugalmas kód?

## UserController
Készítsünk egy web alkalmazás kontrollert `UserController`! Egy olyan osztályt, ami element
egy User példányt, de csak akkor, ha az adatok megfelelőek, azaz érvényesek 
(érvényes, ha legalább 6 karakterből áll, és nem tartalmaz space karaktereket).
Webalkalmazás esetén a bemenetet mindig szűrni kell a szerver oldalon!



Ha csak ennyi van a pecifikációban gondolkodjunk el a következőkön:
* Az előző leírás csak egy szöveg egység, de hány programozói egység valójában?
Hány felelősség? Hány különböző "dolgot" kell implementálnunk? (elment, ellenőriz)
* Ha egy osztályban lenne minden, akkor mi lenne a legjobb név az osztálynak? 
* Ha később bővülni fog a specifikáció milyen új igények jöhetnek be? 
Nem mondták, de mindig be szokott még jönni, hogy. 



Ahány felelősség, annyi osztály, ezért érdmes négy entitással kezdeni:
* User pojo - még senki nem mondta, de biztos lesz életkora, számlaszáma, 
címe, ...
Készítsünk egy konstruktort, ami a paraméterében kapott String-et elmenti a 
userName adattagba. Készítsünk egy gettert az adattagra!
* Validator - ellenörzést végez.
Valószínű ebből lesz több is, ezért nem egy osztályt hozunk létre, majd az 
módosítjuk minden alkalommal, amikor új igény jelentkezik, hanem egy interfészt,
`Validator` néven. Tartalmaz egy 
 `public boolean isValid(String userName)` metódust. A feladat most csak 2 szabályt ír le, 
 implementáljuk ezt egy `AccountValidator` osztályban.
* UserController - fogadja a kéréseket, használ másokat (felső réteg). 
Két külső függősége van: validátor(ok), userService
  *egy `public void createUser(String username)` - ezt hivják, majd kivülről
  *Kellene egy konstruktor, ami függőségeket fogadja, és menti adattagba. 
  Validátorok listája, UserService
  *Kellene egy `private boolean validUserName(String userName)` metódus, ami
  használja a már beadott validátorokat. (ha nincs egy külső se, akkor is működni kell,
  ekkor az input érvényes) Az összes valaidátort használja, és ha bármelyik
  ellenörző elutasítja a bemeneti értéket, akkor a bement érvénytelen
* UserService - webalkalmazástól mentes userekkel kapcsolatos műveleteket 
implementálja. Legyen ez most csak 1 interfész, ami csak a mentést save metódusát deklarálja.
`void save(User user)`

## Js injekció ellen védett UserController
Bővítsük ki az előző kódot, hogy ki tudja szűrni a JS injekció alapú támadásokat!
Készítsünk egy `JsInjectionValidator` osztályt, amely implementálja a `Validator` interfészt,
oly módon, hogy a kapott szöveg érvénytelen, ha tartalmazza a "<script>" szöveget!
