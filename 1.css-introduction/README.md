# CSS: Introduction

Apprendre à styliser vos pages web en utilisant le CSS.

Cet article explique ce qu'est le CSS à l'aide d'exemples de syntaxe simple et couvre également quelques-uns des termes clés du langage.

[Suivre tous les tutoriels sur mon site:](https://djemai-samy.com/posts/0.css-initiation)

- [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)

---

## Prérequis

Il est conseillé d'avoir suivi le tutoriel [HTML: Innitiation](https://djemai-samy.com/posts/0.html-initiation)

---

## Qu'est-ce que CSS ?

**CSS:** (**C**ascading **S**tyle **S**heetsou ou "Feuilles de style en cascade") est utilisé pour styliser et mettre en page des pages Web.

Pour afficher un document, un navigateur doit combiner le contenu du document et les informations de mise en forme.

Par exemple, pour modifier la police, la disposition, la couleur, la taille et l'espacement de votre contenu, le scinder en plusieurs colonnes ou ajouter des animations et autres éléments décoratifs.

## Comment ça marche?

Le traitement se fait en plusieurs phases que nous détaillons ci-dessous:

1. Le navigateur charge le HTML (par exemple, il le reçoit à travers le réseau).
2. Il traduit le HTML en un DOM (Document Object Model) : une représentation du document HTML stockable en mémoire sur votre ordinateur. Nous expliquons le DOM plus en détails dans la prochaine section.
3. Le navigateur récupère ensuite la plupart des ressources attachées au document HTML, telles les images, les vidéos ajoutées à la page, et la feuille CSS externe. JavaScript est traité un peu plus tard et nous n'en parlerons pas ici pour simplifier la présentation.
4. Le navigateur parse le CSS, classe les différentes règles par types de sélecteur (par exemple, élément, classe, ID, etc.) dans des « buckets ». En fonction des sélecteurs trouvés, le navigateur calcule quelle règle s'applique à quel nœud du DOM.
5. Chaque nœud du DOM ciblé par CSS est étiqueté par sa règle de style. L'arbre ainsi obtenu s'appelle l'arbre de rendu (render tree).
6. Pour chaque nœud de l'arbre de rendu, le navigateur calcule l'effet visuel de la règle CSS associée.
Le visuel ainsi produit est affiché à l'écran (cette étape s'appelle « painting »).

![Diagramme de traitement de site web par le navigateur.](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/1.css-introduction/diagramme-traitement.png)

---

## À propos du DOM

Chaque élément, ainsi que ses attributs et son texte est traduit en un nœud du DOM dans une structure en arbre.

Les nœuds sont définis par leurs relations à d'autres nœuds du DOM. Certains éléments sont les parents de nœuds enfants (child nodes) et les nœuds enfants peuvent avoir des frères et sœurs (siblings):

Par exemple, partons du code ci-dessous :

```html
<article>
  <h1>Un titre</h1>
  <p>
    Lorem ipsum, dolor sit amet <strong>consectetur</strong> adipisicing elit
  </p>
</article>
```

![Exemple de DOM.](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/1.css-introduction/1.DOM.png)

Dans le DOM, le nœud correspondant à l'élément ```<article>``` est un parent. Ses enfants (children) sont les nœuds ```<h1>``` et ```<p>```.

Le nœud ```<h1>``` et le nœud ```<p>``` sont considérées comme frères/soeurs (siblings).

Le nœud ```<h1>``` possède un unique enfant, un nœud texte.

Le nœud ```<p>``` est aussi un parent, avec pour enfants les nœuds associés au texte et le nœud ```<strong>```, qui lui-même est parent d'un nœud texte.

Comprendre le DOM vous aidera à concevoir, déboguer et maintenir votre CSS, car le DOM est le point de jonction entre CSS et le contenu HTML du document.

Avec les DevTools de votre navigateur, vous pourrez naviguer à travers le DOM en sélectionnant les éléments pour les inspecter et voir quelles règles s'appliquent sur eux.

---

## 1/ Comment structurer le CSS?

Vous avez maintenant une idée plus claire de CSS. Vous connaissez les bases de son fonctionnement.

Il est temps d'explorer la structure du langage lui-même. Prenons ce simple code HTML:

```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS: Initiation</title>
  </head>
  <body>
    <article>
    <h1>Un titre</h1>
    <p>Lorem ipsum, dolor sit amet <strong>consectetur</strong> adipisicing elit</p>
    </article>
  </body>
</html>
```

Il existe trois méthodes pour appliquer du CSS à un document:

### 1.1/ Style en ligne

Les styles en ligne sont des déclarations CSS qui n'affectent qu'un seul élément, elles sont déclarées grâce à l'attribut style:

```html
<h1 style="color:rgb(34, 29, 171); font-size:40px;">Un titre</h1>
```

Dans l'attribut ```style```, on trouve une ou plusieurs déclarations, sous la forme d'une paire ```propriété: valeur;```.

Chaque paire précise une propriété de l'élément, suivie de la valeur choisie pour cette propriété:

- **Propriétés** : des identifiants lisibles par l'homme indiquant les caractéristiques stylistiques (font-size, width, background-color, par exemple) que vous souhaitez modifier.
- **Valeurs** : une valeur est attribuée à chaque propriété spécifiée. Elle indique comment modifier ces caractéristiques stylistiques.

La propriété et la valeur sont séparées par deux points. Chaque déclaration se termine par un point-virgule.

À chaque propriété définie par CSS correspondent différentes valeurs possibles. Dans l'exemple:

- la propriété ```color``` peut prendre différentes valeurs (rgb, hex...), et permet de modifier la couleur d'un texte.
- La propriété ```font-size``` accepte différentes tailles comme valeurs, et permet de changer la taille de la police d'un texte. Dans notre exemple, nous avons utilisé des pixels en unité.

De manère générale, Cette approche est vraiment à proscrire. Le code produit n'est pas maintenable.
  
Par ailleurs, mélanger le CSS avec le HTML rend la lecture du code plus difficile.

---

### 1.2/ Feuille de style interne

Les règles CSS peuvent être écrites directement dans l'en-tête HTML ```<head>``` dans un élément ```<style>```. On parle alors de feuille de style interne.

```html
<style>
  /*Sélecteur de la balise article */
  article{
    /*Propriétes et valeurs appliquer a la balise article */
    background-color: rgb(200, 200, 200);
    border: 2px solid rgb(23, 215, 16);
  }

  /*Sélecteur de la balise p */
  p{
    /*Propriétes et valeursr appliquer a la balise p */
    color:rgb(215, 16, 16);
    font-size: 25px;
  }
</style>
```

CSS est un langage basé sur des règles — on définit des règles de styles destinées à des éléments ou des groupes d'éléments particuliers dans la page.

La règle commence par un sélecteur, les éléments HTML mis en forme.

Ici, le style s'applique aux articles (```<article>```) et paragraphes (```<p>```).

Suivent une paire d'accolades ```{ }``` à l'intérieur desquelles on trouve une ou plusieurs déclarations, sous la forme de paire ```propriété: valeur```.

- la propriété ```background-color``` permet de changer la couleur de fond d'un élément.
- La propriété ```border```: Permet d'ajouter une bordure à un élément. Sa valeur est divisée en trois parties:
  - La taille de la bordure, ici 2 pixels.
  - Le style de la couleur, ici unie.
  - La couleur de la bordure.

---

### 1.2/ Feuille de style externe

De manière générale, séparer le style dans un fichier dédié est la meilleur solution. Cette technique permet, par exemple, de réutiliser les règles CSS dans d'autres page, et éviter la duplication de code.

nous allong créer un fichier ```styles.css```, notre structure de dossier ressemble à ceci:

```bash
📦1.css-introduction
┣ 📜styles.css
┗ 📜index.html
```

On doit signaler au document HTML que nous souhaitons utiliser des règles CSS présentent dans un autre fichier, pour cela nous allons ajouter a la section ```<head>```, la balise ```<link>``` qui permet de lier le fichier ```styles.css``` et ```index.html```

  ```html
  <link rel="stylesheet" href="./styles.css">
  ```

Dans notre fichier ```styles.css```, ajoutons les règles suivantes:

```css
strong{
  text-decoration: underline;
  color: rgb(141, 12, 141);
}
```

La propriété permet de modifier l'apparence du texte (barré, souligné...).

## Conclusion

Maintenant que vous avez compris ce qu'est CSS et comment il fonctionne, nous pouvons aller à l'étape suivante, ou nous allons voire les différents sélécteurs et comment ils fonctionnent.

## Aller plus loin

[Précédent: HTML: Initiation](https://djemai-samy.com/posts/0.html-initiation)

[Suivant: CSS: Les sélécteurs](https://djemai-samy.com/posts/2.css-selectors.article)
