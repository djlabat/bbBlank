# NPM - osnove

+ "dependencies": Packages required by your application in production.
+ "devDependencies": Packages that are only needed for local development and testing.

izvor:  
https://www.webprogramiranje.org/npm-yarn-osnove/

## AŽURIRANJE PACKAGE MANAGER-A (npm-a)

```bash
npm install -global npm
```

## INICIJALIZACIJA 

Inicijalizacija znaci otvaranje novo projekta.

```bash
npm init
```

## INSTALACIJA NOVIH PAKETA
### a) Globalna instalacija (operativni sistem)

```bash
npm install -global nazivPaketa
```

### b) Lokalna instalacija (u projektu)

```bash
npm install nazivPaketa [flag]
```

Opcije pri instalaciji:

| Flag 			| Shortcut | Namena                          |
| ----------| -------- | ------------------------------- |
| –save 		| -S 	     | Dodavanje paketa u Dependencies |
| –save-dev | -D 	     | Dodavanje paketa u devDependencies |
| @1.2.3 		| /	 	     | Dadatak zalepljen uz naziv paketa koji definiše tačnu verziju paketa koju želimo da instaliramo (ukoliko se izostavi instalira najnoviju verziju) |

## INSTALACIJA SVIH PAKETA IZ package.json

Kada se klonira projekat on ne dolazi sa instaliranim paketima 
već samo sa uputstvom šta treba da se instalira (package.json).
Instalacija svih dependenvcies definisanih u package.json fajlu
se vrši sa:

```bash
npm install
```
 
```bash
npm i
```

## AŽURIRANJE DEPENDENCIES

### Ažuriranje pojedinačnih paketa
Uz naredbu za ažuriranje instaliranog paketa potrebno je da koristimo odgovarajući flag koji je korišćen pri instalaciji:  

```bash
npm update nazivPaketa [opcioni flag]
```

### Reinstalacija svih paketa

```bash
rm -rf node_modules && npm install
```

## UKLANJANJE DEPENDENCIES

Uz naredbu za uklanjanje instaliranog paketa potrebno je da koristimo odgovarajući flag koji je korišćen pri instalaciji:  

```bash
npm uninstall nazivPaketa [opcioni flag npr. --save-dev]
```

## POKRETANJE PAKETA

Odgovarajući paket se pokreće sa naredbom:  

```bash
npm run nazivPaketa
```

## TIPS & TRICS

### Korišćenje Git repozitorijuma umesto npm Modules

Ako ne želimo da koristimo oficijalni sajt već neki privatni repozitorijum, možemo da u package.json koristimo sledeći kod:  

	{
	   "dependencies": {
	       "angular-ui-codemirror": "git+ssh://git@github.com:jpetitcolas/ui-codemirror.git#di"
	   }
	}

	{
	   "dependencies": {
	       "angular-ui-codemirror": "git+ssh://git@github.com:jpetitcolas/ui-codemirror.git#di"
	   }
	}

### Brisanje ne deklarisanih modula

Ukoliko nekada zaboravimo da koristimo `--save` ili `--save-dev` pri instalaciji paketa, koristite naredbu “prune” za brisanje takvih paketa: 

```bash
npm prune
```

ili u produkciji potrebno je dodati –production:  

```bash
npm prune --production
```

Ova komanda briše sve pakete koji se ne nalaze u “package.json” fajlu.

### Definisanje verzije paketa

Sa adekvatinim predznacima možemo da tačnije definišemo verziju paketa:

   + (^) targetira sve glavne verzije npr. (1.*.*)
   + (~) targetira se najnovija minor verzija npr. (1.2.*)
   + Tačna verzija npr. (1.2.3)

### Fiksiranje verzije paketa

Ukoliko želimo da “zauvek” fiksiramo verziju u toku instalacije dovoljno je da koristimo:

```bash
npm install --save --save-exact nazivPaketa
```

### Pregled outdated verzija

```bash
npm outdated
```

Ova naredba pregledno izlistava stanje verzije za svaki paket:

	Package                 Current  Wanted  Latest  Location
	babel-cli                6.14.0  6.16.0  6.18.0  admin-on-rest
	babel-core              MISSING  6.17.0  6.18.2  admin-on-rest
	babel-eslint              6.1.2   7.0.0   7.1.0  admin-on-rest
	babel-preset-es2015      6.14.0  6.16.0  6.18.0  admin-on-rest

## MOJI ZAPISI

```bash

```
### npm START

```bash
npm start [opcion flag]
```

This runs a predefined command specified in the "start" property of a package's "scripts" object.

If the "scripts" object does not define a "start" property, npm will run node server.js.

Note that this is different from the default node behavior of running the file specified in a package's "main" attribute when evoking with node .

As of npm@2.0.0, you can use custom arguments when executing scripts. Refer to npm run-script for more details.
Example

 
    {
      "scripts": {
        "start": "node foo.js"
      }
    }

output:  

		npm start
		> npm@x.x.x start
		> node foo.js
		(foo.js output would be here)

## package-lock.json

package-lock.json is automatically generated for any operations where npm modifies either the node_modules tree, or package. json . It describes the exact tree that was generated, such that subsequent installs are able to generate identical trees, regardless of intermediate dependency updates.