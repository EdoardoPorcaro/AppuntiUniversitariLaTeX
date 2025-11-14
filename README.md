# AppuntiUniversitariLaTeX

Questo template $\LaTeX$ è pensato per tutti gli studenti universitari che vogliano prendere appunti delle lezioni in formato dattiloscritto, giovando non solo dell'ordine che un documento digitale garantisce ma anche dei perfezionamenti tipografici e delle svariate funzionalità che permette $\LaTeX$.

## Indice
1. Compilare un documento $\LaTeX$
    1. TeXStudio
    2. Visual Studio Code
    3. VIM/NeoVIM
    4. `pdflatex`
2. Struttura del template
3. Come usare il template
6. Scelte stilistiche del template
7. Comandi principali
    1. Matematica
5. Comandi personalizzati
6. Per approfondire
7. Licenza
8. Ringraziamenti

## Compilare un documento $\LaTeX$

Tre sono le principali strade che un utente può intraprendere per compilare i propri documenti `.tex`. Li illustro a partire dalla seguente tabella, per poi dare informazioni specifiche e consigli personali per ciascuna strada.

| Opzione | Pesantezza | Livello di esperienza richiesto |
| - | - | - |
| TeXStudio | No (IDE + motore di compilazione) | Basso |
| Visual Studio Code | No (però magari qualcuno lo ha già per altri motivi/per altri linguaggi di programmazione) | Medio |
| `texlive` + `pdflatex` | Sì (compilazione sono da linea di comando, la modifica dei file `.tex` è lasciata ad altro programma | Alto |

## Struttura del template

Il template è strutturato da tre file: `main.tex`, `porcaro.tex` e `contenuto.tex`.

- `porcaro.tex` è il vero cuore del template, perché là sono contenute tutte le inclusioni dei pacchetti e le definizioni di stile;
- `main.tex` è il file principale, è quello da compilare per avere il PDF desiderato e contiene solo la struttura scheletrica del documento (unisce `porcaro.tex` e `contenuto.tex`, aggiungendo anche le definizioni personali dell'utente, la pagina del titolo e la breve descrizione del corso).
- `contenuto.tex` è creato appositamente affinché là ci vada il vero e proprio contenuto del documento; il file è separato così che uno possa concentrarsi completamente sul testo e non sulle definizioni di stile.

## Come usare il template

Usare il template è molto facile e immediato. Scaricando i file dall'[ultima versione disponibile](#), si potrà quasi subito iniziare a scrivere il proprio documento. Prima di iniziare, infatti, basta personalizzare le caratteristiche del documento, riassunte nella tabella seguente, con le informazioni personali.

| Proprietà | Dove modificarla | Descrizione |
| - | - | - |
| Nome e cognome | Riga 4 di `main.tex`, nome al posto di *NOME*, cognome al posto di *COGNOME* | Il proprio nome e cognome. Viene visualizzato nel frontespizio, nell'intestazione in alto a sinistra nelle pagine pari e come metadato *autore* del PDF generato.
| Proprio indirizzo di posta elettronica | Riga 5 di `main.tex`, dentro a `\AutoreEPostaElettronica` al posto di *MAIL@EXAMPLE.ORG* (non rimuovere `mailto:`) | Il proprio indirizzo di posta elettronica a cui essere contattati per informazioni circa i propri appunti; l'indirizzo di posta elettronica è raggiungibile dai lettori cliccando sul proprio nome o nel frontespizio o, nell'intestazione, in alto a sinistra delle pagine pari.
| Nome del corso | Riga 8 di `main.tex`, al posto di *TITOLO CORSO QUI* | Il nome del corso a cui si riferiscono gli appunti, che è poi anche il metadato *titolo* del documento PDF generato e viene visualizzato come titolo nel frontespizio.
| Nome prof. | Riga 9 di `main.tex`, al posto di *NOME PROF QUI* | Il nome del professore o professoressa che eroga il corso. Viene visualizzato solo nel frontespizio.
|  Anno accademico | Riga 10 di `main.tex`, al posto di *2025/2026* | L'anno accademico a cui si riferiscono gli appunti. Viene visualizzato solo nel frontespizio.
| Comandi personalizzati | A partire dalla riga 23 di `main.tex` | Comandi personalizzati che si vuole usare in tutto il documento, separati e conservati qui (anziché in `porcaro.tex`) onde evitare conflitti e confusione con le definizioni del template.

Una volta personalizzate le "informazioni" del documento, si può iniziare subito a comporre il corpo del documento nel file `contenuto.tex`.

## Scelte stilistiche del presente template

## Comandi principali

Sebbene i comandi che ho introdotto io da zero siano contenuti nella successiva sezione [Comandi personalizzati](#comandi-personalizzati), qui riporto i comandi "tradizionali" più utilizzati, perché, per come ho strutturato io il template e dati i pacchetti scelti, potrebbero essere non quelli che ci si aspetta di poter usare. Ad esempio, per creare un riferimento si usi `\cref{}` (del pacchetto [`cleveref`](https://ctan.org/pkg/cleveref)) e non i più comuni `\ref{}` o `\vref{}` (quest'ultimo del pacchetto [`varioref`](https://ctan.org/pkg/varioref)).

### Matematica

Com'è ovvio che sia, i seguenti comandi funzionano solo in math mode.

| Comando | Descrizione | Pacchetto |
| - | - | - |
`\cancel{math}`, `\xcancel{}`, `\cancelto{}`, … | | [`cancel`](https://ctan.org/pkg/cancel)
`\mathsrc{lett}` | Rende la lettera `lett` ancor più in corsivo che una tradizionale `\mathcal{lett}`. | [`mathrsfs`](https://ctan.org/pkg/mathrsfs) |
`\mathbbm{char}` | Rende il carattere `char`, sia esso una lettera o un numero, in stile blackboard bold; se definito `\mathbb{char}` per tale carattere, esso è equivalente a `\mathbb{lett}`. | [`bbm`](https://ctan.org/pkg/bbm)

Oltre a questi, sono inclusi ovviamente i tradizionali pacchetti della [American Mathematical Society](https://www.ams.org/home/page) (`amsmath`, `amssymb`, `amsfonts` e `amsthm`), oltre ai pacchetti [`mathtools`](https://ctan.org/pkg/mathtools) e [`stmaryrd`](https://ctan.org/pkg/stmaryrd), che forniscono simboli matematici e comandi aggiuntivi non presenti negli standard $\LaTeX$ o AMS.

### Riferimenti, collegamenti, ancore

La vera potenza di $\LaTeX$ sta, almeno in parte, nel poter creare in maniera diretta e naturale documenti dinamici, con collegamenti tra sezioni, riferimenti, indici. Nelle tabelle seguenti riassumo i più importanti comandi che, partendo dal mio template, possono aiutarti a creare anche tu documenti interconnessi.

#### Riferimenti

| Comando | Descrizione | Pacchetto |
| - | - | - |
| `\cref{obj-label}` | | `cleveref`
| `\cref{obj-label-first}{obj-label-second}` | | `cleveref`
| `\crefrange{}{}` | | `cleveref`
| `\crefpage{obj-label}` | | Definito da me basandomi su `cleveref`

#### Collegamenti

| Comando | Descrizione | Pacchetto |
| - | - | - |
| `\href{¹}{²}` | Inserisce un collegamento ipertestuale di testo cliccabile `²` che porta all'indirizzo internet `¹`. | `hyperref`
| `\url{¹}` | Equivale a scrivere `\href{¹}{¹}`, con il beneficio aggiunto che in questo caso il testo cliccabile non andrà mai a capo. | `url` (caricato internamente da `hyperref`)
| `\phantomsection\addcontentsline{¹}{²}{³}`| Aggiunge manualmente nell'indice `¹` (`toc`, `lof`, `lot`) e nei segnalibri PDF la voce `³` di livello `²` (`section`, `subsection`, `figure`, …). | `hyperref` e kernel $\LaTeX$, rispettivamente |
| `\addcontentsline{¹}{²}{³}` | Aggiunge manualmente, solo nell'indice `¹` (`toc`, `lof`, `lot`) la voce `³` di livello `²` (`section`, `subsection`, `figure`, …).
| `\phantomsection\pdfbookmark[¹]{²}{³}` | Aggiunge manualmente, solo nei segnalibri PDF, la voce `²` di livello `¹` (`0` per `chapter`, `1` per `section`, …) con identificativo univoco `³`. | `hyperref`
| `\texorpdfstring{¹}{²}` | Usato se nel titolo di una voce di indice (destinata almeno ai segnalibri PDF) appare math mode: si specifica in `¹` il codice $\LaTeX$ e in `²` il testo Unicode per il segnalibro PDF. | `hyperref` |

## Comandi personalizzati

| Comando | Descrizione |
| - | - |
| `\es[opz]{obb}` | Crea un paragrafo *esempio*, il cui titolo nel documento è `obb` mentre il titolo nell'indice dei contenuti e nei segnalibri PDF è `opz`. Il paragrafo *esempio* è aperto, a sinistra del suo titolo `obb`, dall'icona di una matita con la punta verso sinistra mentre è chiuso **manualmente** dall'icona di una matita con la punta verso destra. **Per chiudere il paragrafo, usare `\FineEs\` se l'esempio termina all'interno di una formula in modalità display math oppure `\FineEsTesto\` se l'esempio termina in modalità testo.** Supporta la versione stellata `\es*{obb}`. |
| `\oss[opz]{obb}` | Crea un paragrafo *osservazione*, il cui titolo nel documento è `obb` mentre il titolo nell'indice dei contenuti e nei segnalibri PDF è `opz`. Il paragrafo *osservazione* è aperto, a sinistra del suo titolo `obb`, dall'icona di una punta di penna stilografica rivolta verso sinistra mentre è chiuso **manualmente** dall'icona di una punta di penna stilografica rivolta verso destra. **Per chiudere il paragrafo, usare `\FineOss\` se l'osservazione termina all'interno di una formula in modalità display math oppure `\FineOssTesto\` se l'osservazione termina in modalità testo.** Supporta la versione stellata `\oss*{obb}`. |

## Per approfondire
