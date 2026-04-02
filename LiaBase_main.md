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

![Logo Liascript](assets/liascript/LiaScript_logo.png)

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

**Visual Studio Code** est un éditeur de texte gratuit et open source maintenu par **Microsoft** (eh oui, snif). Très utilisé par les développeur.ses, on va plutôt l'utiliser comme simple éditeur de MarkDown, un peu amélioré par le créateur de Liascript, grâce à quelques plug in.
![Accueil VS Code](assets/VS_Code/VS_Code_acc.png)

Rendez-vous sur la [page de téléchargement](https://code.visualstudio.com/Download) et procédez à l'installation du logiciel, on se retrouve de l'autre côté.

#### Installer et activer les plugins Liascript

Pour utiliser confortablement Liascript, on va devoir installer deux extensions développées par André Dietrich.
Rendez-vous dans le magasin d'extensions (cf. capture ci-dessous ou `Ctrl + Shift + X`).

Entrez `liascript` dans la barre de recherche, normalement trois extensions doivent remonter. Cliquez sur `LiaScript-Preview` puis sur `Install`.
![Liascript Preview](assets/VS_Code/VS_Code_plug_in_LSPreview.png)

Ce plug in va vous permettre de lancer une prévisualisation de ce que vous êtes en train de produire depuis Visual Code, sur votre navigateur favori, en local, sans connexion internet. Plutôt utile pour vérifier et tester votre cours au fil de l'eau !

##### Installer et activer le plugin Liascript Snippets

Le second plug in se nomme **LiaScript-Snippets**, il n'est pas absolument nécessaire à l'utilisation de LiaScript avec VS Code, mais c'est une aide non négligable quand on débute.

![Liascript Snippets](assets/VS_Code/VS_Code_plug_in_LSSnippets.png)

Une fois l'installation faite, ce n'est pas terminé. Sur la page de **LiaScript-Snippets**, on vous demande de copier-coller un morceau de code. Sélectionnez le morceau de code mis en exergue, puis `Ctrl + C`.

![Liascript Snippets suite](assets/VS_Code/VS_Code_plug_in_LSSnippets_2.png)

Faites `Ctrl + Shift + P` puis entrez `settings` et cliquez sur Open User Settings (JSON), et collez le morceau de code entre les deux accolades (je le remets ci-dessous), puis quittez.

```
   "[markdown]": {
      "editor.tabCompletion": "on",
      "editor.quickSuggestions": true,
      "editor.snippetSuggestions": "top"
   },
```

![Liascript Snippets suite](assets/VS_Code/VS_Code_plug_in_LSSnippets_3.png)

**LiaScript-Snippets** va vous permettre d'"appeler" des fonctionalités de LiaScript comme des modèles mise en formes spécifiques (tableaux, graph, etc.), ou des modèles de quizs, et une miriade de choses super chouettes avec le préfixe `lia`.

### Git

![Logo de Git](assets/git/git_logo.png)Git est un logiciel de gestion de versions décentralisé développé par Linus Torvalds, le créateur du noyeau Linux. Pour en savoir plus sur Git et son fonctionnement, vous pouvez consulter [la page Wikipédia](https://fr.wikipedia.org/wiki/Git) qui est bien détaillée.

#### Installer Git

Aller sur le [site officiel](https://git-scm.com/install/windows) et de télécharger Git for Windows.

Sélectionnez l'installateur `Git for Windows/x64 Setup` qui devrait fonctionner dans la plupart des cas.
![Page de téléchargement de Git for Windows](assets/git/git_dl.png)

L'installateur de Git sous Windows a beaucoup d'étapes avec plein de cases à cocher, **laisser toutes les options par défaut et de cliquer sur "Next" jusqu'au bout**. Ça ira très bien pour 99 % des usages.

#### Configurer Git

Une fois installé, ouvrez le terminal de commande **Git Bash**.

![Ouvrir Git Bash](assets\git\git_bash.png)

Vérifiez que Git est bien installé en entrant :

```
git --version
```

Si le terminal vous renvoie `git version 2.5x.x.windows` c'est bon.

![Git version sur Git Bash](assets\git\git_version.png)

C'est là qu'il faut définir l'identité, pour que Git sache qui fait les modifications. 
Voici les commandes à entrer (le --global est important pour que ça s'applique à tous vos futurs projets) :

Pour le nom (avec les guillemets) :

```
git config --global user.name "Prénom Nom"
```

Pour l'email (idéalement celui que vous utilisez pour GitHub) :

```
git config --global user.email "votre.email@exemple.com"
```

Aujourd'hui, le standard est d'appeler la branche principale main (au lieu de l'ancien master). Autant configurer ça tout de suite pour éviter des confusions plus tard :

```
git config --global init.defaultBranch main
```

Pour vérifier que tout a bien fonctionné, taper :

```
git config --list
```

Cela affichera votre nom, votre mail et vos réglages. Si vous voyez vos infos, c'est tout bon !

![Nom, mail et réglages avec git config](assets/Powershell/Powershell_gitconfig.png)

### Cloner votre répertoire GitHub en local

Rendez-vous dans le dossier dans lequel vous souhaitez synchroniser votre répertoire.

A titre personnel, je clone mes répertoires directement dans le dossier Documents, mais vous pouvez choisir un autre dossier.

Une fois dans le dossier, faites un `clic droit` à l'intérieur puis cliquez sur `Open Git Bash here` pour ouvrir le terminal.

![Git bash here](assets\git\open_git_bash_here.png)

Tapez :

```
git clone https://github.com/nomdevotrecompte/nomdurepertoire.git
```

![Clonage de répertoire](assets\git\git_clone.png)

Vous trouverez l'URL du répertoire en vous rendant... dans votre répertoire bien joué, et en cliquant sur `<> code`.

![URL GitHub](assets/github/github_url_clone.png)

Et voilà ! Votre répertoire avec tout son contenu est cloné sur votre PC ! Si c'est votre premier répertoire, seul le `README.md`et la `LICENCE` ont été clonées, mais ce n'est qu'un début.

![Répertoire en local](assets\git\repo_git_local.png)

### Finalisation de la configuration... et premier commit

![Open Folder](assets/VS_Code/VS_Code_open_folder.png)Rouvrez VS Code et ouvrez votre répertoire synchronisé : `File > Open Folder... > "Nom du répertoire > Select folder"` (Sélectionnez simplement le répertoire cloné, ne double-cliquez pas dessus)

Votre arborescence s'affichera sur la partie gauche de la fenêtre de VS Code. Sauf événement cataclismique, elle sera parfaitement identique à celle que vous avez dans l'explorateur de fichiers Windows et votre répertoire dans GitHub.

Sélectionnez le `README.md` pour afficher l'éditeur de texte et voyez ce que ça donne. C'est visuellement beaucoup plus sobre et plus du tout WYSIWYG, mais on s'y fait.

![Arborescence répertoire VS Code](assets\VS_Code\VS_Code_arbo.png)

#### Créer votre premier document

Evidemment, vous n'allez pas vous mettre à composer dans le `README.md` (conservez ce fichier pour expliquer comment utiliser votre ressource !)

Dans l'arborescence de votre répertoire, toujours dans VS Code, cliquez sur l'icône `New File`juste à côté du nom de votre répertoire.

![Newfile](assets\VS_Code\VS_Code_premier_fichier.png) Attention, comme vous le voyez sur la capture, il est indispensable de spécifier le format du fichier nouvellement créé, et ce format, c'est du `.md` donc le format MarkDown. Vous pouvez nommer votre document comme vous le souhaitez, mais ajoutez `.md` à la fin si vous voulez que ça fonctionne.

Cliquez sur le document pour afficher l'éditeur de texte. Par défaut, il vous propose de générer du code, mais vous ne mangez pas de ce pain-là. Positionnez-vous dans l'éditeur comme vous le feriez pour un éditeur de texte classique et tapez :

```
lia-init
```

Vous vous souvenez du plug in [LiaScript Snippets](#7) ? C'est là qu'il entre en action. Appuyez sur `entrée` pour faire apparaître une première base du cours à partir de laquelle vous allez pouvoir avancer, ainsi qu'un certain nombre de métadonnées super utiles.

![Lia-init](assets\VS_Code\VS_Code_lia_init.png)

#### Lier VS Code à GitHub

Il est temps de vous mettre au travail, vous avez cloné votre répertoire GitHub, vous allez maintenant l'alimenter et le mettre à jour. Pour cela, vous aller lier VS Code à votre compte GitHub (il existe d'autres voies pour synchroniser vos répertoires, ils seront détaillés dans des versions ultérieures de ce guide).

En bas à gauche de la fenêtre de VS Code, cliquez sur `Accounts`puis sur `Backups and Sync Settings`.

![VS Code Accounts](assets\VS_Code\VS_Code_sync.png)

Les `Settings Sync`s'ouvrent en haut de la fenêtre (oui on voyage), cliquez sur `Sign in` puis sur `Sign in with GitHub`

![Sign in with GitHub](assets\VS_Code\VS_Code_sync2.png)

![Sign in GitHub](assets\VS_Code\VS_Code_sync3.png) VS Code va automatiquement ouvrir une page de votre navigateur enregistré par défaut pour vous demander si vous souhaitez vous connecter à GitHub, cliquez sur `Sign in` puis continuez. Si, de retour sur VS Code, le nom de votre compte s'affiche quand vous cliquez sur `Accounts` c'est bon !

#### Premier commit

Vous avez créé votre premier document et vous souhaitez qu'ils soit synchronisé sur votre répertoire GitHub, vous allez donc faire ce qu'on appelle un *commit*, c'est-à-dire une modification du répertoire qui sera décrite et signée de votre nom.

Cliquez sur `Source Control`(par défaut, parmi les quelques icônes sur le côté gauche de la fenêtre de VS Code)

![Premier commit](assets\VS_Code\VS_Code_commit.png) Vous arriver dans le panneau de contrôle des sources. Juste en dessous du bouton `Commit` un certain nombre de `Changes` sont listés (notamment la création de votre nouveau document.) Cliquez sur le petit `+` en face de `Changes` les éléments listés deviennent des `Staged Changes`prêts à être envoyé dans votre répertoire GitHub. N'oubliez pas de décrire votre modification/ajout avant de cliquer sur `Commit` puis de cliquer sur `Sync Changes` pour que votre répertoire GitHub soit synchronisé.

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