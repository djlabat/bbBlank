# MARKDOWN
## Naslov H2
### naslov h3
#### i tako dalje h4



NASLOV H1
=========

Naslov h2
---------

[SADRZAJ](#sadrzaj)
[LINK KA NASLOVU 1](#link-ka-naslovu-1)
[LINK KA NASLOVU 2](#link-ka-naslovu-2)

Paragraf, prazan red iznad i ispod
Ovo je drugi red paragrafa ali se nije prelomio jer nema dupli space na kraju reda.  
Ovo je treci red paragrafa da duplim space na kraju prethodnog reda.

Novi paragraf - space iznad

*italic* sa _donjim linijama_ - Ctrl + I - plugin: Markdown All in One. Moze i _italic_
**BOLD** sa __donjim linijama__ - cB  
***italic + bold*** sa ___donjim linijama___ - cI, cB  
~~striketrough~~  

> citiranje nekog teksta
> 
> jos malo citiranja

1. Ordered List...
2. ...ili ti `<ol>`
3. Bitno da je jedinica prvi broj...

    Jedinica otvara OL

10. ...ostali brojevi ne moraju biti u redu.

- Unordered List...
- ...ili ti `<ul>`

    Pragragraf u listi (indent)

- nastavak liste

`backtick` je isto sto i `<code>` u HTML (sirov text)
npr. `<qwe>#`

<!-- Fenced Code Block ↓ -->
```js
{
    "firstName": "John",
    "lastName": "Smith",
    "age": 25
}
```

<!-- Markiranje texta -->
<style>
    mark {background-color:green}
</style>

<mark>Markirani text</mark>
<span style="background-color:blue">Plavi markirani text</span>

<!-- Bojenje texta -->
<span style="color:yellow">Zuto obojeni text</span>

<!-- horizontalna linija ↓ -->
---

<!-- link inline -->
[Dillinger Markdown](https://dillinger.io/ "alt text linka") - inline link

<!-- link brzi -->
<https://dillinger.io/> - brz i direktan link

<!-- link referentni -->
[YouTube] - referentni link (vidi na dnu fajla)

<!-- image -->
![Dillinger - alt text](https://mdg.imgix.net/assets/images/dillinger.png)

<!-- TO DO lista -->
- [x] prvi task
- [ ] Alt + C (an)čekira - plugin: Markdown All in One
- [ ] treci task

| Tabela | zaglavlje |
| :----- | :-------: |
| table  |    data   |

<!-- Emoji -->
That is so funny! :joy: :smile: :angry: :heart:

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

<!-- Highlight -->
I need to highlight these ==very important words==.

## LINK KA NASLOVU

[YouTube]: <https://www.youtube.com>