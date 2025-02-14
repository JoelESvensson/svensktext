# Platser

## Svenska orter

### Filer

2 007 namn på svenska orter ([CSV](ortsnamn.csv), [JSON](ortsnamn.json)).

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`city` | Namnet på orten | Text

### Källa

- [Mattias Hising](https://github.com/hising/svensk-data)

## Sveriges län

### Filer

Sveriges 21 län ([CSV](lan.csv)).

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`name` | Namnet på länet | Text
`letter` | Länsbokstav | Text
`code` | Länskod | Text
`area` | Yta | Heltal
`population` | Folkmängd (2018-03-31) | Heltal
`population_per_square_km` | Invånare per kvadratkilometer | Decimaltal
`residencetown` | Residensstad | Text
`municipalities` | Antal kommuner i länet | Heltal
`founded ` | Året då länet inrättades | Text
`order_from_north_to_south` | Ordningen från norr till söder (residensstad) | Heltal

### Källa

- [Wikipedia - Sveriges län](https://sv.wikipedia.org/wiki/Sveriges_l%C3%A4n#Lista_%C3%B6ver_Sveriges_l%C3%A4n)

## Sveriges kommuner

### Filer

Sveriges 290 kommuner ([CSV](kommuner.csv)).

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`code` | Kommunkod | Tal
`name` | Kommunens namn | Text
`region` | Län | Text
`population` | Folkmängd | Decimaltal
`area` | Total areal, kvadratkilometer | Decimaltal
`land` | Landareal, kvadratkilometer | Decimaltal
`sea` | Inlandsvattenareal, exklusive fyra största sjöarna, kvadratkilometer | Decimaltal
`ocean` | Havsvattenareal, kvadratkilometer | Decimaltal
`density` | Befolkningstäthet, invånare per kvadratkilometer land | Decimaltal
`bounds_ne_lat_google_2015_05_28` |  | Decimaltal
`bounds_ne_lng_google_2015_05_28` |  | Decimaltal
`bounds_sw_lat_google_2015_05_28` |  | Decimaltal
`bounds_sw_lng_google_2015_05_28` |  | Decimaltal
`location_lat_google_2015_05_28` |  | Decimaltal
`location_lng_google_2015_05_28` |  | Decimaltal

Data städad genom att göra om header till engelska namn samt ta bort mellanslag som tusentalavgränsare.

### Källa

- [Marcus Asplund](https://github.com/marcusasplund/kommundata)

## Länder och huvudstäder

### Filer

Världens 202 länder samt deras huvudstäder ([CSV](lander.csv)).

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`country` | Namnet på landet | Text
`capital` | Namnet på huvudstaden | Text
`continent` | Namnet på kontinenten | Text
`alternative_name` | Alternativt namn på landet | Text
`english` | Landet på engelska | Text
`iso_code` | Landskod i versaler om 3 bokstäver (ISO 3166-1) | Text
 
### Källa

- [Världens flaggor](http://www.flaggorvarlden.se/lista)
- https://sv.wikipedia.org/wiki/Kategori:L%C3%A4nder_efter_v%C3%A4rldsdel

## Landskoder

### Filer

245 landskoder i ISO 3166-1-format ([CSV](landskoder.csv)).

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`code2` | Landskod i versaler om 2 bokstäver | Text
`code3` | Landskod i versaler om 3 bokstäver | Text
`number` | Nummer på land om 3 siffror | Tal
`country` | Namnet på landet | Text

### Källa

- [ISO 3166-1-koder](https://sv.wikipedia.org/wiki/ISO_3166)

## Valutor

### Filer

- 216 valutor ([CSV](valutor.csv)).

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`country` | Namnet på landet eller området för valutan | Text
`currency` | Namnet på valutan | Text
`code` | Valutakod med 2-3 tecken (ISO 4217) | Text


Notera att länder kan förekomma flera gånger, exempelvis:

```
Panama,Balboa,PAB
Panama,Amerikansk dollar,USD
```

### Källa

- https://sv.wikipedia.org/wiki/Lista_%C3%B6ver_l%C3%A4nders_valutor

### Se även

- https://sv.wikipedia.org/wiki/ISO_4217
- https://en.wikipedia.org/wiki/ISO_4217

## Svenska vägar

### Filer

- 278 vägnamn ([CSV](vagar.csv))

### Datastruktur

Kolumn | Beskrivning | Datatyp
:------- | :----------  | :----------
`road` | Namnet på vägen | Text
`number` | Nummer på vägen (extraherat från namnet) | Tal
`reach` | Sträckning (d.v.s. orter där vägen passerar) | Text
`type` | Typ av väg (`Europaväg`, `Riksväg` eller `Länsväg`) | Text

### Källa

- https://sv.wikipedia.org/wiki/Lista_%C3%B6ver_svenska_v%C3%A4gar_i_nummerordning

## Källkod

### Python

```py
# Import.
import pandas as pd
url = "https://raw.githubusercontent.com/peterdalle/svensktext/master/platser/lander.csv"
df_countries = pd.read_csv(url, encoding="utf8")
```

### R

```r
# Import.
url <- "https://raw.githubusercontent.com/peterdalle/svensktext/master/platser/lander.csv"
df_countries <- read.csv(url, sep=",", encoding="UTF-8", stringsAsFactors=FALSE, 
                         header=TRUE, col.names=c("country", "capital", "continent", "alternative_name"))

```