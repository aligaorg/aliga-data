# Come contribuire

I dati che permettono ad [Aliga](https://play.google.com/store/apps/details?id=com.williamghelfi.apps.aliga) di funzionare sono ricavati dai veri calendari per la raccolta differenziata che ognuno di noi ha in casa, e poi pazientemente compilati a mano nei file che trovi in questo repository.

## Dubbi e risposte

**È complicato?**
Meno di quanto ti aspetti. Continua a leggere.

**Ma quanto tempo ci vuole?**
Una volta presa la mano, per un calendario semplice come quello di San Sperate ho impiegato circa due ore. E ci ho lavorato una mezzora alla volta, quando ne avevo voglia.  
Per un calendario medio come quello di Assemini, circa quattro ore in totale. Sempre frazionate.  
Per un calendario complesso (ha 12 zone!) come quello di Iglesias, ci possono volere probabilmente anche otto ore.
*Il trucco è sempre frazionarle nel tempo, e fare poco per volta.*

**Come devo fare?**
Innanzitutto è necessario seguire scrupolosamente il **semplice formato** che descriverò qui di seguito.  
Questo perché i dati che inserirai sono destinati alla lettura automatica da parte di programmi per computer, e i programmi per computer non sono per nulla inclini a interpretare i significati vaghi: hanno bisogno di precisione nella forma dei dati!  
Per aiutarti, puoi anche fare copia-incolla di un file già esistente e limitarti a modificarne il contenuto ;-)

**Anche se le regole sono poche, ho comunque difficoltà col formato dei file!**
Niente paura: segui ugualmente le indicazioni che trovi più avanti sotto *Come caricare i miei nuovi file* e poi discuteremo su GitHub del modo più semplice per aiutarti.  
In questo senso, GitHub funziona in modo molto simile a Facebook o Google+ e una volta aperta una *pull request* si può commentare e confrontarsi.  
Così non è necessario che tu faccia tutto giusto al primo colpo, ma sia io che gli altri contributori potremo aiutarti finché il tuo contributo non sarà corretto e pronto per essere integrato nella base dati :)

**Mi dispiace, ho tentato ma non capisco una parola di quello che scrivi :-/**
Non c'è problema! Evidentemente hai la volontà di contribuire, ma non ne hai i mezzi perché nella tua vita ti sei interessato/a di altre cose.  
Il mio consiglio, in questo caso, è quello di cercare un amico o un conoscente che invece si senta a suo agio con questi strumenti e di collaborare insieme all'inserimento nella base dati delle località con cui intendevi contribuire quanto hai tentato da solo/a :-)

## Il formato

Se conosci JSON, ti troverai subito a tuo agio ma continua a leggere.  
Se non lo conosci, nessun problema: continua ugualmente a leggere.

### Due tipi di file

Per ogni località / calendario sono necessari due file:

* `<località>.years.json`  
contiene l'elenco degli anni per cui abbiamo inserito dei calendari relativi alla località in questione, e il periodo di validità
* `<località>.schedule.<anno>.json`   
contiene il calendario vero e proprio dell'anno in questione relativo alla località in questione, con l'indicazione di tutti giorni per cui il calendario è valido nel corso dell'anno in questione.

Capire il periodo di validità è semplice:

* se il periodo di validità è dichiarato, spesso nelle prime o nelle ultime pagine, riportalo
* se il periodo non è dichiarato, riporta semplicemente la prima e l'ultima data che trovi nel calendario vero e proprio. Ad esempio un calendario potrebbe mostrare solamente i giorni a partire dal 5 Maggio, e terminare col 30 Novembre in attesa della pubblicazione di un nuovo calendario.

`<località>` è un codice particolare, a cui diamo il nome di `slug`, che si ottiene molto facilmente dal nome comune della località seguendo queste poche semplici regole:

* scrivi tutto minuscolo
* se ce ne sono, sostituisci gli spazi e gli apostrofi con dei trattini `-`
* se ci sono lettere con l'accento, sostituiscile con la loro versione senza accento

>#### Esempio di slug: Trinità D'Agultu e Vignola
>
> Applichiamo le regole una di seguito all'altra fino ad ottenere lo `slug`.
>
> 1. scrivi tutto minuscolo:  
> `trinità d'agultu e vignola`
> 2. spazi e apostrofi diventano trattini:  
> `trinità-d-agultu-e-vignola`
> 3. via le lettere con l'accento:  
> `trinita-d-agultu-e-vignola`
> 

Una volta fatta l'abitudine, ti verrà naturale e potrai scrivere uno `slug` senza stare troppo a pensarci ;-)

Ora che abbiamo lo `slug`, vediamo un esempio di ciascuno dei due file occorrenti.

>#### Esempio di file degli anni: San Sperate
>
> Come avrai già capito dalle indicazioni precedenti, il nome deil file sarà:  
> `san-sperate.years.json`
> 
> Supponendo di avere a disposizione e voler inserire i calendari per il 2014 e per il 2015, e i relativi periodi (che ho inventato sul momento) di validità il contenuto del file sarà:
> 
> ```json
> {
>   "city": "San Sperate",
>   "calendars": [
>     {
>       "year": 2014,
>       "validfrom": "2014-02-01",
>       "validto": "2014-03-03"
>     },
>     {
>       "year": 2015,
>       "validfrom": "2015-01-01"
>       "validto": "2015-06-30"
>     }
>   ]
> }
> ```

>#### Esempio di file degli del calendario: San Sperate
>
> Supponendo di occuparci per primo del calendario per il 2014, il nome del file sarà:  
> `san-sperate.schedule.2014.json`
> 
> Ed eccone il contenuto, ma attenzione: per evitare di farla troppo lunga, farò finta che in un mese ci siano solo pochi giorni!
> 
> ```json
> {
>  "city": "San Sperate",
>  "year": 2014,
>  "schedule": [
>    {
>      "month": 2,
>      "days": [
>        {
>          "date": "2014-02-01",
>          "zones": [
>            {
>              "name": "Zona unica",
>              "types": null
>            }
>          ]
>        },
>        {
>          "date": "2014-02-02",
>          "zones": [
>            {
>              "name": "Zona unica",
>              "types": null
>            }
>          ]
>        },
>        {
>          "date": "2014-02-03",
>          "zones": [
>            {
>              "name": "Zona unica",
>              "types": [
>                "umido",
>                "ingombranti"
>              ]
>            }
>          ]
>        },
>      },
>      {
>        "month": 3,
>         "days": [
>          {
>            "date": "2014-03-01",
>            "zones": [
>              {
>                "name": "Zona unica",
>                "types": [
>                   "vetro e lattine",
>                   "carta"
>                ]
>              }
>            ]
>          },
>          {
>            "date": "2014-03-02",
>            "zones": [
>              {
>                "name": "Zona unica",
>                "types": null
>              }
>            ]
>          },
>          {
>            "date": "2014-03-03",
>            "zones": [
>              {
>                "name": "Zona unica",
>                "types": [
>                  "umido",
>                  "ingombranti"
>                ]
>              }
>            ]
>          }
>        ]
>      }
>    ]
>  }
>
> ```

**Cosa sono tutte queste parentesi?**  
Possiamo identificare **elementi** e **liste di elementi**.

* un elemento *semplice* è semplicemente una parola o una frase breve tra virgolette, oppure un numero intero senza virgolette:  
`"vetro e lattine"` oppure `2014`

* una lista di elementi (se vuoi, si chiama *array* di elementi), che può contenere elementi semplici o elementi non semplici, è sempre racchiusa tra parentesi quadre:

```json
"types": [
  "umido",
  "ingombranti"
]
```

oppure:  

```json
"schedule": [
  "month": 2,
  "days": {
    "date": "2014-02-01",
    // e così via come sopra
  }
]
```
* un elemento *non semplice*, ovvero un elemento che può contenere elementi semplici e liste, è sempre racchiuso tra parentesi graffe:

```json
{
  "city": "San Sperate",
  "year": 2014,
  "schedule": [
  // e così via come sopra
  ]
}
```

Inoltre, come avrai notato, gli elementi di una lista sia semplici che non semplici sono sempre separati da una virgola (come in italiano!).

**Un suggerimento per i principianti**  
Prendi uno dei file già esistenti, fai copia – incolla, cambia il nome e adattalo. Sarà tutto più facile finché non prendi la mano!

**Un ultimo dettaglio**  
Nei giorni in cui non è prevista la raccolta differenziata porta a porta, inseriremo `null` al posto della lista dei tipi di rifiuto! Controlla nell'esempio!

**Nota bene**  
Questo esempio è per San Sperate, una località che non è suddivisa in zone per la raccolta differenziata.  
Per vedere invece come comportarsi con un comune che è suddiviso in più zone, puoi curiosare nei file di Assemini.

## Come caricare i miei nuovi file

### Se non conosci GitHub o Git

**INSERIRE ISTRUZIONI**

### Se conosci GitHub o Git

Le istruzioni per te sono molto più brevi.

* fai un fork del repository
* crea una nuova branch a partire da `master`
* appena hai qualcosa fai una pull-request, in modo che possiamo subito cominciare a discutere se c'è bisogno di farlo, e continua poi a lavorarci tenendola aggiornata con nuovi commit man mano che prosegui col lavoro

**Non aspettare di aver finito tutto prima di aprire la pull-request!**

## In conclusione

Questo è tutto!  
Se c'è ancora qualche dubbio, contattaci su [Facebook](https://www.facebook.com/aligaapp) o [Twitter](https://twitter.com/aligaapp)