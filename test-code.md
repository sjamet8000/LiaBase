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

---

<button onclick="chercherHAL()">🔍 Interroger HAL</button>
<pre id="resultat"></pre>

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