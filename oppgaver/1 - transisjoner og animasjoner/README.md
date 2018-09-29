# 1 - Transisjoner og animasjoner

## Transisjoner - `transition`

Det er ganske vanlig at knapper endrer bakgrunnsfarge, når man har musepekeren over dem, slik som illustrert under.

<img src="img/hover-no-transition.gif" height="150">

Knappen over har følgende styling:

```css
button {
  font-size: 40px;
  padding: 20px;
  border: none;
  border-radius: 10px;
  color: white;
  background: #4fc7ef;
}
```

og vi definerer en alternativ bakgrunnsfarge, i tilfeller hvor det er en musepeker over knappen, ved å bruke en [pseudo-klasse](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes):

```css
button:hover {
  background: #008080;
}
```

For å gjøre fargeendringen litt "smoothere", kan vi bruke transisjoner.

> CSS transitions provide a way to control animation speed when changing CSS properties. Instead of having property changes take effect immediately, you can cause the changes in a property to take place over a period of time. For example, if you change the color of an element from white to black, usually the change is instantaneous. With CSS transitions enabled, changes occur at time intervals that follow an acceleration curve, all of which can be customized.  
> _Kilde_: [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)

I eksempelet under har definerer vi at overgangen mellom blå og grønn skal ta 400 millisekunder. Dette gjør vi ved å legge til `transition: 400ms`.

<img src="img/hover-transition.gif" height="150">

All CSS for knappen, inkludert transisjonen, blir altså:

```css
button {
  font-size: 40px;
  padding: 20px;
  border: none;
  border-radius: 10px;
  color: white;
  background: #4fc7ef;
  transition: 400ms;
}

button:hover {
  background: #008080;
}
```

## Oppgaver

Åpne opp `src/index.html` i en nettleser. Som i del 0 skal selve oppgavene løses ved å redigere `src/style.css`.

1. Legg til en transisjon til, ved å definere enn annen verdi for `color` i `button:hover`-selektoren.

Fordi vi kun har definert tiden transisjonen skal ta, animeres alle propertiene som endrer seg. Vi kan eksplisitt velge å kun animere én property, ved å spesifisere navnet på propertien, f.eks. `transition: background 400ms`.

Vi kan også definere to transisjoner med ulik hastighet, på følgende måte: `transition: property1 400ms, property2 200ms`.

2. Utvid `transition`-propertien, slik at `color`-transisjonen tar `200ms`.

For å utsette starttidspunktet for en transisjon, legger vi til et delay. Dette kan gjøres slik: `transition: color 200ms 100ms`. Her har vi lagt til et delay på `100ms`. Legg merke til at lengden på transisjonen defineres først.

3. Legg på en delay på `color`-transisjonen, slik at den slutter samtidig som `background`-transisjonen.

Den siste egenskapen ved en transisjon vi kan tweake på, er hvordan den akselererer, også kalt "timing function". De ulike alternativene er illustrert her:

<img width="400" src="img/easing.gif">
  
Defaultverdien er `ease`, men vi kan endre den til f.eks. `linear` slik: `transition: color 200ms 100ms linear`.

Det er også mulig å lage en egendefinert akselerasjonskurve, ved å bruke [cubic-bezier](http://cubic-bezier.com/#.17,.67,.83,.67).

4. Sett akselerasjonen på `color`-transisjonen til `ease-in`. Prøv å bruke Chrome DevTools sin [cubic bezier editor](https://imgur.com/gallery/o2c15CZ) til å tweake på kurven.

## Animasjoner - `animation`
