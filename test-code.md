<!--
author:   Your Name

email:    your@mail.org

version:  0.0.1

language: en

narrator: US English Female

comment:  Try to write a short comment about
          your course, multiline is also okay.

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js

translation: Deutsch  translations/German.md

translation: Français translations/French.md
-->

# Mon premier test de code

Voici un bout de JavaScript. Clique sur le bouton ▶️ en haut à droite du bloc de code pour l'exécuter.

```javascript
console.log("Hello World depuis LiaScript")
```
<script>@input</script>

```javascript
console.log("Hello depuis LiaScript !");
let x = 2 + 2;
console.log("2 + 2 = " + x);
```
<script>@input</script>

## Test appel API

```javascript
fetch('https://api.quotable.io/random')
  .then(response => response.json())
  .then(data => {
    console.log("Citation : " + data.content);
    console.log("Auteur : " + data.author);
  })
  .catch(error => {
    console.log("Erreur : " + error);
  });

"Requête envoyée, résultat ci-dessus ⬇️";
```
<script>@input</script>

## Test API (v2)

```javascript
fetch('https://restcountries.com/v3.1/name/france')
  .then(response => response.json())
  .then(data => {
    const pays = data[0];
    console.log("Pays : " + pays.name.common);
    console.log("Capitale : " + pays.capital[0]);
    console.log("Population : " + pays.population.toLocaleString('fr-FR'));
  })
  .catch(error => {
    console.log("Erreur : " + error);
  });

"Requête envoyée ⬇️";
```
<script>@input</script>

## Interroger HAL en direct

Cherchons les 3 publications les plus récentes contenant "bibliothèque universitaire" dans HAL.

```javascript
const motCle = "bibliothèque universitaire";
const url = `https://api.archives-ouvertes.fr/search/?q=${encodeURIComponent(motCle)}&rows=3&sort=submittedDate_s desc`;

fetch(url)
  .then(response => response.json())
  .then(data => {
    console.log("📊 Nombre total de résultats dans HAL : " + data.response.numFound.toLocaleString('fr-FR'));
    console.log("---");
    console.log("🔎 3 publications les plus récentes :");
    console.log("");
    
    data.response.docs.forEach((doc, i) => {
      // On nettoie les chevrons encodés pour l'affichage
      const citation = doc.label_s.replace(/&#x27E8;/g, '⟨').replace(/&#x27E9;/g, '⟩');
      console.log(`[${i+1}] ${citation}`);
      console.log(`    🔗 ${doc.uri_s}`);
      console.log("");
    });
  })
  .catch(error => {
    console.log("❌ Erreur : " + error);
  });

"Interrogation de HAL en cours...";
```
<script>@input</script>

## Cartographier une thématique (interactif)

<input type="text" id="motcle" value="intelligence artificielle" style="width:300px; padding:5px;">
<button onclick="chercherHAL()">🔍 Interroger HAL</button>
<pre id="resultat"></pre>

{{1}}
```javascript
window.chercherHAL = function() {
  const motCle = document.getElementById('motcle').value;
  const sortie = document.getElementById('resultat');
  sortie.textContent = "⏳ Interrogation de HAL...";
  
  const url = `https://api.archives-ouvertes.fr/search/?q=${encodeURIComponent(motCle)}&rows=0&facet=true&facet.field=keyword_s&facet.limit=10&facet.mincount=2`;
  
  fetch(url)
    .then(r => r.json())
    .then(data => {
      const total = data.response.numFound;
      const facettes = data.facet_counts.facet_fields.keyword_s;
      let texte = `📊 ${total.toLocaleString('fr-FR')} publications pour "${motCle}"\n\n🏷️ Top 10 des mots-clés associés :\n\n`;
      const max = facettes[1]; // le plus grand nombre (le premier)
      for (let i = 0; i < facettes.length; i += 2) {
        const barre = "█".repeat(Math.round((facettes[i+1] / max) * 30));
        texte += `${String(facettes[i+1]).padStart(5)} ${barre} ${facettes[i]}\n`;
      }
      sortie.textContent = texte;
    })
    .catch(e => sortie.textContent = "❌ " + e);
};
"Prêt. Cliquez sur le bouton.";
```
<script>@input</script>

### Extensions

     --{{0}}--
But you can also include other features such as spoken text.

      --{{1}}--
Insert any kind of audio file:

       {{1}}
?[audio](https://bigsoundbank.com/UPLOAD/mp3/1068.mp3)


     --{{2}}--
Even videos or change the language completely.

       {{2-3}}
!?[video](https://www.youtube.com/watch?v=bICfKRyKTwE)


      --{{3 Russian Female}}--
Первоначально создан в 2004 году Джоном Грубером (англ. John Gruber) и Аароном
Шварцем. Многие идеи языка были позаимствованы из существующих соглашений по
разметке текста в электронных письмах...


    {{3}}
Type "voice" to see a list of all available languages.


### Styling

<!-- class = "animated rollIn" style = "animation-delay: 2s; color: purple" -->
The whole text-block should appear in purple color and with a wobbling effect.
Which is a **bad** example, please use it with caution ...
~~ only this is red ;-) ~~ <!-- class = "animated infinite bounce" style = "color: red;" -->

## Charts

Use ASCII-Art to draw diagrams:

                                    Multiline
    1.9 |    DOTS
        |                 ***
      y |               *     *
      - | r r r r r r r*r r r r*r r r r r r r
      a |             *         *
      x |            *           *
      i | B B B B B * B B B B B B * B B B B B
      s |         *                 *
        | *  * *                       * *  *
     -1 +------------------------------------
        0              x-axis               1

## Quizzes

### A Textquiz

What did the **fish** say when he hit a **concrete wall**?

    [[dam]]

### Multiple Choice

Just add as many points as you wish:

    [[X]] Only the **X** marks the correct point.
    [[ ]] Empty ones are wrong.
    [[X]] ...

### Single Choice

Just add as many points as you wish:

    [( )] ...
    [(X)] <-- Only the **X** is allowed.
    [( )] ...

## Executable Code

A drawing example, for demonstrating that any JavaScript library can be used, also for drawing.

```javascript
// Initialize a Line chart in the container with the ID chart1
new Chartist.Line('#chart1', {
  labels: [1, 2, 3, 4],
  series: [[100, 120, 180, 200]]
});

// Initialize a Line chart in the container with the ID chart2
new Chartist.Bar('#chart2', {
  labels: [1, 2, 3, 4],
  series: [[5, 2, 8, 3]]
});
```
<script>@input</script>

<div class="ct-chart ct-golden-section" id="chart1"></div>
<div class="ct-chart ct-golden-section" id="chart2"></div>


### Projects

You can make your code executable and define projects:

``` js     -EvalScript.js
let who = data.first_name + " " + data.last_name;

if(data.online) {
  who + " is online"; }
else {
  who + " is NOT online"; }
```
``` json    +Data.json
{
  "first_name" :  "Sammy",
  "last_name"  :  "Shark",
  "online"     :  true
}
```
<script>
  // insert the JSON dataset into the local variable data
  let data = @input(1);

  // eval the script that uses this dataset
  eval(`@input(0)`);
</script>

## More

Find out what you can even do more with quizzes:

https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/docs/master/README.md