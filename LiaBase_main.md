<!--
author:   Samuel Jamet

email:    samuel.jamet.bib@proton.me

version:  0.0.1

language: fr

comment:  Try to write a short comment about
          your course, multiline is also okay.

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js
-->

# LiaScript

This is your **course** initialization stub.

Please see the [Docs](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/docs/master/README.md)
to find out what is possible in [LiaScript](https://liascript.github.io).

If you want to use instant help in your Atom IDE, please type **lia** to see all available shortcuts.

## Mise en route

### Se créer un compte GitHub

Pour utiliser tranquillement Liascript, la création d'un compte sur GitHub est nécessaire.

![Page de connexion de GitHub](assets/github/githubconnect.png)

### Créer un répertoire

{{1}} Cliquez sur l'icône de votre compte en haut à droit de l'écran, puis sur *Repositories*
![Création d'un répertoire Github](assets/github/github_repo.png)

{{2}} Cliquez sur *New* pour créer un nouveau répertoire.
![Création d'un répertoire GitHub](assets/github/github_repo_2.png)

{{3}} Entrez les informations nécessaires. Evitez les espaces dans le nom du répertoire. la description n'est pas obligatoire, mais elle peut aider à ce que l'on retrouve votre répertoire.
Super important : votre répertoire doit impérativement être **public** pour que Liascript puisse l'interpréter.
![Finalisation d'un répertoire](assets/github/github_repo_3.png)

{{4}} Une fois votre répertoire créé, vous pouvez y accéder depuis *Repositories* en cliquant sur l'icone de votre profil. Notez qu'au moment de la création du répertoire, il ne contient rien que la **LICENCE** et le README.md.
![Répertoire GitHub vide](assets/github/github_repo_4.png)

### Visual Studio Code

Présentation rapide de VS Code
![Accueil VS Code](assets/VS_Code/VS_Code_acc.png)

#### Installer et activer les plugins Liascript

Installation du plugin **Liascript Preview**
![Liascript Preview](assets/VS_Code/VS_Code_plug_in_LSPreview.png)

##### Installer et activer le plugin Liascript Snippets

![Liascript Snippets](assets/VS_Code/VS_Code_plug_in_LSSnippets.png)

![Liascript Snippets suite](assets/VS_Code/VS_Code_plug_in_LSSnippets_2.png)

Faites `Ctrl + Shift + P` puis entrez `settings` et cliquez sur Open User Settings (JSON)

```
Bla bla Bla
```

![Liascript Snippets suite](assets/VS_Code/VS_Code_plug_in_LSSnippets_3.png)

### Git

#### Installer Git

Aller sur le site officiel (git-scm.com) et de télécharger Git for Windows.
L'installateur de Git sous Windows a énormément d'étapes avec plein de cases à cocher, **laisser toutes les options par défaut et de cliquer sur "Next" jusqu'au bout**. Ça ira très bien pour 99 % des usages.

#### Configurer Git

Une fois installé, ouvrez le terminal de commande PowerShell. 

C'est là qu'il faut définir l'identité, pour que Git sache qui fait les modifications. 
Voici les commandes à entrer (le --global est important pour que ça s'applique à tous vos futurs projets) :

Pour le nom (avec les guillemets) :

git config --global user.name "Prénom Nom"


Pour l'email (idéalement celui que vous utilisez pour GitHub) :

git config --global user.email "leur.email@exemple.com"

Aujourd'hui, le standard est d'appeler la branche principale main (au lieu de l'ancien master). Autant configurer ça tout de suite pour éviter des confusions plus tard :

git config --global init.defaultBranch main

Pour vérifier que tout a bien fonctionné, taper :

git config --list

Cela affichera votre nom, votre mail et vos réglages. Si vous voyez vos infos, c'est tout bon !

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