# Oppgave 0 - Bli kjent med `transform`

## Bakgrunn

CSS-propertien `transform` lar oss forflytte, skalere, skråstille og rotere elementer. Dette kan gjøres i tre dimensjoner – rundt x-, y- og/eller z-aksen. "Koordinatsystemet" i et nettleservindu er illustrert under.

<img src="../../img/nettleser-koordinater.png" height="300">

I eksemplene under vil blå boks illustrere elementene _uten_ en gitt `transform` satt, mens den røde boksen vil vise resultatet av å definere en `transform`-property.

### Forflytting - `translate`

**Eksempel 1:**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: translate(20px);
}
```

<img src="img/eksempel-1.png" width="120">

Den røde boksen er den som er beskrevet av CSS-snutten over. Den blå boksen viser hvordan den samme boksen ville sett ut _uten_ `transform: translate(20px)`. `translate(20px)` gjør altså at boksen flytter seg 20px til høyre, eller - sagt på en annen måte - 20px i positiv retning langs x-aksen.

**Eksempel 2**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: translate(20px, -20px);
}
```

<img src="img/eksempel-2.png" width="120">

Ved å legge til et til parameter, kommaseparert fra det første, kan vi også flytte boksen i vertikal retning. Her har vi satt `translate(20px, -20px)`, så som i eksempel 1 flytter vi boksen `20px` i positiv x-retning, men i tillegg flytter vi den også `20px` i _negativ_ y-retning (altså oppover).

**Eksempel 3**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: translateY(20%);
}
```

<img src="img/eksempel-3.png" width="100">

Her har vi brukt en litt annen variant av `translate()`. Med `translateY()` definerer vi eksplisitt at vi vil flytte boksen kun langs y-aksen (vertikalt). Vi har også brukt `50%` i stedet for `-20px`, som betyr at vi forflytter nedover med en lengde som tilsvarer halvparten av høyden til boksen.

I **Eksempel 1** brukte vi `translate(20px)` for å flytte boksen mot høyre, men vi kunne like så gjerne skrevet `translateX(20px)`.

`translateZ()` lar oss forflytte elementer "ut av skjermen", men det kommer vi tilbake til senere.

### Skalering

**Eksempel 1:**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: scale(2);
}
```

<img src="img/eksempel-4.png" width="200">

Her har vi brukt `scale(2)` for å gjøre boksen dobbelt så stor. Tallet definerer altså multipliseringsfaktoren, så `scale(1)` ville ikke gjort noe med størrelsen. Legg merke til at skaleringen er uniform i alle retninger.

**Eksempel 2:**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: scale(0.5, 1);
}
```

<img src="img/eksempel-5.png" width="100">

På samme måte som med `translate()`, kan vi også med `scale()` definere to parametre. Her har vi satt det andre parameteret til `1`, og vi ser at høyden på boksen ikke endrer seg, men at det blir halvparten så stort i bredden. Boksen skaleres altså ned med 50% i x-retning, mens dimensjonen i y-retning bevares.

**Eksempel 3:**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: scaleX(1.5);
}
```

<img src="img/eksempel-6.png" width="150">

Også `scale()` har alternative definisjoner; `scaleX()`, `scaleY()` og `scaleZ()`. Igjen kommer vi tilbake til dette med z-aksen senere.

### Skråstilling

**Eksempel 1**:

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: skewX(30deg);
}
```

<img src="img/eksempel-7.png" height="100">

Nøyaktig hvordan `skewX()` fungerer er lettere forklart med et bilde, enn med ord:

<img src="../../img/skewx.png" height="300">

Den kan kanskje være litt forvirrende at `skewX(30deg)` definerer vinkelen boksen danner med y-aksen, men tenk da heller på hvilken retning boksen _endrer_ seg langt.

**Eksempel 2**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: skewY(30deg);
}
```

<img src="img/eksempel-8.png" width="100">

Igjen, `skewY()` er også lettere forklart med et bilde:

<img src="../../img/skewy.png" height="300">

Og selv om vi definerer vinkelen i forhold til x-aksen, er det altså i y-retning at boksen endrer seg.

**Eksempel 3**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: skew(30deg, 15deg);
}
```

<img src="img/eksempel-9.png" width="150">

Akkurat som med `translate()` og `scale()`, kan vi definere definere `skew()` med to parametre, for å gjøre transformasjoner i både x- og y-retning.

### Rotasjon

**Eksempel 1:**

```css
div {
  height: 100px;
  width: 100px;
  background: red;
  transform: rotate(30deg);
}
```

<img src="img/eksempel-10.png" width="140">

Her ser vi at `rotate(30deg)` roterer boksen 30° _med_ klokka. Tilsvarende ville `rotate(-30deg)` rotert boksen 30° _mot_ klokka. Hvis vi ser på bildet av "koordinatsystemet" til en nettleser igjen, ser vi at dette tilsvarer en rotasjon rundt z-aksen. På samme måte som vi har `translate(20px) == translateX(20px)`, vil en mer eksplisitt versjon av `rotate(30deg)` derfor være `rotateZ(30deg)`
