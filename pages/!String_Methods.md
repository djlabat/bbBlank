# STRING METODE

## SADRZAJ:  
[SECKANJA](#seckanja)  
[PRETRAGA KORISCENJEM INDEX-A](#pretraga-koriscenjem-index-a)  
[PRETRAGA KORISCENJEM UNICODE VREDNOSTI](#pretraga-koriscenjem-unicode-vrednosti)  
[RAZNI ALATI](#razni-alati)  
[CESTO KORISCENO ALI ZAPISANO NA DRUGI NACIN](#cesto-korisceno-ali-zapisano-na-drugi-nacin)  
[PROVERE SADRZAJA](#provere-sadrzaja)  
[PREVAZIDJENE METODE](#prevazidjene-metode)  

---

## ! Paznja !
Sve metode za String NEmenjaju original.  

---

## Promenljive koje se koriste u primerima u fajlu

```js
var abc = "abcdefghijklmnopqrstuvwxyz";  
var esc = 'I don\'t \n know';  
var QWE = 'QWERTY';
var num = 128;
var s_t_r = "     a,  s,   d,  f  f   f,    ";
```

---------------------------------------------------------------------------------------------------------

## **SECKANJA**

### *slice* 

  * slice ~ isecak (od index-a, do indexa) ---negativne vrednosti broji od kraja. Varaca String.  

```js
abc.slice(3, 6)   // def
abc.slice(20)     // uvwxyz
abc.slice(-3)     // xyz
abc.slice(-3, -2) // x 
```



### *substring*

  * substring ~ isecak (od index-a, do indexa) ---parametar ne moze da ima negativne vrednosti . Varaca String.

```js
abc.substring(5, 7)   // fg
abc.substring(13, 0)  // abcdefghijklm
abc.substring(13)     // nopqrstuvwxyz
```

### *substr*

  * substr ~ isecak (od index-a, duzina) ---2. parametar, ne moze da bude ngativan. Ako ga nema, ide do kraja (najvaceg indexa). Varaca String.

```js
abc.substr(5, 7)  // fghijkl
abc.substr(-5)    // vwxyz
abc.substr(5)     // fghijklmnopqrstuvwxyz
abc.substr(5,-7)  // '' 
```

### _↑ PAZNJA: Zajednicko za slice, substring i substr je da: ako nemaju 2. parametar, idu do kraja !_

--------

### *split*

  * split ~ string => array (sta ce da bude znak za secenje)

```js
"a,s,d".split(",") 	// [ "a", "s", "d"] - splitting a string on commas gives an array.
"a,s,d".split("")   // [ "a",  ",",  "s",  ",",  "d" ] - splitting on characters
"a,s,d".split()     // [ "a,s,d" ] - Ako nema "," onda vraca Array [ abc ]. Qukka prikazuje s___space kao s_space sto nije realno. za tacan prikaz Ctrl+Shift+U (OUTPUT)
```

### *trim*

  * trim ~ brise prazan prostor

```js
s_t_r.trim()      // skida space ispred i iza stringa.
s_t_r.trimStart() // uklanja prazne prostore pre stringu
s_t_r.trimLeft()  // -------------- || -----------------
s_t_r.trimEnd()   // uklanja prazne prostore posle stringu
s_t_r.trimRight() // -------------- || -------------------
```

---

## **PRETRAGA KORISCENJEM INDEX-A**

### *indexOf, lastIndexOf, charAt*

```js
abc.indexOf("lmmno", 5)  // 11 - 'l' se nalazi na 11. indexu. Ako ne nadje nigde substring 'lmno' onda vraca -1 // Pretragu je poceo od 5.indexa (slovo 'f')
abc.lastIndexOf("lmno")  // 11 - last occurance
abc.charAt(2)            // character at index: "c"
```

---

## **PRETRAGA KORISCENJEM UNICODE VREDNOSTI**

```js
abc.codePointAt(2)         // 99 - result is codePoint at index 2 (witch is 'c')
String.fromCharCode(99)    // c  - Convert a Unicode number into a character
// abc.charCodeAt(2)          // 99 - deprecated - simalar to codePointAt, but older. Incorect results with higher codes, above 255
// Ako cu da radim sa emojima onda NEkoristiti charCodeAt vec codePointAt ili fromCodePoint
```

---

## **RAZNI ALATI**
```js
abc.replace("abc", "123")  // 123defghi... - find and replace, takes regular expressions (/abc/g, '123'), and callback
s_t_r.replaceAll("f", "X") // "     a,  s,   d,  X  X   X,    "; - svako "f" zamenuje sa "X"
s_t_r.replaceAll(/f/g, (asd)=>asd.toUpperCase()) // Prvi param. ako je RegExp, mora se koristiti sa "g" - global
abc.toUpperCase()          // ABCDEF... - convert to upper case
"QWERTY".toLowerCase()     // qwerty - convert to lower case
'qwe '.repeat(3)           // qwe qwe qwe
"a".localeCompare("b")     /* -1 - poredi dva stringa koji je veci (po Unicode). Pitanje koje se kroz ovu komandu postavlja JS-u je: Da li je "a" . pre ili posle ("b"). Odgovor koji se dobija je -1 (pre) ili 1 (posle) ili 0 (jednaki su). Primeri za rezultat -1:  "a".loc...("aa"), a...A, "aba"..."aba ";
Primeri za 1: a...!@#$ 123 '' ' '. Kao sortiranje fajlova po imenu, pa koji ide pre, a koji posle */
'501'.padStart(10, '*')    // *******501 ili '0' => 0000000501
'064'.padEnd(10, '*')      // 064*******
"Čiča".normalize("NFC")    // Čiča - returns the Unicode Normalization Form of the string   . Slova "Č" i "č" se sastoje iz dva koda i kucaju na srpskoj tastaturi na sledeci nacin: "Č" = AltGr+2, Shift+C ; "č" = AltGr+2, C ; Ova metoda služi za to da pretvori ovakva slova u unikod slovako hocu da ih pretvorim u unikod slova tj . jendo slovo jedan kod                                            . https://developer   . mozilla                                                             . org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize
eval('1+2'); eval('"qwqe".toUpperCase()') // 3; QWQE - posmatra string kao kod - !Nekoristiti u\ produkciji. Takodje postoji i komanda uneval() (pretvara kod u string), ali skoro da je ni jedan browser ne podrzava (2020 / Jul).
```

---

## **CESTO KORISCENO ALI ZAPISANO NA DRUGI NACIN**

```js
num.toString(16)         // number to hex(16), octal (8) or binary (2). Ne moze odmah da pretvori broj u string (npr. 128.toString), nego mora preko promenljive ili preko konctruktora za broj (Number(128).toString(16))
abc.concat(QWE)          // abc + QWE
abc[2]		               // "c" - moguce je citanje vrednosti, ali promena vrednosti je ne moguca jer je string imutabilan.
String.raw`C:\Development\profile\aboutme.html`; // C:\Development\profile\aboutme.html - pisanje "prirodnog" stringa, kako je napisano tako će i izaći, bez \escape karaktera. Ovo je literalni nacin pisanja, koji se najvise i koristi.
abc.length               // 26 - string length
num.valueOf()            // 128
```

---

## **PROVERE SADRZAJA**

```js
abc.startsWith("A")  // false - proverava da li 'abc' pocinje sa "A"
abc.endsWith("z") // true - proverava da li 'abc' zavrsava sa "z"
abc.includes("jk l")  // false - proverava da li 'abc' sadrzi "jk l"
"İstanbul".toLocaleLowerCase('tr') // i̇stanbul - Konverzija po turskom. Tursko "i" !== Englesko "i". Generally, this method returns the same result as the toLowerCase() method. However, for some locales, where language conflict with the regular Unicode case mappings occurs (such as Turkish), the results may vary. 
```

--------------------------------------------------------------------------------

### _↑ PAZNJA: *'abc' izvorni je ostao isti. Nista ga od gornjih metoda nije promenilo. Zato sto je string nepromenljiv! Mozes ga prikazati na drugi nacin, mozes taj drugi nacin snimiti u drugu var. ali onaj osnovni je ne promenljiv._
-----------------------------------

## **PREVAZIDJENE METODE**
.big .blink .bold .fixed .italics .strike

---

## **Funkcija za konverziju Decimalnog coda u surrogate code**
Javascript uses UTF-16 internally
```
function toUTF16(codePoint) { // codePoint = 128512
  var TEN_BITS = 0b1111111111;
  function u(codeUnit) {
    return '\\u'+codeUnit.toString(16).toUpperCase();
  }

  if (codePoint <= 0xFFFF) {
    return u(codePoint);
  }
  codePoint -= 0x10000;

  // Shift right to get to most significant 10 bits
  var leadSurrogate = 0xD800 + (codePoint >> 10);

  // Mask to get least significant 10 bits
  var tailSurrogate = 0xDC00 + (codePoint & TEN_BITS);

  return u(leadSurrogate) + u(tailSurrogate);
}
toUTF16(128512) // "\\uD83D\\uDE00" → smajli
console.log("\uD83D\uDE00")
```