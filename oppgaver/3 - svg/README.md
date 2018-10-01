# SVG

SVG er et XML-språk, i likhet med HTML, som kan bli brukt til å tegne vektorgrafikk. Enten ved å spesfisere alle linjer og objekter eller ved å modifisere bilder.

## Et enkelt eksempel.

```html
<svg
  version="1.1"
  baseProfile="full"
  width="300" height="250"
  xmlns="http://www.w3.org/2000/svg"
>
  <circle cx="150" cy="125" r="125" fill="black" />

  <text x="150" y="150" font-size="60" text-anchor="middle" fill="white">BEKK</text>
</svg>
```

Ved å kopiere og lime inn koden over i en fil med navn bekk.svg og åpne den i nettleseren vil man se følgende skjermdump.

<img src="img/bekk.png" height="200">

`svg`-elementet spesifiserer høyden (`height="250"`) og bredden (`width="300"`) til selve SVGen. Versjonen spesifiseres med `version`, `baseProfile` og `xmlns`.

`circle`-elementet tegner en sirkel med sentrum i `cx="150" cy="125"` med radius 125 piksler (`r="125"`) og svart bakgrunnsfarge (`fill="black"`).

`text`-elementet skriver teksten `BEKK` med hvit skrift (`fill="white"`) i skriftstørrelse 60px (`font-size="60"`) på posisjon spesifisert med `x="150" y="150" text-anchor="middle"`

### Posisjonering

Man bruker et koordinatsystem for å posisjonere elementer i svg-dokumentet.

![grid](https://mdn.mozillademos.org/files/224/Canvas_default_grid.png)

Koordinatsystemet startet i øvre venstre hjørne (0,0). Posisjoner måles i piksler fra dette hjørnet, med positiv x-retning til høyre og positiv y-retning nedover.

> Legg merke til at dette er motsatt av hva man lærte på skolen.

### :trophy: [Oppgave 1](https://codepen.io/sveinpg/pen/qJErqy)

Flytt den rød firkanten ned i høyre hjørne.

<img src="img/rect.png" height="200">

:bulb: Flytter man firkanten for langt vil den havne utenfor viewporten.

:bulb: Mer om posisjonering kan leses på [MDN](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Positions)

## Basic shapes

Det finnes former som man bruke som byggesteiner til å lage mer avanserte SVGer.

- [rect](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/rect) brukes til å tegne rektangler.
- [circle](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/circle) brukes til å tegne sirkler.
- [ellipse](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/ellipse) er en mer generell versjon av `circle`.
- [line](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/line) brukes til å tegne rette linjer mellom to punkter.
- [polyline](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/polyline) brukes til å tegne linjer mellom flere punkter.
- [polygon](https://developer.mozilla.org/en-US/Web/SVG/Element/polygon) brukes på samme måte som `polyline`, men tegner en strek mellom første og siste punkt slik at man får en lukket form.
- [path](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/path) er den mest generelle formen som kan brukes i SVG og kan brukes til å lage alle andre elementer. Man bruker attributten [d](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/d) til å definere pathen som skal tegnes.

### :trophy: [Oppgave 2](https://codepen.io/sveinpg/pen/ePmvey)

Lag en svart firkant med en rød sirkel.

<img src="img/circle.png" height="200">

:bulb: Man bruker attributten `fill` til å sette fyllfarge.

:bulb: SVG-dokumenter leses fra toppen og nedover. Slik at elementer definert lenger ned i dokumentet tegnes på toppen av de som er tegnet allerede.

## Fill and stroke

For å bestemme fargen til et element bruker man attributtene `fill` og `stroke`. Begge tar samme verdier som farger som man kan bruke i css. Enten det er fargenavn (feks `red`) eller rgb-verdier (feks `rgb(255,0,0)`) eller hex-verdier (feks `#fffff`). Man kan i tillegg spesifisere hvor gjennomsiktig en farge skal være (opacity) med attributtene `fill-opacity` og `stroke-opacity`.

### :trophy: [Oppgave 3](https://codepen.io/sveinpg/pen/KGwWbX)

Gi hjertet rød fyllfarge og en svart strek rundt.

<img src="img/hearth.png" height="200">

:bulb: Mer om [fill og stroke](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Fills_and_Strokes)

## Styling med CSS

I tillegg til å sette attributter på objekter kan man bruke CSS til å style `fill` og `stroke`. Ikke alle attributter kan settes med CSS. `fill`, `stroke` og `stroke-dasharray` er blandt attributtene som kan settes med CSS. Attributter som `width`, `height` og `path`-spesifikke kommandoer kan ikke settes med CSS.

> Man kan lese [SVG spesifikasjonen](https://www.w3.org/TR/SVG/propidx.html) for å se hvilke som lar seg modifisere med CSS. Attributene som blir klassifisert som `properties` kan man modifisere med CSS.

Gitt at man har følgende svg.

```html
<?xml version="1.0" standalone="no"?>
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <rect x="10" height="180" y="10" width="180" id="MyRect"/>
</svg>
```

Med følgende styling.

```css
#MyRect {
  fill: red;
  stroke: black;
}
```

Vil det se slik ut.

<img src="img/css.png" height="200">

> Legg merke til at man bruker `id` til å hente ut riktig element.

### :trophy: [Oppgave 4](https://codepen.io/sveinpg/pen/KGwWbX)

Gi hjertet rød fyllfarge og en svart strek rundt ved hjelp av css.

## Animasjoner med css.

Hvis du har vært inne på uxcup.bekk.no har du nok sett de kule animasjonene vi har der. Disse er laget av SVGer som er animert med CSS. Man setter en klasse på SVG-elementet og bruker denne klassen til å gi SVGen en animasjon via `animation` nøkkelen i CSS.

Skulle du ønske at du kunne lage like kule animasjoner? Flaks for deg, det er nemlig det du skal nå.

**Men før du går i gang**: SVGene i de neste to oppgavene er litt mer kompliserte enn et rektangel eller en sirkel, og noen ganger kan SVG-kode se fryktelig avansert ut. Sitter folk virkelig og skriver disse for hånd?! Neida, ser du noe ala det følgende, kan du være ganske sikker på at det har blitt generert via et tegneprogram som Adobe Illustrator eller Sketch:

```html
<path stroke="#262962" d="M182.008654,399.347809 L115.991792,399.347809 C106.727177,398.71496 102.094869,394.025055 102.094869,385.278095 C102.094869,376.531135 106.727177,371.893321 115.991792,371.364652 L166.065341,371.364652 C175.134852,370.521657 179.669607,365.959658 179.669607,357.678656 C179.669607,349.397654 175.134852,344.825987 166.065341,343.963657 L115.001606,343.963657 C106.397115,342.908091 102.094869,338.251628 102.094869,329.994268 C102.094869,321.736907 106.727177,317.085893 115.991792,316.041224 L207.129453,316.041224 C216.411814,314.967702 221.052995,310.324255 221.052995,302.110882 C221.052995,293.89751 216.702397,289.195641 208.001201,288.005276 L59.0658305,288.005276 C55.5795063,288.042623 52.2408351,286.245891 49.049817,282.615079 C45.6218247,278.714633 44.7654635,270.172114 49.049817,265.25657 C51.9060526,261.97954 55.2447238,260.233338 59.0658305,260.017963 L100.765176,260.017963 C105.443491,259.744619 109.017606,258.145953 111.487519,255.221962 C113.957433,252.297971 115.128795,248.99097 115.001606,245.300958 L115.001606,163.000107"/>
```

### :trophy: [Oppgave 5](https://codepen.io/mfeiring/pen/JmdVNM)

Lag to keyframes (`shake` og `dash`) og få raketten til å se mer levende ut. Når du er ferdig burde du ha noe som ligner på raketten under.

<img src="img/rocket.gif" height="250">

:bulb: Man kan lage effekten av at raketten rister med `translate`

:bulb: Man kan lage effekten av at strekene beveger seg med `stroke-dashoffset`

:school_satchel: [Fasit](https://codepen.io/mfeiring/pen/KGpYQz)

### :trophy: [Oppgave 6](https://codepen.io/mfeiring/pen/ePNaBr)

I denne oppgaven har vi satt opp `@keyframes`, men du skal selv få definere `animation` og `stroke-dasharray`. Du kan lese mer om hvordan `stroke-dasharray` funker [her](https://css-tricks.com/svg-line-animation-works/).

<img src="img/lightbulb.gif" height="250">

:bulb: Bruk en kombinasjon av `animation-duration` og `animation-delay`, for å få samme keyframes til å funke for alle `path`-elementene.

:bulb: `animation-delay` er vel og bra, men det funker ikke hvis man ønsker å loope animasjonen. Hvis du ønsker å loope animasjonen, så må du nok trikse litt med keyframes. Du kan evt lese mer om dette [her](https://css-tricks.com/css-keyframe-animation-delay-iterations/)

:school_satchel: [Fasit](https://codepen.io/mfeiring/pen/qJdGRv)
