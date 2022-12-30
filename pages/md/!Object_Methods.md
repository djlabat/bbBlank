# OBJECT METODE

## SADRZAJ

[COPY](#copy)  
[DESCRIPTOR](#descriptor)  
[LOCK (freeze, seal)](#lock)  
[OWN PROPEPRTIES](#own_propeprties)   
[KEY, VALUE](#key_value)  
[PROTOTYPE](#prototype)  
[IS (equal)](#is_equal)  
[OSTALO](#ostalo)   

* SublimeText - Ako hocu da: UNfold all > cK, cJ.  <---->    FOLD all cK, c1  

* Svaka vrsta Objekata u JS-u (Array, Map, Set...) je prototip Objekta. Neke od Objekat metoda se prenose na druge vrste Objekata i mogu se koristiti.

#### PRIMITIVE : OBJEKTI

* Primitive se snimaju u varijable direktno. Vrednosti varijabli se "prepisuju".

```js
x=1; y=x; x=2; console.log(x, y) // 2 1
```

* Objekti se snimaju kao reference. Varijabli kojoj je dodeljen neki objekat, ne snima objekat direktno, vec se u varijablu snima adresa memorije gde je objekat smesten u memoriju. Tako da kada se putem jedne varijable (reference) promeni objekat, objekat je promenjen, i sve reference koje su vezane za taj objekat dace isti rezulta tj. promenjen objekat tj. referiraju ka tom promenjenom objektu.

```js
x={a:1}; y=x; x.a=2; console.log(x, y) // {a:2} {a:2}
````

```js
q=1, w=2 // Obicne dve promenljive
obj= {q, w} // Postoji mogucnost da se ubace spoljne promenljive u objekat i da postanu svojstva.
console.log(obj) // Object { q: 1, w: 2 }
w=3 // manjanjem spoljne promeljive, ne menja svojstva objekta, jer su pri pravljenju objekta one su PREPISANE, a ne linkovavne
console.log(obj) // Object { q: 1, w: 2 }
obj= {q, w} // redeklaracijom prepisuju se nova svojstva
console.log(obj) // Object { q: 1, w: 3 }
```

* Kljucevi objekta mogu biti samo stringovi ili Symboli. To znaci ako stavim broj kao [kljuc] on ce da prodje kroz toString() i bice upisan kao string.  
	npr. [.12e3] bice upisan kao ["120"]

* Sta znaci kad je neki prop. enumerativan? Znaci da, kad ga pozovem u for...in petlju, enum. prop. ce se odazvati tj. uci ce u petlju. Ako nije enum. onda nece.
	
* Kako se podesava da JE enum? Vidi: Object.defineProperty
* Sta znaci deskriptor? To je objekat koji sadrzi svojstva nekog svojstva.

	Postoje dve vrste Object metoda:
	1) Object
	2) Object.prototype

---
## **COPY**

### *Object.assign()*

* Kombinuje vise objekata u jedan. Prvi argument - target-objekat se menja, a ostali source-objekti se NE menjaju. Ako hocu da napravim novi objekat, kombinacijom vise objekata, a da se ni jedan ne promeni, kao 1. argument koristiti {}. Zvanicna definicija metofe: Kopira se enumerabilne stavke iz jednog objekata u drugi.

```js
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };
const returnedTarget = Object.assign(target, source);
console.log(target); // expected output: Object { a: 1, b: 4, c: 5 } // sta je sa b:2? Njega je pregazio b:4
console.log(returnedTarget); // expected output: Object { a: 1, b: 4, c: 5 }


/* ———————— Mana pri kopiranju pomocu assign - plitko kopiranje ——————————————————————————————— */
// To znaci da je samo prvi nivo NEZAVISNO iskopiran (a:1, b:2) dok ugnjezdjeni objekti (c: {age: 30}) NISU nezavisni tj. kako promenim vrednost kod jednog tako ce se promeniti i na svim ostalim klonovima.
let obj = {
  a: 1,
  b: 2,
  c: {
    age: 30
  }
};

var objclone = Object.assign({},obj);
console.log('objclone: ', objclone);
obj.c.age = 45;
console.log('After Change - obj: ', obj);           // 45 - This also changes
console.log('After Change - objclone: ', objclone); // 45
```


### *Object.create()*

* Nesto slicno kao Corel-u Clone. Pravi se novi, PRAZAN, objekat na osnovu postojeceg objekta, ali taj postojeci objekat ce da bude prototype novog objekta, a "skoljka" ce da bude prazna. Drugim recima, od postojeceg objekta pravi se prototip za novi objekat, a tom novom objektu skoljka ce da bude prazna. Ako promenim neko svojstavo objekta od kojeg je napravljen prototip za novi objekta, menja se i prototip u novom objektu. Object.create nije dobro za NE ZAVISNO kopiranje. 

* Ako su potrebni primeri pogledati u HTML fajlu

---
## **DESCRIPTOR**

* Ima 2 vrste descriptor-a: DATA i ACCESSOR. Njihove default vrednosti su:  
	- DATA: writable: false; value: undefined
	- ACCESSOR: undefined (inace mogu da budu: getter ili setter)
	
* Zajednicka svojsva za DATA i ACCESSOR su:
	-	configurable - po default-u FALSE
	- Ako je TRUE, svojtva mogu da se menjaju i da se brisu

* enumerable - po default-u FALSE  
Ako je T bice vidljiv u for...in loop-u

### DATA

### *Object.defineProperty ( obj, propString, descriptorObject )* 

* Na ovaj nacin dodata svojstva su, po default-u imutabilna (confugurable:false) i nisu enumerabilna (enumerable:false).
  // Da bi se promenilo svojstvo(propString) od Objekta(obj), mora prvo da se dozvoli kofigurisanje objekta (confugurable:true), pa potom da se dozvoli upis u to svojstvo (writable:true). Ako jos zelim i da se to svojstvo npr. pojavi u for...in petlji tj. da bude enumerabilno onda moram to ukljuciti (enumerable:true).

```js
const object1 = {};

Object.defineProperty(object1, 'property1', {
  value: 42, writable: false // ako bih pokusao da stavim da je T => Error (strict mode) jer je confugurable:F
});

object1.property1 = 77; // throws an error in strict mode

console.log(object1.property1); // 42	
````
  ### ACCESOR > GET- SET

```js
function ArhiverTemperatura() { // konstruktor za klasu
  var temperatura = null; // unutrasnja svojstva, pocetne vrednosti
  var arhiva = [];

  Object.defineProperty(this, 'temperatura', { // Stvaranje novog objekta sa svojstvom "temperatura". Treci parametar je {objekat u kom se definisu geteri u seteteri.}
    get() { // pozivom svojstva "temoerature"...
      console.log('trenutna temperatura je:'); // ...ispisuje tekst u konzoli i... 
      return temperatura; // ...return-uje mi se poslednjs uneta tj. trenutna temperatura.
    },
    set(value) { // Dodeljivanjem nove vrednosti...
      temperatura = value; // ...upisuje se nova vrednost "value" u svojstvo "temperatura"...
      arhiva.push({ val: temperatura });
    } // ...i takodje se upisuje u svojstvo "archive" unutar objekta  
    // po difoltu su: configurable:false, enumerable:false  
  });

  this.getArchive = function() { return arhiva; }; // metoda za vracanje niza
}

var arc = new ArhiverTemperatura();
arc.temperatura; // 'get!'
arc.temperatura = 11;
arc.temperatura = 13;
arc.getArchive(); // [{ val: 11 }, { val: 13 }]
arc.temperatura; // 13
```



### *Object.defineProperties(obj, { {...}, {...}, ...} )*
	
* Isto kao i ↑prethodni↑ ali za vise svojstava odjednom.
* OBRATI PAZNJU, nisu isti argumenti kao kod Object.defineProperty (vidi ↑ gore). Ovde je drugi argument {blok} u kojem su prop.-si: {deskriptori}. PAZI, kada kucas u editoru sa intelisense. Obrati paznju sta si izabrao, ...Property ili Properties

```js
Object.defineProperties(qwe123 , {
  'a': {value: 11},
  's': {value: 22, writable: true},
  'd': {value: 33, confgurable: true}, // neispitano
})
qwe123
/*
Object { q: 1, w: 2, e: 3, … }
    a: 11
    d: 33
    ​e: 3
    ​q: 1
    ​r: 4
    ​s: 22
    ​w: 2
*/
Object.keys(qwe123) // Array(3) [ "q", "w", "e" ]
Object.values(qwe123) // Array(3) [ 1, 2, 3 ]
for (let prop in qwe123) console.log(prop) // q w e

qwe123.a = '$r6;_=345+' // '$r6;_=345+' // kaze da je promenio vrednost ALI NIJE! Zato sto je po defaultu writable: false
qwe123.a // 11

qwe123.s = '$r6;_=345+' // '$r6;_=345+'
qwe123.s // '$r6;_=345+'
```



### *Object.getOwnPropertyDescriptor()*

* Pravi se novi objekat (tzv. deskriptor) pomocu kojeg se prikazuje konfiguracija nekog svojstva.

```js
deskriptor = Object.getOwnPropertyDescriptor(qwe123, 'q')

console.log(deskriptor.value) // 1
console.log(deskriptor.writable) // T
console.log(deskriptor.enumerable) // T
console.log(deskriptor.configurable) // T
console.log(deskriptor.valueOf()) /*
Object {
  value: 1,
  writable: true,
  enumerable: true,
  configurable: true
}
*/
console.log(deskriptor.set) // undefined
console.log(deskriptor.get) // undefined

deskriptor.value = 11 // 11 // moze da se menja vrednost objekta koji prikazuje konfiguraciju svojstva, ali...
qwe123.q // 1 // ... vrednost u originalnom objektu ostaje nepromenjena. Verovatno zato sto je "deskriptor" nezavistan objekat. Prepisane vrednosi.
```



### *Object.getOwnPropertyDescriptors()*

* Isto sto i ↑ Object.getOwnPropertyDescriptor samo sto prikazuje konfiguracije od SVIH svojstava (ili onih koje si odabrao).

```js
deskriptor = Object.getOwnPropertyDescriptors(qwe123)
/*
deskriptor = {
  "q": {
    "value": 1,
    "writable": true,
    "enumerable": true,
    "configurable": true
  },
	"w": {
    "value": 2,
    "writable": true,
    "enumerable": true,
    "configurable": true
  },
	"e": {
    "value": 3,
    "writable": true,
    "enumerable": true,
    "configurable": true
  }
}
*/

console.log(deskriptor) // isto kao ↑
console.log(deskriptor.valueOf()) // isto kao ↑
console.log(deskriptor.w.value) // 2
console.log(deskriptor.w.writable) // T
console.log(deskriptor.w.enumerable) // T
console.log(deskriptor.w.configurable) // T
console.log(deskriptor.set) // undefined
console.log(deskriptor.get) // undefined

deskriptor.q.value = 11 // 11 // moze da se menja objekat koji prikazuje konfiguraciju svojstva, ali...
qwe123.q // 1 // ... vrednost u originalnom objektu ostaje nepromenjena.
```

---
## **LOCK**  

### *Object.preventExtensions()*

* Onemogucava objekat da mu se dodaju novi props

### *Object.isExtensible()*

* Proverava da li objektu mogu da se dodoaju novi props

### *Object.freeze()*

* Zamrzava objekat da ne moze NISTA da se menja (ni dodaje, ni oduzima, ni kofigurise). !Podobjekat nije smrznut. Svaki posebno mora da se smrzne. Takodje i obrnuto, ako zamrznem podobjekat(ili niz) to ne znaci da ce i maticni objekat biti smrzut. OBJASNJENJE: Ovo je i logicno jer "podobjekat" je samo referenca ka tom drugom (pod)objektu. Objekat ne može da se obriše.

###	*Object.isFrozen()*

* Proverava da li je objekat zamrznut. Vidi "freeze"

###	*Object.seal()*

* Zapečaćeno. (Kao freeze, ali param su promenjivi) Objekatu NE mogu da se dodaju novi props, a postojeci props NE mogu da se konfigurisu. Ali VREDNOSTI postojecih propsa mogu da se menjaju (ako su writable). Objekat ne može da se obriše.

### *Object.isSealed()*

* Proverava da li je objekat zapečaćen. Vidi "seal"


---
## **OWN_PROPEPRTIES**

### *Object.prototype.hasOwnProperty()*

* Proverava da li objekat sadrzi odredjeni properties. pogledaj fajl hasOwnProperty.js

```js
psi.hasOwnProperty('ime') // F
psi[0].hasOwnProperty('ime') // T
psi[0].hasOwnProperty('Bela') // F
```



### *Object.prototype.propertyIsEnumerable("property")*

* Proverava da li prop pripada licno tom objektu i da li je enumerabilan.

```js
qwe123.propertyIsEnumerable("q") // T
psi[0].propertyIsEnumerable('ime') // T
psi['0'].propertyIsEnumerable('god') // T
arr.propertyIsEnumerable(0) // T

arr.propertyIsEnumerable('length') // F
boo.propertyIsEnumerable() // F - ovo nisu Objekti vec primitive
qwe.propertyIsEnumerable() // F
```


---
## **KEY_VALUE**

* Postoji 2 nacina da se pozovu KEY-VALUE metode:

	1. Putem reference (npr. "qwe123"), pri cemu se vraca [ ITERATOR ]
	2. Putem "Object", pri cemu se vraca [ NIZ ]

### **1.) Pozivanje putem Reference**

```js
qwe123.keys()		// █ Pravi iterator (ne niz) od kljuceva objekta. // [q,w,e]
qwe123.values()		// █ Pravi iterator (ne niz) od vrednosti svojstava. // [1,2,3]
qwe123.entries()		// █ Pravi iterator (ne niz) od [kljuceva i vrednosti svojstava]. // [ [q,1], [w,2], [e,3] ]
qwe123.valueOf()		// █ vraca vrednost objekta, isto dobija i kada pozoves objekat qwe123 // { q: 1, w: 2, e: 3 }
```

### **2.) Pozivanje putem Object**

### *Object.keys()*

* Pravi niz (ne iterator) od kljuceva objekta. Moze da se koristi kao kod Array.length
```js 
Object.keys(qwe123).length // [q,w,e].length // 3
```

### *Object.values()*

* Pravi niz od vrednosti svojstava (ako su enumerativni). Slicno je kao for...in loop, ali loop enumerise i propertie od prototype lanca.

```js
Object.values(qwe123) // [1,2,3]
```

### *Object.entries()*

* Pravi [2D-niz] kljuceva i vrednosti

```js
Object.entries(qwe123) // [ [q,1], [w,2], [e,3] ]
```

### *Object.fromEntries(ob)*

* Obrunto od ↑ Object.entries. Transformise neku listu vrednosti oblika [key, value] u objekat {key: value}

```js
Object.fromEntries([
  ['qwe', '123'],
  ['asd', 456]
]); // {qwe:"123", asd:456}
```


### **Izdvajanje kljuceva**

* Properti nekog objekta moze da bude:
	1. string - Name → getOwnPropertyNames
	2. Simbol - Symbol → getOwnPropertySymbols

### 1.) *Object.getOwnPropertyNames(obj)*

* Vraca Array svih kljuceva (ukljucujuci i ne-enumerable, **IS**kljucujuci one koji koriste Symbol).

```js
Object.getOwnPropertyNames(obmix) // [0,1,2,3,4,q,a,qwe,qwe123,abc,…]
```


### 2.) *Object.getOwnPropertySymbols(obj)*

* Vraca Array od svih simbola koji su korisceni u datom objektu

```js
Object.getOwnPropertySymbols(obmix) // [Symbol("sym"), Symbol("nedeklarisani sym")]
```
```js
obmix[Object.getOwnPropertySymbols(obmix)[1]] // "kako ga pozvati?" ← ovo je vrednost koja stoji iz simbol kljuca
```

---
## **PROTOTYPE**

### *Object.setPrototypeOf(target, prototypeObject)*

* Dodeljivanje prototipa nekom objektu, tacnije: "target" objektu se dodeljuje "prototypeObject" da mu bude prototip.

```js		
targetObj = {}

Object.setPrototypeOf(targetObj, obmix)

targetObj.hasOwnProperty(qwe) // false //targetObj "licno" NEMA qwe, vec ga ima u prototipu.
targetObj.qwe // 'qwerty'

targetObj.hasOwnProperty(abc) // false
targetObj.abc[0] // "a"
```

### *Object.getPrototypeOf()*

* Vraca objekat koji je koriscen kao prototip

```js
// ----- MOJA ISPITIVANJA -----
Object.getPrototypeOf(q)      // Number { 0 }
Object.getPrototypeOf(w)      // Number { 0 }
Object.getPrototypeOf(qwe)    // String { "" }
Object.getPrototypeOf(arr)    // Array []
Object.getPrototypeOf(boo)    // Boolean { false } // PAZNJA: vrednost od boo je T ???
Object.getPrototypeOf(ta)     // function ()
Object.getPrototypeOf(qwe123)
/*
Object { … }
__defineGetter__: function __defineGetter__()
__defineSetter__: function __defineSetter__()
__lookupGetter__: function __lookupGetter__()
__lookupSetter__: function __lookupSetter__()
__proto__:
constructor: function Object()
hasOwnProperty: function hasOwnProperty()
isPrototypeOf: function isPrototypeOf()
propertyIsEnumerable: function propertyIsEnumerable()
toLocaleString: function toLocaleString()
toString: function toString()
valueOf: function valueOf()
<get __proto__()>: function __proto__()
<set __proto__()>: function __proto__()
Object.getPrototypeOf(q)
*/
Object.getPrototypeOf({}) 				// isti rezultat kao ↑, vidi ↓
Object.getPrototypeOf(qwe123) === Object.getPrototypeOf({})  // T

Object.getPrototypeOf(Number)     // function ()
Object.getPrototypeOf(Function)   // function()
Object.getPrototypeOf(Object)     // function()
Object.getPrototypeOf(null)       // Uncaught TypeError: can't convert null to object
Object.getPrototypeOf(undefined)  // Uncaught TypeError: can't convert undefined to object
Object.getPrototypeOf(NaN)        // Number { 0 }
Object.getPrototypeOf(0/0)        // Number { 0 }

const prototype1 = {};
const object1 = Object.create(prototype1);
console.log(Object.getPrototypeOf(object1) === prototype1); // █ poredjenje [[Prototype]]-ova izmedju 'object1' i 'prototype1'
// expected output: true
```


### *Object.prototype.isPrototypeOf()*

* proverava da li je neki objekat prototip drugom objektu.
*	Object, Array, String, Number... Imaju prototype (tj. imaju svoju class). Posto su to kostruktori prototip im je Function > a njegov prototip je Object > a on je osnova svega tj. nema prototip tj prototype:null

```js
Object.prototype.isPrototypeOf(String)* // T
```

```js
Object.__proto__.isPrototypeOf() //

// ----- moj primer -----------------------------------
targetObj = {}

Object.setPrototypeOf(targetObj, obmix) // obmix je postao prototip za targetObj

// DOKAZ:
targetObj.hasOwnProperty(qwe) // false
targetObj.qwe // 'qwerty'

targetObj.__proto__.isPrototypeOf(obmix) // F // BTW __proto__ je u FireFox
obmix.__proto__.isPrototypeOf(targetObj) // T

// ----- MDN PRIMER -----------------------------------
function object1() {}
function object2() {}

object1.prototype = Object.create(object2.prototype);

const object3 = new object1();

console.log(object1.prototype.isPrototypeOf(object3)); // T
console.log(object2.prototype.isPrototypeOf(object3)); // T
console.log(object1.prototype.isPrototypeOf(object2)); // T

// ----- moja ispitivanja -----------------------------
console.log([].isPrototypeOf(object3))       // F
console.log([].isPrototypeOf(Array))         // F
console.log(object3.isPrototypeOf(Function)) // F
console.log(object3.isPrototypeOf(Object))   // F
console.log(Math.isPrototypeOf(Number))      // F
console.log(Function.isPrototypeOf(object1)) // F
console.log(object3.isPrototypeOf(Function)) // F
console.log(object3.isPrototypeOf(Object))   // F
```

## **IS_equal**  

### *Object.is()*  
	
* Proverava istoću dve vrednosti. Za razliku od "==" komparacije ovde je:

```js
// NaN == NaN 					// F
Object.is(NaN, NaN)     // T
Object.is(NaN, 0/0);    // T
Object.is(0, -0);       // F

// '' == false == 0     // T
Object.is('', false);   // F
Object.is('', 0);       // F
Object.is(false, 0);    // F
```

## **OSTALO**

###	*Object.prototype.toString()*

* Po default-u vraca "[object Object]", ali ta metoda moze da se promeni pa da vraca sta ti hoces. Vidi primer:

```js
function Dog(name) {
  this.name = name;
}

const dog1 = new Dog('Gabby');

Dog.prototype.toString = function dogToString() {
  return `${this.name}`;
};

console.log(dog1.toString());
// expected output: "Gabby"
```

### *Object.prototype.valueOf()*

* Kao sto samo ime kaze "valueOf" - vrednostOd, a to znaci da vraca vrednost od objekta kada se primoravanjem od njega to zatrazi. To se najcesce desava u situacijama kad je objekat izlozen nekom operatoru, pa se trazi od objekta njegova vrednost. Posto se od objekta trazi da vrati vrednost (value) onda ta vrednost MORA biti primitiva.

* Uglavnom su to +-aritmeticki*% i >komparativni< operanti, i vecina >>~bitwise^== operatora. Operatori koji su vezani za !Boolean&&|| ne koriste "valueOf" vec samo citaju komplatan objekat. Tako npr. !!a je isto sto i !!{...}, sto je uvek true.

> *Zanimljivo: ime "valueOf"... po istom principu je nastalo ime "indexOf"*

```js
const a = {
  br : 1,
  valueOf: function(){return this.br+=2}
}

console.log(a) // {"br": 1, ...}// Pozvan je objekat // nemenja objekat
console.log(a + 3) // 6 // "a" je primoran da vrati vrednost  // MENJA
console.log(a + 3, a) // 8 Object { br: 5, valueOf: valueOf() } // MENJ
console.log(!!a, a) // true { br: 5,... } // nemenj, jer je to ustvari !!{...}
console.log(a**2, a) // 49 {7} // M
console.log(+a, -a, a) // 9 -11 {11} // M
console.log(a>>1, a) // 6 {13} // M
console.log(123&&a, a) // {13} {13} // n
console.log(a>5, a) // true {15} // M
console.log(a%3, a) // 2 {17} // M
console.log(~~a, a) // 19 {19} // M
console.log(a^0, a) // 21 {21} // M
console.log(a&3, a) // 3 {23} // M
console.log(a == a) // true // n
````

### *Object.prototype.toLocaleString()*
