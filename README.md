# Documentazione
## Struttura delle cartelle
* `build` - contiene i file di configurazione dei tool utilizzati.
    * `.stylelintrc`
    * `postcss.config.js`
* `css` - i file bundle generati
    * `main.css`
    * `main.css.map`
    * `main.css.min`
    * `main.css.min.map`
* `scss`
    * `_bootstrap_components.scss` - componenti di bootstrap inclusi nel bundle finale.
    * `_custom.scss` - regole css personalizzate ed eventuali inclusioni di altri file che aggiungono altri componenti o semplicemente altre regole.
    * `_variables.scss` - variabili clonate da bootstrap per la sovrascrittura e variabili custom.
    * `main.scss` - inclusione di tutti i file scss.

---
## Package.json

Ogni script che segue va eseguito nella console e deve essere preceduto dal comando `npm run`.

> __N.B.__ In questo momento lo script `css.lint` è escluso dall'esecuzione effettuata da `npm run css` a causa di una revisione in corso delle regole di sintassi scss contenute in `build/.stylelintrc`.

|Script|descrizione|tool|config|
|:---:|:---|:---:|---:|
|`css`|esegue tutti i task css seguenti con un unico comando e nel seguqnte ordine: ~~`css.lint`~~, `css.compile`, `css.prefix`, `css.minify`.|-|-|
|`css.with.lint`|Come sopra ma aggiunge alla catena di esecuzione anche il controllo del codice.|-|-|
|`css.lint`|controlla eventuali errori del scss e verifica se le best practices sono state rispettate (coming soon).|`stylelint`|`build/.stylelintrc`|
|`css.compile`|compila tutti i file `scss` in un unico file css dentro la cartella `/css` chiamato `main.css`. Crea anche il rispettivo file di mappa `main.css.map`.|`node-sass`|`inline`|
|`css.prefix`|esamina il file `css/main.css` aggiungendo, dove necessario, i prefissi per rendere i file di stile crossbrowser.|`postcss`|`package.json`, `build/postcss.config.js`|
|`css.minify`|prende in ingresso `css/main.css` e lo comprime, eliminando commenti e righe vuote e portando tutto il codice css in un unica riga.|`cleancss`|`inline`|
|`css.watch`|osserva tutti i file contenuti in `scss/**/*.scss`, appena intercetta un cambiamento di uno di questi file riavvia lo script `npm run css`.|`watch`|-|

---
## Link utili
* Link Documentazioni
    * [Bootstrap](http://getbootstrap.com/docs/4.1/getting-started/introduction/)
    * [Nodejs](https://nodejs.org/it/docs/)
    * [stylelint](https://stylelint.io/user-guide/)
    * [node-sass](https://www.npmjs.com/package/node-sass)
    * [postcss](https://github.com/postcss/postcss/tree/master/docs)
        * [post-css-cli](https://github.com/postcss/postcss-cli)
    * [clean-css](https://github.com/jakubpawlowicz/clean-css)
        * [clean-css-cli](https://github.com/jakubpawlowicz/clean-css-cli)
    * [watch](https://github.com/mikeal/watch)

## ToDo list
* Revisionare il file `build/stylelintrc` sulla base delle regole che si vogliono applicare alla scrittura del nostro codice scss.# testttt
