- Ako hocu da vidim koje parametre koristi neka f() u konzoli, kucem: \_.funkcija // bez zagrade
- NaN == NaN // T
- Predicate = f-ja koja vraca Boolean
- \_.identity = (e)=\>e
- iterratee = cbFn() koja se koristi kao parametar (npr. pri upetrebi high-order f-ja: filter, sort. match...)
- collection = Collection functions work on arrays, objects, and array-like objects such as arguments, NodeList and similar. But it works by duck-typing, so avoid passing objects with a numeric length property. **Duck typing** in computer programming is an application of the [duck test](https://en.wikipedia.org/wiki/Duck_test)—"If it walks like a duck and it quacks like a duck, then it must be a duck"—to determine whether an [object](https://en.wikipedia.org/wiki/Object_(computer_science)) can be used for a particular purpose.
- source = argument na osnovu kojeg se pravi f-ja ( može biti Boolean, Number, String, Date, RegExp, Object ili Array )
- \_......By = Sve f-je kojima se naziv zavrsava sa By, prvi argument im je iterator (Array|Object), a drugi parametar je iterratee tj. DEFINICIJA f-je, ne poziv(), kojom će se obaviti to što treba da se obavi.



izbegavati ucitavanje celog lodash-a, nego bolje ovako:

import chain from 'lodash/chain';

import value from 'lodash/value';

import map from 'lodash/map';

import mixin from 'lodash/mixin';

import \_ from 'lodash/wrapperLodash';

mixin(\_, {

map: map,

value: value,

chain: chain

}

i onda normalno koristim te funkcije koje sam importovao.

# Najkorisnije metode:

[isEqual](#_heading=h.1ksv4uv) ili eq. Za poredjenje objekata

[isEmpty](#_heading=h.35nkun2) // null, undefined, [], {} → true JS: Object.keys(obj1).length === 0

[get](#_heading=h.z337ya)(psi, '0.ime') // „Bela"; \_.get(psi, '1.nadimci.3') // „Legenda"

// ako ne nadje, ne pravi gresku nego vraca definisanu vrednost npr „" // JS: this?.sdf || „")

\_.get(psi, '100'., "NEMA!") // "NEMA!"

[sortBy](#_heading=h.3rdcrjn)

\_.sortBy(restorani.results, e =\> e.rating ) // [{1}, {2}, {3}, {4}, {5}]

\_.sortBy(restorani.results, e =\> - e.rating ) // 5,4,3,2,1

[union](#_heading=h.4d34og8) // spajanje nizova bez da ponavlja vrednosti koje su iste u oba niza.

[cloneDeep](#_heading=h.lnxbz9)psiClone = \_.cloneDeep(psi)// duboko kopiranje objekata

[debounce](#_heading=h.26in1rg) // \_.debounce( () =\>{console.log('test') }, 1000); // „test" – posle 1s

[assign](#_heading=h.2jxsxqh)

Izbacivanje iz niza, sa i bez promene niza // pull – difference

Brisanje na pocetku i kraju niza, bez promene niza // drop i dropRight

sa promenom niza //

Brisanje od – do indexa // slice

# Array

- [\_.](#_heading=h.2et92p0)[chunk](#_heading=h.2et92p0)// secka na grupe odredjen velicine
- [\_.](#_heading=h.tyjcwt)[compact](#_heading=h.tyjcwt) // remove falshy
- [\_.](https://lodash.com/docs/#concat)[concat](https://lodash.com/docs/#concat) // spajanje svega u niz
- [\_.](https://lodash.com/docs/#difference)[difference](https://lodash.com/docs/#difference)// 1. Array - 2. Array // ne menja original
- [\_.](https://lodash.com/docs/#differenceBy)[differenceBy](https://lodash.com/docs/#differenceBy)// pre oduzimanja elemenata iz prvog Array-a napravi se iterator pomocu neke funkcije za oba niza, pa se onda ta dva iteratora porede tj. oduzimaju, a na kraju se vracaju originalne vrednosti iz niza, pre iteratora.
- [\_.](https://lodash.com/docs/#differenceWith)[differenceWith](https://lodash.com/docs/#differenceWith)// koristi se komparator \_.isEqual. Dobro je za: iz [niza] uklanjanje {objekata}/[nizova] koji su isti.
- [\_.](https://lodash.com/docs/#drop)[drop](https://lodash.com/docs/#drop) // brise x elementa sa leve strane; arr.slice(x) // brise do x indexa
- [\_.](https://lodash.com/docs/#dropRight)[dropRight](https://lodash.com/docs/#dropRight) // brise x elementa sa desne strane
- [\_.](https://lodash.com/docs/#dropRightWhile)[dropRightWhile](https://lodash.com/docs/#dropRightWhile) // brise elemente sa desne strane, sve dok f() vraca true
- [\_.](https://lodash.com/docs/#dropWhile)[dropWhile](https://lodash.com/docs/#dropWhile) // brise elemente sa leve strane, sve dok f() vraca true
- [\_.](https://lodash.com/docs/#fill)[fill](https://lodash.com/docs/#fill)// arr.fill()
- [\_.](#_heading=h.3dy6vkm)[findIndex](#_heading=h.3dy6vkm) (niz\_ili\_str, cbFun(), index\_od) ;\_.findIndex(['a','b','c','d','e'], v=\>v=='c' ) // 2 ; \_.findIndex('qwerty', v=\>v=='r' ) // 3
- [\_.](https://lodash.com/docs/#findLastIndex)[findLastIndex](https://lodash.com/docs/#findLastIndex)
- [\_.](https://lodash.com/docs/#head)[first -\> head](https://lodash.com/docs/#head)
- [\_.](https://lodash.com/docs/#flatten)[flatten](https://lodash.com/docs/#flatten)
- [\_.](https://lodash.com/docs/#flattenDeep)[flattenDeep](https://lodash.com/docs/#flattenDeep)
- [\_.](https://lodash.com/docs/#flattenDepth)[flattenDepth](https://lodash.com/docs/#flattenDepth)
- [\_.](https://lodash.com/docs/#fromPairs)[fromPairs](https://lodash.com/docs/#fromPairs)// ([['a', 1], ['b', 2]]);// =\> { 'a': 1, 'b': 2 }
- [\_.](https://lodash.com/docs/#head)[head](https://lodash.com/docs/#head) // vraca 1. elm niza
- [\_.](https://lodash.com/docs/#indexOf)[indexOf](https://lodash.com/docs/#indexOf)
- [\_.](https://lodash.com/docs/#initial)[initial](https://lodash.com/docs/#initial) // vraca sve osim poslednjeg elm niza
- [\_.](https://lodash.com/docs/#intersection)[intersection](https://lodash.com/docs/#intersection) // presek skupova; vraca zajednicko // ( [2, 1],[2, 3]) →  [2]
- [\_.](https://lodash.com/docs/#intersectionBy)[intersectionBy](https://lodash.com/docs/#intersectionBy) \\
- [\_.](https://lodash.com/docs/#intersectionWith)[intersectionWith](https://lodash.com/docs/#intersectionWith)
- [\_.](https://lodash.com/docs/#join)[join](https://lodash.com/docs/#join)
- [\_.last](#_heading=h.1t3h5sf)[// isto sto i \_.initial // Vraca sve osim poslednjeg elm niza](#_heading=h.1t3h5sf)
- [\_.](https://lodash.com/docs/#lastIndexOf)[lastIndexOf](https://lodash.com/docs/#lastIndexOf)
- [\_.](https://lodash.com/docs/#nth)[nth](https://lodash.com/docs/#nth), (arr, 3) → 4 // isto sto i arr[3]
- [\_.](https://lodash.com/docs/#pull)[pull](https://lodash.com/docs/#pull)(arr, 1,3) → [2, 4, 5] / Izbacuje SVE 1 i 3. Menja orig.
- [\_.](https://lodash.com/docs/#pullAll)[pullAll](https://lodash.com/docs/#pullAll)(arr, [1,3]) → koristi niz // kao difference ali menja original.
- [\_.](https://lodash.com/docs/#pullAllBy)[pullAllBy](https://lodash.com/docs/#pullAllBy)
- [\_.](https://lodash.com/docs/#pullAllWith)[pullAllWith](https://lodash.com/docs/#pullAllWith)
- [\_.](https://lodash.com/docs/#pullAt)[pullAt](https://lodash.com/docs/#pullAt)(arr, [1,3]) →[1,3,5] // koristi indexe
- [\_.](https://lodash.com/docs/#remove)[remove](https://lodash.com/docs/#remove) // kao filter, ali menja original
- [\_.](https://lodash.com/docs/#reverse)[reverse](https://lodash.com/docs/#reverse)
- [\_.](https://lodash.com/docs/#slice)[slice](https://lodash.com/docs/#slice)
- [\_.](https://lodash.com/docs/#sortedIndex)[sortedIndex](https://lodash.com/docs/#sortedIndex)([30, 50], 40) → 1 // Govori mi da 40 treba da se ubaci na index 1 da bi se odrazo red u nizu - to je binarne pretraga
- [\_.](https://lodash.com/docs/#sortedIndexBy)[sortedIndexBy](https://lodash.com/docs/#sortedIndexBy)// isto kao gore, ali radi sa :vrednostima nekog svojstva: u [{nizu}, {objekata}]
- [\_.](https://lodash.com/docs/#sortedIndexOf)[sortedIndexOf](https://lodash.com/docs/#sortedIndexOf)// isto kao IndexOf ali radi binarnu pretragu
- [\_.](https://lodash.com/docs/#sortedLastIndex)[sortedLastIndex](https://lodash.com/docs/#sortedLastIndex)// \_.sortedLastIndex([4, 5, 5, 5, 6], 5) // posledenje mesto gde moze da stane 5
- [\_.](https://lodash.com/docs/#sortedLastIndexBy)[sortedLastIndexBy](https://lodash.com/docs/#sortedLastIndexBy)
- [\_.](https://lodash.com/docs/#sortedLastIndexOf)[sortedLastIndexOf](https://lodash.com/docs/#sortedLastIndexOf)
- [\_.sortedUniq](https://lodash.com/docs/#sortedUniq)// \_.sortBy(\_.uniq([3,1,2,3,2]) ) // [1,2,3]
- [\_.sortedUniqBy](https://lodash.com/docs/#sortedUniqBy)
- [\_.tail](https://lodash.com/docs/#tail)(arr) // [2,3,4,5]
- [\_.take](https://lodash.com/docs/#take) // \_.take([a,b,c,d,e], 3) // [a,b,c] // uzima odredjeni broj elemenata od pocetka tj. sa leva
- [\_.takeRight](https://lodash.com/docs/#takeRight) // uzima odredjeni broj elemenata od kraja tj. sa desna
- [\_.takeRightWhile](https://lodash.com/docs/#takeRightWhile)
- [\_.takeWhile](https://lodash.com/docs/#takeWhile)
- [\_.](https://lodash.com/docs/#union)[union](https://lodash.com/docs/#union)([2], [1, 2]); →  [2, 1] // spajanje I uklanjanje viska
- [\_.](https://lodash.com/docs/#unionBy)[unionBy](https://lodash.com/docs/#unionBy)
- [\_.](https://lodash.com/docs/#unionWith)[unionWith](https://lodash.com/docs/#unionWith)
- [\_.](https://lodash.com/docs/#uniq)[uniq](https://lodash.com/docs/#uniq)([2, 1, 2]); →  [2, 1] // uklanjanje viska
- [\_.uniqBy](https://lodash.com/docs/#uniqBy)
- [\_.uniqWith](https://lodash.com/docs/#uniqWith)
- [\_.unzip](https://lodash.com/docs/#unzip)
- [\_.unzipWith](https://lodash.com/docs/#unzipWith)
- [\_.](https://lodash.com/docs/#without)[without](https://lodash.com/docs/#without)([2, 1, 2, 3], 1, 2) → [3]
- [\_.](https://lodash.com/docs/#xor)[xor](https://lodash.com/docs/#xor) ([2, 1], [2, 3]); → [1, 3]
- [\_.xorBy](https://lodash.com/docs/#xorBy)
- [\_.xorWith](https://lodash.com/docs/#xorWith)
- [\_.](https://lodash.com/docs/#zip)[zip](https://lodash.com/docs/#zip)(['a', 'b'], [1, 2], [true, false]);→  [['a', 1, true], ['b', 2, false]]
- [\_.](https://lodash.com/docs/#zipObject)[zipObject](https://lodash.com/docs/#zipObject)(['a', 'b'], [1, 2]); → { 'a': 1, 'b': 2 }
- [\_.](https://lodash.com/docs/#zipObjectDeep)[zipObjectDeep](https://lodash.com/docs/#zipObjectDeep)(['a.b[0].c', 'a.b[1].d'], [1, 2]); →  { 'a': { 'b': [{ 'c': 1 }, { 'd': 2 }] } }
- [\_.](https://lodash.com/docs/#zipWith)[zipWith](https://lodash.com/docs/#zipWith)([1, 2], [10, 20], [100, 200], function(a, b, c) { return a + b + c }); → [111, 222]

# Collection

- [\_.](#_heading=h.2s8eyo1)[countBy](#_heading=h.2s8eyo1)[// brojanje elemenata u nizu // ([6,4,4]) =\> {„6":1, „4":2} // ([„qwerty", „asd", „zxc"], „length") =\> {„6":1, „3":2}](#_heading=h.2s8eyo1)
- [\_.each -\> forEach](https://lodash.com/docs/#forEach)
- [\_.eachRight -\> forEachRight](https://lodash.com/docs/#forEachRight)
- [\_.every](https://lodash.com/docs/#every)
- [\_.filter](https://lodash.com/docs/#filter)
- [\_.find](https://lodash.com/docs/#find)
- [\_.findLast](https://lodash.com/docs/#findLast)
- [\_.flatMap](https://lodash.com/docs/#flatMap)
- [\_.flatMapDeep](https://lodash.com/docs/#flatMapDeep)
- [\_.flatMapDepth](https://lodash.com/docs/#flatMapDepth)
- [\_.forEach](https://lodash.com/docs/#forEach)
- [\_.forEachRight](https://lodash.com/docs/#forEachRight)
- [\_.groupBy](#_heading=h.17dp8vu)[// grupisanje po oderdjenom kriterijumu // ([1,34,23,6,5], (e)=\> e%2==0 ?"par" : "nepar") =\>{ nepar: [1, 23, 5], par: [34, 6] } // \_.groupBy(\_.words(lorem), \_.head) // =\> praljenje recnika](#_heading=h.17dp8vu)
- [\_.includes](https://lodash.com/docs/#includes)
- [\_.invokeMap](https://lodash.com/docs/#invokeMap)
- [\_.keyBy](https://lodash.com/docs/#keyBy)
- [\_.map](https://lodash.com/docs/#map)
- [\_.orderBy](https://lodash.com/docs/#orderBy)
- [\_.partition](https://lodash.com/docs/#partition) // deli Array na dva podniza. Uslov podelel je predikat f-ja. \_. partition([1,34,23,6,5], (e)=\> e%2==0) // =\> [[34, 6], [1, 23, 5] ] // ← podela na parne i neparne
- [\_.reduce](https://lodash.com/docs/#reduce)
- [\_.reduceRight](https://lodash.com/docs/#reduceRight)
- [\_.reject](https://lodash.com/docs/#reject) \*obrnuto od filter
- [\_.](https://lodash.com/docs/#sample)[sample](https://lodash.com/docs/#sample)(qwe) // e(,w,y,w,e,y,e…) | (arr) // 3(,1,5,4,2…)
- [\_.](https://lodash.com/docs/#sampleSize)[sampleSize](https://lodash.com/docs/#sampleSize)(qwe,2) // ["y","r"] (, ["w", "t"]…)
- [\_.shuffle](https://lodash.com/docs/#shuffle)\*mućkanje [niza] ili "str"-a. Vraca [niz]
- [\_.size](https://lodash.com/docs/#size) // length – moze I objekat
- [\_.some](https://lodash.com/docs/#some)
- [\_.sortBy](#_heading=h.3rdcrjn)

# Date

- [\_.](https://lodash.com/docs/#now)[now](https://lodash.com/docs/#now)

# Function

- [\_.afte](https://lodash.com/docs/#after)r \*pravi f-ju koja će da se pokrece posle \>=n puta // res = \_.after(3, ()=\>{console.log("after")}); res();res();res();
- [\_.ary](https://lodash.com/docs/#ary)(func, n) // pravi novu f-ju sa n argumenata, ignorisuci ostale
- [\_.before](https://lodash.com/docs/#before) \*obrnuto od after
- [\_.bind](https://lodash.com/docs/#bind) (func, this, [delimicnoDodatiArgumenti])
- [\_.bindKey](https://lodash.com/docs/#bindKey) (obj, key, [partials↑])
- [\_.curry](https://lodash.com/docs/#curry) // curried(1)(2)(3) == curried(1, 2, 3) == curried(1, 2)(3) == curried(1)(\_, 3)(2) // [1,2,3]
- [\_.curryRight](https://lodash.com/docs/#curryRight)// curried(1)(2)(3) // [3,2,1]
- [\_.](https://lodash.com/docs/#debounce)[debounce](https://lodash.com/docs/#debounce)\*odlaganje f() // q = \_.debounce(f(),1000); q() // ima {objekat} sa opcijama. Nisam razumeo. Mislim da su opcije vise za backend
- [\_.defer](https://lodash.com/docs/#defer)
- [\_.delay](https://lodash.com/docs/#delay) // setTimeout(func, wait)
- [\_.flip](https://lodash.com/docs/#flip) (fn) // dobija se nova f-ja sa obrnutim redosledom argumenata
- [\_.memoize](https://lodash.com/docs/#memoize)
- [\_.negate](https://lodash.com/docs/#negate)// negacija predikat f-je
- [\_.once](https://lodash.com/docs/#once) \*pravi f-ju koja kad se jednom pokrene davace uvek isti (prvobirni) rezultat, bez obzira na promenu parametara.
- [\_.overArgs](https://lodash.com/docs/#overArgs)
- [\_.partial](https://lodash.com/docs/#partial)(fn, …arg) // pravi se nova f-ja sa pretpostavljenim parametrima
- [\_.partialRight](https://lodash.com/docs/#partialRight)\*čita i piše argumente s' desna
- [\_.rearg](https://lodash.com/docs/#rearg)(fn(a,b,c), [2,0,1]) // fn(c,a,b) \*za preuređuvanje redosleda parametara
- [\_.rest](https://lodash.com/docs/#rest)
- [\_.spread](https://lodash.com/docs/#spread)
- [\_.throttle](https://lodash.com/docs/#throttle)
- [\_.unary](https://lodash.com/docs/#unary)
- [\_.wrap](https://lodash.com/docs/#wrap)

# Lang

- [\_.castArray](https://lodash.com/docs/#castArray) // a =\> [a]
- [\_.clone](https://lodash.com/docs/#clone)
- [\_.cloneDeep](https://lodash.com/docs/#cloneDeep)
- [\_.cloneDeepWith](https://lodash.com/docs/#cloneDeepWith)
- [\_.cloneWith](https://lodash.com/docs/#cloneWith)
- [\_.conformsTo](https://lodash.com/docs/#conformsTo)(obj, {param:predikatFn}) // T/F \*proverava da li "param" ispunjava uslov. "param" je svojstvo od "obj"
- [\_.](https://lodash.com/docs/#eq)[eq](https://lodash.com/docs/#eq) (2,3) // proverava da li je 2 jednako 3
- [\_.](https://lodash.com/docs/#gt)[gt](https://lodash.com/docs/#gt) vece
- [\_.](https://lodash.com/docs/#gte)[gte](https://lodash.com/docs/#gte) vece ili jednako
- [\_.](https://lodash.com/docs/#isArguments)[isArguments](https://lodash.com/docs/#isArguments)
- [\_.isArray](https://lodash.com/docs/#isArray)
- [\_.isArrayBuffer](https://lodash.com/docs/#isArrayBuffer)
- [\_.isArrayLike](https://lodash.com/docs/#isArrayLike)
- [\_.isArrayLikeObject](https://lodash.com/docs/#isArrayLikeObject)
- [\_.isBoolean](https://lodash.com/docs/#isBoolean)
- [\_.isBuffer](https://lodash.com/docs/#isBuffer)
- [\_.isDate](https://lodash.com/docs/#isDate)
- [\_.isElement](https://lodash.com/docs/#isElement)
- [\_.isEmpty](https://lodash.com/docs/#isEmpty)
- [\_.isEqual](https://lodash.com/docs/#isEqual)
- [\_.isEqualWith](https://lodash.com/docs/#isEqualWith)
- [\_.isError](https://lodash.com/docs/#isError)
- [\_.isFinite](https://lodash.com/docs/#isFinite)
- [\_.isFunction](https://lodash.com/docs/#isFunction)
- [\_.isInteger](https://lodash.com/docs/#isInteger)
- [\_.isLength](https://lodash.com/docs/#isLength)
- [\_.isMap](https://lodash.com/docs/#isMap)
- [\_.isMatch](https://lodash.com/docs/#isMatch)
- [\_.isMatchWith](https://lodash.com/docs/#isMatchWith)
- [\_.isNaN](https://lodash.com/docs/#isNaN)
- [\_.isNative](https://lodash.com/docs/#isNative)
- [\_.isNil](https://lodash.com/docs/#isNil)
- [\_.isNull](https://lodash.com/docs/#isNull)
- [\_.isNumber](https://lodash.com/docs/#isNumber)
- [\_.isObject](https://lodash.com/docs/#isObject)
- [\_.isObjectLike](https://lodash.com/docs/#isObjectLike)
- [\_.isPlainObject](https://lodash.com/docs/#isPlainObject)
- [\_.isRegExp](https://lodash.com/docs/#isRegExp)
- [\_.isSafeInteger](https://lodash.com/docs/#isSafeInteger)
- [\_.isSet](https://lodash.com/docs/#isSet)
- [\_.isString](https://lodash.com/docs/#isString)
- [\_.isSymbol](https://lodash.com/docs/#isSymbol)
- [\_.isTypedArray](https://lodash.com/docs/#isTypedArray)
- [\_.isUndefined](https://lodash.com/docs/#isUndefined)
- [\_.isWeakMap](https://lodash.com/docs/#isWeakMap)
- [\_.isWeakSet](https://lodash.com/docs/#isWeakSet)
- [\_.lt](https://lodash.com/docs/#lt)
- [\_.lte](https://lodash.com/docs/#lte)
- [\_.toArray](https://lodash.com/docs/#toArray)
- [\_.toFinite](https://lodash.com/docs/#toFinite)
- [\_.toInteger](https://lodash.com/docs/#toInteger)
- [\_.toLength](https://lodash.com/docs/#toLength)
- [\_.toNumber](https://lodash.com/docs/#toNumber)
- [\_.toPlainObject](https://lodash.com/docs/#toPlainObject)
- [\_.toSafeInteger](https://lodash.com/docs/#toSafeInteger)
- [\_.toString](https://lodash.com/docs/#toString)

# Math

- [\_.add](#_heading=h.44sinio)
- [\_.ceil](https://lodash.com/docs/#ceil)
- [\_.divide](https://lodash.com/docs/#divide)
- [\_.floor](https://lodash.com/docs/#floor)
- [\_.max](https://lodash.com/docs/#max)
- [\_.maxBy](https://lodash.com/docs/#maxBy)
- [\_.mean](https://lodash.com/docs/#mean)
- [\_.meanBy](https://lodash.com/docs/#meanBy)
- [\_.min](https://lodash.com/docs/#min)
- [\_.minBy](https://lodash.com/docs/#minBy)
- [\_.multiply](https://lodash.com/docs/#multiply)
- [\_.round](https://lodash.com/docs/#round)
- [\_.subtract](https://lodash.com/docs/#subtract)
- [\_.sum](https://lodash.com/docs/#sum)
- [\_.sumBy](https://lodash.com/docs/#sumBy)

# Number

- [\_.](https://lodash.com/docs/#clamp)[clamp](https://lodash.com/docs/#clamp) // yyY[xxx]Zzz - ogranicenje prikaza broja
- (1,2,4) =\> 2; // 1 je broj koji treba da se prikaze, a 2 I 4 su ogranicenja, znaci brojevi koji mogu da se prikazu su samo 2, 3 I 4. Posto je 1 \< 2, prikazuje se 2 jer je to najmanji broj koji moze da se prikaze.
- (2,2,4) =\> 2;
- (3,2,4) =\> 3;
- (4,2,4) =\> 4;
- (5,2,4) =\> 4;
- (100,2,4) =\> 4;
- [\_.inRange](https://lodash.com/docs/#inRange)// (broj, start, end) // Proverava da li je broj izmedju start i end
- [\_.random](#_heading=h.1fob9te)

# Object

- [\_.](https://lodash.com/docs/#assign)[assign](https://lodash.com/docs/#assign)(obj1, obj2, obj3)// {novi obj koji ima sva svojstva od obj123}
- [\_.](https://lodash.com/docs/#assignIn)[assignIn](https://lodash.com/docs/#assignIn) → extend // kao assign ali jos nasledjuje i ako sam nesto cackao po prototupe
- [\_.assignInWith](https://lodash.com/docs/#assignInWith)
- [\_.assignWith](https://lodash.com/docs/#assignWith)
- [\_.at](https://lodash.com/docs/#at)
- [\_.create](https://lodash.com/docs/#create)
- [\_.defaults](https://lodash.com/docs/#defaults)
- [\_.defaultsDeep](https://lodash.com/docs/#defaultsDeep)
- [\_.entries -\> toPairs](https://lodash.com/docs/#toPairs)
- [\_.entriesIn -\> toPairsIn](https://lodash.com/docs/#toPairsIn)
- [\_.extend -\> assignIn](https://lodash.com/docs/#assignIn)
- [\_.extendWith -\> assignInWith](https://lodash.com/docs/#assignInWith)
- [\_.findKey](https://lodash.com/docs/#findKey)
- [\_.findLastKey](https://lodash.com/docs/#findLastKey)
- [\_.forIn](https://lodash.com/docs/#forIn)
- [\_.forInRight](https://lodash.com/docs/#forInRight)
- [\_.forOwn](https://lodash.com/docs/#forOwn)
- [\_.forOwnRight](https://lodash.com/docs/#forOwnRight)
- [\_.functions](https://lodash.com/docs/#functions)
- [\_.functionsIn](https://lodash.com/docs/#functionsIn)
- [\_.get](#_heading=h.z337ya)
- [\_.has](https://lodash.com/docs/#has)
- [\_.hasIn](https://lodash.com/docs/#hasIn)
- [\_.invert](https://lodash.com/docs/#invert)
- [\_.invertBy](https://lodash.com/docs/#invertBy)
- [\_.invoke](https://lodash.com/docs/#invoke)
- [\_.keys](https://lodash.com/docs/#keys)
- [\_.keysIn](https://lodash.com/docs/#keysIn)
- [\_.mapKeys](https://lodash.com/docs/#mapKeys)
- [\_.mapValues](https://lodash.com/docs/#mapValues)
- [\_.merge](https://lodash.com/docs/#merge)
- [\_.mergeWith](https://lodash.com/docs/#mergeWith)
- [\_.omit](https://lodash.com/docs/#omit)// izaberes objekat i neka njegova svojstva koja NE zelis u novom objektu, i od ostatka svojstava se pravi novi objekat. Suprotno od \_.pick

\_.omit(psi, [[1], '0', 2])

![](RackMultipart20230421-1-k01wzt_html_3797c90d96b08dea.png)

- [\_.omitBy](https://lodash.com/docs/#omitBy)
- [\_.pick](#_heading=h.3j2qqm3)// izaberes objekat i ['neka','njegova', 'svojstva'] i od toga sto si izabrao, pravi se novi objekat. // \_.pick(psi, ['3.ime', '2.god', '2.nadimci.0'])

![](RackMultipart20230421-1-k01wzt_html_5114f4ddbb47409b.png)

- [\_.](https://lodash.com/docs/#pickBy)[pickBy](https://lodash.com/docs/#pickBy)// var object = { 'a': 1, 'b': '2', 'c': 3 };

\_.pickBy(object, \_.isNumber);

// =\> { 'a': 1, 'c': 3 }

- [\_.result](https://lodash.com/docs/#result)
- [\_.set](https://lodash.com/docs/#set)
- [\_.setWith](https://lodash.com/docs/#setWith)
- [\_.toPairs](https://lodash.com/docs/#toPairs)
- [\_.toPairsIn](https://lodash.com/docs/#toPairsIn)
- [\_.transform](https://lodash.com/docs/#transform)
- [\_.unset](https://lodash.com/docs/#unset)
- [\_.update](https://lodash.com/docs/#update)
- [\_.updateWith](https://lodash.com/docs/#updateWith)
- [\_.values](https://lodash.com/docs/#values)
- [\_.valuesIn](https://lodash.com/docs/#valuesIn)

# Seq

- [\_](https://lodash.com/docs/#lodash)
- [\_.](https://lodash.com/docs/#chain)[chain](https://lodash.com/docs/#chain)// Povezivanje f-ja
  - var youngest = \_. chain(users)
  - .sortBy('age')
  - .map(function(o) {
  - return o.user + ' is ' + o.age;
  - })
  - .value();
- [\_.](https://lodash.com/docs/#tap)[tap](https://lodash.com/docs/#tap)
- [\_.thru](https://lodash.com/docs/#thru)
- [\_.prototype[Symbol.iterator]](https://lodash.com/docs/#prototype-Symbol-iterator)
- [\_.prototype.at](https://lodash.com/docs/#prototype-at)
- [\_.prototype.chain](https://lodash.com/docs/#prototype-chain)
- [\_.prototype.commit](https://lodash.com/docs/#prototype-commit)
- [\_.prototype.next](https://lodash.com/docs/#prototype-next)
- [\_.prototype.plant](https://lodash.com/docs/#prototype-plant)
- [\_.prototype.reverse](https://lodash.com/docs/#prototype-reverse)
- [\_.prototype.toJSON -\> value](https://lodash.com/docs/#prototype-value)
- [\_.prototype.value](https://lodash.com/docs/#prototype-value)
- [\_.prototype.valueOf -\> value](https://lodash.com/docs/#prototype-value)

# String

- [\_.camelCase](https://lodash.com/docs/#camelCase)
- [\_.capitalize](https://lodash.com/docs/#capitalize)\* joe → Joe
- [\_.deburr](https://lodash.com/docs/#deburr)\* déjà vu → deja vu
- [\_.endsWith](https://lodash.com/docs/#endsWith)
- [\_.escape](https://lodash.com/docs/#escape) \* & \< \> ' " → &amp &lt &gt…
- [\_.escapeRegExp](https://lodash.com/docs/#escapeRegExp)
- [\_.kebabCase](#_heading=h.1y810tw)\* asdQwe asd\_qweAsd → asd-qwe-asd-qwe-asd
- [\_.lowerCase](https://lodash.com/docs/#lowerCase)
- [\_.lowerFirst](https://lodash.com/docs/#lowerFirst)
- [\_.pad](https://lodash.com/docs/#pad)
- [\_.padEnd](https://lodash.com/docs/#padEnd)
- [\_.padStart](https://lodash.com/docs/#padStart)
- [\_.parseInt](https://lodash.com/docs/#parseInt)
- [\_.repeat](https://lodash.com/docs/#repeat)
- [\_.replace](https://lodash.com/docs/#replace)
- [\_.snakeCase](#_heading=h.4i7ojhp)[\* asdasQasdDasd → asdas\_qasd\_dasd](#_heading=h.4i7ojhp)
- [\_.split](https://lodash.com/docs/#split)
- [\_.startCase](https://lodash.com/docs/#startCase)\* --foo-bar—ili fooBar →  Foo Bar ; \_\_FOO\_BAR\_\_ → FOO BAR
- [\_.startsWith](https://lodash.com/docs/#startsWith)
- [\_.template](https://lodash.com/docs/#template)
- [\_.toLower](https://lodash.com/docs/#toLower)
- [\_.toUpper](https://lodash.com/docs/#toUpper)
- [\_.trim](https://lodash.com/docs/#trim)
- [\_.trimEnd](https://lodash.com/docs/#trimEnd)
- [\_.trimStart](https://lodash.com/docs/#trimStart)

- [\_.truncate](#_heading=h.2xcytpi)[// ('123456789 123456789 123456789', { length: 20, omission:' itd.', 'separator': ' '}) // "123456789 itd."](#_heading=h.2xcytpi)

- [\_.unescape](https://lodash.com/docs/#unescape) //
- [\_.upperCase](https://lodash.com/docs/#upperCase)
- [\_.upperFirst](https://lodash.com/docs/#upperFirst)
- [\_.words](https://lodash.com/docs/#words) // cepa recenice na reci

# Util

- [\_.attempt](https://lodash.com/docs/#attempt)
- [\_.bindAll](https://lodash.com/docs/#bindAll)
- [\_.cond](https://lodash.com/docs/#cond) ([predikatFn1, uslovljenaFn1], [predFn2, uslovFn2], [pFn3, uFn3], [p4, u4])
- [\_.conforms](https://lodash.com/docs/#conforms)
- [\_.constant](https://lodash.com/docs/#constant)('qwe') // ne vraca 'qwe', nego vraca definicuju f-ju koja vraca 'qwe'// function () {return "qwe"}
- [\_.defaultTo](https://lodash.com/docs/#defaultTo) (qwe, 'def') // proverava qwe da li je undefined, NaN ili null, pa ako jeste vraca neku definisanu default vredonst ('def')
- [\_.](#_heading=h.3whwml4)[flow](#_heading=h.3whwml4)// kao buduci pipline |\> u JS-u. Pokretanje vise f-ja u citljivom formatu
- [\_.](https://lodash.com/docs/#flowRight)[flowRight](https://lodash.com/docs/#flowRight)
- \_.[identity](#_heading=h.2bn6wsx)(val) // val
- [\_.iteratee](https://lodash.com/docs/#iteratee) \* callbackfn
- [\_.matches](https://lodash.com/docs/#matches) (source)\* Pravi Predikat f-ju od {source-objekta}. Ta f-ja će dubinski da poredi k:v {datog joj objekta} sa k:v {source-objekta}. Ako se SVI k:v od {src-obj} poklapaju sa NEKIM k:v od {dat-obj} vraca T.

skraćenica {k1:v1, adres.k2:v2}

- [\_.matchesProperty](https://lodash.com/docs/#matchesProperty)(["adresa", "pema", "key"], "vrednost za poređenje") \* Pravi predikat f-ju koja će da POREDI vrednost koja leži na ["adresa", "pema", "key"] datog obj. i "vrednost za poređenje". Skraćenica je ["key", "value"] - a to je niz argumenata za matchProperty()
- [\_.method](https://lodash.com/docs/#method)
- [\_.methodOf](https://lodash.com/docs/#methodOf)
- [\_.mixin](https://lodash.com/docs/#mixin)// mogucnost da napravimo nove funkcije unurat lodash-a
- [\_.noConflict](https://lodash.com/docs/#noConflict)
- [\_.noop](https://lodash.com/docs/#noop)\* f-ja koja vraca undefined
- [\_.nthArg](https://lodash.com/docs/#nthArg)\* definise f-ju koja vraca n-ti argument. Parametar moze biti I negativan broj
- [\_.over](https://lodash.com/docs/#over) ([niz, funkcija]) \*definiše se f-ja koja pokrece [funkcije iz niza]. Znaci, [gomila f-ja] se pokrece sa (jednim skupom parametara) i na kraju se dobija [gomila rezultata]
- [\_.overEvery](https://lodash.com/docs/#overEvery)\* Radi sa predikatskim f-jama (npr. Boolean, isNan). Ako sve f-je sa datim argumentom vrate T, rezultat ce biti T.
- [\_.overSome](https://lodash.com/docs/#overSome)\* Ako bar jedna vrati T, rezultat ce biti T
- [\_.property](https://lodash.com/docs/#property) (p.a.th) // (path) =\> value
- [\_.propertyOf](https://lodash.com/docs/#propertyOf)
- [\_.range](https://lodash.com/docs/#range)[1 2 3]
- [\_.rangeRight](https://lodash.com/docs/#rangeRight)[3 2 1]
- [\_.runInContext](https://lodash.com/docs/#runInContext)\* Sluzi za pravljenje novi lodash f-ja. Nisam bas skroz razumeo.
- [\_.](https://lodash.com/docs/#stubArray)[stubArray](https://lodash.com/docs/#stubArray)[]
- [\_.](https://lodash.com/docs/#stubFalse)[stubFalse](https://lodash.com/docs/#stubFalse) false
- [\_.stubObject](https://lodash.com/docs/#stubObject) {}
- [\_.](https://lodash.com/docs/#stubString)[stubString](https://lodash.com/docs/#stubString) ''
- [\_.](#_heading=h.qsh70q)[stubTrue](#_heading=h.qsh70q) true
- [\_.](#_heading=h.3as4poj)[times](#_heading=h.3as4poj) // izvrsava f() x puta i rezultate pise u novi array //
- [\_.toPath](#_heading=h.1pxezwc) //('a[0].b.c'); =\> ['a', '0', 'b', 'c']
- [\_.uniqueId](#_heading=h.49x2ik5) ('qwe') =\> 'qwe1(,2,3…)'

# Properties

- [\_.](https://lodash.com/docs/#VERSION)[VERSION](https://lodash.com/docs/#VERSION)
- [\_.templateSettings](https://lodash.com/docs/#templateSettings)
- [\_.templateSettings.escape](https://lodash.com/docs/#templateSettings-escape)
- [\_.templateSettings.evaluate](https://lodash.com/docs/#templateSettings-evaluate)
- [\_.templateSettings.imports](https://lodash.com/docs/#templateSettings-imports)
- [\_.templateSettings.interpolate](https://lodash.com/docs/#templateSettings-interpolate)
- [\_.templateSettings.variable](https://lodash.com/docs/#templateSettings-variable)

# Methods

- [\_.](https://lodash.com/docs/#templateSettings-imports-_)[templateSettings.imports.\_](https://lodash.com/docs/#templateSettings-imports-_)

## "Array" Methods

## \_.chunk(array, [size=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L6839)[npm package](https://www.npmjs.com/package/lodash.chunk)

Creates an array of elements split into groups the length of size. If array can't be split evenly, the final chunk will be the remaining elements.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to process.
2. [size=1]_(number)_: The length of each chunk

**Returns**

_(Array)_: Returns the new array of chunks.

**Example**

\_.chunk(['a', 'b', 'c', 'd'], 2);

// =\> [['a', 'b'], ['c', 'd']]

\_.chunk(['a', 'b', 'c', 'd'], 3);

// =\> [['a', 'b', 'c'], ['d']]

Try in REPL\_.compact(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L6874)[npm package](https://www.npmjs.com/package/lodash.compact)

Creates an array with all falsey values removed. The values false, null, 0, "", undefined, and NaN are falsey.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to compact.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

\_.compact([0, 1, false, 2, '', 3]);

// =\> [1, 2, 3]

Try in REPL

## \_.concat(array, [values])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L6911)[npm package](https://www.npmjs.com/package/lodash.concat)

Creates a new array concatenating array with any additional arrays and/or values.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to concatenate.
2. [values]_(...\*)_: The values to concatenate.

**Returns**

_(Array)_: Returns the new concatenated array.

**Example**

var array = [1];

var other = \_.concat(array, 2, [3], [[4]]);

console.log(other);

// =\> [1, 2, 3, [4]]

console.log(array);

// =\> [1]

Try in REPL

## \_.difference(array, [values])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L6947)[npm package](https://www.npmjs.com/package/lodash.difference)

Creates an array of array values not included in the other given arrays using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons. The order and references of result values are determined by the first array.

**Note:** Unlike [\_.pullAll](https://lodash.com/docs/#pullAll), this method returns a new array.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [values]_(...Array)_: The values to exclude.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

\_.difference([2, 1], [2, 3]);

// =\> [1]

Try in REPL

## \_.differenceBy(array, [values], [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L6979)[npm package](https://www.npmjs.com/package/lodash.differenceby)

This method is like [\_.difference](https://lodash.com/docs/#difference) except that it accepts iteratee which is invoked for each element of array and values to generate the criterion by which they're compared. The order and references of result values are determined by the first array. The iteratee is invoked with one argument:
_(value)_.

**Note:** Unlike [\_.pullAllBy](https://lodash.com/docs/#pullAllBy), this method returns a new array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [values]_(...Array)_: The values to exclude.
3. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

\_.differenceBy([2.1, 1.2], [2.3, 3.4], Math.floor);

// =\> [1.2]

// The `_.property` iteratee shorthand.

\_.differenceBy([{ 'x': 2 }, { 'x': 1 }], [{ 'x': 1 }], 'x');

// =\> [{ 'x': 2 }]

Try in REPL

## \_.differenceWith(array, [values], [comparator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7012)[npm package](https://www.npmjs.com/package/lodash.differencewith)

This method is like [\_.difference](https://lodash.com/docs/#difference) except that it accepts comparator which is invoked to compare elements of array to values. The order and references of result values are determined by the first array. The comparator is invoked with two arguments: _(arrVal, othVal)_.

**Note:** Unlike [\_.pullAllWith](https://lodash.com/docs/#pullAllWith), this method returns a new array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [values]_(...Array)_: The values to exclude.
3. [comparator]_(Function)_: The comparator invoked per element.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

## \_.drop(array, [n=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7047)[npm package](https://www.npmjs.com/package/lodash.drop)

Creates a slice of array with n elements dropped from the beginning.

**Since**

0.5.0

**Arguments**

1. array_(Array)_: The array to query.
2. [n=1]_(number)_: The number of elements to drop.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

\_.drop([1, 2, 3]);

// =\> [2, 3]

\_.drop([1, 2, 3], 2);

// =\> [3]

\_.drop([1, 2, 3], 5);

// =\> []

\_.drop([1, 2, 3], 0);

// =\> [1, 2, 3]

Try in REPL

## \_.dropRight(array, [n=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7081)[npm package](https://www.npmjs.com/package/lodash.dropright)

Creates a slice of array with n elements dropped from the end.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to query.
2. [n=1]_(number)_: The number of elements to drop.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

\_.dropRight([1, 2, 3]);

// =\> [1, 2]

\_.dropRight([1, 2, 3], 2);

// =\> [1]

\_.dropRight([1, 2, 3], 5);

// =\> []

\_.dropRight([1, 2, 3], 0);

// =\> [1, 2, 3]

Try in REPL

## \_.dropRightWhile(array, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7126)[npm package](https://www.npmjs.com/package/lodash.droprightwhile)

Creates a slice of array excluding elements dropped from the end. Elements are dropped until predicate returns falsey. The predicate is invoked with three arguments: _(value, index, array)_.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to query.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

var users = [

  { 'user': 'barney',  'active': true },

  { 'user': 'fred',    'active': false },

  { 'user': 'pebbles', 'active': false }

];

\_.dropRightWhile(users, function(o) { return !o.active; });

// =\> objects for ['barney']

// The `_.matches` iteratee shorthand.

\_.dropRightWhile(users, { 'user': 'pebbles', 'active': false });

// =\> objects for ['barney', 'fred']

// The `_.matchesProperty` iteratee shorthand.

\_.dropRightWhile(users, ['active', false]);

// =\> objects for ['barney']

// The `_.property` iteratee shorthand.

\_.dropRightWhile(users, 'active');

// =\> objects for ['barney', 'fred', 'pebbles']

Try in REPL

## \_.dropWhile(array, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7167)[npm package](https://www.npmjs.com/package/lodash.dropwhile)

Creates a slice of array excluding elements dropped from the beginning. Elements are dropped until predicate returns falsey. The predicate is invoked with three arguments: _(value, index, array)_.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to query.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

var users = [

  { 'user': 'barney',  'active': false },

  { 'user': 'fred',    'active': false },

  { 'user': 'pebbles', 'active': true }

];

\_.dropWhile(users, function(o) { return !o.active; });

// =\> objects for ['pebbles']

// The `_.matches` iteratee shorthand.

\_.dropWhile(users, { 'user': 'barney', 'active': false });

// =\> objects for ['fred', 'pebbles']

// The `_.matchesProperty` iteratee shorthand.

\_.dropWhile(users, ['active', false]);

// =\> objects for ['pebbles']

// The `_.property` iteratee shorthand.

\_.dropWhile(users, 'active');

// =\> objects for ['barney', 'fred', 'pebbles']

Try in REPL

## \_.fill(array, value, [start=0], [end=array.length])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7202)[npm package](https://www.npmjs.com/package/lodash.fill)

Fills elements of array with value from start up to, but not including, end.

**Note:** This method mutates array.

**Since**

3.2.0

**Arguments**

1. array_(Array)_: The array to fill.
2. value_(\*)_: The value to fill array with.
3. [start=0]_(number)_: The start position.
4. [end=array.length]_(number)_: The end position.

**Returns**

_(Array)_: Returns array.

**Example**

var array = [1, 2, 3];

\_.fill(array, 'a');

console.log(array);

// =\> ['a', 'a', 'a']

\_.fill(Array(3), 2);

// =\> [2, 2, 2]

\_.fill([4, 6, 8, 10], '\*', 1, 3);

// =\> [4, '\*', '\*', 10]

Try in REPL

## \_.findIndex(array, [predicate=\_.identity], [fromIndex=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7249)[npm package](https://www.npmjs.com/package/lodash.findindex)

This method is like [\_.find](https://lodash.com/docs/#find) except that it returns the index of the first element predicate returns truthy for instead of the element itself.

**Since**

1.1.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.
3. [fromIndex=0]_(number)_: The index to search from.

**Returns**

_(number)_: Returns the index of the found element, else -1.

**Example**

var users = [

  { 'user': 'barney',  'active': false },

  { 'user': 'fred',    'active': false },

  { 'user': 'pebbles', 'active': true }

];

\_.findIndex(users, function(o) { return o.user == 'barney'; });

// =\> 0

// The `_.matches` iteratee shorthand.

\_.findIndex(users, { 'user': 'fred', 'active': false });

// =\> 1

// The `_.matchesProperty` iteratee shorthand.

\_.findIndex(users, ['active', false]);

// =\> 0

// The `_.property` iteratee shorthand.

\_.findIndex(users, 'active');

// =\> 2

Try in REPL

## \_.findLastIndex(array, [predicate=\_.identity], [fromIndex=array.length-1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7296)[npm package](https://www.npmjs.com/package/lodash.findlastindex)

This method is like [\_.findIndex](https://lodash.com/docs/#findIndex) except that it iterates over elements of collection from right to left.

**Since**

2.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.
3. [fromIndex=array.length-1]_(number)_: The index to search from.

**Returns**

_(number)_: Returns the index of the found element, else -1.

**Example**

var users = [

  { 'user': 'barney',  'active': true },

  { 'user': 'fred',    'active': false },

  { 'user': 'pebbles', 'active': false }

];

\_.findLastIndex(users, function(o) { return o.user == 'pebbles'; });

// =\> 2

// The `_.matches` iteratee shorthand.

\_.findLastIndex(users, { 'user': 'barney', 'active': true });

// =\> 0

// The `_.matchesProperty` iteratee shorthand.

\_.findLastIndex(users, ['active', false]);

// =\> 2

// The `_.property` iteratee shorthand.

\_.findLastIndex(users, 'active');

// =\> 0

Try in REPL

## \_.flatten(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7325)[npm package](https://www.npmjs.com/package/lodash.flatten)

Flattens array a single level deep.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to flatten.

**Returns**

_(Array)_: Returns the new flattened array.

**Example**

\_.flatten([1, [2, [3, [4]], 5]]);

// =\> [1, 2, [3, [4]], 5]

Try in REPL

## \_.flattenDeep(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7344)[npm package](https://www.npmjs.com/package/lodash.flattendeep)

Recursively flattens array.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to flatten.

**Returns**

_(Array)_: Returns the new flattened array.

**Example**

\_.flattenDeep([1, [2, [3, [4]], 5]]);

// =\> [1, 2, 3, 4, 5]

Try in REPL

## \_.flattenDepth(array, [depth=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7369)[npm package](https://www.npmjs.com/package/lodash.flattendepth)

Recursively flatten array up to depth times.

**Since**

4.4.0

**Arguments**

1. array_(Array)_: The array to flatten.
2. [depth=1]_(number)_: The maximum recursion depth.

**Returns**

_(Array)_: Returns the new flattened array.

**Example**

var array = [1, [2, [3, [4]], 5]];

\_.flattenDepth(array, 1);

// =\> [1, 2, [3, [4]], 5]

\_.flattenDepth(array, 2);

// =\> [1, 2, 3, [4], 5]

Try in REPL

## \_.fromPairs(pairs)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7393)[npm package](https://www.npmjs.com/package/lodash.frompairs)

The inverse of [\_.toPairs](https://lodash.com/docs/#toPairs); this method returns an object composed from key-value pairs.

**Since**

4.0.0

**Arguments**

1. pairs_(Array)_: The key-value pairs.

**Returns**

_(Object)_: Returns the new object.

**Example**

\_.fromPairs([['a', 1], ['b', 2]]);

// =\> { 'a': 1, 'b': 2 }

Try in REPL

## \_.head(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7423)[npm package](https://www.npmjs.com/package/lodash.head)

Gets the first element of array.

**Since**

0.1.0

**Aliases**

_\_.first_

**Arguments**

1. array_(Array)_: The array to query.

**Returns**

_(\*)_: Returns the first element of array.

**Example**

\_.head([1, 2, 3]);

// =\> 1

\_.head([]);

// =\> undefined

Try in REPL

## \_.indexOf(array, value, [fromIndex=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7450)[npm package](https://www.npmjs.com/package/lodash.indexof)

Gets the index at which the first occurrence of value is found in array using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons. If fromIndex is negative, it's used as the offset from the end of array.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. value_(\*)_: The value to search for.
3. [fromIndex=0]_(number)_: The index to search from.

**Returns**

_(number)_: Returns the index of the matched value, else -1.

**Example**

\_.indexOf([1, 2, 1, 2], 2);

// =\> 1

// Search from the `fromIndex`.

\_.indexOf([1, 2, 1, 2], 2, 2);

// =\> 3

Try in REPL

## \_.initial(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7476)[npm package](https://www.npmjs.com/package/lodash.initial)

Gets all but the last element of array.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to query.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

\_.initial([1, 2, 3]);

// =\> [1, 2]

Try in REPL

## \_.intersection([arrays])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7498)[npm package](https://www.npmjs.com/package/lodash.intersection)

Creates an array of unique values that are included in all given arrays using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons. The order and references of result values are determined by the first array.

**Since**

0.1.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.

**Returns**

_(Array)_: Returns the new array of intersecting values.

**Example**

\_.intersection([2, 1], [2, 3]);

// =\> [2]

Try in REPL

## \_.intersectionBy([arrays], [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7528)[npm package](https://www.npmjs.com/package/lodash.intersectionby)

This method is like [\_.intersection](https://lodash.com/docs/#intersection) except that it accepts iteratee which is invoked for each element of each arrays to generate the criterion by which they're compared. The order and references of result values are determined by the first array. The iteratee is invoked with one argument:
_(value)_.

**Since**

4.0.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns the new array of intersecting values.

**Example**

\_.intersectionBy([2.1, 1.2], [2.3, 3.4], Math.floor);

// =\> [2.1]

// The `_.property` iteratee shorthand.

\_.intersectionBy([{ 'x': 1 }], [{ 'x': 2 }, { 'x': 1 }], 'x');

// =\> [{ 'x': 1 }]

Try in REPL

## \_.intersectionWith([arrays], [comparator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7563)[npm package](https://www.npmjs.com/package/lodash.intersectionwith)

This method is like [\_.intersection](https://lodash.com/docs/#intersection) except that it accepts comparator which is invoked to compare elements of arrays. The order and references of result values are determined by the first array. The comparator is invoked with two arguments: _(arrVal, othVal)_.

**Since**

4.0.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.
2. [comparator]_(Function)_: The comparator invoked per element.

**Returns**

_(Array)_: Returns the new array of intersecting values.

**Example**

var objects = [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }];

var others = [{ 'x': 1, 'y': 1 }, { 'x': 1, 'y': 2 }];

\_.intersectionWith(objects, others, \_.isEqual);

// =\> [{ 'x': 1, 'y': 2 }]

Try in REPL

## \_.join(array, [separator=','])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7591)[npm package](https://www.npmjs.com/package/lodash.join)

Converts all elements in array into a string separated by separator.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to convert.
2. [separator=',']_(string)_: The element separator.

**Returns**

_(string)_: Returns the joined string.

**Example**

\_.join(['a', 'b', 'c'], '~');

// =\> 'a~b~c'

Try in REPL

## \_.last(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7609)[npm package](https://www.npmjs.com/package/lodash.last)

Gets the last element of array.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to query.

**Returns**

_(\*)_: Returns the last element of array.

**Example**

\_.last([1, 2, 3]);

// =\> 3

Try in REPL

## \_.lastIndexOf(array, value, [fromIndex=array.length-1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7635)[npm package](https://www.npmjs.com/package/lodash.lastindexof)

This method is like [\_.indexOf](https://lodash.com/docs/#indexOf) except that it iterates over elements of array from right to left.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. value_(\*)_: The value to search for.
3. [fromIndex=array.length-1]_(number)_: The index to search from.

**Returns**

_(number)_: Returns the index of the matched value, else -1.

**Example**

\_.lastIndexOf([1, 2, 1, 2], 2);

// =\> 3

// Search from the `fromIndex`.

\_.lastIndexOf([1, 2, 1, 2], 2, 2);

// =\> 1

Try in REPL

## \_.nth(array, [n=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7671)[npm package](https://www.npmjs.com/package/lodash.nth)

Gets the element at index n of array. If n is negative, the nth element from the end is returned.

**Since**

4.11.0

**Arguments**

1. array_(Array)_: The array to query.
2. [n=0]_(number)_: The index of the element to return.

**Returns**

_(\*)_: Returns the nth element of array.

**Example**

var array = ['a', 'b', 'c', 'd'];

\_.nth(array, 1);

// =\> 'b'

\_.nth(array, -2);

// =\> 'c';

Try in REPL

## \_.pull(array, [values])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7698)[npm package](https://www.npmjs.com/package/lodash.pull)

Removes all given values from array using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons.

**Note:** Unlike [\_.without](https://lodash.com/docs/#without), this method mutates array. Use [\_.remove](https://lodash.com/docs/#remove) to remove elements from an array by predicate.

**Since**

2.0.0

**Arguments**

1. array_(Array)_: The array to modify.
2. [values]_(...\*)_: The values to remove.

**Returns**

_(Array)_: Returns array.

**Example**

var array = ['a', 'b', 'c', 'a', 'b', 'c'];

\_.pull(array, 'a', 'c');

console.log(array);

// =\> ['b', 'b']

Try in REPL

## \_.pullAll(array, values)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7720)[npm package](https://www.npmjs.com/package/lodash.pullall)

This method is like [\_.pull](https://lodash.com/docs/#pull) except that it accepts an array of values to remove.

**Note:** Unlike [\_.difference](https://lodash.com/docs/#difference), this method mutates array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to modify.
2. values_(Array)_: The values to remove.

**Returns**

_(Array)_: Returns array.

**Example**

var array = ['a', 'b', 'c', 'a', 'b', 'c'];

\_.pullAll(array, ['a', 'c']);

console.log(array);

// =\> ['b', 'b']

Try in REPL

## \_.pullAllBy(array, values, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7749)[npm package](https://www.npmjs.com/package/lodash.pullallby)

This method is like [\_.pullAll](https://lodash.com/docs/#pullAll) except that it accepts iteratee which is invoked for each element of array and values to generate the criterion by which they're compared. The iteratee is invoked with one argument: _(value)_.

**Note:** Unlike [\_.differenceBy](https://lodash.com/docs/#differenceBy), this method mutates array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to modify.
2. values_(Array)_: The values to remove.
3. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns array.

**Example**

var array = [{ 'x': 1 }, { 'x': 2 }, { 'x': 3 }, { 'x': 1 }];

\_.pullAllBy(array, [{ 'x': 1 }, { 'x': 3 }], 'x');

console.log(array);

// =\> [{ 'x': 2 }]

Try in REPL

## \_.pullAllWith(array, values, [comparator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7778)[npm package](https://www.npmjs.com/package/lodash.pullallwith)

This method is like [\_.pullAll](https://lodash.com/docs/#pullAll) except that it accepts comparator which is invoked to compare elements of array to values. The comparator is invoked with two arguments: _(arrVal, othVal)_.

**Note:** Unlike [\_.differenceWith](https://lodash.com/docs/#differenceWith), this method mutates array.

**Since**

4.6.0

**Arguments**

1. array_(Array)_: The array to modify.
2. values_(Array)_: The values to remove.
3. [comparator]_(Function)_: The comparator invoked per element.

**Returns**

_(Array)_: Returns array.

**Example**

var array = [{ 'x': 1, 'y': 2 }, { 'x': 3, 'y': 4 }, { 'x': 5, 'y': 6 }];

\_.pullAllWith(array, [{ 'x': 3, 'y': 4 }], \_.isEqual);

console.log(array);

// =\> [{ 'x': 1, 'y': 2 }, { 'x': 5, 'y': 6 }]

Try in REPL

## \_.pullAt(array, [indexes])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7808)[npm package](https://www.npmjs.com/package/lodash.pullat)

Removes elements from array corresponding to indexes and returns an array of removed elements.

**Note:** Unlike [\_.at](https://lodash.com/docs/#at), this method mutates array.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to modify.
2. [indexes]_(...(number|number[]))_: The indexes of elements to remove.

**Returns**

_(Array)_: Returns the new array of removed elements.

**Example**

var array = ['a', 'b', 'c', 'd'];

var pulled = \_.pullAt(array, [1, 3]);

console.log(array);

// =\> ['a', 'c']

console.log(pulled);

// =\> ['b', 'd']

Try in REPL

## \_.remove(array, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7847)[npm package](https://www.npmjs.com/package/lodash.remove)

Removes all elements from array that predicate returns truthy for and returns an array of the removed elements. The predicate is invoked with three arguments: _(value, index, array)_.

**Note:** Unlike [\_.filter](https://lodash.com/docs/#filter), this method mutates array. Use [\_.pull](https://lodash.com/docs/#pull) to pull elements from an array by value.

**Since**

2.0.0

**Arguments**

1. array_(Array)_: The array to modify.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the new array of removed elements.

**Example**

var array = [1, 2, 3, 4];

var evens = \_.remove(array, function(n) {

  return n % 2 == 0;

});

console.log(array);

// =\> [1, 3]

console.log(evens);

// =\> [2, 4]

Try in REPL

## \_.reverse(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7891)[npm package](https://www.npmjs.com/package/lodash.reverse)

Reverses array so that the first element becomes the last, the second element becomes the second to last, and so on.

**Note:** This method mutates array and is based on [Array#reverse](https://mdn.io/Array/reverse).

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to modify.

**Returns**

_(Array)_: Returns array.

**Example**

var array = [1, 2, 3];

\_.reverse(array);

// =\> [3, 2, 1]

console.log(array);

// =\> [3, 2, 1]

Try in REPL

## \_.slice(array, [start=0], [end=array.length])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7911)[npm package](https://www.npmjs.com/package/lodash.slice)

Creates a slice of array from start up to, but not including, end.

**Note:** This method is used instead of [Array#slice](https://mdn.io/Array/slice) to ensure dense arrays are returned.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to slice.
2. [start=0]_(number)_: The start position.
3. [end=array.length]_(number)_: The end position.

**Returns**

_(Array)_: Returns the slice of array.

## \_.sortedIndex(array, value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7944)[npm package](https://www.npmjs.com/package/lodash.sortedindex)

Uses a binary search to determine the lowest index at which value should be inserted into array in order to maintain its sort order.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The sorted array to inspect.
2. value_(\*)_: The value to evaluate.

**Returns**

_(number)_: Returns the index at which value should be inserted into array.

**Example**

\_.sortedIndex([30, 50], 40);

// =\> 1

Try in REPL

## \_.sortedIndexBy(array, value, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7973)[npm package](https://www.npmjs.com/package/lodash.sortedindexby)

This method is like [\_.sortedIndex](https://lodash.com/docs/#sortedIndex) except that it accepts iteratee which is invoked for value and each element of array to compute their sort ranking. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The sorted array to inspect.
2. value_(\*)_: The value to evaluate.
3. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(number)_: Returns the index at which value should be inserted into array.

**Example**

var objects = [{ 'x': 4 }, { 'x': 5 }];

\_.sortedIndexBy(objects, { 'x': 4 }, function(o) { return o.x; });

// =\> 0

// The `_.property` iteratee shorthand.

\_.sortedIndexBy(objects, { 'x': 4 }, 'x');

// =\> 0

Try in REPL

## \_.sortedIndexOf(array, value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L7993)[npm package](https://www.npmjs.com/package/lodash.sortedindexof)

This method is like [\_.indexOf](https://lodash.com/docs/#indexOf) except that it performs a binary search on a sorted array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. value_(\*)_: The value to search for.

**Returns**

_(number)_: Returns the index of the matched value, else -1.

**Example**

\_.sortedIndexOf([4, 5, 5, 5, 6], 5);

// =\> 1

Try in REPL

## \_.sortedLastIndex(array, value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8022)[npm package](https://www.npmjs.com/package/lodash.sortedlastindex)

This method is like [\_.sortedIndex](https://lodash.com/docs/#sortedIndex) except that it returns the highest index at which value should be inserted into array in order to maintain its sort order.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The sorted array to inspect.
2. value_(\*)_: The value to evaluate.

**Returns**

_(number)_: Returns the index at which value should be inserted into array.

**Example**

\_.sortedLastIndex([4, 5, 5, 5, 6], 5);

// =\> 4

Try in REPL

## \_.sortedLastIndexBy(array, value, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8051)[npm package](https://www.npmjs.com/package/lodash.sortedlastindexby)

This method is like [\_.sortedLastIndex](https://lodash.com/docs/#sortedLastIndex) except that it accepts iteratee which is invoked for value and each element of array to compute their sort ranking. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The sorted array to inspect.
2. value_(\*)_: The value to evaluate.
3. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(number)_: Returns the index at which value should be inserted into array.

**Example**

var objects = [{ 'x': 4 }, { 'x': 5 }];

\_.sortedLastIndexBy(objects, { 'x': 4 }, function(o) { return o.x; });

// =\> 1

// The `_.property` iteratee shorthand.

\_.sortedLastIndexBy(objects, { 'x': 4 }, 'x');

// =\> 1

Try in REPL

## \_.sortedLastIndexOf(array, value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8071)[npm package](https://www.npmjs.com/package/lodash.sortedlastindexof)

This method is like [\_.lastIndexOf](https://lodash.com/docs/#lastIndexOf) except that it performs a binary search on a sorted array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. value_(\*)_: The value to search for.

**Returns**

_(number)_: Returns the index of the matched value, else -1.

**Example**

\_.sortedLastIndexOf([4, 5, 5, 5, 6], 5);

// =\> 3

Try in REPL

## \_.sortedUniq(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8097)[npm package](https://www.npmjs.com/package/lodash.sorteduniq)

This method is like [\_.uniq](https://lodash.com/docs/#uniq) except that it's designed and optimized for sorted arrays.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.

**Returns**

_(Array)_: Returns the new duplicate free array.

**Example**

\_.sortedUniq([1, 1, 2]);

// =\> [1, 2]

Try in REPL

## \_.sortedUniqBy(array, [iteratee])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8119)[npm package](https://www.npmjs.com/package/lodash.sorteduniqby)

This method is like [\_.uniqBy](https://lodash.com/docs/#uniqBy) except that it's designed and optimized for sorted arrays.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [iteratee]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns the new duplicate free array.

**Example**

\_.sortedUniqBy([1.1, 1.2, 2.3, 2.4], Math.floor);

// =\> [1.1, 2.3]

Try in REPL

## \_.tail(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8139)[npm package](https://www.npmjs.com/package/lodash.tail)

Gets all but the first element of array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to query.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

\_.tail([1, 2, 3]);

// =\> [2, 3]

Try in REPL

## \_.take(array, [n=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8169)[npm package](https://www.npmjs.com/package/lodash.take)

Creates a slice of array with n elements taken from the beginning.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to query.
2. [n=1]_(number)_: The number of elements to take.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

\_.take([1, 2, 3]);

// =\> [1]

\_.take([1, 2, 3], 2);

// =\> [1, 2]

\_.take([1, 2, 3], 5);

// =\> [1, 2, 3]

\_.take([1, 2, 3], 0);

// =\> []

Try in REPL

## \_.takeRight(array, [n=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8202)[npm package](https://www.npmjs.com/package/lodash.takeright)

Creates a slice of array with n elements taken from the end.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to query.
2. [n=1]_(number)_: The number of elements to take.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

\_.takeRight([1, 2, 3]);

// =\> [3]

\_.takeRight([1, 2, 3], 2);

// =\> [2, 3]

\_.takeRight([1, 2, 3], 5);

// =\> [1, 2, 3]

\_.takeRight([1, 2, 3], 0);

// =\> []

Try in REPL

## \_.takeRightWhile(array, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8247)[npm package](https://www.npmjs.com/package/lodash.takerightwhile)

Creates a slice of array with elements taken from the end. Elements are taken until predicate returns falsey. The predicate is invoked with three arguments: _(value, index, array)_.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to query.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

var users = [

  { 'user': 'barney',  'active': true },

  { 'user': 'fred',    'active': false },

  { 'user': 'pebbles', 'active': false }

];

\_.takeRightWhile(users, function(o) { return !o.active; });

// =\> objects for ['fred', 'pebbles']

// The `_.matches` iteratee shorthand.

\_.takeRightWhile(users, { 'user': 'pebbles', 'active': false });

// =\> objects for ['pebbles']

// The `_.matchesProperty` iteratee shorthand.

\_.takeRightWhile(users, ['active', false]);

// =\> objects for ['fred', 'pebbles']

// The `_.property` iteratee shorthand.

\_.takeRightWhile(users, 'active');

// =\> []

Try in REPL

## \_.takeWhile(array, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8288)[npm package](https://www.npmjs.com/package/lodash.takewhile)

Creates a slice of array with elements taken from the beginning. Elements are taken until predicate returns falsey. The predicate is invoked with three arguments: _(value, index, array)_.

**Since**

3.0.0

**Arguments**

1. array_(Array)_: The array to query.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the slice of array.

**Example**

var users = [

  { 'user': 'barney',  'active': false },

  { 'user': 'fred',    'active': false },

  { 'user': 'pebbles', 'active': true }

];

\_.takeWhile(users, function(o) { return !o.active; });

// =\> objects for ['barney', 'fred']

// The `_.matches` iteratee shorthand.

\_.takeWhile(users, { 'user': 'barney', 'active': false });

// =\> objects for ['barney']

// The `_.matchesProperty` iteratee shorthand.

\_.takeWhile(users, ['active', false]);

// =\> objects for ['barney', 'fred']

// The `_.property` iteratee shorthand.

\_.takeWhile(users, 'active');

// =\> []

Try in REPL

## \_.union([arrays])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8310)[npm package](https://www.npmjs.com/package/lodash.union)

Creates an array of unique values, in order, from all given arrays using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons.

**Since**

0.1.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.

**Returns**

_(Array)_: Returns the new array of combined values.

**Example**

\_.union([2], [1, 2]);

// =\> [2, 1]

Try in REPL

## \_.unionBy([arrays], [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8337)[npm package](https://www.npmjs.com/package/lodash.unionby)

This method is like [\_.union](https://lodash.com/docs/#union) except that it accepts iteratee which is invoked for each element of each arrays to generate the criterion by which uniqueness is computed. Result values are chosen from the first array in which the value occurs. The iteratee is invoked with one argument:
_(value)_.

**Since**

4.0.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns the new array of combined values.

**Example**

\_.unionBy([2.1], [1.2, 2.3], Math.floor);

// =\> [2.1, 1.2]

// The `_.property` iteratee shorthand.

\_.unionBy([{ 'x': 1 }], [{ 'x': 2 }, { 'x': 1 }], 'x');

// =\> [{ 'x': 1 }, { 'x': 2 }]

Try in REPL

## \_.unionWith([arrays], [comparator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8366)[npm package](https://www.npmjs.com/package/lodash.unionwith)

This method is like [\_.union](https://lodash.com/docs/#union) except that it accepts comparator which is invoked to compare elements of arrays. Result values are chosen from the first array in which the value occurs. The comparator is invoked with two arguments: _(arrVal, othVal)_.

**Since**

4.0.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.
2. [comparator]_(Function)_: The comparator invoked per element.

**Returns**

_(Array)_: Returns the new array of combined values.

**Example**

var objects = [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }];

var others = [{ 'x': 1, 'y': 1 }, { 'x': 1, 'y': 2 }];

\_.unionWith(objects, others, \_.isEqual);

// =\> [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }, { 'x': 1, 'y': 1 }]

Try in REPL

## \_.uniq(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8390)[npm package](https://www.npmjs.com/package/lodash.uniq)

Creates a duplicate-free version of an array, using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons, in which only the first occurrence of each element is kept. The order of result values is determined by the order they occur in the array.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to inspect.

**Returns**

_(Array)_: Returns the new duplicate free array.

**Example**

\_.uniq([2, 1, 2]);

// =\> [2, 1]

Try in REPL

## \_.uniqBy(array, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8417)[npm package](https://www.npmjs.com/package/lodash.uniqby)

This method is like [\_.uniq](https://lodash.com/docs/#uniq) except that it accepts iteratee which is invoked for each element in array to generate the criterion by which uniqueness is computed. The order of result values is determined by the order they occur in the array. The iteratee is invoked with one argument:
_(value)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns the new duplicate free array.

**Example**

\_.uniqBy([2.1, 1.2, 2.3], Math.floor);

// =\> [2.1, 1.2]

// The `_.property` iteratee shorthand.

\_.uniqBy([{ 'x': 1 }, { 'x': 2 }, { 'x': 1 }], 'x');

// =\> [{ 'x': 1 }, { 'x': 2 }]

Try in REPL

## \_.uniqWith(array, [comparator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8441)[npm package](https://www.npmjs.com/package/lodash.uniqwith)

This method is like [\_.uniq](https://lodash.com/docs/#uniq) except that it accepts comparator which is invoked to compare elements of array. The order of result values is determined by the order they occur in the array.The comparator is invoked with two arguments: _(arrVal, othVal)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [comparator]_(Function)_: The comparator invoked per element.

**Returns**

_(Array)_: Returns the new duplicate free array.

**Example**

var objects = [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }, { 'x': 1, 'y': 2 }];

\_.uniqWith(objects, \_.isEqual);

// =\> [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }]

Try in REPL

## \_.unzip(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8465)[npm package](https://www.npmjs.com/package/lodash.unzip)

This method is like [\_.zip](https://lodash.com/docs/#zip) except that it accepts an array of grouped elements and creates an array regrouping the elements to their pre-zip configuration.

**Since**

1.2.0

**Arguments**

1. array_(Array)_: The array of grouped elements to process.

**Returns**

_(Array)_: Returns the new array of regrouped elements.

**Example**

var zipped = \_.zip(['a', 'b'], [1, 2], [true, false]);

// =\> [['a', 1, true], ['b', 2, false]]

\_.unzip(zipped);

// =\> [['a', 'b'], [1, 2], [true, false]]

Try in REPL

## \_.unzipWith(array, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8502)[npm package](https://www.npmjs.com/package/lodash.unzipwith)

This method is like [\_.unzip](https://lodash.com/docs/#unzip) except that it accepts iteratee to specify how regrouped values should be combined. The iteratee is invoked with the elements of each group: _(...group)_.

**Since**

3.8.0

**Arguments**

1. array_(Array)_: The array of grouped elements to process.
2. [iteratee=\_.identity]_(Function)_: The function to combine regrouped values.

**Returns**

_(Array)_: Returns the new array of regrouped elements.

**Example**

var zipped = \_.zip([1, 2], [10, 20], [100, 200]);

// =\> [[1, 10, 100], [2, 20, 200]]

\_.unzipWith(zipped, \_.add);

// =\> [3, 30, 300]

Try in REPL

## \_.without(array, [values])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8535)[npm package](https://www.npmjs.com/package/lodash.without)

Creates an array excluding all given values using [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) for equality comparisons.

**Note:** Unlike [\_.pull](https://lodash.com/docs/#pull), this method returns a new array.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to inspect.
2. [values]_(...\*)_: The values to exclude.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

\_.without([2, 1, 2, 3], 1, 2);

// =\> [3]

Try in REPL

## \_.xor([arrays])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8559)[npm package](https://www.npmjs.com/package/lodash.xor)

Creates an array of unique values that is the [symmetric difference](https://en.wikipedia.org/wiki/Symmetric_difference) of the given arrays. The order of result values is determined by the order they occur in the arrays.

**Since**

2.4.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

\_.xor([2, 1], [2, 3]);

// =\> [1, 3]

Try in REPL

## \_.xorBy([arrays], [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8586)[npm package](https://www.npmjs.com/package/lodash.xorby)

This method is like [\_.xor](https://lodash.com/docs/#xor) except that it accepts iteratee which is invoked for each element of each arrays to generate the criterion by which by which they're compared. The order of result values is determined by the order they occur in the arrays. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

\_.xorBy([2.1, 1.2], [2.3, 3.4], Math.floor);

// =\> [1.2, 3.4]

// The `_.property` iteratee shorthand.

\_.xorBy([{ 'x': 1 }], [{ 'x': 2 }, { 'x': 1 }], 'x');

// =\> [{ 'x': 2 }]

Try in REPL

## \_.xorWith([arrays], [comparator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8615)[npm package](https://www.npmjs.com/package/lodash.xorwith)

This method is like [\_.xor](https://lodash.com/docs/#xor) except that it accepts comparator which is invoked to compare elements of arrays. The order of result values is determined by the order they occur in the arrays. The comparator is invoked with two arguments: _(arrVal, othVal)_.

**Since**

4.0.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to inspect.
2. [comparator]_(Function)_: The comparator invoked per element.

**Returns**

_(Array)_: Returns the new array of filtered values.

**Example**

var objects = [{ 'x': 1, 'y': 2 }, { 'x': 2, 'y': 1 }];

var others = [{ 'x': 1, 'y': 1 }, { 'x': 1, 'y': 2 }];

\_.xorWith(objects, others, \_.isEqual);

// =\> [{ 'x': 2, 'y': 1 }, { 'x': 1, 'y': 1 }]

Try in REPL

## \_.zip([arrays])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8637)[npm package](https://www.npmjs.com/package/lodash.zip)

Creates an array of grouped elements, the first of which contains the first elements of the given arrays, the second of which contains the second elements of the given arrays, and so on.

**Since**

0.1.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to process.

**Returns**

_(Array)_: Returns the new array of grouped elements.

**Example**

\_.zip(['a', 'b'], [1, 2], [true, false]);

// =\> [['a', 1, true], ['b', 2, false]]

Try in REPL

## \_.zipObject([props=[]], [values=[]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8655)[npm package](https://www.npmjs.com/package/lodash.zipobject)

This method is like [\_.fromPairs](https://lodash.com/docs/#fromPairs) except that it accepts two arrays, one of property identifiers and one of corresponding values.

**Since**

0.4.0

**Arguments**

1. [props=[]]_(Array)_: The property identifiers.
2. [values=[]]_(Array)_: The property values.

**Returns**

_(Object)_: Returns the new object.

**Example**

\_.zipObject(['a', 'b'], [1, 2]);

// =\> { 'a': 1, 'b': 2 }

Try in REPL

## \_.zipObjectDeep([props=[]], [values=[]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8674)[npm package](https://www.npmjs.com/package/lodash.zipobjectdeep)

This method is like [\_.zipObject](https://lodash.com/docs/#zipObject) except that it supports property paths.

**Since**

4.1.0

**Arguments**

1. [props=[]]_(Array)_: The property identifiers.
2. [values=[]]_(Array)_: The property values.

**Returns**

_(Object)_: Returns the new object.

**Example**

\_.zipObjectDeep(['a.b[0].c', 'a.b[1].d'], [1, 2]);

// =\> { 'a': { 'b': [{ 'c': 1 }, { 'd': 2 }] } }

Try in REPL

## \_.zipWith([arrays], [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8698)[npm package](https://www.npmjs.com/package/lodash.zipwith)

This method is like [\_.zip](https://lodash.com/docs/#zip) except that it accepts iteratee to specify how grouped values should be combined. The iteratee is invoked with the elements of each group: _(...group)_.

**Since**

3.8.0

**Arguments**

1. [arrays]_(...Array)_: The arrays to process.
2. [iteratee=\_.identity]_(Function)_: The function to combine grouped values.

**Returns**

_(Array)_: Returns the new array of grouped elements.

**Example**

\_.zipWith([1, 2], [10, 20], [100, 200], function(a, b, c) {

  return a + b + c;

});

// =\> [111, 222]

Try in REPL

## "Collection" Methods

## \_.countBy(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9077)[npm package](https://www.npmjs.com/package/lodash.countby)

Creates an object composed of keys generated from the results of running each element of collection thru iteratee. The corresponding value of each key is the number of times the key was returned by iteratee. The iteratee is invoked with one argument: _(value)_.

**Since**

0.5.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee to transform keys.

**Returns**

_(Object)_: Returns the composed aggregate object.

**Example**

\_.countBy([6.1, 4.2, 6.3], Math.floor);

// =\> { '4': 1, '6': 2 }

// The `_.property` iteratee shorthand.

\_.countBy(['one', 'two', 'three'], 'length');

// =\> { '3': 2, '5': 1 }

Try in REPL

## \_.every(collection, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9126)[npm package](https://www.npmjs.com/package/lodash.every)

Checks if predicate returns truthy for **all** elements of collection. Iteration is stopped once predicate returns falsey. The predicate is invoked with three arguments: _(value, index|key, collection)_.

**Note:** This method returns true for [empty collections](https://en.wikipedia.org/wiki/Empty_set) because [everything is true](https://en.wikipedia.org/wiki/Vacuous_truth) of elements of empty collections.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(boolean)_: Returns true if all elements pass the predicate check, else false.

**Example**

\_.every([true, 1, null, 'yes'], Boolean);

// =\> false

var users = [

  { 'user': 'barney', 'age': 36, 'active': false },

  { 'user': 'fred',   'age': 40, 'active': false }

];

// The `_.matches` iteratee shorthand.

\_.every(users, { 'user': 'barney', 'active': false });

// =\> false

// The `_.matchesProperty` iteratee shorthand.

\_.every(users, ['active', false]);

// =\> true

// The `_.property` iteratee shorthand.

\_.every(users, 'active');

// =\> false

Try in REPL

## \_.filter(collection, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9171)[npm package](https://www.npmjs.com/package/lodash.filter)

Iterates over elements of collection, returning an array of all elements predicate returns truthy for. The predicate is invoked with three arguments: _(value, index|key, collection)_.

**Note:** Unlike [\_.remove](https://lodash.com/docs/#remove), this method returns a new array.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the new filtered array.

**Example**

var users = [

  { 'user': 'barney', 'age': 36, 'active': true },

  { 'user': 'fred',   'age': 40, 'active': false }

];

\_.filter(users, function(o) { return !o.active; });

// =\> objects for ['fred']

// The `_.matches` iteratee shorthand.

\_.filter(users, { 'age': 36, 'active': true });

// =\> objects for ['barney']

// The `_.matchesProperty` iteratee shorthand.

\_.filter(users, ['active', false]);

// =\> objects for ['fred']

// The `_.property` iteratee shorthand.

\_.filter(users, 'active');

// =\> objects for ['barney']

Try in REPL

## \_.find(collection, [predicate=\_.identity], [fromIndex=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9212)[npm package](https://www.npmjs.com/package/lodash.find)

Iterates over elements of collection, returning the first element predicate returns truthy for. The predicate is invoked with three arguments: _(value, index|key, collection)_.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to inspect.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.
3. [fromIndex=0]_(number)_: The index to search from.

**Returns**

_(\*)_: Returns the matched element, else undefined.

**Example**

var users = [

  { 'user': 'barney',  'age': 36, 'active': true },

  { 'user': 'fred',    'age': 40, 'active': false },

  { 'user': 'pebbles', 'age': 1,  'active': true }

];

\_.find(users, function(o) { return o.age \< 40; });

// =\> object for 'barney'

// The `_.matches` iteratee shorthand.

\_.find(users, { 'age': 1, 'active': true });

// =\> object for 'pebbles'

// The `_.matchesProperty` iteratee shorthand.

\_.find(users, ['active', false]);

// =\> object for 'fred'

// The `_.property` iteratee shorthand.

\_.find(users, 'active');

// =\> object for 'barney'

Try in REPL

## \_.findLast(collection, [predicate=\_.identity], [fromIndex=collection.length-1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9233)[npm package](https://www.npmjs.com/package/lodash.findlast)

This method is like [\_.find](https://lodash.com/docs/#find) except that it iterates over elements of collection from right to left.

**Since**

2.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to inspect.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.
3. [fromIndex=collection.length-1]_(number)_: The index to search from.

**Returns**

_(\*)_: Returns the matched element, else undefined.

**Example**

\_.findLast([1, 2, 3, 4], function(n) {

  return n % 2 == 1;

});

// =\> 3

Try in REPL

## \_.flatMap(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9256)[npm package](https://www.npmjs.com/package/lodash.flatmap)

Creates a flattened array of values by running each element in collection thru iteratee and flattening the mapped results. The iteratee is invoked with three arguments: _(value, index|key, collection)_.

**Since**

4.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the new flattened array.

**Example**

function duplicate(n) {

  return [n, n];

}

\_.flatMap([1, 2], duplicate);

// =\> [1, 1, 2, 2]

Try in REPL

## \_.flatMapDeep(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9280)[npm package](https://www.npmjs.com/package/lodash.flatmapdeep)

This method is like [\_.flatMap](https://lodash.com/docs/#flatMap) except that it recursively flattens the mapped results.

**Since**

4.7.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the new flattened array.

**Example**

function duplicate(n) {

  return [[[n, n]]];

}

\_.flatMapDeep([1, 2], duplicate);

// =\> [1, 1, 2, 2]

Try in REPL

## \_.flatMapDepth(collection, [iteratee=\_.identity], [depth=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9305)[npm package](https://www.npmjs.com/package/lodash.flatmapdepth)

This method is like [\_.flatMap](https://lodash.com/docs/#flatMap) except that it recursively flattens the mapped results up to depth times.

**Since**

4.7.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.
3. [depth=1]_(number)_: The maximum recursion depth.

**Returns**

_(Array)_: Returns the new flattened array.

**Example**

function duplicate(n) {

  return [[[n, n]]];

}

\_.flatMapDepth([1, 2], duplicate, 2);

// =\> [[1, 1], [2, 2]]

Try in REPL

## \_.forEach(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9340)[npm package](https://www.npmjs.com/package/lodash.foreach)

Iterates over elements of collection and invokes iteratee for each element. The iteratee is invoked with three arguments: _(value, index|key, collection)_. Iteratee functions may exit iteration early by explicitly returning false.

**Note:** As with other "Collections" methods, objects with a "length" property are iterated like arrays. To avoid this behavior use [\_.forIn](https://lodash.com/docs/#forIn) or [\_.forOwn](https://lodash.com/docs/#forOwn) for object iteration.

**Since**

0.1.0

**Aliases**

_\_.each_

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(\*)_: Returns collection.

**Example**

\_.forEach([1, 2], function(value) {

  console.log(value);

});

// =\> Logs `1` then `2`.

\_.forEach({ 'a': 1, 'b': 2 }, function(value, key) {

  console.log(key);

});

// =\> Logs 'a' then 'b' (iteration order is not guaranteed).

Try in REPL

## \_.forEachRight(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9365)[npm package](https://www.npmjs.com/package/lodash.foreachright)

This method is like [\_.forEach](https://lodash.com/docs/#forEach) except that it iterates over elements of collection from right to left.

**Since**

2.0.0

**Aliases**

_\_.eachRight_

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(\*)_: Returns collection.

**Example**

\_.forEachRight([1, 2], function(value) {

  console.log(value);

});

// =\> Logs `2` then `1`.

Try in REPL

## \_.groupBy(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9393)[npm package](https://www.npmjs.com/package/lodash.groupby)

Creates an object composed of keys generated from the results of running each element of collection thru iteratee. The order of grouped values is determined by the order they occur in collection. The corresponding value of each key is an array of elements responsible for generating the key. The iteratee is invoked with one argument: _(value)_.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee to transform keys.

**Returns**

_(Object)_: Returns the composed aggregate object.

**Example**

\_.groupBy([6.1, 4.2, 6.3], Math.floor);

// =\> { '4': [4.2], '6': [6.1, 6.3] }

// The `_.property` iteratee shorthand.

\_.groupBy(['one', 'two', 'three'], 'length');

// =\> { '3': ['one', 'two'], '5': ['three'] }

Try in REPL

## \_.includes(collection, value, [fromIndex=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9431)[npm package](https://www.npmjs.com/package/lodash.includes)

Checks if value is in collection. If collection is a string, it's checked for a substring of value, otherwise [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) is used for equality comparisons. If fromIndex is negative, it's used as the offset from the end of collection.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object|string)_: The collection to inspect.
2. value_(\*)_: The value to search for.
3. [fromIndex=0]_(number)_: The index to search from.

**Returns**

_(boolean)_: Returns true if value is found, else false.

**Example**

\_.includes([1, 2, 3], 1);

// =\> true

\_.includes([1, 2, 3], 1, 2);

// =\> false

\_.includes({ 'a': 1, 'b': 2 }, 1);

// =\> true

\_.includes('abcd', 'bc');

// =\> true

Try in REPL

## \_.invokeMap(collection, path, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9467)[npm package](https://www.npmjs.com/package/lodash.invokemap)

Invokes the method at path of each element in collection, returning an array of the results of each invoked method. Any additional arguments are provided to each invoked method. If path is a function, it's invoked for, and this bound to, each element in collection.

**Since**

4.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. path_(Array|Function|string)_: The path of the method to invoke or the function invoked per iteration.
3. [args]_(...\*)_: The arguments to invoke each method with.

**Returns**

_(Array)_: Returns the array of results.

**Example**

\_.invokeMap([[5, 1, 7], [3, 2, 1]], 'sort');

// =\> [[1, 5, 7], [1, 2, 3]]

\_.invokeMap([123, 456], String.prototype.split, '');

// =\> [['1', '2', '3'], ['4', '5', '6']]

Try in REPL

## \_.keyBy(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9506)[npm package](https://www.npmjs.com/package/lodash.keyby)

Creates an object composed of keys generated from the results of running each element of collection thru iteratee. The corresponding value of each key is the last element responsible for generating the key. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee to transform keys.

**Returns**

_(Object)_: Returns the composed aggregate object.

**Example**

var array = [

  { 'dir': 'left', 'code': 97 },

  { 'dir': 'right', 'code': 100 }

];

\_.keyBy(array, function(o) {

  return String.fromCharCode(o.code);

});

// =\> { 'a': { 'dir': 'left', 'code': 97 }, 'd': { 'dir': 'right', 'code': 100 } }

\_.keyBy(array, 'dir');

// =\> { 'left': { 'dir': 'left', 'code': 97 }, 'right': { 'dir': 'right', 'code': 100 } }

Try in REPL

## \_.map(collection, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9552)[npm package](https://www.npmjs.com/package/lodash.map)

Creates an array of values by running each element in collection thru iteratee. The iteratee is invoked with three arguments:
_(value, index|key, collection)_.

 Many lodash methods are guarded to work as iteratees for methods like [\_.every](https://lodash.com/docs/#every), [\_.filter](https://lodash.com/docs/#filter), [\_.map](https://lodash.com/docs/#map), [\_.mapValues](https://lodash.com/docs/#mapValues), [\_.reject](https://lodash.com/docs/#reject), and [\_.some](https://lodash.com/docs/#some).

 The guarded methods are:
ary, chunk, curry, curryRight, drop, dropRight, every, fill, invert, parseInt, random, range, rangeRight, repeat, sampleSize, slice, some, sortBy, split, take, takeRight, template, trim, trimEnd, trimStart, and words

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the new mapped array.

**Example**

function square(n) {

  return n \* n;

}

\_.map([4, 8], square);

// =\> [16, 64]

\_.map({ 'a': 4, 'b': 8 }, square);

// =\> [16, 64] (iteration order is not guaranteed)

var users = [

  { 'user': 'barney' },

  { 'user': 'fred' }

];

// The `_.property` iteratee shorthand.

\_.map(users, 'user');

// =\> ['barney', 'fred']

Try in REPL

## \_.orderBy(collection, [iteratees=[\_.identity]], [orders])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9586)[npm package](https://www.npmjs.com/package/lodash.orderby)

This method is like [\_.sortBy](https://lodash.com/docs/#sortBy) except that it allows specifying the sort orders of the iteratees to sort by. If orders is unspecified, all values are sorted in ascending order. Otherwise, specify an order of "desc" for descending or "asc" for ascending sort order of corresponding values.

**Since**

4.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratees=[\_.identity]]_(Array[]|Function[]|Object[]|string[])_: The iteratees to sort by.
3. [orders]_(string[])_: The sort orders of iteratees.

**Returns**

_(Array)_: Returns the new sorted array.

**Example**

var users = [

  { 'user': 'fred',   'age': 48 },

  { 'user': 'barney', 'age': 34 },

  { 'user': 'fred',   'age': 40 },

  { 'user': 'barney', 'age': 36 }

];

// Sort by `user` in ascending order and by `age` in descending order.

\_.orderBy(users, ['user', 'age'], ['asc', 'desc']);

// =\> objects for [['barney', 36], ['barney', 34], ['fred', 48], ['fred', 40]]

Try in REPL

## \_.partition(collection, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9636)[npm package](https://www.npmjs.com/package/lodash.partition)

Creates an array of elements split into two groups, the first of which contains elements predicate returns truthy for, the second of which contains elements predicate returns falsey for. The predicate is invoked with one argument: _(value)_.

**Since**

3.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the array of grouped elements.

**Example**

var users = [

  { 'user': 'barney',  'age': 36, 'active': false },

  { 'user': 'fred',    'age': 40, 'active': true },

  { 'user': 'pebbles', 'age': 1,  'active': false }

];

\_.partition(users, function(o) { return o.active; });

// =\> objects for [['fred'], ['barney', 'pebbles']]

// The `_.matches` iteratee shorthand.

\_.partition(users, { 'age': 1, 'active': false });

// =\> objects for [['pebbles'], ['barney', 'fred']]

// The `_.matchesProperty` iteratee shorthand.

\_.partition(users, ['active', false]);

// =\> objects for [['barney', 'pebbles'], ['fred']]

// The `_.property` iteratee shorthand.

\_.partition(users, 'active');

// =\> objects for [['fred'], ['barney', 'pebbles']]

Try in REPL

## \_.reduce(collection, [iteratee=\_.identity], [accumulator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9677)[npm package](https://www.npmjs.com/package/lodash.reduce)

Reduces collection to a value which is the accumulated result of running each element in collection thru iteratee, where each successive invocation is supplied the return value of the previous. If accumulator is not given, the first element of collection is used as the initial value. The iteratee is invoked with four arguments:
_(accumulator, value, index|key, collection)_.

 Many lodash methods are guarded to work as iteratees for methods like [\_.reduce](https://lodash.com/docs/#reduce), [\_.reduceRight](https://lodash.com/docs/#reduceRight), and [\_.transform](https://lodash.com/docs/#transform).

 The guarded methods are:
assign, defaults, defaultsDeep, includes, merge, orderBy, and sortBy

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.
3. [accumulator]_(\*)_: The initial value.

**Returns**

_(\*)_: Returns the accumulated value.

**Example**

\_.reduce([1, 2], function(sum, n) {

  return sum + n;

}, 0);

// =\> 3

\_.reduce({ 'a': 1, 'b': 2, 'c': 1 }, function(result, value, key) {

  (result[value] || (result[value] = [])).push(key);

  return result;

}, {});

// =\> { '1': ['a', 'c'], '2': ['b'] } (iteration order is not guaranteed)

Try in REPL

## \_.reduceRight(collection, [iteratee=\_.identity], [accumulator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9706)[npm package](https://www.npmjs.com/package/lodash.reduceright)

This method is like [\_.reduce](https://lodash.com/docs/#reduce) except that it iterates over elements of collection from right to left.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.
3. [accumulator]_(\*)_: The initial value.

**Returns**

_(\*)_: Returns the accumulated value.

**Example**

var array = [[0, 1], [2, 3], [4, 5]];

\_.reduceRight(array, function(flattened, other) {

  return flattened.concat(other);

}, []);

// =\> [4, 5, 2, 3, 0, 1]

Try in REPL

## \_.reject(collection, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9747)[npm package](https://www.npmjs.com/package/lodash.reject)

The opposite of [\_.filter](https://lodash.com/docs/#filter); this method returns the elements of collection that predicate does **not** return truthy for.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the new filtered array.

**Example**

var users = [

  { 'user': 'barney', 'age': 36, 'active': false },

  { 'user': 'fred',   'age': 40, 'active': true }

];

\_.reject(users, function(o) { return !o.active; });

// =\> objects for ['fred']

// The `_.matches` iteratee shorthand.

\_.reject(users, { 'age': 40, 'active': true });

// =\> objects for ['barney']

// The `_.matchesProperty` iteratee shorthand.

\_.reject(users, ['active', false]);

// =\> objects for ['fred']

// The `_.property` iteratee shorthand.

\_.reject(users, 'active');

// =\> objects for ['barney']

Try in REPL

## \_.sample(collection)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9766)[npm package](https://www.npmjs.com/package/lodash.sample)

Gets a random element from collection.

**Since**

2.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to sample.

**Returns**

_(\*)_: Returns the random element.

**Example**

\_.sample([1, 2, 3, 4]);

// =\> 2

Try in REPL

## \_.sampleSize(collection, [n=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9791)[npm package](https://www.npmjs.com/package/lodash.samplesize)

Gets n random elements at unique keys from collection up to the size of collection.

**Since**

4.0.0

**Arguments**

1. collection_(Array|Object)_: The collection to sample.
2. [n=1]_(number)_: The number of elements to sample.

**Returns**

_(Array)_: Returns the random elements.

**Example**

\_.sampleSize([1, 2, 3], 2);

// =\> [3, 1]

\_.sampleSize([1, 2, 3], 4);

// =\> [2, 3, 1]

Try in REPL

## \_.shuffle(collection)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9816)[npm package](https://www.npmjs.com/package/lodash.shuffle)

Creates an array of shuffled values, using a version of the [Fisher-Yates shuffle](https://en.wikipedia.org/wiki/Fisher-Yates_shuffle).

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to shuffle.

**Returns**

_(Array)_: Returns the new shuffled array.

**Example**

\_.shuffle([1, 2, 3, 4]);

// =\> [4, 1, 3, 2]

Try in REPL

## \_.size(collection)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9842)[npm package](https://www.npmjs.com/package/lodash.size)

Gets the size of collection by returning its length for array-like values or the number of own enumerable string keyed properties for objects.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object|string)_: The collection to inspect.

**Returns**

_(number)_: Returns the collection size.

**Example**

\_.size([1, 2, 3]);

// =\> 3

\_.size({ 'a': 1, 'b': 2 });

// =\> 2

\_.size('pebbles');

// =\> 7

Try in REPL

## \_.some(collection, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9892)[npm package](https://www.npmjs.com/package/lodash.some)

Checks if predicate returns truthy for **any** element of collection. Iteration is stopped once predicate returns truthy. The predicate is invoked with three arguments: _(value, index|key, collection)_.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(boolean)_: Returns true if any element passes the predicate check, else false.

**Example**

\_.some([null, 0, 'yes', false], Boolean);

// =\> true

var users = [

  { 'user': 'barney', 'active': true },

  { 'user': 'fred',   'active': false }

];

// The `_.matches` iteratee shorthand.

\_.some(users, { 'user': 'barney', 'active': false });

// =\> false

// The `_.matchesProperty` iteratee shorthand.

\_.some(users, ['active', false]);

// =\> true

// The `_.property` iteratee shorthand.

\_.some(users, 'active');

// =\> true

Try in REPL

## \_.sortBy(collection, [iteratees=[\_.identity]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9929)[npm package](https://www.npmjs.com/package/lodash.sortby)

Creates an array of elements, sorted in ascending order by the results of running each element in a collection thru each iteratee. This method performs a stable sort, that is, it preserves the original sort order of equal elements. The iteratees are invoked with one argument: _(value)_.

**Since**

0.1.0

**Arguments**

1. collection_(Array|Object)_: The collection to iterate over.
2. [iteratees=[\_.identity]]_(...(Function|Function[]))_: The iteratees to sort by.

**Returns**

_(Array)_: Returns the new sorted array.

**Example**

var users = [

  { 'user': 'fred',   'age': 48 },

  { 'user': 'barney', 'age': 36 },

  { 'user': 'fred',   'age': 40 },

  { 'user': 'barney', 'age': 34 }

];

\_.sortBy(users, [function(o) { return o.user; }]);

// =\> objects for [['barney', 36], ['barney', 34], ['fred', 48], ['fred', 40]]

\_.sortBy(users, ['user', 'age']);

// =\> objects for [['barney', 34], ['barney', 36], ['fred', 40], ['fred', 48]]

Try in REPL

## "Date" Methods

## \_.now()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9960)[npm package](https://www.npmjs.com/package/lodash.now)

Gets the timestamp of the number of milliseconds that have elapsed since the Unix epoch _(1 January_ _1970 00__:00:00 UTC)_.

**Since**

2.4.0

**Returns**

_(number)_: Returns the timestamp.

**Example**

\_.defer(function(stamp) {

  console.log(\_.now() - stamp);

}, \_.now());

// =\> Logs the number of milliseconds it took for the deferred invocation.

Try in REPL

## "Function" Methods

## \_.after(n, func)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9990)[npm package](https://www.npmjs.com/package/lodash.after)

The opposite of [\_.before](https://lodash.com/docs/#before); this method creates a function that invokes func once it's called n or more times.

**Since**

0.1.0

**Arguments**

1. n_(number)_: The number of calls before func is invoked.
2. func_(Function)_: The function to restrict.

**Returns**

_(Function)_: Returns the new restricted function.

**Example**

var saves = ['profile', 'settings'];

var done = \_.after(saves.length, function() {

  console.log('done saving!');

});

\_.forEach(saves, function(type) {

  asyncSave({ 'type': type, 'complete': done });

});

// =\> Logs 'done saving!' after the two async saves have completed.

Try in REPL

## \_.ary(func, [n=func.length])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10019)[npm package](https://www.npmjs.com/package/lodash.ary)

Creates a function that invokes func, with up to n arguments, ignoring any additional arguments.

**Since**

3.0.0

**Arguments**

1. func_(Function)_: The function to cap arguments for.
2. [n=func.length]_(number)_: The arity cap.

**Returns**

_(Function)_: Returns the new capped function.

**Example**

\_.map(['6', '8', '10'], \_.ary(parseInt, 1));

// =\> [6, 8, 10]

Try in REPL

## \_.before(n, func)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10042)[npm package](https://www.npmjs.com/package/lodash.before)

Creates a function that invokes func, with the this binding and arguments of the created function, while it's called less than n times. Subsequent calls to the created function return the result of the last func invocation.

**Since**

3.0.0

**Arguments**

1. n_(number)_: The number of calls at which func is no longer invoked.
2. func_(Function)_: The function to restrict.

**Returns**

_(Function)_: Returns the new restricted function.

**Example**

jQuery(element).on('click', \_.before(5, addContactToList));

// =\> Allows adding up to 4 contacts to the list.

Try in REPL

## \_.bind(func, thisArg, [partials])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10094)[npm package](https://www.npmjs.com/package/lodash.bind)

Creates a function that invokes func with the this binding of thisArg and partials prepended to the arguments it receives.

 The \_.bind.placeholder value, which defaults to \_ in monolithic builds, may be used as a placeholder for partially applied arguments.

**Note:** Unlike native Function#bind, this method doesn't set the "length" property of bound functions.

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to bind.
2. thisArg_(\*)_: The this binding of func.
3. [partials]_(...\*)_: The arguments to be partially applied.

**Returns**

_(Function)_: Returns the new bound function.

**Example**

function greet(greeting, punctuation) {

  return greeting + ' ' + this.user + punctuation;

}

var object = { 'user': 'fred' };

var bound = \_.bind(greet, object, 'hi');

bound('!');

// =\> 'hi fred!'

// Bound with placeholders.

var bound = \_.bind(greet, object, \_, '!');

bound('hi');

// =\> 'hi fred!'

Try in REPL

## \_.bindKey(object, key, [partials])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10148)[npm package](https://www.npmjs.com/package/lodash.bindkey)

Creates a function that invokes the method at object[key] with partials prepended to the arguments it receives.

 This method differs from [\_.bind](https://lodash.com/docs/#bind) by allowing bound functions to reference methods that may be redefined or don't yet exist. See [Peter Michaux's article](http://peter.michaux.ca/articles/lazy-function-definition-pattern) for more details.

 The \_.bindKey.placeholder value, which defaults to \_ in monolithic builds, may be used as a placeholder for partially applied arguments.

**Since**

0.10.0

**Arguments**

1. object_(Object)_: The object to invoke the method on.
2. key_(string)_: The key of the method.
3. [partials]_(...\*)_: The arguments to be partially applied.

**Returns**

_(Function)_: Returns the new bound function.

**Example**

var object = {

  'user': 'fred',

  'greet': function(greeting, punctuation) {

    return greeting + ' ' + this.user + punctuation;

  }

};

var bound = \_.bindKey(object, 'greet', 'hi');

bound('!');

// =\> 'hi fred!'

object.greet = function(greeting, punctuation) {

  return greeting + 'ya ' + this.user + punctuation;

};

bound('!');

// =\> 'hiya fred!'

// Bound with placeholders.

var bound = \_.bindKey(object, 'greet', \_, '!');

bound('hi');

// =\> 'hiya fred!'

Try in REPL

## \_.curry(func, [arity=func.length])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10198)[npm package](https://www.npmjs.com/package/lodash.curry)

Creates a function that accepts arguments of func and either invokes func returning its result, if at least arity number of arguments have been provided, or returns a function that accepts the remaining func arguments, and so on. The arity of func may be specified if func.length is not sufficient.

 The \_.curry.placeholder value, which defaults to \_ in monolithic builds, may be used as a placeholder for provided arguments.

**Note:** This method doesn't set the "length" property of curried functions.

**Since**

2.0.0

**Arguments**

1. func_(Function)_: The function to curry.
2. [arity=func.length]_(number)_: The arity of func.

**Returns**

_(Function)_: Returns the new curried function.

**Example**

var abc = function(a, b, c) {

  return [a, b, c];

};

var curried = \_.curry(abc);

curried(1)(2)(3);

// =\> [1, 2, 3]

curried(1, 2)(3);

// =\> [1, 2, 3]

curried(1, 2, 3);

// =\> [1, 2, 3]

// Curried with placeholders.

curried(1)(\_, 3)(2);

// =\> [1, 2, 3]

Try in REPL

## \_.curryRight(func, [arity=func.length])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10243)[npm package](https://www.npmjs.com/package/lodash.curryright)

This method is like [\_.curry](https://lodash.com/docs/#curry) except that arguments are applied to func in the manner of [\_.partialRight](https://lodash.com/docs/#partialRight) instead of [\_.partial](https://lodash.com/docs/#partial).

 The \_.curryRight.placeholder value, which defaults to \_ in monolithic builds, may be used as a placeholder for provided arguments.

**Note:** This method doesn't set the "length" property of curried functions.

**Since**

3.0.0

**Arguments**

1. func_(Function)_: The function to curry.
2. [arity=func.length]_(number)_: The arity of func.

**Returns**

_(Function)_: Returns the new curried function.

**Example**

var abc = function(a, b, c) {

  return [a, b, c];

};

var curried = \_.curryRight(abc);

curried(3)(2)(1);

// =\> [1, 2, 3]

curried(2, 3)(1);

// =\> [1, 2, 3]

curried(1, 2, 3);

// =\> [1, 2, 3]

// Curried with placeholders.

curried(3)(1, \_)(2);

// =\> [1, 2, 3]

Try in REPL

## \_.debounce(func, [wait=0], [options={}])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10304)[npm package](https://www.npmjs.com/package/lodash.debounce)

Creates a debounced function that delays invoking func until after wait milliseconds have elapsed since the last time the debounced function was invoked. The debounced function comes with a cancel method to cancel delayed func invocations and a flush method to immediately invoke them. Provide options to indicate whether func should be invoked on the leading and/or trailing edge of the wait timeout. The func is invoked with the last arguments provided to the debounced function. Subsequent calls to the debounced function return the result of the last func invocation.

**Note:** If leading and trailing options are true, func is invoked on the trailing edge of the timeout only if the debounced function is invoked more than once during the wait timeout.

 If wait is 0 and leading is false, func invocation is deferred until to the next tick, similar to setTimeout with a timeout of 0.

 See [David Corbacho's article](https://css-tricks.com/debouncing-throttling-explained-examples/) for details over the differences between [\_.debounce](https://lodash.com/docs/#debounce) and [\_.throttle](https://lodash.com/docs/#throttle).

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to debounce.
2. [wait=0]_(number)_: The number of milliseconds to delay.
3. [options={}]_(Object)_: The options object.
4. [options.leading=false]_(boolean)_: Specify invoking on the leading edge of the timeout.
5. [options.maxWait]_(number)_: The maximum time func is allowed to be delayed before it's invoked.
6. [options.trailing=true]_(boolean)_: Specify invoking on the trailing edge of the timeout.

**Returns**

_(Function)_: Returns the new debounced function.

**Example**

// Avoid costly calculations while the window size is in flux.

jQuery(window).on('resize', \_.debounce(calculateLayout, 150));

// Invoke `sendMail` when clicked, debouncing subsequent calls.

jQuery(element).on('click', \_.debounce(sendMail, 300, {

  'leading': true,

  'trailing': false

}));

// Ensure `batchLog` is invoked once after 1 second of debounced calls.

var debounced = \_.debounce(batchLog, 250, { 'maxWait': 1000 });

var source = new EventSource('/stream');

jQuery(source).on('message', debounced);

// Cancel the trailing debounced invocation.

jQuery(window).on('popstate', debounced.cancel);

Try in REPL

## \_.defer(func, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10447)[npm package](https://www.npmjs.com/package/lodash.defer)

Defers invoking the func until the current call stack has cleared. Any additional arguments are provided to func when it's invoked.

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to defer.
2. [args]_(...\*)_: The arguments to invoke func with.

**Returns**

_(number)_: Returns the timer id.

**Example**

\_.defer(function(text) {

  console.log(text);

}, 'deferred');

// =\> Logs 'deferred' after one millisecond.

Try in REPL

## \_.delay(func, wait, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10470)[npm package](https://www.npmjs.com/package/lodash.delay)

Invokes func after wait milliseconds. Any additional arguments are provided to func when it's invoked.

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to delay.
2. wait_(number)_: The number of milliseconds to delay invocation.
3. [args]_(...\*)_: The arguments to invoke func with.

**Returns**

_(number)_: Returns the timer id.

**Example**

\_.delay(function(text) {

  console.log(text);

}, 1000, 'later');

// =\> Logs 'later' after one second.

Try in REPL

## \_.flip(func)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10492)[npm package](https://www.npmjs.com/package/lodash.flip)

Creates a function that invokes func with arguments reversed.

**Since**

4.0.0

**Arguments**

1. func_(Function)_: The function to flip arguments for.

**Returns**

_(Function)_: Returns the new flipped function.

**Example**

var flipped = \_.flip(function() {

  return \_.toArray(arguments);

});

flipped('a', 'b', 'c', 'd');

// =\> ['d', 'c', 'b', 'a']

Try in REPL

## \_.memoize(func, [resolver])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10540)[npm package](https://www.npmjs.com/package/lodash.memoize)

Creates a function that memoizes the result of func. If resolver is provided, it determines the cache key for storing the result based on the arguments provided to the memoized function. By default, the first argument provided to the memoized function is used as the map cache key. The func is invoked with the this binding of the memoized function.

**Note:** The cache is exposed as the cache property on the memoized function. Its creation may be customized by replacing the \_.memoize.Cache constructor with one whose instances implement the [Map](http://ecma-international.org/ecma-262/7.0/#sec-properties-of-the-map-prototype-object) method interface of clear, delete, get, has, and set.

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to have its output memoized.
2. [resolver]_(Function)_: The function to resolve the cache key.

**Returns**

_(Function)_: Returns the new memoized function.

**Example**

var object = { 'a': 1, 'b': 2 };

var other = { 'c': 3, 'd': 4 };

var values = \_.memoize(\_.values);

values(object);

// =\> [1, 2]

values(other);

// =\> [3, 4]

object.a = 2;

values(object);

// =\> [1, 2]

// Modify the result cache.

values.cache.set(object, ['a', 'b']);

values(object);

// =\> ['a', 'b']

// Replace `_.memoize.Cache`.

\_.memoize.Cache = WeakMap;

Try in REPL

## \_.negate(predicate)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10583)[npm package](https://www.npmjs.com/package/lodash.negate)

Creates a function that negates the result of the predicate func. The func predicate is invoked with the this binding and arguments of the created function.

**Since**

3.0.0

**Arguments**

1. predicate_(Function)_: The predicate to negate.

**Returns**

_(Function)_: Returns the new negated function.

**Example**

function isEven(n) {

  return n % 2 == 0;

}

\_.filter([1, 2, 3, 4, 5, 6], \_.negate(isEven));

// =\> [1, 3, 5]

Try in REPL

## \_.once(func)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10617)[npm package](https://www.npmjs.com/package/lodash.once)

Creates a function that is restricted to invoking func once. Repeat calls to the function return the value of the first invocation. The func is invoked with the this binding and arguments of the created function.

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to restrict.

**Returns**

_(Function)_: Returns the new restricted function.

**Example**

var initialize = \_.once(createApplication);

initialize();

initialize();

// =\> `createApplication` is invoked once

Try in REPL

## \_.overArgs(func, [transforms=[\_.identity]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10652)[npm package](https://www.npmjs.com/package/lodash.overargs)

Creates a function that invokes func with its arguments transformed.

**Since**

4.0.0

**Arguments**

1. func_(Function)_: The function to wrap.
2. [transforms=[\_.identity]]_(...(Function|Function[]))_: The argument transforms.

**Returns**

_(Function)_: Returns the new function.

**Example**

function doubled(n) {

  return n \* 2;

}

function square(n) {

  return n \* n;

}

var func = \_.overArgs(function(x, y) {

  return [x, y];

}, [square, doubled]);

func(9, 3);

// =\> [81, 6]

func(10, 5);

// =\> [100, 10]

Try in REPL

## \_.partial(func, [partials])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10702)[npm package](https://www.npmjs.com/package/lodash.partial)

Creates a function that invokes func with partials prepended to the arguments it receives. This method is like [\_.bind](https://lodash.com/docs/#bind) except it does **not** alter the this binding.

 The \_.partial.placeholder value, which defaults to \_ in monolithic builds, may be used as a placeholder for partially applied arguments.

**Note:** This method doesn't set the "length" property of partially applied functions.

**Since**

0.2.0

**Arguments**

1. func_(Function)_: The function to partially apply arguments to.
2. [partials]_(...\*)_: The arguments to be partially applied.

**Returns**

_(Function)_: Returns the new partially applied function.

**Example**

function greet(greeting, name) {

  return greeting + ' ' + name;

}

var sayHelloTo = \_.partial(greet, 'hello');

sayHelloTo('fred');

// =\> 'hello fred'

// Partially applied with placeholders.

var greetFred = \_.partial(greet, \_, 'fred');

greetFred('hi');

// =\> 'hi fred'

Try in REPL

## \_.partialRight(func, [partials])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10739)[npm package](https://www.npmjs.com/package/lodash.partialright)

This method is like [\_.partial](https://lodash.com/docs/#partial) except that partially applied arguments are appended to the arguments it receives.

 The \_.partialRight.placeholder value, which defaults to \_ in monolithic builds, may be used as a placeholder for partially applied arguments.

**Note:** This method doesn't set the "length" property of partially applied functions.

**Since**

1.0.0

**Arguments**

1. func_(Function)_: The function to partially apply arguments to.
2. [partials]_(...\*)_: The arguments to be partially applied.

**Returns**

_(Function)_: Returns the new partially applied function.

**Example**

function greet(greeting, name) {

  return greeting + ' ' + name;

}

var greetFred = \_.partialRight(greet, 'fred');

greetFred('hi');

// =\> 'hi fred'

// Partially applied with placeholders.

var sayHelloTo = \_.partialRight(greet, 'hello', \_);

sayHelloTo('fred');

// =\> 'hello fred'

Try in REPL

## \_.rearg(func, indexes)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10766)[npm package](https://www.npmjs.com/package/lodash.rearg)

Creates a function that invokes func with arguments arranged according to the specified indexes where the argument value at the first index is provided as the first argument, the argument value at the second index is provided as the second argument, and so on.

**Since**

3.0.0

**Arguments**

1. func_(Function)_: The function to rearrange arguments for.
2. indexes_(...(number|number[]))_: The arranged argument indexes.

**Returns**

_(Function)_: Returns the new function.

**Example**

var rearged = \_.rearg(function(a, b, c) {

  return [a, b, c];

}, [2, 0, 1]);

rearged('b', 'c', 'a')

// =\> ['a', 'b', 'c']

Try in REPL

## \_.rest(func, [start=func.length-1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10795)[npm package](https://www.npmjs.com/package/lodash.rest)

Creates a function that invokes func with the this binding of the created function and arguments from start and beyond provided as an array.

**Note:** This method is based on the [rest parameter](https://mdn.io/rest_parameters).

**Since**

4.0.0

**Arguments**

1. func_(Function)_: The function to apply a rest parameter to.
2. [start=func.length-1]_(number)_: The start position of the rest parameter.

**Returns**

_(Function)_: Returns the new function.

**Example**

var say = \_.rest(function(what, names) {

  return what + ' ' + \_.initial(names).join(', ') +

    (\_.size(names) \> 1 ? ', & ' : '') + \_.last(names);

});

say('hello', 'fred', 'barney', 'pebbles');

// =\> 'hello fred, barney, & pebbles'

Try in REPL

## \_.spread(func, [start=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10837)[npm package](https://www.npmjs.com/package/lodash.spread)

Creates a function that invokes func with the this binding of the create function and an array of arguments much like [Function#apply](http://www.ecma-international.org/ecma-262/7.0/#sec-function.prototype.apply).

**Note:** This method is based on the [spread operator](https://mdn.io/spread_operator).

**Since**

3.2.0

**Arguments**

1. func_(Function)_: The function to spread arguments over.
2. [start=0]_(number)_: The start position of the spread.

**Returns**

_(Function)_: Returns the new function.

**Example**

var say = \_.spread(function(who, what) {

  return who + ' says ' + what;

});

say(['fred', 'hello']);

// =\> 'fred says hello'

var numbers = Promise.all([

  Promise.resolve(40),

  Promise.resolve(36)

]);

numbers.then(\_.spread(function(x, y) {

  return x + y;

}));

// =\> a Promise of 76

Try in REPL

## \_.throttle(func, [wait=0], [options={}])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10897)[npm package](https://www.npmjs.com/package/lodash.throttle)

Creates a throttled function that only invokes func at most once per every wait milliseconds. The throttled function comes with a cancel method to cancel delayed func invocations and a flush method to immediately invoke them. Provide options to indicate whether func should be invoked on the leading and/or trailing edge of the wait timeout. The func is invoked with the last arguments provided to the throttled function. Subsequent calls to the throttled function return the result of the last func invocation.

**Note:** If leading and trailing options are true, func is invoked on the trailing edge of the timeout only if the throttled function is invoked more than once during the wait timeout.

 If wait is 0 and leading is false, func invocation is deferred until to the next tick, similar to setTimeout with a timeout of 0.

 See [David Corbacho's article](https://css-tricks.com/debouncing-throttling-explained-examples/) for details over the differences between [\_.throttle](https://lodash.com/docs/#throttle) and [\_.debounce](https://lodash.com/docs/#debounce).

**Since**

0.1.0

**Arguments**

1. func_(Function)_: The function to throttle.
2. [wait=0]_(number)_: The number of milliseconds to throttle invocations to.
3. [options={}]_(Object)_: The options object.
4. [options.leading=true]_(boolean)_: Specify invoking on the leading edge of the timeout.
5. [options.trailing=true]_(boolean)_: Specify invoking on the trailing edge of the timeout.

**Returns**

_(Function)_: Returns the new throttled function.

**Example**

// Avoid excessively updating the position while scrolling.

jQuery(window).on('scroll', \_.throttle(updatePosition, 100));

// Invoke `renewToken` when the click event is fired, but not more than once every 5 minutes.

var throttled = \_.throttle(renewToken, 300000, { 'trailing': false });

jQuery(element).on('click', throttled);

// Cancel the trailing throttled invocation.

jQuery(window).on('popstate', throttled.cancel);

Try in REPL

## \_.unary(func)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10930)[npm package](https://www.npmjs.com/package/lodash.unary)

Creates a function that accepts up to one argument, ignoring any additional arguments.

**Since**

4.0.0

**Arguments**

1. func_(Function)_: The function to cap arguments for.

**Returns**

_(Function)_: Returns the new capped function.

**Example**

\_.map(['6', '8', '10'], \_.unary(parseInt));

// =\> [6, 8, 10]

Try in REPL

## \_.wrap(value, [wrapper=identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10956)[npm package](https://www.npmjs.com/package/lodash.wrap)

Creates a function that provides value to wrapper as its first argument. Any additional arguments provided to the function are appended to those provided to the wrapper. The wrapper is invoked with the this binding of the created function.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to wrap.
2. [wrapper=identity]_(Function)_: The wrapper function.

**Returns**

_(Function)_: Returns the new function.

**Example**

var p = \_.wrap(\_.escape, function(func, text) {

  return '\<p\>' + func(text) + '\</p\>';

});

p('fred, barney, & pebbles');

// =\> '\<p\>fred, barney, &amp; pebbles\</p\>'

Try in REPL

## "Lang" Methods

## \_.castArray(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L10995)[npm package](https://www.npmjs.com/package/lodash.castarray)

Casts value as an array if it's not one.

**Since**

4.4.0

**Arguments**

1. value_(\*)_: The value to inspect.

**Returns**

_(Array)_: Returns the cast array.

**Example**

\_.castArray(1);

// =\> [1]

\_.castArray({ 'a': 1 });

// =\> [{ 'a': 1 }]

\_.castArray('abc');

// =\> ['abc']

\_.castArray(null);

// =\> [null]

\_.castArray(undefined);

// =\> [undefined]

\_.castArray();

// =\> []

var array = [1, 2, 3];

console.log(\_.castArray(array) === array);

// =\> true

Try in REPL

## \_.clone(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11029)[npm package](https://www.npmjs.com/package/lodash.clone)

Creates a shallow clone of value.

**Note:** This method is loosely based on the [structured clone algorithm](https://mdn.io/Structured_clone_algorithm) and supports cloning arrays, array buffers, booleans, date objects, maps, numbers, Object objects, regexes, sets, strings, symbols, and typed arrays. The own enumerable properties of arguments objects are cloned as plain objects. An empty object is returned for uncloneable values such as error objects, functions, DOM nodes, and WeakMaps.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to clone.

**Returns**

_(\*)_: Returns the cloned value.

**Example**

var objects = [{ 'a': 1 }, { 'b': 2 }];

var shallow = \_.clone(objects);

console.log(shallow[0] === objects[0]);

// =\> true

Try in REPL

## \_.cloneDeep(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11087)[npm package](https://www.npmjs.com/package/lodash.clonedeep)

This method is like [\_.clone](https://lodash.com/docs/#clone) except that it recursively clones value.

**Since**

1.0.0

**Arguments**

1. value_(\*)_: The value to recursively clone.

**Returns**

_(\*)_: Returns the deep cloned value.

**Example**

var objects = [{ 'a': 1 }, { 'b': 2 }];

var deep = \_.cloneDeep(objects);

console.log(deep[0] === objects[0]);

// =\> false

Try in REPL

## \_.cloneDeepWith(value, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11119)[npm package](https://www.npmjs.com/package/lodash.clonedeepwith)

This method is like [\_.cloneWith](https://lodash.com/docs/#cloneWith) except that it recursively clones value.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to recursively clone.
2. [customizer]_(Function)_: The function to customize cloning.

**Returns**

_(\*)_: Returns the deep cloned value.

**Example**

function customizer(value) {

  if (\_.isElement(value)) {

    return value.cloneNode(true);

  }

}

var el = \_.cloneDeepWith(document.body, customizer);

console.log(el === document.body);

// =\> false

console.log(el.nodeName);

// =\> 'BODY'

console.log(el.childNodes.length);

// =\> 20

Try in REPL

## \_.cloneWith(value, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11064)[npm package](https://www.npmjs.com/package/lodash.clonewith)

This method is like [\_.clone](https://lodash.com/docs/#clone) except that it accepts customizer which is invoked to produce the cloned value. If customizer returns undefined, cloning is handled by the method instead. The customizer is invoked with up to four arguments; _(value [, index|key, object, stack])_.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to clone.
2. [customizer]_(Function)_: The function to customize cloning.

**Returns**

_(\*)_: Returns the cloned value.

**Example**

function customizer(value) {

  if (\_.isElement(value)) {

    return value.cloneNode(false);

  }

}

var el = \_.cloneWith(document.body, customizer);

console.log(el === document.body);

// =\> false

console.log(el.nodeName);

// =\> 'BODY'

console.log(el.childNodes.length);

// =\> 0

Try in REPL

## \_.conformsTo(object, source)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11148)[npm package](https://www.npmjs.com/package/lodash.conformsto)

Checks if object conforms to source by invoking the predicate properties of source with the corresponding property values of object.

**Note:** This method is equivalent to [\_.conforms](https://lodash.com/docs/#conforms) when source is partially applied.

**Since**

4.14.0

**Arguments**

1. object_(Object)_: The object to inspect.
2. source_(Object)_: The object of property predicates to conform to.

**Returns**

_(boolean)_: Returns true if object conforms, else false.

**Example**

var object = { 'a': 1, 'b': 2 };

\_.conformsTo(object, { 'b': function(n) { return n \> 1; } });

// =\> true

\_.conformsTo(object, { 'b': function(n) { return n \> 2; } });

// =\> false

Try in REPL

## \_.eq(value, other)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11184)[npm package](https://www.npmjs.com/package/lodash.eq)

Performs a [SameValueZero](http://ecma-international.org/ecma-262/7.0/#sec-samevaluezero) comparison between two values to determine if they are equivalent.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.

**Returns**

_(boolean)_: Returns true if the values are equivalent, else false.

**Example**

var object = { 'a': 1 };

var other = { 'a': 1 };

\_.eq(object, object);

// =\> true

\_.eq(object, other);

// =\> false

\_.eq('a', 'a');

// =\> true

\_.eq('a', Object('a'));

// =\> false

\_.eq(NaN, NaN);

// =\> true

Try in REPL

## \_.gt(value, other)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11211)[npm package](https://www.npmjs.com/package/lodash.gt)

Checks if value is greater than other.

**Since**

3.9.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.

**Returns**

_(boolean)_: Returns true if value is greater than other, else false.

**Example**

\_.gt(3, 1);

// =\> true

\_.gt(3, 3);

// =\> false

\_.gt(1, 3);

// =\> false

Try in REPL

## \_.gte(value, other)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11236)[npm package](https://www.npmjs.com/package/lodash.gte)

Checks if value is greater than or equal to other.

**Since**

3.9.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.

**Returns**

_(boolean)_: Returns true if value is greater than or equal to other, else false.

**Example**

\_.gte(3, 1);

// =\> true

\_.gte(3, 3);

// =\> true

\_.gte(1, 3);

// =\> false

Try in REPL

## \_.isArguments(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11258)[npm package](https://www.npmjs.com/package/lodash.isarguments)

Checks if value is likely an arguments object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an arguments object, else false.

**Example**

\_.isArguments(function() { return arguments; }());

// =\> true

\_.isArguments([1, 2, 3]);

// =\> false

Try in REPL

## \_.isArray(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11286)[npm package](https://www.npmjs.com/package/lodash.isarray)

Checks if value is classified as an Array object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an array, else false.

**Example**

\_.isArray([1, 2, 3]);

// =\> true

\_.isArray(document.body.children);

// =\> false

\_.isArray('abc');

// =\> false

\_.isArray(\_.noop);

// =\> false

Try in REPL

## \_.isArrayBuffer(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11305)[npm package](https://www.npmjs.com/package/lodash.isarraybuffer)

Checks if value is classified as an ArrayBuffer object.

**Since**

4.3.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an array buffer, else false.

**Example**

\_.isArrayBuffer(new ArrayBuffer(2));

// =\> true

\_.isArrayBuffer(new Array(2));

// =\> false

Try in REPL

## \_.isArrayLike(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11332)[npm package](https://www.npmjs.com/package/lodash.isarraylike)

Checks if value is array-like. A value is considered array-like if it's not a function and has a value.length that's an integer greater than or equal to 0 and less than or equal to Number.MAX\_SAFE\_INTEGER.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is array-like, else false.

**Example**

\_.isArrayLike([1, 2, 3]);

// =\> true

\_.isArrayLike(document.body.children);

// =\> true

\_.isArrayLike('abc');

// =\> true

\_.isArrayLike(\_.noop);

// =\> false

Try in REPL

## \_.isArrayLikeObject(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11361)[npm package](https://www.npmjs.com/package/lodash.isarraylikeobject)

This method is like [\_.isArrayLike](https://lodash.com/docs/#isArrayLike) except that it also checks if value is an object.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an array-like object, else false.

**Example**

\_.isArrayLikeObject([1, 2, 3]);

// =\> true

\_.isArrayLikeObject(document.body.children);

// =\> true

\_.isArrayLikeObject('abc');

// =\> false

\_.isArrayLikeObject(\_.noop);

// =\> false

Try in REPL

## \_.isBoolean(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11382)[npm package](https://www.npmjs.com/package/lodash.isboolean)

Checks if value is classified as a boolean primitive or object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a boolean, else false.

**Example**

\_.isBoolean(false);

// =\> true

\_.isBoolean(null);

// =\> false

Try in REPL

## \_.isBuffer(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11404)[npm package](https://www.npmjs.com/package/lodash.isbuffer)

Checks if value is a buffer.

**Since**

4.3.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a buffer, else false.

**Example**

\_.isBuffer(new Buffer(2));

// =\> true

\_.isBuffer(new Uint8Array(2));

// =\> false

Try in REPL

## \_.isDate(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11423)[npm package](https://www.npmjs.com/package/lodash.isdate)

Checks if value is classified as a Date object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a date object, else false.

**Example**

\_.isDate(new Date);

// =\> true

\_.isDate('Mon April 23 2012');

// =\> false

Try in REPL

## \_.isElement(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11442)[npm package](https://www.npmjs.com/package/lodash.iselement)

Checks if value is likely a DOM element.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a DOM element, else false.

**Example**

\_.isElement(document.body);

// =\> true

\_.isElement('\<body\>');

// =\> false

Try in REPL

## \_.isEmpty(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11479)[npm package](https://www.npmjs.com/package/lodash.isempty)

Checks if value is an empty object, collection, map, or set.

 Objects are considered empty if they have no own enumerable string keyed properties.

 Array-like values such as arguments objects, arrays, buffers, strings, or jQuery-like collections are considered empty if they have a length of 0. Similarly, maps and sets are considered empty if they have a size of 0.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is empty, else false.

**Example**

\_.isEmpty(null);

// =\> true

\_.isEmpty(true);

// =\> true

\_.isEmpty(1);

// =\> true

\_.isEmpty([1, 2, 3]);

// =\> false

\_.isEmpty({ 'a': 1 });

// =\> false

Try in REPL

## \_.isEqual(value, other)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11531)[npm package](https://www.npmjs.com/package/lodash.isequal)

Performs a deep comparison between two values to determine if they are equivalent.

**Note:** This method supports comparing arrays, array buffers, booleans, date objects, error objects, maps, numbers, Object objects, regexes, sets, strings, symbols, and typed arrays. Object objects are compared by their own, not inherited, enumerable properties. Functions and DOM nodes are compared by strict equality, i.e. ===.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.

**Returns**

_(boolean)_: Returns true if the values are equivalent, else false.

**Example**

var object = { 'a': 1 };

var other = { 'a': 1 };

\_.isEqual(object, other);

// =\> true

object === other;

// =\> false

Try in REPL

## \_.isEqualWith(value, other, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11567)[npm package](https://www.npmjs.com/package/lodash.isequalwith)

This method is like [\_.isEqual](https://lodash.com/docs/#isEqual) except that it accepts customizer which is invoked to compare values. If customizer returns undefined, comparisons are handled by the method instead. The customizer is invoked with up to six arguments: _(objValue, othValue [, index|key, object, other, stack])_.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.
3. [customizer]_(Function)_: The function to customize comparisons.

**Returns**

_(boolean)_: Returns true if the values are equivalent, else false.

**Example**

function isGreeting(value) {

  return /^h(?:i|ello)$/.test(value);

}

function customizer(objValue, othValue) {

  if (isGreeting(objValue) && isGreeting(othValue)) {

    return true;

  }

}

var array = ['hello', 'goodbye'];

var other = ['hi', 'goodbye'];

\_.isEqualWith(array, other, customizer);

// =\> true

Try in REPL

## \_.isError(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11591)[npm package](https://www.npmjs.com/package/lodash.iserror)

Checks if value is an Error, EvalError, RangeError, ReferenceError, SyntaxError, TypeError, or URIError object.

**Since**

3.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an error object, else false.

**Example**

\_.isError(new Error);

// =\> true

\_.isError(Error);

// =\> false

Try in REPL

## \_.isFinite(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11626)[npm package](https://www.npmjs.com/package/lodash.isfinite)

Checks if value is a finite primitive number.

**Note:** This method is based on [Number.isFinite](https://mdn.io/Number/isFinite).

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a finite number, else false.

**Example**

\_.isFinite(3);

// =\> true

\_.isFinite(Number.MIN\_VALUE);

// =\> true

\_.isFinite(Infinity);

// =\> false

\_.isFinite('3');

// =\> false

Try in REPL

## \_.isFunction(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11647)[npm package](https://www.npmjs.com/package/lodash.isfunction)

Checks if value is classified as a Function object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a function, else false.

**Example**

\_.isFunction(\_);

// =\> true

\_.isFunction(/abc/);

// =\> false

Try in REPL

## \_.isInteger(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11683)[npm package](https://www.npmjs.com/package/lodash.isinteger)

Checks if value is an integer.

**Note:** This method is based on [Number.isInteger](https://mdn.io/Number/isInteger).

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an integer, else false.

**Example**

\_.isInteger(3);

// =\> true

\_.isInteger(Number.MIN\_VALUE);

// =\> false

\_.isInteger(Infinity);

// =\> false

\_.isInteger('3');

// =\> false

Try in REPL

## \_.isLength(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11713)[npm package](https://www.npmjs.com/package/lodash.islength)

Checks if value is a valid array-like length.

**Note:** This method is loosely based on [ToLength](http://ecma-international.org/ecma-262/7.0/#sec-tolength).

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a valid length, else false.

**Example**

\_.isLength(3);

// =\> true

\_.isLength(Number.MIN\_VALUE);

// =\> false

\_.isLength(Infinity);

// =\> false

\_.isLength('3');

// =\> false

Try in REPL

## \_.isMap(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11793)[npm package](https://www.npmjs.com/package/lodash.ismap)

Checks if value is classified as a Map object.

**Since**

4.3.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a map, else false.

**Example**

\_.isMap(new Map);

// =\> true

\_.isMap(new WeakMap);

// =\> false

Try in REPL

## \_.isMatch(object, source)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11823)[npm package](https://www.npmjs.com/package/lodash.ismatch)

Performs a partial deep comparison between object and source to determine if object contains equivalent property values.

**Note:** This method is equivalent to [\_.matches](https://lodash.com/docs/#matches) when source is partially applied.

 Partial comparisons will match empty array and empty object source values against any array or object value, respectively. See [\_.isEqual](https://lodash.com/docs/#isEqual) for a list of supported value comparisons.

**Since**

3.0.0

**Arguments**

1. object_(Object)_: The object to inspect.
2. source_(Object)_: The object of property values to match.

**Returns**

_(boolean)_: Returns true if object is a match, else false.

**Example**

var object = { 'a': 1, 'b': 2 };

\_.isMatch(object, { 'b': 2 });

// =\> true

\_.isMatch(object, { 'b': 1 });

// =\> false

Try in REPL

## \_.isMatchWith(object, source, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11859)[npm package](https://www.npmjs.com/package/lodash.ismatchwith)

This method is like [\_.isMatch](https://lodash.com/docs/#isMatch) except that it accepts customizer which is invoked to compare values. If customizer returns undefined, comparisons are handled by the method instead. The customizer is invoked with five arguments: _(objValue, srcValue, index|key, object, source)_.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The object to inspect.
2. source_(Object)_: The object of property values to match.
3. [customizer]_(Function)_: The function to customize comparisons.

**Returns**

_(boolean)_: Returns true if object is a match, else false.

**Example**

function isGreeting(value) {

  return /^h(?:i|ello)$/.test(value);

}

function customizer(objValue, srcValue) {

  if (isGreeting(objValue) && isGreeting(srcValue)) {

    return true;

  }

}

var object = { 'greeting': 'hello' };

var source = { 'greeting': 'hi' };

\_.isMatchWith(object, source, customizer);

// =\> true

Try in REPL

## \_.isNaN(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11892)[npm package](https://www.npmjs.com/package/lodash.isnan)

Checks if value is NaN.

**Note:** This method is based on [Number.isNaN](https://mdn.io/Number/isNaN) and is not the same as global [isNaN](https://mdn.io/isNaN) which returns true for undefined and other non-number values.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is NaN, else false.

**Example**

\_.isNaN(NaN);

// =\> true

\_.isNaN(new Number(NaN));

// =\> true

isNaN(undefined);

// =\> true

\_.isNaN(undefined);

// =\> false

Try in REPL

## \_.isNative(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11925)[npm package](https://www.npmjs.com/package/lodash.isnative)

Checks if value is a pristine native function.

**Note:** This method can't reliably detect native functions in the presence of the core-js package because core-js circumvents this kind of detection. Despite multiple requests, the core-js maintainer has made it clear: any attempt to fix the detection will be obstructed. As a result, we're left with little choice but to throw an error. Unfortunately, this also affects packages, like [babel-polyfill](https://www.npmjs.com/package/babel-polyfill), which rely on core-js.

**Since**

3.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a native function, else false.

**Example**

\_.isNative(Array.prototype.push);

// =\> true

\_.isNative(\_);

// =\> false

Try in REPL

## \_.isNil(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11973)[npm package](https://www.npmjs.com/package/lodash.isnil)

Checks if value is null or undefined.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is nullish, else false.

**Example**

\_.isNil(null);

// =\> true

\_.isNil(void 0);

// =\> true

\_.isNil(NaN);

// =\> false

Try in REPL

## \_.isNull(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11949)[npm package](https://www.npmjs.com/package/lodash.isnull)

Checks if value is null.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is null, else false.

**Example**

\_.isNull(null);

// =\> true

\_.isNull(void 0);

// =\> false

Try in REPL

## \_.isNumber(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12003)[npm package](https://www.npmjs.com/package/lodash.isnumber)

Checks if value is classified as a Number primitive or object.

**Note:** To exclude Infinity, -Infinity, and NaN, which are classified as numbers, use the [\_.isFinite](https://lodash.com/docs/#isFinite) method.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a number, else false.

**Example**

\_.isNumber(3);

// =\> true

\_.isNumber(Number.MIN\_VALUE);

// =\> true

\_.isNumber(Infinity);

// =\> true

\_.isNumber('3');

// =\> false

Try in REPL

## \_.isObject(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11743)[npm package](https://www.npmjs.com/package/lodash.isobject)

Checks if value is the [language type](http://www.ecma-international.org/ecma-262/7.0/#sec-ecmascript-language-types) of Object. _(e.g. arrays, functions, objects, regexes,_ _new Number(0)__, and_ _new String('')__)_

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is an object, else false.

**Example**

\_.isObject({});

// =\> true

\_.isObject([1, 2, 3]);

// =\> true

\_.isObject(\_.noop);

// =\> true

\_.isObject(null);

// =\> false

Try in REPL

## \_.isObjectLike(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L11772)[npm package](https://www.npmjs.com/package/lodash.isobjectlike)

Checks if value is object-like. A value is object-like if it's not null and has a typeof result of "object".

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is object-like, else false.

**Example**

\_.isObjectLike({});

// =\> true

\_.isObjectLike([1, 2, 3]);

// =\> true

\_.isObjectLike(\_.noop);

// =\> false

\_.isObjectLike(null);

// =\> false

Try in REPL

## \_.isPlainObject(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12036)[npm package](https://www.npmjs.com/package/lodash.isplainobject)

Checks if value is a plain object, that is, an object created by the Object constructor or one with a [[Prototype]] of null.

**Since**

0.8.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a plain object, else false.

**Example**

function Foo() {

  this.a = 1;

}

\_.isPlainObject(new Foo);

// =\> false

\_.isPlainObject([1, 2, 3]);

// =\> false

\_.isPlainObject({ 'x': 0, 'y': 0 });

// =\> true

\_.isPlainObject(Object.create(null));

// =\> true

Try in REPL

## \_.isRegExp(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12066)[npm package](https://www.npmjs.com/package/lodash.isregexp)

Checks if value is classified as a RegExp object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a regexp, else false.

**Example**

\_.isRegExp(/abc/);

// =\> true

\_.isRegExp('/abc/');

// =\> false

Try in REPL

## \_.isSafeInteger(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12095)[npm package](https://www.npmjs.com/package/lodash.issafeinteger)

Checks if value is a safe integer. An integer is safe if it's an IEEE-754 double precision number which isn't the result of a rounded unsafe integer.

**Note:** This method is based on [Number.isSafeInteger](https://mdn.io/Number/isSafeInteger).

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a safe integer, else false.

**Example**

\_.isSafeInteger(3);

// =\> true

\_.isSafeInteger(Number.MIN\_VALUE);

// =\> false

\_.isSafeInteger(Infinity);

// =\> false

\_.isSafeInteger('3');

// =\> false

Try in REPL

## \_.isSet(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12116)[npm package](https://www.npmjs.com/package/lodash.isset)

Checks if value is classified as a Set object.

**Since**

4.3.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a set, else false.

**Example**

\_.isSet(new Set);

// =\> true

\_.isSet(new WeakSet);

// =\> false

Try in REPL

## \_.isString(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12135)[npm package](https://www.npmjs.com/package/lodash.isstring)

Checks if value is classified as a String primitive or object.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a string, else false.

**Example**

\_.isString('abc');

// =\> true

\_.isString(1);

// =\> false

Try in REPL

## \_.isSymbol(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12157)[npm package](https://www.npmjs.com/package/lodash.issymbol)

Checks if value is classified as a Symbol primitive or object.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a symbol, else false.

**Example**

\_.isSymbol(Symbol.iterator);

// =\> true

\_.isSymbol('abc');

// =\> false

Try in REPL

## \_.isTypedArray(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12179)[npm package](https://www.npmjs.com/package/lodash.istypedarray)

Checks if value is classified as a typed array.

**Since**

3.0.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a typed array, else false.

**Example**

\_.isTypedArray(new Uint8Array);

// =\> true

\_.isTypedArray([]);

// =\> false

Try in REPL

## \_.isUndefined(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12198)[npm package](https://www.npmjs.com/package/lodash.isundefined)

Checks if value is undefined.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is undefined, else false.

**Example**

\_.isUndefined(void 0);

// =\> true

\_.isUndefined(null);

// =\> false

Try in REPL

## \_.isWeakMap(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12219)[npm package](https://www.npmjs.com/package/lodash.isweakmap)

Checks if value is classified as a WeakMap object.

**Since**

4.3.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a weak map, else false.

**Example**

\_.isWeakMap(new WeakMap);

// =\> true

\_.isWeakMap(new Map);

// =\> false

Try in REPL

## \_.isWeakSet(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12240)[npm package](https://www.npmjs.com/package/lodash.isweakset)

Checks if value is classified as a WeakSet object.

**Since**

4.3.0

**Arguments**

1. value_(\*)_: The value to check.

**Returns**

_(boolean)_: Returns true if value is a weak set, else false.

**Example**

\_.isWeakSet(new WeakSet);

// =\> true

\_.isWeakSet(new Set);

// =\> false

Try in REPL

## \_.lt(value, other)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12267)[npm package](https://www.npmjs.com/package/lodash.lt)

Checks if value is less than other.

**Since**

3.9.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.

**Returns**

_(boolean)_: Returns true if value is less than other, else false.

**Example**

\_.lt(1, 3);

// =\> true

\_.lt(3, 3);

// =\> false

\_.lt(3, 1);

// =\> false

Try in REPL

## \_.lte(value, other)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12292)[npm package](https://www.npmjs.com/package/lodash.lte)

Checks if value is less than or equal to other.

**Since**

3.9.0

**Arguments**

1. value_(\*)_: The value to compare.
2. other_(\*)_: The other value to compare.

**Returns**

_(boolean)_: Returns true if value is less than or equal to other, else false.

**Example**

\_.lte(1, 3);

// =\> true

\_.lte(3, 3);

// =\> true

\_.lte(3, 1);

// =\> false

Try in REPL

## \_.toArray(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12319)[npm package](https://www.npmjs.com/package/lodash.toarray)

Converts value to an array.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(Array)_: Returns the converted array.

**Example**

\_.toArray({ 'a': 1, 'b': 2 });

// =\> [1, 2]

\_.toArray('abc');

// =\> ['a', 'b', 'c']

\_.toArray(1);

// =\> []

\_.toArray(null);

// =\> []

Try in REPL

## \_.toFinite(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12358)[npm package](https://www.npmjs.com/package/lodash.tofinite)

Converts value to a finite number.

**Since**

4.12.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(number)_: Returns the converted number.

**Example**

\_.toFinite(3.2);

// =\> 3.2

\_.toFinite(Number.MIN\_VALUE);

// =\> 5e-324

\_.toFinite(Infinity);

// =\> 1.7976931348623157e+308

\_.toFinite('3.2');

// =\> 3.2

Try in REPL

## \_.toInteger(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12396)[npm package](https://www.npmjs.com/package/lodash.tointeger)

Converts value to an integer.

**Note:** This method is loosely based on [ToInteger](http://www.ecma-international.org/ecma-262/7.0/#sec-tointeger).

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(number)_: Returns the converted integer.

**Example**

\_.toInteger(3.2);

// =\> 3

\_.toInteger(Number.MIN\_VALUE);

// =\> 0

\_.toInteger(Infinity);

// =\> 1.7976931348623157e+308

\_.toInteger('3.2');

// =\> 3

Try in REPL

## \_.toLength(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12430)[npm package](https://www.npmjs.com/package/lodash.tolength)

Converts value to an integer suitable for use as the length of an array-like object.

**Note:** This method is based on [ToLength](http://ecma-international.org/ecma-262/7.0/#sec-tolength).

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(number)_: Returns the converted integer.

**Example**

\_.toLength(3.2);

// =\> 3

\_.toLength(Number.MIN\_VALUE);

// =\> 0

\_.toLength(Infinity);

// =\> 4294967295

\_.toLength('3.2');

// =\> 3

Try in REPL

## \_.toNumber(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12457)[npm package](https://www.npmjs.com/package/lodash.tonumber)

Converts value to a number.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to process.

**Returns**

_(number)_: Returns the number.

**Example**

\_.toNumber(3.2);

// =\> 3.2

\_.toNumber(Number.MIN\_VALUE);

// =\> 5e-324

\_.toNumber(Infinity);

// =\> Infinity

\_.toNumber('3.2');

// =\> 3.2

Try in REPL

## \_.toPlainObject(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12502)[npm package](https://www.npmjs.com/package/lodash.toplainobject)

Converts value to a plain object flattening inherited enumerable string keyed properties of value to own properties of the plain object.

**Since**

3.0.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(Object)_: Returns the converted plain object.

**Example**

function Foo() {

  this.b = 2;

}

Foo.prototype.c = 3;

\_.assign({ 'a': 1 }, new Foo);

// =\> { 'a': 1, 'b': 2 }

\_.assign({ 'a': 1 }, \_.toPlainObject(new Foo));

// =\> { 'a': 1, 'b': 2, 'c': 3 }

Try in REPL

## \_.toSafeInteger(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12530)[npm package](https://www.npmjs.com/package/lodash.tosafeinteger)

Converts value to a safe integer. A safe integer can be compared and represented correctly.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(number)_: Returns the converted integer.

**Example**

\_.toSafeInteger(3.2);

// =\> 3

\_.toSafeInteger(Number.MIN\_VALUE);

// =\> 0

\_.toSafeInteger(Infinity);

// =\> 9007199254740991

\_.toSafeInteger('3.2');

// =\> 3

Try in REPL

## \_.toString(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12557)[npm package](https://www.npmjs.com/package/lodash.tostring)

Converts value to a string. An empty string is returned for null and undefined values. The sign of -0 is preserved.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(string)_: Returns the converted string.

**Example**

\_.toString(null);

// =\> ''

\_.toString(-0);

// =\> '-0'

\_.toString([1, 2, 3]);

// =\> '1,2,3'

Try in REPL

## "Math" Methods

## \_.add(augend, addend)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16192)[npm package](https://www.npmjs.com/package/lodash.add)

Adds two numbers.

**Since**

3.4.0

**Arguments**

1. augend_(number)_: The first number in an addition.
2. addend_(number)_: The second number in an addition.

**Returns**

_(number)_: Returns the total.

**Example**

\_.add(6, 4);

// =\> 10

Try in REPL

## \_.ceil(number, [precision=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16217)[npm package](https://www.npmjs.com/package/lodash.ceil)

Computes number rounded up to precision.

**Since**

3.10.0

**Arguments**

1. number_(number)_: The number to round up.
2. [precision=0]_(number)_: The precision to round up to.

**Returns**

_(number)_: Returns the rounded up number.

**Example**

\_.ceil(4.006);

// =\> 5

\_.ceil(6.004, 2);

// =\> 6.01

\_.ceil(6040, -2);

// =\> 6100

Try in REPL

## \_.divide(dividend, divisor)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16234)[npm package](https://www.npmjs.com/package/lodash.divide)

Divide two numbers.

**Since**

4.7.0

**Arguments**

1. dividend_(number)_: The first number in a division.
2. divisor_(number)_: The second number in a division.

**Returns**

_(number)_: Returns the quotient.

**Example**

\_.divide(6, 4);

// =\> 1.5

Try in REPL

## \_.floor(number, [precision=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16259)[npm package](https://www.npmjs.com/package/lodash.floor)

Computes number rounded down to precision.

**Since**

3.10.0

**Arguments**

1. number_(number)_: The number to round down.
2. [precision=0]_(number)_: The precision to round down to.

**Returns**

_(number)_: Returns the rounded down number.

**Example**

\_.floor(4.006);

// =\> 4

\_.floor(0.046, 2);

// =\> 0.04

\_.floor(4060, -2);

// =\> 4000

Try in REPL

## \_.max(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16279)[npm package](https://www.npmjs.com/package/lodash.max)

Computes the maximum value of array. If array is empty or falsey, undefined is returned.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to iterate over.

**Returns**

_(\*)_: Returns the maximum value.

**Example**

\_.max([4, 2, 8, 6]);

// =\> 8

\_.max([]);

// =\> undefined

Try in REPL

## \_.maxBy(array, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16308)[npm package](https://www.npmjs.com/package/lodash.maxby)

This method is like [\_.max](https://lodash.com/docs/#max) except that it accepts iteratee which is invoked for each element in array to generate the criterion by which the value is ranked. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(\*)_: Returns the maximum value.

**Example**

var objects = [{ 'n': 1 }, { 'n': 2 }];

\_.maxBy(objects, function(o) { return o.n; });

// =\> { 'n': 2 }

// The `_.property` iteratee shorthand.

\_.maxBy(objects, 'n');

// =\> { 'n': 2 }

Try in REPL

## \_.mean(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16328)[npm package](https://www.npmjs.com/package/lodash.mean)

Computes the mean of the values in array.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to iterate over.

**Returns**

_(number)_: Returns the mean.

**Example**

\_.mean([4, 2, 8, 6]);

// =\> 5

Try in REPL

## \_.meanBy(array, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16355)[npm package](https://www.npmjs.com/package/lodash.meanby)

This method is like [\_.mean](https://lodash.com/docs/#mean) except that it accepts iteratee which is invoked for each element in array to generate the value to be averaged. The iteratee is invoked with one argument: _(value)_.

**Since**

4.7.0

**Arguments**

1. array_(Array)_: The array to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(number)_: Returns the mean.

**Example**

var objects = [{ 'n': 4 }, { 'n': 2 }, { 'n': 8 }, { 'n': 6 }];

\_.meanBy(objects, function(o) { return o.n; });

// =\> 5

// The `_.property` iteratee shorthand.

\_.meanBy(objects, 'n');

// =\> 5

Try in REPL

## \_.min(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16377)[npm package](https://www.npmjs.com/package/lodash.min)

Computes the minimum value of array. If array is empty or falsey, undefined is returned.

**Since**

0.1.0

**Arguments**

1. array_(Array)_: The array to iterate over.

**Returns**

_(\*)_: Returns the minimum value.

**Example**

\_.min([4, 2, 8, 6]);

// =\> 2

\_.min([]);

// =\> undefined

Try in REPL

## \_.minBy(array, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16406)[npm package](https://www.npmjs.com/package/lodash.minby)

This method is like [\_.min](https://lodash.com/docs/#min) except that it accepts iteratee which is invoked for each element in array to generate the criterion by which the value is ranked. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(\*)_: Returns the minimum value.

**Example**

var objects = [{ 'n': 1 }, { 'n': 2 }];

\_.minBy(objects, function(o) { return o.n; });

// =\> { 'n': 1 }

// The `_.property` iteratee shorthand.

\_.minBy(objects, 'n');

// =\> { 'n': 1 }

Try in REPL

## \_.multiply(multiplier, multiplicand)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16427)[npm package](https://www.npmjs.com/package/lodash.multiply)

Multiply two numbers.

**Since**

4.7.0

**Arguments**

1. multiplier_(number)_: The first number in a multiplication.
2. multiplicand_(number)_: The second number in a multiplication.

**Returns**

_(number)_: Returns the product.

**Example**

\_.multiply(6, 4);

// =\> 24

Try in REPL

## \_.round(number, [precision=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16452)[npm package](https://www.npmjs.com/package/lodash.round)

Computes number rounded to precision.

**Since**

3.10.0

**Arguments**

1. number_(number)_: The number to round.
2. [precision=0]_(number)_: The precision to round to.

**Returns**

_(number)_: Returns the rounded number.

**Example**

\_.round(4.006);

// =\> 4

\_.round(4.006, 2);

// =\> 4.01

\_.round(4060, -2);

// =\> 4100

Try in REPL

## \_.subtract(minuend, subtrahend)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16469)[npm package](https://www.npmjs.com/package/lodash.subtract)

Subtract two numbers.

**Since**

4.0.0

**Arguments**

1. minuend_(number)_: The first number in a subtraction.
2. subtrahend_(number)_: The second number in a subtraction.

**Returns**

_(number)_: Returns the difference.

**Example**

\_.subtract(6, 4);

// =\> 2

Try in REPL

## \_.sum(array)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16487)[npm package](https://www.npmjs.com/package/lodash.sum)

Computes the sum of the values in array.

**Since**

3.4.0

**Arguments**

1. array_(Array)_: The array to iterate over.

**Returns**

_(number)_: Returns the sum.

**Example**

\_.sum([4, 2, 8, 6]);

// =\> 20

Try in REPL

## \_.sumBy(array, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16516)[npm package](https://www.npmjs.com/package/lodash.sumby)

This method is like [\_.sum](https://lodash.com/docs/#sum) except that it accepts iteratee which is invoked for each element in array to generate the value to be summed. The iteratee is invoked with one argument: _(value)_.

**Since**

4.0.0

**Arguments**

1. array_(Array)_: The array to iterate over.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(number)_: Returns the sum.

**Example**

var objects = [{ 'n': 4 }, { 'n': 2 }, { 'n': 8 }, { 'n': 6 }];

\_.sumBy(objects, function(o) { return o.n; });

// =\> 20

// The `_.property` iteratee shorthand.

\_.sumBy(objects, 'n');

// =\> 20

Try in REPL

## "Number" Methods

## \_.clamp(number, [lower], upper)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13981)[npm package](https://www.npmjs.com/package/lodash.clamp)

Clamps number within the inclusive lower and upper bounds.

**Since**

4.0.0

**Arguments**

1. number_(number)_: The number to clamp.
2. [lower]_(number)_: The lower bound.
3. upper_(number)_: The upper bound.

**Returns**

_(number)_: Returns the clamped number.

**Example**

\_.clamp(-10, -5, 5);

// =\> -5

\_.clamp(10, -5, 5);

// =\> 5

Try in REPL

## \_.inRange(number, [start=0], end)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14035)[npm package](https://www.npmjs.com/package/lodash.inrange)

Checks if n is between start and up to, but not including, end. If end is not specified, it's set to start with start then set to 0. If start is greater than end the params are swapped to support negative ranges.

**Since**

3.3.0

**Arguments**

1. number_(number)_: The number to check.
2. [start=0]_(number)_: The start of the range.
3. end_(number)_: The end of the range.

**Returns**

_(boolean)_: Returns true if number is in the range, else false.

**Example**

\_.inRange(3, 2, 4);

// =\> true

\_.inRange(4, 8);

// =\> true

\_.inRange(4, 2);

// =\> false

\_.inRange(2, 2);

// =\> false

\_.inRange(1.2, 2);

// =\> true

\_.inRange(5.2, 4);

// =\> false

\_.inRange(-3, -2, -6);

// =\> true

Try in REPL

## \_.random([lower=0], [upper=1], [floating])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14078)[npm package](https://www.npmjs.com/package/lodash.random)

Produces a random number between the inclusive lower and upper bounds. If only one argument is provided a number between 0 and the given number is returned. If floating is true, or either lower or upper are floats, a floating-point number is returned instead of an integer.

**Note:** JavaScript follows the IEEE-754 standard for resolving floating-point values which can produce unexpected results.

**Since**

0.7.0

**Arguments**

1. [lower=0]_(number)_: The lower bound.
2. [upper=1]_(number)_: The upper bound.
3. [floating]_(boolean)_: Specify returning a floating-point number.

**Returns**

_(number)_: Returns the random number.

**Example**

\_.random(0, 5);

// =\> an integer between 0 and 5

\_.random(5);

// =\> also an integer between 0 and 5

\_.random(5, true);

// =\> a floating-point number between 0 and 5

\_.random(1.2, 5.2);

// =\> a floating-point number between 1.2 and 5.2

Try in REPL

## "Object" Methods

## \_.assign(object, [sources])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12595)[npm package](https://www.npmjs.com/package/lodash.assign)

Assigns own enumerable string keyed properties of source objects to the destination object. Source objects are applied from left to right. Subsequent sources overwrite property assignments of previous sources.

**Note:** This method mutates object and is loosely based on [Object.assign](https://mdn.io/Object/assign).

**Since**

0.10.0

**Arguments**

1. object_(Object)_: The destination object.
2. [sources]_(...Object)_: The source objects.

**Returns**

_(Object)_: Returns object.

**Example**

function Foo() {

  this.a = 1;

}

function Bar() {

  this.c = 3;

}

Foo.prototype.b = 2;

Bar.prototype.d = 4;

\_.assign({ 'a': 0 }, new Foo, new Bar);

// =\> { 'a': 1, 'c': 3 }

Try in REPL

## \_.assignIn(object, [sources])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12638)[npm package](https://www.npmjs.com/package/lodash.assignin)

This method is like [\_.assign](https://lodash.com/docs/#assign) except that it iterates over own and inherited source properties.

**Note:** This method mutates object.

**Since**

4.0.0

**Aliases**

_\_.extend_

**Arguments**

1. object_(Object)_: The destination object.
2. [sources]_(...Object)_: The source objects.

**Returns**

_(Object)_: Returns object.

**Example**

function Foo() {

  this.a = 1;

}

function Bar() {

  this.c = 3;

}

Foo.prototype.b = 2;

Bar.prototype.d = 4;

\_.assignIn({ 'a': 0 }, new Foo, new Bar);

// =\> { 'a': 1, 'b': 2, 'c': 3, 'd': 4 }

Try in REPL

## \_.assignInWith(object, sources, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12671)[npm package](https://www.npmjs.com/package/lodash.assigninwith)

This method is like [\_.assignIn](https://lodash.com/docs/#assignIn) except that it accepts customizer which is invoked to produce the assigned values. If customizer returns undefined, assignment is handled by the method instead. The customizer is invoked with five arguments: _(objValue, srcValue, key, object, source)_.

**Note:** This method mutates object.

**Since**

4.0.0

**Aliases**

_\_.extendWith_

**Arguments**

1. object_(Object)_: The destination object.
2. sources_(...Object)_: The source objects.
3. [customizer]_(Function)_: The function to customize assigned values.

**Returns**

_(Object)_: Returns object.

**Example**

function customizer(objValue, srcValue) {

  return \_.isUndefined(objValue) ? srcValue : objValue;

}

var defaults = \_.partialRight(\_.assignInWith, customizer);

defaults({ 'a': 1 }, { 'b': 2 }, { 'a': 3 });

// =\> { 'a': 1, 'b': 2 }

Try in REPL

## \_.assignWith(object, sources, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12703)[npm package](https://www.npmjs.com/package/lodash.assignwith)

This method is like [\_.assign](https://lodash.com/docs/#assign) except that it accepts customizer which is invoked to produce the assigned values. If customizer returns undefined, assignment is handled by the method instead. The customizer is invoked with five arguments: _(objValue, srcValue, key, object, source)_.

**Note:** This method mutates object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The destination object.
2. sources_(...Object)_: The source objects.
3. [customizer]_(Function)_: The function to customize assigned values.

**Returns**

_(Object)_: Returns object.

**Example**

function customizer(objValue, srcValue) {

  return \_.isUndefined(objValue) ? srcValue : objValue;

}

var defaults = \_.partialRight(\_.assignWith, customizer);

defaults({ 'a': 1 }, { 'b': 2 }, { 'a': 3 });

// =\> { 'a': 1, 'b': 2 }

Try in REPL

## \_.at(object, [paths])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12724)[npm package](https://www.npmjs.com/package/lodash.at)

Creates an array of values corresponding to paths of object.

**Since**

1.0.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [paths]_(...(string|string[]))_: The property paths to pick.

**Returns**

_(Array)_: Returns the picked values.

**Example**

var object = { 'a': [{ 'b': { 'c': 3 } }, 4] };

\_.at(object, ['a[0].b.c', 'a[1]']);

// =\> [3, 4]

Try in REPL

## \_.create(prototype, [properties])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12760)[npm package](https://www.npmjs.com/package/lodash.create)

Creates an object that inherits from the prototype object. If a properties object is given, its own enumerable string keyed properties are assigned to the created object.

**Since**

2.3.0

**Arguments**

1. prototype_(Object)_: The object to inherit from.
2. [properties]_(Object)_: The properties to assign to the object.

**Returns**

_(Object)_: Returns the new object.

**Example**

function Shape() {

  this.x = 0;

  this.y = 0;

}

function Circle() {

  Shape.call(this);

}

Circle.prototype = \_.create(Shape.prototype, {

  'constructor': Circle

});

var circle = new Circle;

circle instanceof Circle;

// =\> true

circle instanceof Shape;

// =\> true

Try in REPL

## \_.defaults(object, [sources])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12786)[npm package](https://www.npmjs.com/package/lodash.defaults)

Assigns own and inherited enumerable string keyed properties of source objects to the destination object for all destination properties that resolve to undefined. Source objects are applied from left to right. Once a property is set, additional values of the same property are ignored.

**Note:** This method mutates object.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The destination object.
2. [sources]_(...Object)_: The source objects.

**Returns**

_(Object)_: Returns object.

**Example**

\_.defaults({ 'a': 1 }, { 'b': 2 }, { 'a': 3 });

// =\> { 'a': 1, 'b': 2 }

Try in REPL

## \_.defaultsDeep(object, [sources])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12836)[npm package](https://www.npmjs.com/package/lodash.defaultsdeep)

This method is like [\_.defaults](https://lodash.com/docs/#defaults) except that it recursively assigns default properties.

**Note:** This method mutates object.

**Since**

3.10.0

**Arguments**

1. object_(Object)_: The destination object.
2. [sources]_(...Object)_: The source objects.

**Returns**

_(Object)_: Returns object.

**Example**

\_.defaultsDeep({ 'a': { 'b': 2 } }, { 'a': { 'b': 1, 'c': 3 } });

// =\> { 'a': { 'b': 2, 'c': 3 } }

Try in REPL

## \_.findKey(object, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12876)[npm package](https://www.npmjs.com/package/lodash.findkey)

This method is like [\_.find](https://lodash.com/docs/#find) except that it returns the key of the first element predicate returns truthy for instead of the element itself.

**Since**

1.1.0

**Arguments**

1. object_(Object)_: The object to inspect.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(\*)_: Returns the key of the matched element, else undefined.

**Example**

var users = {

  'barney':  { 'age': 36, 'active': true },

  'fred':    { 'age': 40, 'active': false },

  'pebbles': { 'age': 1,  'active': true }

};

\_.findKey(users, function(o) { return o.age \< 40; });

// =\> 'barney' (iteration order is not guaranteed)

// The `_.matches` iteratee shorthand.

\_.findKey(users, { 'age': 1, 'active': true });

// =\> 'pebbles'

// The `_.matchesProperty` iteratee shorthand.

\_.findKey(users, ['active', false]);

// =\> 'fred'

// The `_.property` iteratee shorthand.

\_.findKey(users, 'active');

// =\> 'barney'

Try in REPL

## \_.findLastKey(object, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12915)[npm package](https://www.npmjs.com/package/lodash.findlastkey)

This method is like [\_.findKey](https://lodash.com/docs/#findKey) except that it iterates over elements of a collection in the opposite order.

**Since**

2.0.0

**Arguments**

1. object_(Object)_: The object to inspect.
2. [predicate=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(\*)_: Returns the key of the matched element, else undefined.

**Example**

var users = {

  'barney':  { 'age': 36, 'active': true },

  'fred':    { 'age': 40, 'active': false },

  'pebbles': { 'age': 1,  'active': true }

};

\_.findLastKey(users, function(o) { return o.age \< 40; });

// =\> returns 'pebbles' assuming `_.findKey` returns 'barney'

// The `_.matches` iteratee shorthand.

\_.findLastKey(users, { 'age': 36, 'active': true });

// =\> 'barney'

// The `_.matchesProperty` iteratee shorthand.

\_.findLastKey(users, ['active', false]);

// =\> 'fred'

// The `_.property` iteratee shorthand.

\_.findLastKey(users, 'active');

// =\> 'pebbles'

Try in REPL

## \_.forIn(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12947)[npm package](https://www.npmjs.com/package/lodash.forin)

Iterates over own and inherited enumerable string keyed properties of an object and invokes iteratee for each property. The iteratee is invoked with three arguments: _(value, key, object)_. Iteratee functions may exit iteration early by explicitly returning false.

**Since**

0.3.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Object)_: Returns object.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.forIn(new Foo, function(value, key) {

  console.log(key);

});

// =\> Logs 'a', 'b', then 'c' (iteration order is not guaranteed).

Try in REPL

## \_.forInRight(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12979)[npm package](https://www.npmjs.com/package/lodash.forinright)

This method is like [\_.forIn](https://lodash.com/docs/#forIn) except that it iterates over properties of object in the opposite order.

**Since**

2.0.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Object)_: Returns object.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.forInRight(new Foo, function(value, key) {

  console.log(key);

});

// =\> Logs 'c', 'b', then 'a' assuming `_.forIn` logs 'a', 'b', then 'c'.

Try in REPL

## \_.forOwn(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13013)[npm package](https://www.npmjs.com/package/lodash.forown)

Iterates over own enumerable string keyed properties of an object and invokes iteratee for each property. The iteratee is invoked with three arguments: _(value, key, object)_. Iteratee functions may exit iteration early by explicitly returning false.

**Since**

0.3.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Object)_: Returns object.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.forOwn(new Foo, function(value, key) {

  console.log(key);

});

// =\> Logs 'a' then 'b' (iteration order is not guaranteed).

Try in REPL

## \_.forOwnRight(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13043)[npm package](https://www.npmjs.com/package/lodash.forownright)

This method is like [\_.forOwn](https://lodash.com/docs/#forOwn) except that it iterates over properties of object in the opposite order.

**Since**

2.0.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Object)_: Returns object.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.forOwnRight(new Foo, function(value, key) {

  console.log(key);

});

// =\> Logs 'b' then 'a' assuming `_.forOwn` logs 'a' then 'b'.

Try in REPL

## \_.functions(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13070)[npm package](https://www.npmjs.com/package/lodash.functions)

Creates an array of function property names from own enumerable properties of object.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The object to inspect.

**Returns**

_(Array)_: Returns the function names.

**Example**

function Foo() {

  this.a = \_.constant('a');

  this.b = \_.constant('b');

}

Foo.prototype.c = \_.constant('c');

\_.functions(new Foo);

// =\> ['a', 'b']

Try in REPL

## \_.functionsIn(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13097)[npm package](https://www.npmjs.com/package/lodash.functionsin)

Creates an array of function property names from own and inherited enumerable properties of object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The object to inspect.

**Returns**

_(Array)_: Returns the function names.

**Example**

function Foo() {

  this.a = \_.constant('a');

  this.b = \_.constant('b');

}

Foo.prototype.c = \_.constant('c');

\_.functionsIn(new Foo);

// =\> ['a', 'b', 'c']

Try in REPL

## \_.get(object, path, [defaultValue])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13126)[npm package](https://www.npmjs.com/package/lodash.get)

Gets the value at path of object. If the resolved value is undefined, the defaultValue is returned in its place.

**Since**

3.7.0

**Arguments**

1. object_(Object)_: The object to query.
2. path_(Array|string)_: The path of the property to get.
3. [defaultValue]_(\*)_: The value returned for undefined resolved values.

**Returns**

_(\*)_: Returns the resolved value.

**Example**

var object = { 'a': [{ 'b': { 'c': 3 } }] };

\_.get(object, 'a[0].b.c');

// =\> 3

\_.get(object, ['a', '0', 'b', 'c']);

// =\> 3

\_.get(object, 'a.b.c', 'default');

// =\> 'default'

Try in REPL

## \_.has(object, path)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13158)[npm package](https://www.npmjs.com/package/lodash.has)

Checks if path is a direct property of object.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The object to query.
2. path_(Array|string)_: The path to check.

**Returns**

_(boolean)_: Returns true if path exists, else false.

**Example**

var object = { 'a': { 'b': 2 } };

var other = \_.create({ 'a': \_.create({ 'b': 2 }) });

\_.has(object, 'a');

// =\> true

\_.has(object, 'a.b');

// =\> true

\_.has(object, ['a', 'b']);

// =\> true

\_.has(other, 'a');

// =\> false

Try in REPL

## \_.hasIn(object, path)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13188)[npm package](https://www.npmjs.com/package/lodash.hasin)

Checks if path is a direct or inherited property of object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The object to query.
2. path_(Array|string)_: The path to check.

**Returns**

_(boolean)_: Returns true if path exists, else false.

**Example**

var object = \_.create({ 'a': \_.create({ 'b': 2 }) });

\_.hasIn(object, 'a');

// =\> true

\_.hasIn(object, 'a.b');

// =\> true

\_.hasIn(object, ['a', 'b']);

// =\> true

\_.hasIn(object, 'b');

// =\> false

Try in REPL

## \_.invert(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13210)[npm package](https://www.npmjs.com/package/lodash.invert)

Creates an object composed of the inverted keys and values of object. If object contains duplicate values, subsequent values overwrite property assignments of previous values.

**Since**

0.7.0

**Arguments**

1. object_(Object)_: The object to invert.

**Returns**

_(Object)_: Returns the new inverted object.

**Example**

var object = { 'a': 1, 'b': 2, 'c': 1 };

\_.invert(object);

// =\> { '1': 'c', '2': 'b' }

Try in REPL

## \_.invertBy(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13245)[npm package](https://www.npmjs.com/package/lodash.invertby)

This method is like [\_.invert](https://lodash.com/docs/#invert) except that the inverted object is generated from the results of running each element of object thru iteratee. The corresponding inverted value of each inverted key is an array of keys responsible for generating the inverted value. The iteratee is invoked with one argument: _(value)_.

**Since**

4.1.0

**Arguments**

1. object_(Object)_: The object to invert.
2. [iteratee=\_.identity]_(Function)_: The iteratee invoked per element.

**Returns**

_(Object)_: Returns the new inverted object.

**Example**

var object = { 'a': 1, 'b': 2, 'c': 1 };

\_.invertBy(object);

// =\> { '1': ['a', 'c'], '2': ['b'] }

\_.invertBy(object, function(value) {

  return 'group' + value;

});

// =\> { 'group1': ['a', 'c'], 'group2': ['b'] }

Try in REPL

## \_.invoke(object, path, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13276)[npm package](https://www.npmjs.com/package/lodash.invoke)

Invokes the method at path of object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The object to query.
2. path_(Array|string)_: The path of the method to invoke.
3. [args]_(...\*)_: The arguments to invoke the method with.

**Returns**

_(\*)_: Returns the result of the invoked method.

**Example**

var object = { 'a': [{ 'b': { 'c': [1, 2, 3, 4] } }] };

\_.invoke(object, 'a[0].b.c.slice', 1, 3);

// =\> [2, 3]

Try in REPL

## \_.keys(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13306)[npm package](https://www.npmjs.com/package/lodash.keys)

Creates an array of the own enumerable property names of object.

**Note:** Non-object values are coerced to objects. See the [ES spec](http://ecma-international.org/ecma-262/7.0/#sec-object.keys) for more details.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Array)_: Returns the array of property names.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.keys(new Foo);

// =\> ['a', 'b'] (iteration order is not guaranteed)

\_.keys('hi');

// =\> ['0', '1']

Try in REPL

## \_.keysIn(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13333)[npm package](https://www.npmjs.com/package/lodash.keysin)

Creates an array of the own and inherited enumerable property names of object.

**Note:** Non-object values are coerced to objects.

**Since**

3.0.0

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Array)_: Returns the array of property names.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.keysIn(new Foo);

// =\> ['a', 'b', 'c'] (iteration order is not guaranteed)

Try in REPL

## \_.mapKeys(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13358)[npm package](https://www.npmjs.com/package/lodash.mapkeys)

The opposite of [\_.mapValues](https://lodash.com/docs/#mapValues); this method creates an object with the same values as object and keys generated by running each own enumerable string keyed property of object thru iteratee. The iteratee is invoked with three arguments: _(value, key, object)_.

**Since**

3.8.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Object)_: Returns the new mapped object.

**Example**

\_.mapKeys({ 'a': 1, 'b': 2 }, function(value, key) {

  return key + value;

});

// =\> { 'a1': 1, 'b2': 2 }

Try in REPL

## \_.mapValues(object, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13396)[npm package](https://www.npmjs.com/package/lodash.mapvalues)

Creates an object with the same keys as object and values generated by running each own enumerable string keyed property of object thru iteratee. The iteratee is invoked with three arguments:
_(value, key, object)_.

**Since**

2.4.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Object)_: Returns the new mapped object.

**Example**

var users = {

  'fred':    { 'user': 'fred',    'age': 40 },

  'pebbles': { 'user': 'pebbles', 'age': 1 }

};

\_.mapValues(users, function(o) { return o.age; });

// =\> { 'fred': 40, 'pebbles': 1 } (iteration order is not guaranteed)

// The `_.property` iteratee shorthand.

\_.mapValues(users, 'age');

// =\> { 'fred': 40, 'pebbles': 1 } (iteration order is not guaranteed)

Try in REPL

## \_.merge(object, [sources])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13437)[npm package](https://www.npmjs.com/package/lodash.merge)

This method is like [\_.assign](https://lodash.com/docs/#assign) except that it recursively merges own and inherited enumerable string keyed properties of source objects into the destination object. Source properties that resolve to undefined are skipped if a destination value exists. Array and plain object properties are merged recursively. Other objects and value types are overridden by assignment. Source objects are applied from left to right. Subsequent sources overwrite property assignments of previous sources.

**Note:** This method mutates object.

**Since**

0.5.0

**Arguments**

1. object_(Object)_: The destination object.
2. [sources]_(...Object)_: The source objects.

**Returns**

_(Object)_: Returns object.

**Example**

var object = {

  'a': [{ 'b': 2 }, { 'd': 4 }]

};

var other = {

  'a': [{ 'c': 3 }, { 'e': 5 }]

};

\_.merge(object, other);

// =\> { 'a': [{ 'b': 2, 'c': 3 }, { 'd': 4, 'e': 5 }] }

Try in REPL

## \_.mergeWith(object, sources, customizer)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13472)[npm package](https://www.npmjs.com/package/lodash.mergewith)

This method is like [\_.merge](https://lodash.com/docs/#merge) except that it accepts customizer which is invoked to produce the merged values of the destination and source properties. If customizer returns undefined, merging is handled by the method instead. The customizer is invoked with six arguments:
_(objValue, srcValue, key, object, source, stack)_.

**Note:** This method mutates object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The destination object.
2. sources_(...Object)_: The source objects.
3. customizer_(Function)_: The function to customize assigned values.

**Returns**

_(Object)_: Returns object.

**Example**

function customizer(objValue, srcValue) {

  if (\_.isArray(objValue)) {

    return objValue.concat(srcValue);

  }

}

var object = { 'a': [1], 'b': [2] };

var other = { 'a': [3], 'b': [4] };

\_.mergeWith(object, other, customizer);

// =\> { 'a': [1, 3], 'b': [2, 4] }

Try in REPL

## \_.omit(object, [paths])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13496)[npm package](https://www.npmjs.com/package/lodash.omit)

The opposite of [\_.pick](https://lodash.com/docs/#pick); this method creates an object composed of the own and inherited enumerable property paths of object that are not omitted.

**Note:** This method is considerably slower than [\_.pick](https://lodash.com/docs/#pick).

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The source object.
2. [paths]_(...(string|string[]))_: The property paths to omit.

**Returns**

_(Object)_: Returns the new object.

**Example**

var object = { 'a': 1, 'b': '2', 'c': 3 };

\_.omit(object, ['a', 'c']);

// =\> { 'b': '2' }

Try in REPL

## \_.omitBy(object, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13538)[npm package](https://www.npmjs.com/package/lodash.omitby)

The opposite of [\_.pickBy](https://lodash.com/docs/#pickBy); this method creates an object composed of the own and inherited enumerable string keyed properties of object that predicate doesn't return truthy for. The predicate is invoked with two arguments: _(value, key)_.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The source object.
2. [predicate=\_.identity]_(Function)_: The function invoked per property.

**Returns**

_(Object)_: Returns the new object.

**Example**

var object = { 'a': 1, 'b': '2', 'c': 3 };

\_.omitBy(object, \_.isNumber);

// =\> { 'b': '2' }

Try in REPL

## \_.pick(object, [paths])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13559)[npm package](https://www.npmjs.com/package/lodash.pick)

Creates an object composed of the picked object properties.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The source object.
2. [paths]_(...(string|string[]))_: The property paths to pick.

**Returns**

_(Object)_: Returns the new object.

**Example**

var object = { 'a': 1, 'b': '2', 'c': 3 };

\_.pick(object, ['a', 'c']);

// =\> { 'a': 1, 'c': 3 }

Try in REPL

## \_.pickBy(object, [predicate=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13581)[npm package](https://www.npmjs.com/package/lodash.pickby)

Creates an object composed of the object properties predicate returns truthy for. The predicate is invoked with two arguments: _(value, key)_.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The source object.
2. [predicate=\_.identity]_(Function)_: The function invoked per property.

**Returns**

_(Object)_: Returns the new object.

**Example**

var object = { 'a': 1, 'b': '2', 'c': 3 };

\_.pickBy(object, \_.isNumber);

// =\> { 'a': 1, 'c': 3 }

Try in REPL

## \_.result(object, path, [defaultValue])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13623)[npm package](https://www.npmjs.com/package/lodash.result)

This method is like [\_.get](https://lodash.com/docs/#get) except that if the resolved value is a function it's invoked with the this binding of its parent object and its result is returned.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The object to query.
2. path_(Array|string)_: The path of the property to resolve.
3. [defaultValue]_(\*)_: The value returned for undefined resolved values.

**Returns**

_(\*)_: Returns the resolved value.

**Example**

var object = { 'a': [{ 'b': { 'c1': 3, 'c2': \_.constant(4) } }] };

\_.result(object, 'a[0].b.c1');

// =\> 3

\_.result(object, 'a[0].b.c2');

// =\> 4

\_.result(object, 'a[0].b.c3', 'default');

// =\> 'default'

\_.result(object, 'a[0].b.c3', \_.constant('default'));

// =\> 'default'

Try in REPL

## \_.set(object, path, value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13673)[npm package](https://www.npmjs.com/package/lodash.set)

Sets the value at path of object. If a portion of path doesn't exist, it's created. Arrays are created for missing index properties while objects are created for all other missing properties. Use [\_.setWith](https://lodash.com/docs/#setWith) to customize path creation.

**Note:** This method mutates object.

**Since**

3.7.0

**Arguments**

1. object_(Object)_: The object to modify.
2. path_(Array|string)_: The path of the property to set.
3. value_(\*)_: The value to set.

**Returns**

_(Object)_: Returns object.

**Example**

var object = { 'a': [{ 'b': { 'c': 3 } }] };

\_.set(object, 'a[0].b.c', 4);

console.log(object.a[0].b.c);

// =\> 4

\_.set(object, ['x', '0', 'y', 'z'], 5);

console.log(object.x[0].y.z);

// =\> 5

Try in REPL

## \_.setWith(object, path, value, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13701)[npm package](https://www.npmjs.com/package/lodash.setwith)

This method is like [\_.set](https://lodash.com/docs/#set) except that it accepts customizer which is invoked to produce the objects of path. If customizer returns undefined path creation is handled by the method instead. The customizer is invoked with three arguments: _(nsValue, key, nsObject)_.

**Note:** This method mutates object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The object to modify.
2. path_(Array|string)_: The path of the property to set.
3. value_(\*)_: The value to set.
4. [customizer]_(Function)_: The function to customize assigned values.

**Returns**

_(Object)_: Returns object.

**Example**

var object = {};

\_.setWith(object, '[0][1]', 'a', Object);

// =\> { '0': { '1': 'a' } }

Try in REPL

## \_.toPairs(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13730)[npm package](https://www.npmjs.com/package/lodash.topairs)

Creates an array of own enumerable string keyed-value pairs for object which can be consumed by [\_.fromPairs](https://lodash.com/docs/#fromPairs). If object is a map or set, its entries are returned.

**Since**

4.0.0

**Aliases**

_\_.entries_

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Array)_: Returns the key-value pairs.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.toPairs(new Foo);

// =\> [['a', 1], ['b', 2]] (iteration order is not guaranteed)

Try in REPL

## \_.toPairsIn(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13756)[npm package](https://www.npmjs.com/package/lodash.topairsin)

Creates an array of own and inherited enumerable string keyed-value pairs for object which can be consumed by [\_.fromPairs](https://lodash.com/docs/#fromPairs). If object is a map or set, its entries are returned.

**Since**

4.0.0

**Aliases**

_\_.entriesIn_

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Array)_: Returns the key-value pairs.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.toPairsIn(new Foo);

// =\> [['a', 1], ['b', 2], ['c', 3]] (iteration order is not guaranteed)

Try in REPL

## \_.transform(object, [iteratee=\_.identity], [accumulator])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13788)[npm package](https://www.npmjs.com/package/lodash.transform)

An alternative to [\_.reduce](https://lodash.com/docs/#reduce); this method transforms object to a new accumulator object which is the result of running each of its own enumerable string keyed properties thru iteratee, with each invocation potentially mutating the accumulator object. If accumulator is not provided, a new object with the same [[Prototype]] will be used. The iteratee is invoked with four arguments: _(accumulator, value, key, object)_. Iteratee functions may exit iteration early by explicitly returning false.

**Since**

1.3.0

**Arguments**

1. object_(Object)_: The object to iterate over.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.
3. [accumulator]_(\*)_: The custom accumulator value.

**Returns**

_(\*)_: Returns the accumulated value.

**Example**

\_.transform([2, 3, 4], function(result, n) {

  result.push(n \*= n);

  return n % 2 == 0;

}, []);

// =\> [4, 9]

\_.transform({ 'a': 1, 'b': 2, 'c': 1 }, function(result, value, key) {

  (result[value] || (result[value] = [])).push(key);

}, {});

// =\> { '1': ['a', 'c'], '2': ['b'] }

Try in REPL

## \_.unset(object, path)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13838)[npm package](https://www.npmjs.com/package/lodash.unset)

Removes the property at path of object.

**Note:** This method mutates object.

**Since**

4.0.0

**Arguments**

1. object_(Object)_: The object to modify.
2. path_(Array|string)_: The path of the property to unset.

**Returns**

_(boolean)_: Returns true if the property is deleted, else false.

**Example**

var object = { 'a': [{ 'b': { 'c': 7 } }] };

\_.unset(object, 'a[0].b.c');

// =\> true

console.log(object);

// =\> { 'a': [{ 'b': {} }] };

\_.unset(object, ['a', '0', 'b', 'c']);

// =\> true

console.log(object);

// =\> { 'a': [{ 'b': {} }] };

Try in REPL

## \_.update(object, path, updater)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13869)[npm package](https://www.npmjs.com/package/lodash.update)

This method is like [\_.set](https://lodash.com/docs/#set) except that accepts updater to produce the value to set. Use [\_.updateWith](https://lodash.com/docs/#updateWith) to customize path creation. The updater is invoked with one argument: _(value)_.

**Note:** This method mutates object.

**Since**

4.6.0

**Arguments**

1. object_(Object)_: The object to modify.
2. path_(Array|string)_: The path of the property to set.
3. updater_(Function)_: The function to produce the updated value.

**Returns**

_(Object)_: Returns object.

**Example**

var object = { 'a': [{ 'b': { 'c': 3 } }] };

\_.update(object, 'a[0].b.c', function(n) { return n \* n; });

console.log(object.a[0].b.c);

// =\> 9

\_.update(object, 'x[0].y.z', function(n) { return n ? n + 1 : 0; });

console.log(object.x[0].y.z);

// =\> 0

Try in REPL

## \_.updateWith(object, path, updater, [customizer])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13897)[npm package](https://www.npmjs.com/package/lodash.updatewith)

This method is like [\_.update](https://lodash.com/docs/#update) except that it accepts customizer which is invoked to produce the objects of path. If customizer returns undefined path creation is handled by the method instead. The customizer is invoked with three arguments: _(nsValue, key, nsObject)_.

**Note:** This method mutates object.

**Since**

4.6.0

**Arguments**

1. object_(Object)_: The object to modify.
2. path_(Array|string)_: The path of the property to set.
3. updater_(Function)_: The function to produce the updated value.
4. [customizer]_(Function)_: The function to customize assigned values.

**Returns**

_(Object)_: Returns object.

**Example**

var object = {};

\_.updateWith(object, '[0][1]', \_.constant('a'), Object);

// =\> { '0': { '1': 'a' } }

Try in REPL

## \_.values(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13928)[npm package](https://www.npmjs.com/package/lodash.values)

Creates an array of the own enumerable string keyed property values of object.

**Note:** Non-object values are coerced to objects.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Array)_: Returns the array of property values.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.values(new Foo);

// =\> [1, 2] (iteration order is not guaranteed)

\_.values('hi');

// =\> ['h', 'i']

Try in REPL

## \_.valuesIn(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L13956)[npm package](https://www.npmjs.com/package/lodash.valuesin)

Creates an array of the own and inherited enumerable string keyed property values of object.

**Note:** Non-object values are coerced to objects.

**Since**

3.0.0

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Array)_: Returns the array of property values.

**Example**

function Foo() {

  this.a = 1;

  this.b = 2;

}

Foo.prototype.c = 3;

\_.valuesIn(new Foo);

// =\> [1, 2, 3] (iteration order is not guaranteed)

Try in REPL

## "Seq" Methods

## \_(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1648)

Creates a lodash object which wraps value to enable implicit method chain sequences. Methods that operate on and return arrays, collections, and functions can be chained together. Methods that retrieve a single value or may return a primitive value will automatically end the chain sequence and return the unwrapped value. Otherwise, the value must be unwrapped with \_#value.

 Explicit chain sequences, which must be unwrapped with \_#value, may be enabled using [\_.chain](https://lodash.com/docs/#chain).

 The execution of chained methods is lazy, that is, it's deferred until \_#value is implicitly or explicitly called.

 Lazy evaluation allows several methods to support shortcut fusion. Shortcut fusion is an optimization to merge iteratee calls; this avoids the creation of intermediate arrays and can greatly reduce the number of iteratee executions. Sections of a chain sequence qualify for shortcut fusion if the section is applied to an array and iteratees accept only one argument. The heuristic for whether a section qualifies for shortcut fusion is subject to change.

 Chaining is supported in custom builds as long as the \_#value method is directly or indirectly included in the build.

 In addition to lodash methods, wrappers have Array and String methods.

 The wrapper Array methods are:
concat, join, pop, push, shift, sort, splice, and unshift

 The wrapper String methods are:
replace and split

 The wrapper methods that support shortcut fusion are:
at, compact, drop, dropRight, dropWhile, filter, find, findLast, head, initial, last, map, reject, reverse, slice, tail, take, takeRight, takeRightWhile, takeWhile, and toArray

 The chainable wrapper methods are:
after, ary, assign, assignIn, assignInWith, assignWith, at, before, bind, bindAll, bindKey, castArray, chain, chunk, commit, compact, concat, conforms, constant, countBy, create, curry, debounce, defaults, defaultsDeep, defer, delay, difference, differenceBy, differenceWith, drop, dropRight, dropRightWhile, dropWhile, extend, extendWith, fill, filter, flatMap, flatMapDeep, flatMapDepth, flatten, flattenDeep, flattenDepth, flip, flow, flowRight, fromPairs, functions, functionsIn, groupBy, initial, intersection, intersectionBy, intersectionWith, invert, invertBy, invokeMap, iteratee, keyBy, keys, keysIn, map, mapKeys, mapValues, matches, matchesProperty, memoize, merge, mergeWith, method, methodOf, mixin, negate, nthArg, omit, omitBy, once, orderBy, over, overArgs, overEvery, overSome, partial, partialRight, partition, pick, pickBy, plant, property, propertyOf, pull, pullAll, pullAllBy, pullAllWith, pullAt, push, range, rangeRight, rearg, reject, remove, rest, reverse, sampleSize, set, setWith, shuffle, slice, sort, sortBy, splice, spread, tail, take, takeRight, takeRightWhile, takeWhile, tap, throttle, thru, toArray, toPairs, toPairsIn, toPath, toPlainObject, transform, unary, union, unionBy, unionWith, uniq, uniqBy, uniqWith, unset, unshift, unzip, unzipWith, update, updateWith, values, valuesIn, without, wrap, xor, xorBy, xorWith, zip, zipObject, zipObjectDeep, and zipWith

 The wrapper methods that are **not** chainable by default are:
add, attempt, camelCase, capitalize, ceil, clamp, clone, cloneDeep, cloneDeepWith, cloneWith, conformsTo, deburr, defaultTo, divide, each, eachRight, endsWith, eq, escape, escapeRegExp, every, find, findIndex, findKey, findLast, findLastIndex, findLastKey, first, floor, forEach, forEachRight, forIn, forInRight, forOwn, forOwnRight, get, gt, gte, has, hasIn, head, identity, includes, indexOf, inRange, invoke, isArguments, isArray, isArrayBuffer, isArrayLike, isArrayLikeObject, isBoolean, isBuffer, isDate, isElement, isEmpty, isEqual, isEqualWith, isError, isFinite, isFunction, isInteger, isLength, isMap, isMatch, isMatchWith, isNaN, isNative, isNil, isNull, isNumber, isObject, isObjectLike, isPlainObject, isRegExp, isSafeInteger, isSet, isString, isUndefined, isTypedArray, isWeakMap, isWeakSet, join, kebabCase, last, lastIndexOf, lowerCase, lowerFirst, lt, lte, max, maxBy, mean, meanBy, min, minBy, multiply, noConflict, noop, now, nth, pad, padEnd, padStart, parseInt, pop, random, reduce, reduceRight, repeat, result, round, runInContext, sample, shift, size, snakeCase, some, sortedIndex, sortedIndexBy, sortedLastIndex, sortedLastIndexBy, startCase, startsWith, stubArray, stubFalse, stubObject, stubString, stubTrue, subtract, sum, sumBy, template, times, toFinite, toInteger, toJSON, toLength, toLower, toNumber, toSafeInteger, toString, toUpper, trim, trimEnd, trimStart, truncate, unescape, uniqueId, upperCase, upperFirst, value, and words

**Arguments**

1. value_(\*)_: The value to wrap in a lodash instance.

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

function square(n) {

  return n \* n;

}

var wrapped = \_([1, 2, 3]);

// Returns an unwrapped value.

wrapped.reduce(\_.add);

// =\> 6

// Returns a wrapped value.

var squares = wrapped.map(square);

\_.isArray(squares);

// =\> false

\_.isArray(squares.value());

// =\> true

Try in REPL

## \_.chain(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8737)

Creates a lodash wrapper instance that wraps value with explicit method chain sequences enabled. The result of such sequences must be unwrapped with \_#value.

**Since**

1.3.0

**Arguments**

1. value_(\*)_: The value to wrap.

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

var users = [

  { 'user': 'barney',  'age': 36 },

  { 'user': 'fred',    'age': 40 },

  { 'user': 'pebbles', 'age': 1 }

];

var youngest = \_

  .chain(users)

  .sortBy('age')

  .map(function(o) {

    return o.user + ' is ' + o.age;

  })

  .head()

  .value();

// =\> 'pebbles is 1'

Try in REPL

## \_.tap(value, interceptor)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8766)

This method invokes interceptor and returns value. The interceptor is invoked with one argument; _(value)_. The purpose of this method is to "tap into" a method chain sequence in order to modify intermediate results.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: The value to provide to interceptor.
2. interceptor_(Function)_: The function to invoke.

**Returns**

_(\*)_: Returns value.

**Example**

\_([1, 2, 3])

 .tap(function(array) {

// Mutate input array.

   array.pop();

 })

 .reverse()

 .value();

// =\> [2, 1]

Try in REPL

## \_.thru(value, interceptor)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8794)

This method is like [\_.tap](https://lodash.com/docs/#tap) except that it returns the result of interceptor. The purpose of this method is to "pass thru" values replacing intermediate results in a method chain sequence.

**Since**

3.0.0

**Arguments**

1. value_(\*)_: The value to provide to interceptor.
2. interceptor_(Function)_: The function to invoke.

**Returns**

_(\*)_: Returns the result of interceptor.

**Example**

\_('  abc  ')

 .chain()

 .trim()

 .thru(function(value) {

   return [value];

 })

 .value();

// =\> ['abc']

Try in REPL

## \_.prototype[Symbol.iterator]()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8949)

Enables the wrapper to be iterable.

**Since**

4.0.0

**Returns**

_(Object)_: Returns the wrapper object.

**Example**

var wrapped = \_([1, 2]);

wrapped[Symbol.iterator]() === wrapped;

// =\> true

Array.from(wrapped);

// =\> [1, 2]

Try in REPL

## \_.prototype.at([paths])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8814)

This method is the wrapper version of [\_.at](https://lodash.com/docs/#at).

**Since**

1.0.0

**Arguments**

1. [paths]_(...(string|string[]))_: The property paths to pick.

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

var object = { 'a': [{ 'b': { 'c': 3 } }, 4] };

\_(object).at(['a[0].b.c', 'a[1]']).value();

// =\> [3, 4]

Try in REPL

## \_.prototype.chain()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8865)

Creates a lodash wrapper instance with explicit method chain sequences enabled.

**Since**

0.1.0

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

var users = [

  { 'user': 'barney', 'age': 36 },

  { 'user': 'fred',   'age': 40 }

];

// A sequence without explicit chaining.

\_(users).head();

// =\> { 'user': 'barney', 'age': 36 }

// A sequence with explicit chaining.

\_(users)

  .chain()

  .head()

  .pick('user')

  .value();

// =\> { 'user': 'barney' }

Try in REPL

## \_.prototype.commit()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8895)

Executes the chain sequence and returns the wrapped result.

**Since**

3.2.0

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

var array = [1, 2];

var wrapped = \_(array).push(3);

console.log(array);

// =\> [1, 2]

wrapped = wrapped.commit();

console.log(array);

// =\> [1, 2, 3]

wrapped.last();

// =\> 3

console.log(array);

// =\> [1, 2, 3]

Try in REPL

## \_.prototype.next()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8921)

Gets the next value on a wrapped object following the [iterator protocol](https://mdn.io/iteration_protocols#iterator).

**Since**

4.0.0

**Returns**

_(Object)_: Returns the next iterator value.

**Example**

var wrapped = \_([1, 2]);

wrapped.next();

// =\> { 'done': false, 'value': 1 }

wrapped.next();

// =\> { 'done': false, 'value': 2 }

wrapped.next();

// =\> { 'done': true, 'value': undefined }

Try in REPL

## \_.prototype.plant(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L8977)

Creates a clone of the chain sequence planting value as the wrapped value.

**Since**

3.2.0

**Arguments**

1. value_(\*)_: The value to plant.

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

function square(n) {

  return n \* n;

}

var wrapped = \_([1, 2]).map(square);

var other = wrapped.plant([3, 4]);

other.value();

// =\> [9, 16]

wrapped.value();

// =\> [1, 4]

Try in REPL

## \_.prototype.reverse()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9017)

This method is the wrapper version of [\_.reverse](https://lodash.com/docs/#reverse).

**Note:** This method mutates the wrapped array.

**Since**

0.1.0

**Returns**

_(Object)_: Returns the new lodash wrapper instance.

**Example**

var array = [1, 2, 3];

\_(array).reverse().value()

// =\> [3, 2, 1]

console.log(array);

// =\> [3, 2, 1]

Try in REPL

## \_.prototype.value()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L9049)

Executes the chain sequence to resolve the unwrapped value.

**Since**

0.1.0

**Aliases**

_\_.prototype.toJSON, \_.prototype.valueOf_

**Returns**

_(\*)_: Returns the resolved unwrapped value.

**Example**

\_([1, 2, 3]).value();

// =\> [1, 2, 3]

Try in REPL

## "String" Methods

## \_.camelCase([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14139)[npm package](https://www.npmjs.com/package/lodash.camelcase)

Converts string to [camel case](https://en.wikipedia.org/wiki/CamelCase).

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the camel cased string.

**Example**

\_.camelCase('Foo Bar');

// =\> 'fooBar'

\_.camelCase('--foo-bar--');

// =\> 'fooBar'

\_.camelCase('\_\_FOO\_BAR\_\_');

// =\> 'fooBar'

Try in REPL

## \_.capitalize([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14159)[npm package](https://www.npmjs.com/package/lodash.capitalize)

Converts the first character of string to upper case and the remaining to lower case.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to capitalize.

**Returns**

_(string)_: Returns the capitalized string.

**Example**

\_.capitalize('FRED');

// =\> 'Fred'

Try in REPL

## \_.deburr([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14181)[npm package](https://www.npmjs.com/package/lodash.deburr)

Deburrs string by converting [Latin-1 Supplement](https://en.wikipedia.org/wiki/Latin-1_Supplement_(Unicode_block)#Character_table) and [Latin Extended-A](https://en.wikipedia.org/wiki/Latin_Extended-A) letters to basic Latin letters and removing [combining diacritical marks](https://en.wikipedia.org/wiki/Combining_Diacritical_Marks).

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to deburr.

**Returns**

_(string)_: Returns the deburred string.

**Example**

\_.deburr('déjà vu');

// =\> 'deja vu'

Try in REPL

## \_.endsWith([string=''], [target], [position=string.length])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14209)[npm package](https://www.npmjs.com/package/lodash.endswith)

Checks if string ends with the given target string.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to inspect.
2. [target]_(string)_: The string to search for.
3. [position=string.length]_(number)_: The position to search up to.

**Returns**

_(boolean)_: Returns true if string ends with target, else false.

**Example**

\_.endsWith('abc', 'c');

// =\> true

\_.endsWith('abc', 'b');

// =\> false

\_.endsWith('abc', 'b', 2);

// =\> true

Try in REPL

## \_.escape([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14251)[npm package](https://www.npmjs.com/package/lodash.escape)

Converts the characters "&", "\<", "\>", '"', and "'" in string to their corresponding HTML entities.

**Note:** No other characters are escaped. To escape additional characters use a third-party library like [_he_](https://mths.be/he).

 Though the "\>" character is escaped for symmetry, characters like "\>" and "/" don't need escaping in HTML and have no special meaning unless they're part of a tag or unquoted attribute value. See [Mathias Bynens's article](https://mathiasbynens.be/notes/ambiguous-ampersands)_(under "semi-related fun fact")_ for more details.

 When working with HTML you should always [quote attribute values](http://wonko.com/post/html-escaping) to reduce XSS vectors.

**Since**

0.1.0

**Arguments**

1. [string='']_(string)_: The string to escape.

**Returns**

_(string)_: Returns the escaped string.

**Example**

\_.escape('fred, barney, & pebbles');

// =\> 'fred, barney, &amp; pebbles'

Try in REPL

## \_.escapeRegExp([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14273)[npm package](https://www.npmjs.com/package/lodash.escaperegexp)

Escapes the RegExp special characters "^", "$", "", ".", "\*", "+", "?", "(", ")", "[", "]", "{", "}", and "|" in string.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to escape.

**Returns**

_(string)_: Returns the escaped string.

**Example**

\_.escapeRegExp('[lodash](https://lodash.com/)');

// =\> '\[lodash\]\(https://lodash\.com/\)'

Try in REPL

## \_.kebabCase([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14301)[npm package](https://www.npmjs.com/package/lodash.kebabcase)

Converts string to [kebab case](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles).

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the kebab cased string.

**Example**

\_.kebabCase('Foo Bar');

// =\> 'foo-bar'

\_.kebabCase('fooBar');

// =\> 'foo-bar'

\_.kebabCase('\_\_FOO\_BAR\_\_');

// =\> 'foo-bar'

Try in REPL

## \_.lowerCase([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14325)[npm package](https://www.npmjs.com/package/lodash.lowercase)

Converts string, as space separated words, to lower case.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the lower cased string.

**Example**

\_.lowerCase('--Foo-Bar--');

// =\> 'foo bar'

\_.lowerCase('fooBar');

// =\> 'foo bar'

\_.lowerCase('\_\_FOO\_BAR\_\_');

// =\> 'foo bar'

Try in REPL

## \_.lowerFirst([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14346)[npm package](https://www.npmjs.com/package/lodash.lowerfirst)

Converts the first character of string to lower case.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the converted string.

**Example**

\_.lowerFirst('Fred');

// =\> 'fred'

\_.lowerFirst('FRED');

// =\> 'fRED'

Try in REPL

## \_.pad([string=''], [length=0], [chars=' '])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14371)[npm package](https://www.npmjs.com/package/lodash.pad)

Pads string on the left and right sides if it's shorter than length. Padding characters are truncated if they can't be evenly divided by length.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to pad.
2. [length=0]_(number)_: The padding length.
3. [chars=' ']_(string)_: The string used as padding.

**Returns**

_(string)_: Returns the padded string.

**Example**

\_.pad('abc', 8);

// =\> '  abc   '

\_.pad('abc', 8, '\_-');

// =\> '\_-abc\_-\_'

\_.pad('abc', 3);

// =\> 'abc'

Try in REPL

## \_.padEnd([string=''], [length=0], [chars=' '])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14410)[npm package](https://www.npmjs.com/package/lodash.padend)

Pads string on the right side if it's shorter than length. Padding characters are truncated if they exceed length.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to pad.
2. [length=0]_(number)_: The padding length.
3. [chars=' ']_(string)_: The string used as padding.

**Returns**

_(string)_: Returns the padded string.

**Example**

\_.padEnd('abc', 6);

// =\> 'abc   '

\_.padEnd('abc', 6, '\_-');

// =\> 'abc\_-\_'

\_.padEnd('abc', 3);

// =\> 'abc'

Try in REPL

## \_.padStart([string=''], [length=0], [chars=' '])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14443)[npm package](https://www.npmjs.com/package/lodash.padstart)

Pads string on the left side if it's shorter than length. Padding characters are truncated if they exceed length.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to pad.
2. [length=0]_(number)_: The padding length.
3. [chars=' ']_(string)_: The string used as padding.

**Returns**

_(string)_: Returns the padded string.

**Example**

\_.padStart('abc', 6);

// =\> '   abc'

\_.padStart('abc', 6, '\_-');

// =\> '\_-\_abc'

\_.padStart('abc', 3);

// =\> 'abc'

Try in REPL

## \_.parseInt(string, [radix=10])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14477)[npm package](https://www.npmjs.com/package/lodash.parseint)

Converts string to an integer of the specified radix. If radix is undefined or 0, a radix of 10 is used unless value is a hexadecimal, in which case a radix of 16 is used.

**Note:** This method aligns with the [ES5 implementation](https://es5.github.io/#x15.1.2.2) of parseInt.

**Since**

1.1.0

**Arguments**

1. string_(string)_: The string to convert.
2. [radix=10]_(number)_: The radix to interpret value by.

**Returns**

_(number)_: Returns the converted integer.

**Example**

\_.parseInt('08');

// =\> 8

\_.map(['6', '08', '10'], \_.parseInt);

// =\> [6, 8, 10]

Try in REPL

## \_.repeat([string=''], [n=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14508)[npm package](https://www.npmjs.com/package/lodash.repeat)

Repeats the given string n times.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to repeat.
2. [n=1]_(number)_: The number of times to repeat the string.

**Returns**

_(string)_: Returns the repeated string.

**Example**

\_.repeat('\*', 3);

// =\> '\*\*\*'

\_.repeat('abc', 2);

// =\> 'abcabc'

\_.repeat('abc', 0);

// =\> ''

Try in REPL

## \_.replace([string=''], pattern, replacement)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14536)[npm package](https://www.npmjs.com/package/lodash.replace)

Replaces matches for pattern in string with replacement.

**Note:** This method is based on [String#replace](https://mdn.io/String/replace).

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to modify.
2. pattern_(RegExp|string)_: The pattern to replace.
3. replacement_(Function|string)_: The match replacement.

**Returns**

_(string)_: Returns the modified string.

**Example**

\_.replace('Hi Fred', 'Fred', 'Barney');

// =\> 'Hi Barney'

Try in REPL

## \_.snakeCase([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14564)[npm package](https://www.npmjs.com/package/lodash.snakecase)

Converts string to [snake case](https://en.wikipedia.org/wiki/Snake_case).

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the snake cased string.

**Example**

\_.snakeCase('Foo Bar');

// =\> 'foo\_bar'

\_.snakeCase('fooBar');

// =\> 'foo\_bar'

\_.snakeCase('--FOO-BAR--');

// =\> 'foo\_bar'

Try in REPL

## \_.split([string=''], separator, [limit])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14587)[npm package](https://www.npmjs.com/package/lodash.split)

Splits string by separator.

**Note:** This method is based on [String#split](https://mdn.io/String/split).

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to split.
2. separator_(RegExp|string)_: The separator pattern to split by.
3. [limit]_(number)_: The length to truncate results to.

**Returns**

_(Array)_: Returns the string segments.

**Example**

\_.split('a-b-c', '-', 2);

// =\> ['a', 'b']

Try in REPL

## \_.startCase([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14629)[npm package](https://www.npmjs.com/package/lodash.startcase)

Converts string to [start case](https://en.wikipedia.org/wiki/Letter_case#Stylistic_or_specialised_usage).

**Since**

3.1.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the start cased string.

**Example**

\_.startCase('--foo-bar--');

// =\> 'Foo Bar'

\_.startCase('fooBar');

// =\> 'Foo Bar'

\_.startCase('\_\_FOO\_BAR\_\_');

// =\> 'FOO BAR'

Try in REPL

## \_.startsWith([string=''], [target], [position=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14656)[npm package](https://www.npmjs.com/package/lodash.startswith)

Checks if string starts with the given target string.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to inspect.
2. [target]_(string)_: The string to search for.
3. [position=0]_(number)_: The position to search from.

**Returns**

_(boolean)_: Returns true if string starts with target, else false.

**Example**

\_.startsWith('abc', 'a');

// =\> true

\_.startsWith('abc', 'b');

// =\> false

\_.startsWith('abc', 'b', 1);

// =\> true

Try in REPL

## \_.template([string=''], [options={}])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14770)[npm package](https://www.npmjs.com/package/lodash.template)

Creates a compiled template function that can interpolate data properties in "interpolate" delimiters, HTML-escape interpolated data properties in "escape" delimiters, and execute JavaScript in "evaluate" delimiters. Data properties may be accessed as free variables in the template. If a setting object is given, it takes precedence over [\_.templateSettings](https://lodash.com/docs/#templateSettings) values.

**Note:** In the development build [\_.template](https://lodash.com/docs/#template) utilizes [sourceURLs](http://www.html5rocks.com/en/tutorials/developertools/sourcemaps/#toc-sourceurl) for easier debugging.

 For more information on precompiling templates see [lodash's custom builds documentation](https://lodash.com/custom-builds).

 For more information on Chrome extension sandboxes see [Chrome's extensions documentation](https://developer.chrome.com/extensions/sandboxingEval).

**Since**

0.1.0

**Arguments**

1. [string='']_(string)_: The template string.
2. [options={}]_(Object)_: The options object.
3. [options.escape=\_.templateSettings.escape]_(RegExp)_: The HTML "escape" delimiter.
4. [options.evaluate=\_.templateSettings.evaluate]_(RegExp)_: The "evaluate" delimiter.
5. [options.imports=\_.templateSettings.imports]_(Object)_: An object to import into the template as free variables.
6. [options.interpolate=\_.templateSettings.interpolate]_(RegExp)_: The "interpolate" delimiter.
7. [options.sourceURL='lodash.templateSources[n]']_(string)_: The sourceURL of the compiled template.
8. [options.variable='obj']_(string)_: The data object variable name.

**Returns**

_(Function)_: Returns the compiled template function.

**Example**

// Use the "interpolate" delimiter to create a compiled template.

var compiled = \_.template('hello \<%= user %\>!');

compiled({ 'user': 'fred' });

// =\> 'hello fred!'

// Use the HTML "escape" delimiter to escape data property values.

var compiled = \_.template('\<b\>\<%- value %\>\</b\>');

compiled({ 'value': '\<script\>' });

// =\> '\<b\>&lt;script&gt;\</b\>'

// Use the "evaluate" delimiter to execute JavaScript and generate HTML.

var compiled = \_.template('\<% \_.forEach(users, function(user) { %\>\<li\>\<%- user %\>\</li\>\<% }); %\>');

compiled({ 'users': ['fred', 'barney'] });

// =\> '\<li\>fred\</li\>\<li\>barney\</li\>'

// Use the internal `print` function in "evaluate" delimiters.

var compiled = \_.template('\<% print("hello " + user); %\>!');

compiled({ 'user': 'barney' });

// =\> 'hello barney!'

// Use the ES template literal delimiter as an "interpolate" delimiter.

// Disable support by replacing the "interpolate" delimiter.

var compiled = \_.template('hello ${ user }!');

compiled({ 'user': 'pebbles' });

// =\> 'hello pebbles!'

// Use backslashes to treat delimiters as plain text.

var compiled = \_.template('\<%= "\\\<%- value %\\\>" %\>');

compiled({ 'value': 'ignored' });

// =\> '\<%- value %\>'

// Use the `imports` option to import `jQuery` as `jq`.

var text = '\<% jq.each(users, function(user) { %\>\<li\>\<%- user %\>\</li\>\<% }); %\>';

var compiled = \_.template(text, { 'imports': { 'jq': jQuery } });

compiled({ 'users': ['fred', 'barney'] });

// =\> '\<li\>fred\</li\>\<li\>barney\</li\>'

// Use the `sourceURL` option to specify a custom sourceURL for the template.

var compiled = \_.template('hello \<%= user %\>!', { 'sourceURL': '/basic/greeting.jst' });

compiled(data);

// =\> Find the source of "greeting.jst" under the Sources tab or Resources panel of the web inspector.

// Use the `variable` option to ensure a with-statement isn't used in the compiled template.

var compiled = \_.template('hi \<%= data.user %\>!', { 'variable': 'data' });

compiled.source;

// =\> function(data) {

//   var \_\_t, \_\_p = '';

//   \_\_p += 'hi ' + ((\_\_t = ( data.user )) == null ? '' : \_\_t) + '!';

//   return \_\_p;

// }

// Use custom template delimiters.

\_.templateSettings.interpolate = /{{([\s\S]+?)}}/g;

var compiled = \_.template('hello {{ user }}!');

compiled({ 'user': 'mustache' });

// =\> 'hello mustache!'

// Use the `source` property to inline compiled templates for meaningful

// line numbers in error messages and stack traces.

fs.writeFileSync(path.join(process.cwd(), 'jst.js'), '\

  var JST = {\

    "main": ' + \_.template(mainText).source + '\

  };\

');

Try in REPL

## \_.toLower([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14904)[npm package](https://www.npmjs.com/package/lodash.tolower)

Converts string, as a whole, to lower case just like [String#toLowerCase](https://mdn.io/toLowerCase).

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the lower cased string.

**Example**

\_.toLower('--Foo-Bar--');

// =\> '--foo-bar--'

\_.toLower('fooBar');

// =\> 'foobar'

\_.toLower('\_\_FOO\_BAR\_\_');

// =\> '\_\_foo\_bar\_\_'

Try in REPL

## \_.toUpper([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14929)[npm package](https://www.npmjs.com/package/lodash.toupper)

Converts string, as a whole, to upper case just like [String#toUpperCase](https://mdn.io/toUpperCase).

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the upper cased string.

**Example**

\_.toUpper('--foo-bar--');

// =\> '--FOO-BAR--'

\_.toUpper('fooBar');

// =\> 'FOOBAR'

\_.toUpper('\_\_foo\_bar\_\_');

// =\> '\_\_FOO\_BAR\_\_'

Try in REPL

## \_.trim([string=''], [chars=whitespace])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14955)[npm package](https://www.npmjs.com/package/lodash.trim)

Removes leading and trailing whitespace or specified characters from string.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to trim.
2. [chars=whitespace]_(string)_: The characters to trim.

**Returns**

_(string)_: Returns the trimmed string.

**Example**

\_.trim('  abc  ');

// =\> 'abc'

\_.trim('-\_-abc-\_-', '\_-');

// =\> 'abc'

\_.map(['  foo  ', '  bar  '], \_.trim);

// =\> ['foo', 'bar']

Try in REPL

## \_.trimEnd([string=''], [chars=whitespace])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L14990)[npm package](https://www.npmjs.com/package/lodash.trimend)

Removes trailing whitespace or specified characters from string.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to trim.
2. [chars=whitespace]_(string)_: The characters to trim.

**Returns**

_(string)_: Returns the trimmed string.

**Example**

\_.trimEnd('  abc  ');

// =\> '  abc'

\_.trimEnd('-\_-abc-\_-', '\_-');

// =\> '-\_-abc'

Try in REPL

## \_.trimStart([string=''], [chars=whitespace])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15023)[npm package](https://www.npmjs.com/package/lodash.trimstart)

Removes leading whitespace or specified characters from string.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to trim.
2. [chars=whitespace]_(string)_: The characters to trim.

**Returns**

_(string)_: Returns the trimmed string.

**Example**

\_.trimStart('  abc  ');

// =\> 'abc  '

\_.trimStart('-\_-abc-\_-', '\_-');

// =\> 'abc-\_-'

Try in REPL

## \_.truncate([string=''], [options={}])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15074)[npm package](https://www.npmjs.com/package/lodash.truncate)

Truncates string if it's longer than the given maximum string length. The last characters of the truncated string are replaced with the omission string which defaults to "...".

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to truncate.
2. [options={}]_(Object)_: The options object.
3. [options.length=30]_(number)_: The maximum string length.
4. [options.omission='...']_(string)_: The string to indicate text is omitted.
5. [options.separator]_(RegExp|string)_: The separator pattern to truncate to.

**Returns**

_(string)_: Returns the truncated string.

**Example**

\_.truncate('hi-diddly-ho there, neighborino');

// =\> 'hi-diddly-ho there, neighbo...'

\_.truncate('hi-diddly-ho there, neighborino', {

  'length': 24,

  'separator': ' '

});

// =\> 'hi-diddly-ho there,...'

\_.truncate('hi-diddly-ho there, neighborino', {

  'length': 24,

  'separator': /,? +/

});

// =\> 'hi-diddly-ho there...'

\_.truncate('hi-diddly-ho there, neighborino', {

  'omission': ' [...]'

});

// =\> 'hi-diddly-ho there, neig [...]'

Try in REPL

## \_.unescape([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15149)[npm package](https://www.npmjs.com/package/lodash.unescape)

The inverse of [\_.escape](https://lodash.com/docs/#escape); this method converts the HTML entities &amp;, &lt;, &gt;, &quot;, and &#39; in string to their corresponding characters.

**Note:** No other HTML entities are unescaped. To unescape additional HTML entities use a third-party library like [_he_](https://mths.be/he).

**Since**

0.6.0

**Arguments**

1. [string='']_(string)_: The string to unescape.

**Returns**

_(string)_: Returns the unescaped string.

**Example**

\_.unescape('fred, barney, &amp; pebbles');

// =\> 'fred, barney, & pebbles'

Try in REPL

## \_.upperCase([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15176)[npm package](https://www.npmjs.com/package/lodash.uppercase)

Converts string, as space separated words, to upper case.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the upper cased string.

**Example**

\_.upperCase('--foo-bar');

// =\> 'FOO BAR'

\_.upperCase('fooBar');

// =\> 'FOO BAR'

\_.upperCase('\_\_foo\_bar\_\_');

// =\> 'FOO BAR'

Try in REPL

## \_.upperFirst([string=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15197)[npm package](https://www.npmjs.com/package/lodash.upperfirst)

Converts the first character of string to upper case.

**Since**

4.0.0

**Arguments**

1. [string='']_(string)_: The string to convert.

**Returns**

_(string)_: Returns the converted string.

**Example**

\_.upperFirst('fred');

// =\> 'Fred'

\_.upperFirst('FRED');

// =\> 'FRED'

Try in REPL

## \_.words([string=''], [pattern])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15218)[npm package](https://www.npmjs.com/package/lodash.words)

Splits string into an array of its words.

**Since**

3.0.0

**Arguments**

1. [string='']_(string)_: The string to inspect.
2. [pattern]_(RegExp|string)_: The pattern to match words.

**Returns**

_(Array)_: Returns the words of string.

**Example**

\_.words('fred, barney, & pebbles');

// =\> ['fred', 'barney', 'pebbles']

\_.words('fred, barney, & pebbles', /[^, ]+/g);

// =\> ['fred', 'barney', '&', 'pebbles']

Try in REPL

## "Util" Methods

## \_.attempt(func, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15252)[npm package](https://www.npmjs.com/package/lodash.attempt)

Attempts to invoke func, returning either the result or the caught error object. Any additional arguments are provided to func when it's invoked.

**Since**

3.0.0

**Arguments**

1. func_(Function)_: The function to attempt.
2. [args]_(...\*)_: The arguments to invoke func with.

**Returns**

_(\*)_: Returns the func result or error object.

**Example**

// Avoid throwing errors for invalid selectors.

var elements = \_.attempt(function(selector) {

  return document.querySelectorAll(selector);

}, '\>\_\>');

if (\_.isError(elements)) {

  elements = [];

}

Try in REPL

## \_.bindAll(object, methodNames)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15286)[npm package](https://www.npmjs.com/package/lodash.bindall)

Binds methods of an object to the object itself, overwriting the existing method.

**Note:** This method doesn't set the "length" property of bound functions.

**Since**

0.1.0

**Arguments**

1. object_(Object)_: The object to bind and assign the bound methods to.
2. methodNames_(...(string|string[]))_: The object method names to bind.

**Returns**

_(Object)_: Returns object.

**Example**

var view = {

  'label': 'docs',

  'click': function() {

    console.log('clicked ' + this.label);

  }

};

\_.bindAll(view, ['click']);

jQuery(element).on('click', view.click);

// =\> Logs 'clicked docs' when clicked.

Try in REPL

## \_.cond(pairs)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15323)[npm package](https://www.npmjs.com/package/lodash.cond)

Creates a function that iterates over pairs and invokes the corresponding function of the first predicate to return truthy. The predicate-function pairs are invoked with the this binding and arguments of the created function.

**Since**

4.0.0

**Arguments**

1. pairs_(Array)_: The predicate-function pairs.

**Returns**

_(Function)_: Returns the new composite function.

**Example**

var func = \_.cond([

  [\_.matches({ 'a': 1 }),           \_.constant('matches A')],

  [\_.conforms({ 'b': \_.isNumber }), \_.constant('matches B')],

  [\_.stubTrue,                      \_.constant('no match')]

]);

func({ 'a': 1, 'b': 2 });

// =\> 'matches A'

func({ 'a': 0, 'b': 1 });

// =\> 'matches B'

func({ 'a': '1', 'b': '2' });

// =\> 'no match'

Try in REPL

## \_.conforms(source)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15369)[npm package](https://www.npmjs.com/package/lodash.conforms)

Creates a function that invokes the predicate properties of source with the corresponding property values of a given object, returning true if all predicates return truthy, else false.

**Note:** The created function is equivalent to [\_.conformsTo](https://lodash.com/docs/#conformsTo) with source partially applied.

**Since**

4.0.0

**Arguments**

1. source_(Object)_: The object of property predicates to conform to.

**Returns**

_(Function)_: Returns the new spec function.

**Example**

var objects = [

  { 'a': 2, 'b': 1 },

  { 'a': 1, 'b': 2 }

];

\_.filter(objects, \_.conforms({ 'b': function(n) { return n \> 1; } }));

// =\> [{ 'a': 1, 'b': 2 }]

Try in REPL

## \_.constant(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15392)[npm package](https://www.npmjs.com/package/lodash.constant)

Creates a function that returns value.

**Since**

2.4.0

**Arguments**

1. value_(\*)_: The value to return from the new function.

**Returns**

_(Function)_: Returns the new constant function.

**Example**

var objects = \_.times(2, \_.constant({ 'a': 1 }));

console.log(objects);

// =\> [{ 'a': 1 }, { 'a': 1 }]

console.log(objects[0] === objects[1]);

// =\> true

Try in REPL

## \_.defaultTo(value, defaultValue)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15418)[npm package](https://www.npmjs.com/package/lodash.defaultto)

Checks value to determine whether a default value should be returned in its place. The defaultValue is returned if value is NaN, null, or undefined.

**Since**

4.14.0

**Arguments**

1. value_(\*)_: The value to check.
2. defaultValue_(\*)_: The default value.

**Returns**

_(\*)_: Returns the resolved value.

**Example**

\_.defaultTo(1, 10);

// =\> 1

\_.defaultTo(undefined, 10);

// =\> 10

Try in REPL

## \_.flow([funcs])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15444)[npm package](https://www.npmjs.com/package/lodash.flow)

Creates a function that returns the result of invoking the given functions with the this binding of the created function, where each successive invocation is supplied the return value of the previous.

**Since**

3.0.0

**Arguments**

1. [funcs]_(...(Function|Function[]))_: The functions to invoke.

**Returns**

_(Function)_: Returns the new composite function.

**Example**

function square(n) {

  return n \* n;

}

var addSquare = \_.flow([\_.add, square]);

addSquare(1, 2);

// =\> 9

Try in REPL

## \_.flowRight([funcs])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15467)[npm package](https://www.npmjs.com/package/lodash.flowright)

This method is like [\_.flow](https://lodash.com/docs/#flow) except that it creates a function that invokes the given functions from right to left.

**Since**

3.0.0

**Arguments**

1. [funcs]_(...(Function|Function[]))_: The functions to invoke.

**Returns**

_(Function)_: Returns the new composite function.

**Example**

function square(n) {

  return n \* n;

}

var addSquare = \_.flowRight([square, \_.add]);

addSquare(1, 2);

// =\> 9

Try in REPL

## \_.identity(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15485)[npm package](https://www.npmjs.com/package/lodash.identity)

This method returns the first argument it receives.

**Since**

0.1.0

**Arguments**

1. value_(\*)_: Any value.

**Returns**

_(\*)_: Returns value.

**Example**

var object = { 'a': 1 };

console.log(\_.identity(object) === object);

// =\> true

Try in REPL

## \_.iteratee([func=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15531)[npm package](https://www.npmjs.com/package/lodash.iteratee)

Creates a function that invokes func with the arguments of the created function. If func is a property name, the created function returns the property value for a given element. If func is an array or object, the created function returns true for elements that contain the equivalent source properties, otherwise it returns false.

**Since**

4.0.0

**Arguments**

1. [func=\_.identity]_(\*)_: The value to convert to a callback.

**Returns**

_(Function)_: Returns the callback.

**Example**

var users = [

  { 'user': 'barney', 'age': 36, 'active': true },

  { 'user': 'fred',   'age': 40, 'active': false }

];

// The `_.matches` iteratee shorthand.

\_.filter(users, \_.iteratee({ 'user': 'barney', 'active': true }));

// =\> [{ 'user': 'barney', 'age': 36, 'active': true }]

// The `_.matchesProperty` iteratee shorthand.

\_.filter(users, \_.iteratee(['user', 'fred']));

// =\> [{ 'user': 'fred', 'age': 40 }]

// The `_.property` iteratee shorthand.

\_.map(users, \_.iteratee('user'));

// =\> ['barney', 'fred']

// Create custom iteratee shorthands.

\_.iteratee = \_.wrap(\_.iteratee, function(iteratee, func) {

  return !\_.isRegExp(func) ? iteratee(func) : function(string) {

    return func.test(string);

  };

});

\_.filter(['abc', 'def'], /ef/);

// =\> ['def']

Try in REPL

## \_.matches(source)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15563)[npm package](https://www.npmjs.com/package/lodash.matches)

Creates a function that performs a partial deep comparison between a given object and source, returning true if the given object has equivalent property values, else false.

**Note:** The created function is equivalent to [\_.isMatch](https://lodash.com/docs/#isMatch) with source partially applied.

 Partial comparisons will match empty array and empty object source values against any array or object value, respectively. See [\_.isEqual](https://lodash.com/docs/#isEqual) for a list of supported value comparisons.

**Since**

3.0.0

**Arguments**

1. source_(Object)_: The object of property values to match.

**Returns**

_(Function)_: Returns the new spec function.

**Example**

var objects = [

  { 'a': 1, 'b': 2, 'c': 3 },

  { 'a': 4, 'b': 5, 'c': 6 }

];

\_.filter(objects, \_.matches({ 'a': 4, 'c': 6 }));

// =\> [{ 'a': 4, 'b': 5, 'c': 6 }]

Try in REPL

## \_.matchesProperty(path, srcValue)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15593)[npm package](https://www.npmjs.com/package/lodash.matchesproperty)

Creates a function that performs a partial deep comparison between the value at path of a given object to srcValue, returning true if the object value is equivalent, else false.

**Note:** Partial comparisons will match empty array and empty object srcValue values against any array or object value, respectively. See [\_.isEqual](https://lodash.com/docs/#isEqual) for a list of supported value comparisons.

**Since**

3.2.0

**Arguments**

1. path_(Array|string)_: The path of the property to get.
2. srcValue_(\*)_: The value to match.

**Returns**

_(Function)_: Returns the new spec function.

**Example**

var objects = [

  { 'a': 1, 'b': 2, 'c': 3 },

  { 'a': 4, 'b': 5, 'c': 6 }

];

\_.find(objects, \_.matchesProperty('a', 4));

// =\> { 'a': 4, 'b': 5, 'c': 6 }

Try in REPL

## \_.method(path, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15621)[npm package](https://www.npmjs.com/package/lodash.method)

Creates a function that invokes the method at path of a given object. Any additional arguments are provided to the invoked method.

**Since**

3.7.0

**Arguments**

1. path_(Array|string)_: The path of the method to invoke.
2. [args]_(...\*)_: The arguments to invoke the method with.

**Returns**

_(Function)_: Returns the new invoker function.

**Example**

var objects = [

  { 'a': { 'b': \_.constant(2) } },

  { 'a': { 'b': \_.constant(1) } }

];

\_.map(objects, \_.method('a.b'));

// =\> [2, 1]

\_.map(objects, \_.method(['a', 'b']));

// =\> [2, 1]

Try in REPL

## \_.methodOf(object, [args])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15650)[npm package](https://www.npmjs.com/package/lodash.methodof)

The opposite of [\_.method](https://lodash.com/docs/#method); this method creates a function that invokes the method at a given path of object. Any additional arguments are provided to the invoked method.

**Since**

3.7.0

**Arguments**

1. object_(Object)_: The object to query.
2. [args]_(...\*)_: The arguments to invoke the method with.

**Returns**

_(Function)_: Returns the new invoker function.

**Example**

var array = \_.times(3, \_.constant),

    object = { 'a': array, 'b': array, 'c': array };

\_.map(['a[2]', 'c[0]'], \_.methodOf(object));

// =\> [2, 0]

\_.map([['a', '2'], ['c', '0']], \_.methodOf(object));

// =\> [2, 0]

Try in REPL

## \_.mixin([object=lodash], source, [options={}])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15692)[npm package](https://www.npmjs.com/package/lodash.mixin)

Adds all own enumerable string keyed function properties of a source object to the destination object. If object is a function, then methods are added to its prototype as well.

**Note:** Use [\_.runInContext](https://lodash.com/docs/#runInContext) to create a pristine lodash function to avoid conflicts caused by modifying the original.

**Since**

0.1.0

**Arguments**

1. [object=lodash]_(Function|Object)_: The destination object.
2. source_(Object)_: The object of functions to add.
3. [options={}]_(Object)_: The options object.
4. [options.chain=true]_(boolean)_: Specify whether mixins are chainable.

**Returns**

_(\*)_: Returns object.

**Example**

function vowels(string) {

  return \_.filter(string, function(v) {

    return /[aeiou]/i.test(v);

  });

}

\_.mixin({ 'vowels': vowels });

\_.vowels('fred');

// =\> ['e']

\_('fred').vowels().value();

// =\> ['e']

\_.mixin({ 'vowels': vowels }, { 'chain': false });

\_('fred').vowels();

// =\> ['e']

Try in REPL

## \_.noConflict()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15741)[npm package](https://www.npmjs.com/package/lodash.noconflict)

Reverts the \_ variable to its previous value and returns a reference to the lodash function.

**Since**

0.1.0

**Returns**

_(Function)_: Returns the lodash function.

**Example**

var lodash = \_.noConflict();

Try in REPL

## \_.noop()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15760)[npm package](https://www.npmjs.com/package/lodash.noop)

This method returns undefined.

**Since**

2.3.0

**Example**

\_.times(2, \_.noop);

// =\> [undefined, undefined]

Try in REPL

## \_.nthArg([n=0])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15784)[npm package](https://www.npmjs.com/package/lodash.ntharg)

Creates a function that gets the argument at index n. If n is negative, the nth argument from the end is returned.

**Since**

4.0.0

**Arguments**

1. [n=0]_(number)_: The index of the argument to return.

**Returns**

_(Function)_: Returns the new pass-thru function.

**Example**

var func = \_.nthArg(1);

func('a', 'b', 'c', 'd');

// =\> 'b'

var func = \_.nthArg(-2);

func('a', 'b', 'c', 'd');

// =\> 'c'

Try in REPL

## \_.over([iteratees=[\_.identity]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15809)[npm package](https://www.npmjs.com/package/lodash.over)

Creates a function that invokes iteratees with the arguments it receives and returns their results.

**Since**

4.0.0

**Arguments**

1. [iteratees=[\_.identity]]_(...(Function|Function[]))_: The iteratees to invoke.

**Returns**

_(Function)_: Returns the new function.

**Example**

var func = \_.over([Math.max, Math.min]);

func(1, 2, 3, 4);

// =\> [4, 1]

Try in REPL

## \_.overEvery([predicates=[\_.identity]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15835)[npm package](https://www.npmjs.com/package/lodash.overevery)

Creates a function that checks if **all** of the predicates return truthy when invoked with the arguments it receives.

**Since**

4.0.0

**Arguments**

1. [predicates=[\_.identity]]_(...(Function|Function[]))_: The predicates to check.

**Returns**

_(Function)_: Returns the new function.

**Example**

var func = \_.overEvery([Boolean, isFinite]);

func('1');

// =\> true

func(null);

// =\> false

func(NaN);

// =\> false

Try in REPL

## \_.overSome([predicates=[\_.identity]])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15861)[npm package](https://www.npmjs.com/package/lodash.oversome)

Creates a function that checks if **any** of the predicates return truthy when invoked with the arguments it receives.

**Since**

4.0.0

**Arguments**

1. [predicates=[\_.identity]]_(...(Function|Function[]))_: The predicates to check.

**Returns**

_(Function)_: Returns the new function.

**Example**

var func = \_.overSome([Boolean, isFinite]);

func('1');

// =\> true

func(null);

// =\> true

func(NaN);

// =\> false

Try in REPL

## \_.property(path)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15885)[npm package](https://www.npmjs.com/package/lodash.property)

Creates a function that returns the value at path of a given object.

**Since**

2.4.0

**Arguments**

1. path_(Array|string)_: The path of the property to get.

**Returns**

_(Function)_: Returns the new accessor function.

**Example**

var objects = [

  { 'a': { 'b': 2 } },

  { 'a': { 'b': 1 } }

];

\_.map(objects, \_.property('a.b'));

// =\> [2, 1]

\_.map(\_.sortBy(objects, \_.property(['a', 'b'])), 'a.b');

// =\> [1, 2]

Try in REPL

## \_.propertyOf(object)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15910)[npm package](https://www.npmjs.com/package/lodash.propertyof)

The opposite of [\_.property](https://lodash.com/docs/#property); this method creates a function that returns the value at a given path of object.

**Since**

3.0.0

**Arguments**

1. object_(Object)_: The object to query.

**Returns**

_(Function)_: Returns the new accessor function.

**Example**

var array = [0, 1, 2],

    object = { 'a': array, 'b': array, 'c': array };

\_.map(['a[2]', 'c[0]'], \_.propertyOf(object));

// =\> [2, 0]

\_.map([['a', '2'], ['c', '0']], \_.propertyOf(object));

// =\> [2, 0]

Try in REPL

## \_.range([start=0], end, [step=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15957)[npm package](https://www.npmjs.com/package/lodash.range)

Creates an array of numbers _(positive and/or negative)_ progressing from start up to, but not including, end. A step of -1 is used if a negative start is specified without an end or step. If end is not specified, it's set to start with start then set to 0.

**Note:** JavaScript follows the IEEE-754 standard for resolving floating-point values which can produce unexpected results.

**Since**

0.1.0

**Arguments**

1. [start=0]_(number)_: The start of the range.
2. end_(number)_: The end of the range.
3. [step=1]_(number)_: The value to increment or decrement by.

**Returns**

_(Array)_: Returns the range of numbers.

**Example**

\_.range(4);

// =\> [0, 1, 2, 3]

\_.range(-4);

// =\> [0, -1, -2, -3]

\_.range(1, 5);

// =\> [1, 2, 3, 4]

\_.range(0, 20, 5);

// =\> [0, 5, 10, 15]

\_.range(0, -4, -1);

// =\> [0, -1, -2, -3]

\_.range(1, 4, 0);

// =\> [1, 1, 1]

\_.range(0);

// =\> []

Try in REPL

## \_.rangeRight([start=0], end, [step=1])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L15995)[npm package](https://www.npmjs.com/package/lodash.rangeright)

This method is like [\_.range](https://lodash.com/docs/#range) except that it populates values in descending order.

**Since**

4.0.0

**Arguments**

1. [start=0]_(number)_: The start of the range.
2. end_(number)_: The end of the range.
3. [step=1]_(number)_: The value to increment or decrement by.

**Returns**

_(Array)_: Returns the range of numbers.

**Example**

\_.rangeRight(4);

// =\> [3, 2, 1, 0]

\_.rangeRight(-4);

// =\> [-3, -2, -1, 0]

\_.rangeRight(1, 5);

// =\> [4, 3, 2, 1]

\_.rangeRight(0, 20, 5);

// =\> [15, 10, 5, 0]

\_.rangeRight(0, -4, -1);

// =\> [-3, -2, -1, 0]

\_.rangeRight(1, 4, 0);

// =\> [1, 1, 1]

\_.rangeRight(0);

// =\> []

Try in REPL

## \_.runInContext([context=root])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1406)[npm package](https://www.npmjs.com/package/lodash.runincontext)

Create a new pristine lodash function using the context object.

**Since**

1.1.0

**Arguments**

1. [context=root]_(Object)_: The context object.

**Returns**

_(Function)_: Returns a new lodash function.

**Example**

\_.mixin({ 'foo': \_.constant('foo') });

var lodash = \_.runInContext();

lodash.mixin({ 'bar': lodash.constant('bar') });

\_.isFunction(\_.foo);

// =\> true

\_.isFunction(\_.bar);

// =\> false

lodash.isFunction(lodash.foo);

// =\> false

lodash.isFunction(lodash.bar);

// =\> true

// Create a suped-up `defer` in Node.js.

var defer = \_.runInContext({ 'setTimeout': setImmediate }).defer;

Try in REPL

## \_.stubArray()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16015)[npm package](https://www.npmjs.com/package/lodash.stubarray)

This method returns a new empty array.

**Since**

4.13.0

**Returns**

_(Array)_: Returns the new empty array.

**Example**

var arrays = \_.times(2, \_.stubArray);

console.log(arrays);

// =\> [[], []]

console.log(arrays[0] === arrays[1]);

// =\> false

Try in REPL

## \_.stubFalse()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16032)[npm package](https://www.npmjs.com/package/lodash.stubfalse)

This method returns false.

**Since**

4.13.0

**Returns**

_(boolean)_: Returns false.

**Example**

\_.times(2, \_.stubFalse);

// =\> [false, false]

Try in REPL

## \_.stubObject()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16054)[npm package](https://www.npmjs.com/package/lodash.stubobject)

This method returns a new empty object.

**Since**

4.13.0

**Returns**

_(Object)_: Returns the new empty object.

**Example**

var objects = \_.times(2, \_.stubObject);

console.log(objects);

// =\> [{}, {}]

console.log(objects[0] === objects[1]);

// =\> false

Try in REPL

## \_.stubString()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16071)[npm package](https://www.npmjs.com/package/lodash.stubstring)

This method returns an empty string.

**Since**

4.13.0

**Returns**

_(string)_: Returns the empty string.

**Example**

\_.times(2, \_.stubString);

// =\> ['', '']

Try in REPL

## \_.stubTrue()

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16088)[npm package](https://www.npmjs.com/package/lodash.stubtrue)

This method returns true.

**Since**

4.13.0

**Returns**

_(boolean)_: Returns true.

**Example**

\_.times(2, \_.stubTrue);

// =\> [true, true]

Try in REPL

## \_.times(n, [iteratee=\_.identity])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16111)[npm package](https://www.npmjs.com/package/lodash.times)

Invokes the iteratee n times, returning an array of the results of each invocation. The iteratee is invoked with one argument; _(index)_.

**Since**

0.1.0

**Arguments**

1. n_(number)_: The number of times to invoke iteratee.
2. [iteratee=\_.identity]_(Function)_: The function invoked per iteration.

**Returns**

_(Array)_: Returns the array of results.

**Example**

\_.times(3, String);

// =\> ['0', '1', '2']

 \_.times(4, \_.constant(0));

// =\> [0, 0, 0, 0]

Try in REPL

## \_.toPath(value)

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16146)[npm package](https://www.npmjs.com/package/lodash.topath)

Converts value to a property path array.

**Since**

4.0.0

**Arguments**

1. value_(\*)_: The value to convert.

**Returns**

_(Array)_: Returns the new property path array.

**Example**

\_.toPath('a.b.c');

// =\> ['a', 'b', 'c']

\_.toPath('a[0].b.c');

// =\> ['a', '0', 'b', 'c']

Try in REPL

## \_.uniqueId([prefix=''])

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16170)[npm package](https://www.npmjs.com/package/lodash.uniqueid)

Generates a unique ID. If prefix is given, the ID is appended to it.

**Since**

0.1.0

**Arguments**

1. [prefix='']_(string)_: The value to prefix the ID with.

**Returns**

_(string)_: Returns the unique ID.

**Example**

\_.uniqueId('contact\_');

// =\> 'contact\_104'

\_.uniqueId();

// =\> '105'

Try in REPL

## Properties

## \_.VERSION

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L16861)

(string): The semantic version number.

## \_.templateSettings

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1717)[npm package](https://www.npmjs.com/package/lodash.templatesettings)

(Object): By default, the template delimiters used by lodash are like those in embedded Ruby _(ERB)_ as well as ES2015 template strings. Change the following template settings to use alternative delimiters.

## \_.templateSettings.escape

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1725)

(RegExp): Used to detect data property values to be HTML-escaped.

## \_.templateSettings.evaluate

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1733)

(RegExp): Used to detect code to be evaluated.

## \_.templateSettings.imports

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1757)

(Object): Used to import variables into the compiled template.

## \_.templateSettings.interpolate

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1741)

(RegExp): Used to detect data property values to inject.

## \_.templateSettings.variable

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1749)

(string): Used to reference the data object in the template text.

## Methods

## \_.templateSettings.imports.\_

[source](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L1765)

A reference to the lodash function.