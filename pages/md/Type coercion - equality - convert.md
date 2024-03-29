# PRAVILA POREDJENA SA OPERATOROM ==  

## 1.) AKO SU OPERANTI ISTOG TIPA:

### OBJEKTI
Ako oba referiraju ka istom objektu samo onda je T

### BROJEVI
+0 i -0 se tretira kao 0.
BILO STA se poredi sa NaN, pa cak i sam NaN je F

### SIMBOLI
Ako oba referiraju ka istom simbolu SAMO ONDA je T

## 2.) AKO NISU ISTOG TIPA

### null, undef, NaN
- Samo su sledece kombinacije T:  
	```js
	null == undef  // T
	null == null   // T
	undef == undef // T   
	```
- BILO STA OSTALO da se poredi sa "null" ili "undefined" (i NaN) je F.  
- Zasto su "null" i "undefined" jednaki? Zato sto "null" ne postoji u JSON-u, pa u situacije kada se konvertuje String => JSON, JS pretvara "null" => "undefined".

### Objekat == primitiva (coerce)
- Ako je sa jedne strane object, a sa druge primitiva, onda se radi prisilna konverzija objekta u primitivu (coerce).  

- Objekti se konvertuju koristeci njihove `[@@toPrimitive]()` ("default" kao hint - argument), `valueOf()`, i `toString()` metode, i to bas tim redosledom.  

- Isto se desava i pri konverziji `Objkat => Number`, `Objekat => Boolean`, samo sto se kao hint koristi "number" odnosno "boolean".

- Pri konverziji Object => String. redosled je drugaciji: `toString()`, `valueOf()` ("string" kao hint), 

- Da bi dobio primitivnu vrednost iz objekta (Boolean, String, Number ili Date), koristi se metoda valueOf().

#### PRIMERI KONVERZIJA RAZNIH OBJEKATA U PRIMITIVU
--------------------------------------
```js
// KOVERZIJA {OBJEKTA} U PRIMITIVU
o = {q:1}
o.valueOf() // Object { q : 1 }
o.toString() // "[object Object]"
o.valueOf().toString() // "[object Object]"

o == "[object Object]" // true
o == +"[object Object]" // false, zato sto je desna strana zapravo NaN, a poredjenja sa NaN uvek daje F
````
---------------------------------------
```js
// KOVERZIJA [ARRAY] U PRIMITIVU
a = []
a.valueOf() // Array []
a.toString() // ""
a.valueOf().toString() // ""

a == "" // true
a == [''] // true
a == [] // false
````
---------------------------------------
```js
// KOVERZIJA "STRING"-OBJEKTA U PRIMITIVU
s = new String(1)
s.toString() // "1"
s.valueOf() // "1"
s.toString().valueOf() // "1"

s == "1" // true
s == 1 // true
````
---------------------------------------
```js
// KOVERZIJA !!BOOLEAN-OBJEKTA U PRIMITIVU
b = Boolean(1)
b.valueOf() // true
b.toString() // "true"
b.valueOf().toString() // "true"
````
--------------------------------------- 
```js
// KOVERZIJA +NUMBER-OBJEKTA U PRIMITIVU 
n = Number(1)
n.valueOf() // 1
n.toString() // "1"
n.valueOf().toString() // "1"
````
---------------------------------------
```js
// KOVERZIJA DATE-OBJEKTA U PRIMITIVU
d = Date()
d.valueOf() // "danas"
d.toString() // "danas"
````
---------------------------------------

## 3.) AKO SU OBE STRANE KONVERTOVANE U PRIMITIVU:

- ako je jedan Symbol, a druni nije => F  
Sym == neSym => F   

- Ako je jedan Boo, a drugi nije Boo, Boo se pretvara Num, pa se poredi.  
Boo == neBoo   =>   Num == neBoo

- Ako je jedan Str, pretvara se u Num, pa se poredi.  
Str => Num // vraca "broj" ili NaN ako nije uspela konverzija

- Ako je jedan Boo a drugi Str, oba se pretvaraju u Num.
Boo == Str   =>   Num == Num   

- Znaci sve (Boo i Str) se svodi na Num pa se poredi.  

## SIMETRIJA

- `A == B` je isto sto i `B == A`

## PRIMERI KOJI ZBUNJUJU

```JS
0 == null; // false, bilo sta da se poredi sa null je F, osim null ili undefined  
0 == undefined; // false, bilo sta da se poredi sa undefined je F.  
````

```JS
!![]; // truthy, jer svaki objekat, pa i prazan je true
[] == true // false, jer [] kad se pretvori u string je ""
````

```JS
const number1 = new Number(3);
const number2 = new Number(3);
number1 == 3; // true, konverzija Objekat u Primitivu.
number1 == number2; // false, unikatnost objekata
```

```JS
const string1 = "hello";
const string2 = String("hello");
const string3 = new String("hello"); // Objekat
const string4 = new String("hello");
const string5 = string3
console.log(string1 == string2); // true
console.log(string1 == string3); // true, konverzija Objekta
console.log(string2 == string3); // true, konverzija Objekta
console.log(string3 == string4); // false, ukatnost objekata
console.log(string4 == string4); // true, isti objekat
console.log(string3 == string5); // true, referenca ka istom objektu
```

## POREDJENJE NIZOVA I STRINGOVA

```JS
a = [1, 2, 3];
b = "1,2,3";
a == b; // true, `a` converts to string

c = [true, 0.5, "hey"];
d = c.toString(); // "true,0.5,hey"
c == d; // true
```

<STYLE>
	h1 {color:#f80; font-weight: 700}
	h2 {color:#ff0}
	h3 {color:#8f0;font-style: italic;]}
</STYLE>