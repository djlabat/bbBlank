# FUNCTION

## SKRACENI NACIN PISANJA METODA

```js
  const bicycle = {
    gear: 2,
    setGear(newGear) { // umesto    setGear: function (newGear) {...} // izbaceno je ": function"
      this.gear = newGear;
    }
  };
```

## ARGUMENTS

  * Arguments je poseban objekat koji je sastavni deo f-je.

```js
  Arguments { 0: 4, 1: 2, 2: 7, … }
````
  * Vise mi lici na Array, ali po metodama koje su mu na raspolaganju nije.  
  Nekada je bio sastavni deo Function objekta ali to je prevazidjeno.

```js
  function func1(a, b, c) {
    console.log(arguments[0]); // 4
    console.log(arguments[1]); // 2
    console.log(arguments[2]); // 7
  }

  func1(4, 2, 7);
```


### *length*

  * prikazuje broj parametara koji se ocekuje od f-je

```js
  function func1() {} // 0
  function func2(a, b) {} // 2
  function func3(a, b, c=1) {} // 2 - Zasto 2, kad ima tri? Treci nije obavezan pa se ne ubraja.
```


### *name*

  * prikazuje ime funkcija. Ako nema ime onda je 'anonymous' ili ''

```js
  const func1 = function() {}
  const object = {func2: function() {} }
  function func3(){}
  const func4 = () => {}

  console.log(func1.name) // "func1"
  console.log(object.func2.name) // "func2"
  console.log(func3.name) // "func3"
  console.log(func4.name) // "func4"
```

## **METHODS**


### *apply*

  * zove f-ju sa zadanom vrednoscu 'this' (prvi parametar), a ostali parametri su niz ili nesto nizoliko.
  * Prvi parametar: The value of this provided for the call to func. Note that this may not be the actual value seen by the method: if the method is a function in non-strict mode code, null and undefined will be replaced with the global object, and primitive values will be boxed. This argument is required.

```js
numbers = [5, 6, 2, 3, 7];

max = Math.max.apply(null, numbers) // 7
min = Math.min.apply(undefined, numbers) // 2
min = Math.min.apply(numbers, numbers) // 2
min = Math.min.apply(Number, numbers) // 2
min = Math.min.apply(Boolean, numbers) // 2
min = Math.min.apply(String, numbers) // 2
min = Math.min.apply('', numbers) // 2
min = Math.min.apply(qwe, numbers) // 2

// .apply se ranije koristio u slucaju kad hoces da spojis dva niza, pri tome da trajno promenis prvi niz. Danas se koristi u te svrhe ...rest.
const array = ['a', 'b']; // prvi probni niz
const elements = [0, 1, 2]; // drugi probni niz
// console.log(array.push(elements)) // array = ["a", "b", [ 0, 1, 2 ] ] / ne uspeli pokusaj jer je elements ubacen u celini
// console.log(array+elements) // [ a, b0, 1, 2 ] / neuspeli pokusaj spajanja
console.log(array.concat(elements)) // ["a", "b", 0, 1, 2] / radi zadatak ali pravi novi niz, ne edituje array
array.push.apply(array, elements) // array = ["a", "b", 0, 1, 2]
console.log(elements) // [ 0, 1, 2 ]

// .caller - prevazidjeno
// .displayName - ne preporucuje se koriscenje
```

## CONSTRUCTOR

  * constructor: Function() // Svaka funkcija u JS-u je Function Object  
  (function(){}).constructor === Function // true