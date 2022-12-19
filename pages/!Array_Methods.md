# ARRAY METODE

## SADRZAJ:  
[SECKANJA](#seckanja)  
[RAZNI ALATI](#razni-alati)  
[FILTRIRANJE POMOCU CALLBACK F-JA](#filtriranje-pomocu-callback-f-ja)  
[REDUCE](#reduce)  
[MAP](#map)  
[PAKOVANJE U STRING](#pakovanje-u-string)  
[ARRAY PROTOTYPE](#array-prototype)  
[MANJE BITNE STVARI](#manje-bitne-stvari)  

---

## ! Paznja !
* Skoro sve metode za Array MENJAJU original, osim onih koje koriste callbackfn.  
* (VS CODE) Ako mi trebaju tacniji podatci sta koja metoda radi> hover preko metode i pojavi se opis.

---

## Promenljive koje se koriste u primerima u fajlu

```js
let abc = ["a", "b", "c", "d", "e"];
let zxc = ['z', 'x', 'c']
let one2 = [1, 2]
```

---------------------------------------------------------------------------------------------------------

## **SECKANJA**

### UKRATKO TABELA ISPOD PRIKAZUJE STA KOJA (SEC) METODA VRACA:
| 	   METODA: | shift  | unshift  | splice  |  push  |  pop  |
|         ---: |  :---: | :---:    | :---:   | :---:  | :---: |
| VRACA NAZAD: |  'a'   | length   | ['x']   | length |  'z'  |

* metode koje seku na pocetku i kraju (shift i pop) vracaju ono sto su obrisali
* metode koje ubacuju na pocetku i kraju (unshift i push) vracaju novi length
* splice vraca ono sto je odsekao, ali kao Array

### *slice*  

  * slice ~ crop, isecak ( od index-a, do indexa) ---negativne vrednosti broji od kraja. NEmenja original 'abc'  

```js
abc = ["a", "b", "c", "d", "e"]
abc.slice(1, 4) // [b,c,d]
abc             // [a,b,c,d,e] // ostao NEporomenjen

// NEGATIVNI BROJEVI
[0,1,2,3,4,5,6,7].slice(-3)     // poslednja tri // [5,6,7]
[0,1,2,3,4,5,6,7].slice(3)      // od 3. zareza spreda se pocinje // [3,4,5,6,7]
[0,1,2,3,4,5,6,7].slice(-3,7)   // [5,6]
[0,1,2,3,4,5,6,7].slice(-4,-1)  // [4,5,6]
[0,1,2,3,4,5,6,7].slice(4,-2)   // [4,5]

// PRAVLJENJE NEZAVISNE KOPIJE
let sliceed2 = abc.slice(); console.log(sliceed2); // [a,b,c,d,e]
```

### *splice*  
  
  * splice ~ replace - MENJA original 'abc' - Pamtim, kao da se na "slice" zalepi 'p'  

```js
abc = ["a", "b", "c", "d", "e"]
let spliced = abc.splice(2, 1, 'Q', 'W') // index_od, duzina, novi_elementi - 'splice' od 'abc' odseca 'c' i zamenjuje ga sa 'Q', 'W' i vraca novi array od odsecenog ['c']
abc // [a,b,Q,W,d,e]
// Ako hocu da UBACIM novi element na ODREDJENU poziciju:
spliced = abc.splice(3, 1, abc[3], 'E') 
abc // [a,b,Q,W,E,d,e]
```

### *pop* 
  
  * pop - menja original 'abc'

```js
abc = ["a", "b", "c", "d", "e"]
let popped = abc.pop(); // e
console.log(popped, typeof popped); // e string
console.log(abc); // ['a', 'b', 'c', 'd']
```


### *push* 
  
  * push - menja original 'abc'

```js
abc = ["a", "b", "c", "d", "e"]
let pushed = abc.push("Pu");
console.log(abc); //  [ 'a', 'b', 'c', 'd', 'e', 'Pu' ]
console.log(pushed, typeof pushed); // 6 'number' = abc.length
```


### *shift*

  * shift - menja original 'abc'

```js
abc = ["a", "b", "c", "d", "e"]
let shifted = abc.shift();
console.log(abc); //  [ 'b', 'c', 'd', 'e' ]
console.log(shifted, typeof shifted); // a string
````

### *unshift*
  
  * unshift - menja original 'abc'

```js
abc = ["a", "b", "c", "d", "e"]
let unshifted = abc.unshift("XxX", "YOY");
console.log(abc); //  [ 'XxX', 'YOY', 'a', 'b', 'c', 'd', 'e' ]
console.log(unshifted, typeof unshifted); // 7 'number' = abc.length
```  
  
---------------------------------------------------------------------------------------------------------

## **RAZNI ALATI**

  * PAZNJA: Alati ispod menjaju original.

```js
var q1 = [1,2,3,4];           // Svi ispod su prakticno reference za 'q1'
var q2 = q1.fill(5,0,1);      // q2 = q1 = [5,2,3,4]
var q3 = q1.sort();           // q3 = q2 = q1 = [2,3,4,5]
var q4 = q3.reverse()         // q4 = q3 = q2 = q1 = [5,4,3,2]
var q5 = q2.copyWithin(1,2,3) // q5 = q4 = q3 = q2 = q1 = [5,3,3,2]
```

### *reverse*

  * reverse ~ mirror MENJA ORIGINAL!

```js
abc = ["a", "b", "c", "d", "e"]
let reversed = abc.reverse();
console.log(abc); //  [ 'e', 'd', 'c', 'b', 'a' ]
console.log(reversed); //  [ 'e', 'd', 'c', 'b', 'a' ]
```

### *fill* 

  * fill ~ repeat() --- cime, od...do. MENJA ORIGINAL!

```js
console.log(abc); //  [ 'e', 'd', 'c', 'b', 'a' ]
let filled = abc.fill('A', 2, 5); console.log(filled); // ['e', 'd', 'A', 'A', 'A']
console.log(abc); // ['e', 'd', 'A', 'A', 'A']
````

### *copyWithin*
  
  * copyWithin --- kopiranje elemenata unutar niza
  * parametri (gde_kopirati, sta_od, sta_do) - "sta_od" standardna vrednost mu je 'abc.length'. MENJA ORIGINAL!

```js
let copied = abc.copyWithin(0, 4, 5); console.log(copied); // [e, b, c, d, e]
```

  * Ne moze da pravi nove elemente u nizu, tj. ne moze da menja .length

### *sort*

  * sort - sortiranje po unikod vrednostima (sve se konvertuje u strignove pa se sortira). MENJA ORIGINAL!

```js
let nizAZ = ['B', 2, 'a', 'c', 'b', 1, 3, 'C', 'A', '.', '!', '?',]
let sorted1 = nizAZ.sort(); console.log(nizAZ); //[!.123?ABCabc]
console.log(sorted1); // [!.123?ABCabc]
// lexikografsko sortiranje brojeva
let niz12 = [22, 2, 3, 1, 11]
let sorted2_1 = niz12.sort(); console.log(sorted2_1); // [1 11 2 22 3]
console.log(niz12); // [1 11 2 22 3]
// sortiranje po vrednosti brojeva
let sorted2_2 = niz12.sort((a, b) => b - a); console.log(sorted2_2); // [22 11 3 2 1]
console.log(niz12); // [22 11 3 2 1]
console.log([1, 2, 3, 4, 5, 6, 7, 8, 9].sort((a, b) => { return 0.5 - Math.random() })); // [4,2,1,3,9,7,5,6,8] - ali ovo je los nacin
```

### *concat* 

  * concat - spajanje nizova. MENJA ORIGINAL!

```js
abc = ["a", "b", "c"]; zxc = ['z', 'x', 'c']; one2 = [1, 2]
let concated = zxc.concat("qwe", one2, abc); console.log(concated); // [z,x,c,qwe,1,2,a,b,c]
console.log("CONCAT: ", zxc, one2, abc); // [z,x,c][1,2][a,b,c]
concated = zxc.concat(); console.log(concated); // [z,x,c] // pravljenje kopije
```

### *includes* 
  
  * includes ~ find - provera da li zadati element postoji u nizu. Varaca Boolean.

```js
// callback f-ja moze da ima 2 parametra: vrednost_elementa, index_pocetka_pretrage. MENJA ORIGINAL!
abc = ["a", "b", "c", "d", "e"]
let included = abc.includes('A')
console.log(included); // false
console.log(abc); // [ 'a', 'b', 'c', 'd', 'e' ]
```

## **FILTRIRANJE POMOCU CALLBACK F-JA**

### *filter*

  * filter - Pravi novi niz filtracijom elemenata zadatog niza, po zadatoj f-ji
  * f-ja moze da ima 4 parametra: vrednost_elementa, index_elementa, pozvani_niz, thisArg (vrednost koja se koristi kao 'this' argument pri pozivanju f-je)

```js
abc = ['YoY', 'XxX', 'A', 'A', 'A', 'YoY', 'XxX']
let filtered = abc.filter(vred_elem => vred_elem.length > 1); // ako cb f-ja bude true, prolazi filter
console.log(abc); // [ 'YoY', 'XxX', 'A', 'A', 'A', 'YoY', 'XxX' ]
console.log(filtered);// [ 'YoY', 'XxX', 'YoY', 'XxX' ]
console.log(abc.filter(ve => ve === 'A')); //[A,A,A]
console.log(abc.filter((ve, ie, niz) => { return niz[ie % 3] === 'A' })); //! [A,YoY]
// ^^^ na pitanje: da li 'YOY' ulazi u novi niz => index od 'YOY' je 5, tj. ie = 5
// a 5%3 = 2 sto znaci da ce biti [2], a element pod indexom 2 je 'A',
// cime se ispunjava uslov za ulazak u novi niz
console.log(abc.filter((x) => { return /[a-z]/.test(x) })); //! [YoY,XxX,YoY,XxX]
abc //! [YoY,XxX,A,A,A,YOY,XxX]
intersekcijaDvaNiza = abc.filter(value => ['A', 'b', 'c', 'd'].includes(value));
console.log(intersekcijaDvaNiza); //! ['A','A','A']
// Kako oznacavati prethodni/sledeci element u nizu
// filter (e, i, a) → [ a[i-1], e, a[i+1] ]
```

### *every* 
  
  * *every* - proverava da li svi elementi mogu da prodju zadatu funkciju. Ako svi prodju, vraca True; ako jedan punke, prekida se provera i vraca False.
  * f-ja moze da ima 4 parametra: vrednost_elementa, index_elementa, pozvani_niz, thisArg (vrednost koja se koristi kao 'this' argument pri pozivanju f-je)

```js
console.log(abc.every(x => x.length > 0 && x.length <= 3)); // true
console.log(abc); //! [YoY,XxX,d,A,A,A,YoY,XxX]
```

### *some*
  
  * some - proverava da li bar jedan element moze da prodje callback f-ju. Vraca boolean
  * callback f-ja moze da ima 4 parametra: vrednost_elementa, index_elementa, pozvani_niz, thisArg (vrednost koja se koristi kao 
  'this' argument pri pozivanju f-je)

```js
const someed = [1, 2, 'qwe', 4, 5].some(ve => ve == '4'); console.log(someed); //! true
```

### *find*

  * find - proverava sve elemente sa callback f-jom, a ako f-ja negde vrati 'true' pretraga se prekida i vraca se vrednost tog elementa.
  * callback f-ja moze da ima 4 parametra: vrednost_elementa, index_elementa, pozvani_niz, thisArg (vrednost koja se koristi kao 'this' argument pri pozivanju f-je)

```js
console.log(abc.find(x => /[Y]/.test(x))); // YOY // sadrzi Y
console.log(abc); //! [YoY,XxX,A,A,A,YoY,XxX]
```

### *findIndex*

  * findIndex - proverava sve elemente sa callback f-jom, a ako f-ja negde vrati 'true' pretraga se prekida i vraca se index tog elementa.

```js
console.log(abc.findIndex((x => /[Y]/.test(x)))) // 5
console.log(abc); //! [YoY,XxX,A,A,A,YoY,XxX]
abc = ['YoY', 'XxX', 'A', 'A', 'A', 'YoY', 'XxX']
```

### *indexOf*

  * indexOf - trazi element, a vraca INDEX OD njega. proverava da li postoji zadati element. Ako ga nadje prkida pretragu i vraca index gde ga je naisao. Ako nije nasao -1
  * Metoda moze da ima 2 parametra: vrednost_elementa, index_pocetka_pretrage

```js
console.log(abc.indexOf('YOY')); // -1 // da sam trazio 'YoY' bilo bi 0
console.log(abc); //! [YoY,XxX,A,A,A,YoY,XxX]
```

### *lastIndexOf*

  * lastIndexOf - isto sto i 'indexOf, ali pretraga se vrsi sa kraja
  * Metoda moze da ima 2 parametra: vrednost_elementa, index_pocetka_pretrage

```js
abc = ['a', 'ss', 'dD', 'F', 'ss']
console.log(abc.lastIndexOf('ss', -2)); //! 1
```

### *flat*

  * flat - svodjenje multi-dimenzionalnih nizova
  * Metoda moze da ima 1 parametar: dubina_svodjenja. Default je 1

```js
num = [1,[2,[3,[4,[5,[6,[7,[8]]]]]]]]
console.log(num.flat(3)); //! [1,2,3,4,[5,[6,[7,[8]]]]]
```

### *flatMap*
  
  * flatMap ~ map+flat

```js  
let arr1 = ["it's Sunny in", "", "California"];
console.log(arr1.flatMap(x => x.split(" "))); //! ["it's","Sunny","in", "", "California"]
// Stara alternativa
console.log(arr1.map(x => x.split(" "))); //! [["it's","Sunny","in"],[""],["California"]]
console.log(arr1.map(x => x.split(" ")).flat(1)); //! ["it's","Sunny","in", "", "California"]
// Primer 2
str2split = 'qwe|asd|zxc&rty|fgh|vbn^uio|jkl&nm|mn'
str2split.split('^') // [ qwe|asd|zxc&rty|fgh|vbn, uio|jkl&nm|mn ]
.flatMap(str=>str.split("&")) // [ qwe|asd|zxc, rty|fgh|vbn, uio|jkl, nm|mn ]
.flatMap(str=>str.split("|")) // [ qwe, asd, zxc, rty, fgh, vbn, uio, jkl, nm, mn ]
// Stara alternativa
str2split.split('^')
.map(str=>str.split("&"))
.flat()
.map(str=>str.split("|"))
.flat()
```

## **REDUCE**

### *reduce*

  * reduce() Sta radi? Reduce() uzma dva susedna elementa niza i nesto uradi sa njima, u zavisnosti od toga sta je definisano u callback funkciji. U sledecem krugu racunanja, ono sto je bio RETURN od prethodne callback funkcije, bice prvi argument u trenutnoj funkciji (zove se akomulator ili prethodna vrednost), a za drugi argument se uzima sledeci element niza (sabirak ili trenutna vrednost).

  * Kada se prvi put startuje callback funkcija tu nema RETURN od prethodne kalkulacije, a treba da ga bude. Ona se moze dodeliti kao drugi argument od reduce() ili kao prvi element niza koji se obradjuje. Najbolja je praksa da se stavlja kao drugi argument od reduce, jer ako se ne stavi onda ce callback funkcija po defaultu uzeti [0] element niza kao pocetnu vrednost a iteracija sabiraka pocinje od [1] elementa (umesto od [0]), sto moze dati neocekivane rezultate.

  * callback f-ja koja ide u reduce moze da ima 4 parametra: akomulator, sabirak, index_sabirka, niz_koji_se_obradjuje

```js
function sabirach(akumulator, sabirak) { return akumulator + sabirak } // callback f-ja
let reduced = niz12.reduce(sabirach); console.log(reduced); //! 39 - vidi ispod objasnjenje
// pocetna vrednost akumulatora je 22, a 1. sabirak je 11, 2. sab. je 3, pa 2, pa 1
console.log(niz12); //! [22,11,3,2,1]

let reduced100 = niz12.reduce(sabirach, 100); console.log(reduced100); //! 139
// pocetna vrednost akumulatora je 100, a 1. sabirak je 22
console.log(niz12); //! [22,11,3,2,1]

let reducedConcat = nizAZ.reduce((a, s) => { return a.concat('*' + s + '*') }, 'QWE*');
console.log(reducedConcat); //! QWE**!**.**1**2**3**?**A**B**C**a**b**c*
// da sam kao pocetnu vrednost stavio [], onda bi return bio array
console.log(nizAZ); //! [!.123?ABCabc]

// evo primera gde se najbolje vidi kako funkcionise reduce()
arr.reduce((a,s)=>{
  console.log(a, s)
  return nan
}, 100)
// Output:
// 100 1
// NaN 2
// NaN 3
// NaN 4
// NaN 5

// ovo je jedan moj primer funkcije koja komparira da li je prvi parametar jednak sa ostalim parametrima, a izmedju svake komparacije je OR. Znaci dovoljno samo jedan da je TRUE i vratice TRUE
function equalOr(x, ...vals) {
  c = [];
  vals.reduce((a, s) => {
    c.push(a == s)
    return a
  }, x)
  return c.some(e=>e==true)
}
equalOr(q, w,e,q)
```

### *reduceRight*

  * reduceRight---Isto sto i 'reduce' samo sto pocinje sa kraja

```js  
let reduceRighted = [[0, 1], [2, 3], [4, 5], [6, 7], [8, 9]].reduceRight((aku, sab) => aku.concat(sab));
console.log(reduceRighted); //! [8, 9, 6, 7, 4, 5, 2, 3, 0, 1]
```

### *PRIMENA REDUCE-a:*

  * *brojanje slova*

```js
var brojanjeSlova = "qwe qe e"
  .split("") // [q,w,e, ,q,e, ,e]
  .reduce ((rezultat, slovo)=>{
  if (slovo in rezultat) rezultat[slovo]++
  else rezultat[slovo]=1
  return rezultat
  }, {}) // bitno je koristiti {} kao pocetni objekat da bi i prvo slovo proslo kroz cb fju
console.log (brojanjeSlova) // {q:2, w:1, e:3, " ":2}
```

  * *Grupisanje objekata po svojstvu "prosek"*

```js
function grupisi(obAR, propOB) {
  return obAR.reduce( (acc, objSab) => {
    let key = objSab[propOB]
    if (!acc[key]) {
      acc[key] = []
    }
    acc[key].push(objSab)
    return acc
  }, {})
}
console.log(grupisi(psi, 'god'))
/* Object {}
1: Array [ {…} ]
10: Array [ {…} ]
40: Array [ {…} ]
60: Array [ {…} ]
200: Array [ {…} ] 
} */
```

  * sakupljanje svih nadimaka pasa na jednu gomilu

```js  
function sviNadimci (obj, prop) {
  return obj.reduce((rez, trenObj) => {
    return [...rez, ...trenObj[prop]]
  }, [])
}

sviNadimci(psi, "nadimci") // [ Beki, Čupi, Pufi, Lizača, Vuki, Vule, Matori, Legenda, Šari, Šarpi, … ]


```

## **MAP** 

### *map*

  * map - Slicno kao forEach, samo sto pravi novi Array, a ne menja original
  * otvara se svaki element niza, nesto mu se uradi i pravi se novi niz.
  * callback f-ja moze da ima 3 parametra: vrednost_elementa, index_elementa, pozvani_niz
```js
// npr. [6,5,4].map(v, i, n) // ← neparvilan, jednostavan zapis
//  1. krug: v=6, i=0, n=[6,5,4]
//  2. krug: v=5, i=1, n=[6,5,4]
//  3. krug: v=4, i=2, n=[6,5,4]
// console.log(one2) //! [1,2]
let maped = one2.map(x => x + 10); console.log(maped); //! [11,12]
let maped2 = zxc.map(x => x.toUpperCase()); console.log(maped2); //! [Z,X,C]
// console.log(one2) //! [1,2]
let arrObj = [{ qqq: 1, www: 2, eee: 3 }, { aaa: 4, sss: 5, ddd: 6 }] // [{}, {}]
let maped3 = arrObj.map(x => (x.qqq + x.www) * x.eee); console.log(maped3); //! [9,NaN]
````

### *forEach*

  * forEach - Izvrsava se callback f-ja nad svakim elementom. !!! Radi samo sa Array + ne moze da radi sa praznim elementima niza. forEach ne menja Array, ali c.b. f-ja moze da ga promeni. Ne mora da ima return (primer 1), osim ako mu ne kazes (primer 2). Sporija od .map.

  * callback f-ja moze da ima 4 parametra: vrednost_elementa, index_elementa, pozvani_niz, thisArg (vrednost koja se koristi kao 'this' argument pri pozivanju f-je)

```js 
// Primer 1
zxc = ["z", "x", "c"]
let foreacher = zxc.forEach(x => console.log(x));// undefined - svaki element od "zxc" je bacen u console.log(), a povratna informacija za "foreacher" je nista, undefined.

// Primer 2
one2 = [1, 2]
one2.forEach((num, index) => {
  return one2[index] = num * 2;
});
one2 // [2, 4] - svaki element od "one2" je pomnozen sa 2.

// Primer 2.1 - Sa .map bi to izgledalo ovako:
one2 = one2.map((num, index) => {
  return one2[index] = num * 2;
})
one2 // [2, 4]

// Primer 3
d = {}
arr = 'qwertyuiopasdfghjklzxcvbnm'.split('') // [q, w, e, r, ...]
arr.forEach((q) => {
    d[q] = undefined
})
d // {q:undef., w:undef., e:undef., r:undef., ...}
````

## **PAKOVANJE U STRING**

### *toString*

  * *toString* - ne pretvara u String, nego ga samo prikazuje kao String. 
  * Ako hocu da ga pretvorim, moram taj prikaz da snimim u neku novu promenljivu.

```js
abc; //! [YOY,XxX,A,A,A,YOY,XxX]
abc.toString(); //! YOY,XxX,A,A,A,YOY,XxX
abc; //! [YOY,XxX,A,A,A,YOY,XxX]
```

### *join*

  * join - Spaja elemente nizolikog objekta u String.
  * To radi pomocu dopisivanja (konkatenacija).

```js  
elements = ['Fire', 'Air', 'Water'];
elements.join() // "Fire,Air,Water"
elements.join('') // "FireAirWater"
elements.join('-') // "Fire-Air-Water"
elements // ne promenjeno - ['Fire', 'Air', 'Water']
```

## **ARRAY PROTOTYPE**

### *Array()*

  * Array "constructor" je metoda koja sluzi za pravljenje novih nizova. Array() u sebi sadrzi jos neke sub-metode. Array, bez zagrada, je Objekat Array, koji u sebi, pod "prototype.constructor" sadrzi metodu Array()

```js
arrayed = Array(2); // [ undefined, undefined ], length: 2
arrayed = Array(2, 3, 'q', []); //! [ 2, 3, 'q', [] ]
arrayed = [2,3,'q',[]] // isto kao gore ali literal
console.log(Array.prototype.constructor==Array) // T
console.log(Array.constructor==Array) // F *ovo je konstruktor za f-ju.
````
### *Array.of()*

  * Array.of() - Ako se unosi vise parametara onda je isto kao i "constructor", ali ako se unese samo jedan parametar onda se vidi razlika:

```js
arrayed = Array.of(3); // [ 3 ], normalan niz sa jednim elementom '3', length: 1
arrayed = Array(3); // [ <3 empty slots> ]
````

### *Array.from()*

  * Array.from() - Pravi niz od necega sto je nizolikog oblika (str, arr, Map, Set) ili od iteratora.
  * Metoda moze da ima 3 parametra: {izvor_od_cega_ce_da_se_pravi_niz}, map_f-ja, thisArg (vrednost koja se koristi kao 'this' argument pri pozivanju map f-je).
  * https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from

```js
let nizAZ_2 = Array.from(nizAZ); // Pravljenje novog niza na osnovu postojeceg (kopiranje)
let arrayedFrom = Array.from(5); // prazan niz, length = 5
Array.from(Array(5).keys()) // [0,1,2,3,4] - Array(5).keys() je Array iterator. Od indexa su napravljene vrednosti. 
Array.from(Array(6).keys()).slice(1) // [1,2,3,4,5] - moj naziv za ovo je AFAKS (pocetna slova funkcija)
// Array.from(obj, mapFn, thisArg)
// has the same result as Array.from(obj).map(mapFn, thisArg),
// except that it does not create an intermediate array.
```

### *Array.isArray()*
  
  * Array.isArray() - proverava da li je niz

```js
let isArrayed = ['e'] + 'Q'; console.log(isArrayed); //! eQ
console.log(Array.isArray(isArrayed)); //! false
```

```js
arr = [1,2]
arr['qwe']=4 // dodavanje asocijativnog elementa
arr[Symbol('asd')]=999 // dodavanje simbol elementa
delete Symbol // ne moze biti obrisan, iako prijavljuje "true" tj. da je obrisan.
Array.isArray(arr) // true [1,2] // kad se "otvori" niz onda se vide i ostali elementi (asoc. i sym.)
```

```js
// drugi nacin da se proveri da li je "str" string:
str = 'qwe'
typeof str === "string" // true
```

###  *Array.entries*

  * Array.entries - Vraca iteraciju u obliku [kljuc, vrednost].

```js
var array1 = ['a', 'b', 'c'];
var iterator1 = array1.entries(); // to sto vraca se zove Array Iterator (a,b,c)
console.log(iterator1.next().value); // Array [0, "a"]
console.log(iterator1.next().value); // Array [1, "b"]
var entriesFromArr = Array.from(iterator1)
console.log(entriesFromArr); //! [[0,"a"], [1,"b"], [2,"c"]]
```
`
### *Array.keys*

  * Array.keys - vrace ITERATOR kljuceva (ako je Array onda su to indexi)
```js
console.log(nizAZ_2); //! [ '.', 1, 2, 3, '?', 'A', 'B', 'C', 'a', 'b', 'c' ]
console.log(Array.from(nizAZ_2.keys())); //! [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
// Kod objekta moze da se koristi za vracanje duzine objekta (posto objekat nema "length" attribut) - Object.keys(qwe).length
```

### *manje bitne stvari*

Array.name // "Array" - zamrznuta vrednost  

arr = []  
arr.constructor.name === 'Array' ? 1:0 // 1
Object.isFrozen(arr.constructor.name) // true

// prototype: Array [] // tu se nalaze sve metode vezane za Array ('seckanja', 'razni alati', 'filteri', map, reduce). ?Sto znaci ja kad pozivam neku metodu za Array, ja zapravo pozivam prototip?