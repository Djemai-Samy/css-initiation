# CSS: Les sélecteurs

Apprendre à styliser vos pages web en utilisant le CSS.

Dans cet article nous explorerons en détails le fonctionnement des différents types de sélécteurs CSS.

[Suivre tous les tutoriels sur mon site:](https://djemai-samy.com/posts/0.css-initiation)

- [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)
- [CSS: Sélécteurs](https://djemai-samy.com/posts/2.css-selectors.article)

---

## Prérequis

Il est conseillé d'avoir suivi la première parti de ce tutoriel: [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)

---

## Qu'est-ce qu'un sélecteur ?

Un sélecteur est une expression qui indique au navigateur à quelle entité HTML s'applique la règle CSS correspondante.

Le ou les éléments ciblés par le sélecteur sont le sujet de ce sélecteur.

---

## 1/ Les Listes de sélecteurs

Quand un groupe de déclarations CSS s'applique à plusieurs éléments distincts, on peut combiner les sélecteurs individuels en une liste.

Par exemple, si j'ai le même CSS pour un ```<p>``` et pour un ```<span>```.
On pourrait écrire deux règles :

```css
p{
  color: red;
}
span{
  color: red;
}
```

Ou bien une seule règle en combinant les sélecteurs, séparés par une virgule :

```css
p, span{
  color: red;
}
```

---

## 2/ Types de sélecteurs

On peut regrouper les sélecteurs en différents groupes:

### 2.1/ Sélecteurs basique

Commençons par les sélecteur les plus simples et les plus utilisés

---

#### 2.1.1/ Sélecteur Universel

Le sélecteur universel ```*``` cible tous les éléments du DOM, la balise ```<body>``` aussi.

```css
* {
  /*Règles à appliquer à tous les élément du DOM*/
  }
```

Resultat:

![Graphique Sélecteur Universel](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-universel.svg)

---

#### 2.1.2/ Sélecteur de balise

Nous avons déja vu ce sélécteur, qui permet de sélectionner un élément avec le nom de la balise:

```css
div {
  /*Règles à appliquer à tous les élément <div> du DOM*/
  }
```

Resultat:

![Graphique Sélecteur de balise](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-tag.svg)

---

#### 2.1.3/ Sélecteur de classe

On peut regrouper un ensemble d'élément HTML pour leur appliquer le meme style en utilisant les classes.

D'abord, il faut ajouter l'attribut ```class="a"``` dans notre document HTML, pour tout élément que nous voulons cibler.

Pour sélectionner les éléments par leur classe en CSS, en utilise ```.```:

```css
.a{
  /*Règles à appliquer à tous les éléments aillant pour nom de classe a */
}
```

Resultat:

![Graphique Sélecteur de classe](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-class.svg)

---

#### 2.1.4/ Sélecteur d'identifiant
  
On peut utiliser l'```id``` d'un élément pour le ciblé en CSS, pour cela on utilise ```#```:

```css
#a{
  /*Règles à appliquer à l'élément aillant pour nom identifiant a */
}
```

Resultat:

![Graphique Sélecteur d'identifiant](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-id.svg)

---

### 2.2/ Sélecteurs combinateurs

On peut aussi combiner des sélcteurs basique pour être plus précis:

---

#### 2.2.1/ Sélecteur de descendants

Cible tous les éléments descendant du première élément:

```css
div a {
  /*Règles à appliquer à tous les descendant a des div */
  }
```

Resultat:

![Graphique Sélecteur de descendants](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-descendent.svg)

---

#### 2.2.2/ Sélecteur d'enfants

Cible tous les éléments enfants directe du première élément;

```css
div > a {
  /*Règles à appliquer aux enfants a des div */
  }
```

Resultat:

![Graphique Sélecteur d'enfants](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-child.svg)

---

#### 2.2.3/ Sélecteur de frères

Cible tous les éléments venant à la suite du première élément:

```css
div ~ a {
  /*Règles à appliquer à tous les a venant à la suite des div */
  }
```

Resultat:

![Graphique Sélecteur CSS de frères](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-siblings.svg)

---

#### 2.2.4/ Sélecteur de frère adjacent

Cible l'élément venant directement à la suite du première élément:

```css
div + a {
  /*Règles à appliquer à l'élement a venant à la suite des div */
  }
```

Resultat:

![Graphique Sélecteur CSS frère adjacent](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-adjacent.svg)

---

#### 2.2.5/ Sélecteur 'ou'

Nous l'avons vu plus haut, nous pouvons cibler plusieurs éléments en les séparant les sélecteurs par une virgule:

```css
div, a {
  /*Règles à appliquer aux éléments div ou a */
  }
```

Resultat:

![Graphique Sélecteur CSS logique 'ou'](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-or.svg)

---

#### 2.2.6/ Sélecteur 'et'

Nous pouvons cibler les éléments répondant à tous les sélécteurs mentionnés:

```css
div.a {
  /*Règles à appliquer aux éléments div dont la classe est a */
  }
```

Resultat:

![Graphique Sélecteur CSS logique 'et'](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-and.svg)

---

#### 2.3/ Sélecteurs d'attributs

On peut séléctionner des élément en utilisant leurs attributs

#### 2.3.1/ Possédant l'attribut

Cible tous les éléments possédant l'attribut entre ```[ ]```:

```css
[a] {
  /*Règles à appliquer à tous les éléments possédant l'attribut a */
  }
```

Resultat:

![Graphique Sélecteur CSS Possédant l'attribut](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-has.svg)

---

#### 2.3.2/ Attribut égal à

Cible tous les éléments possédant l'attribut avec la valeur exacte mentionnée:

```css
[a="1"] {
  /*Règles à appliquer à tous les éléments possédant l'attribut a
    aillant pour valeur 1*/
  }
```

Resultat:

![Graphique Sélecteur CSS Attribut égal à](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-exact.svg)

---

#### 2.3.3/ Attribut qui commence par

Cible tous les éléments dont la valeur de l'attribut commence par la valeur mentionnés:

```css
[a^="1"] {
  /*Règles à appliquer à tous les éléments possédant l'attribut a
    dont valeur commence par 1*/
  }
```

Resultat:

![Graphique Sélecteur CSS Attribut qui commence par](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-att-begins.svg)

---

#### 2.3.4/ Attribut qui finit par

Cible tous les éléments dont la valeur de l'attribut finit par la valeur mentionnés:

```css
[a$="1"] {
  /*Règles à appliquer à tous les éléments possédant l'attribut a
    dont valeur fini par 1*/
  }
```

Resultat:

![Graphique Sélecteur CSS Attribut qui finit par](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-att-ends.svg)

---

#### 2.3.5/ Attribut contenant une valeur

Cible tous les éléments dont la valeur de l'attribut possède quelque part la valeur mentionnés:

```css
[a*="1"] {
  /*Règles à appliquer à tous les éléments possédant l'attribut a
    dont valeur contient 1 quelque parts*/
  }
```

Resultat:

![Graphique Sélecteur CSS Attribut contenant une valeur](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-att-substring.svg)

---

## 3/ Pseudo classe

Une pseudo-classe est un mot-clé qui peut être ajouté à un sélecteur afin d'indiquer l'état spécifique dans lequel l'élément doit être pour être ciblé par la déclaration.

### 3.1/ Etat

On peut préciser dans quel état l'élément est pour que style soit appliqué:

#### 3.1.1/ Souris sur l'élément

Afin d'appliquer du style à un élément quand l'utilisateur passe la souris dessus, on utilise la pseudo-classe ```hover```:

```css
a:hover {
  /*Règles à appliquer à tous les élément a quand la souris passe dessus*/
  }
```

---

#### 3.1.2/ L'élément est en focus

Applique du style à un élément est en ```focus```, c'est à dire, quand l'utilisateur séléctionne un élément avec le ```tab``` ou en cliquant dessus:

```css
a:focus {
  /*Règles à appliquer à tous les élément a quand la souris passe dessus*/
  }
```

---

#### 3.1.3/ Champs obligatoire
  
Applique du style à aux champs d'utilisateur possédant l'attribut ```required```:

```css
a:required {
  /*Règles à appliquer à tous les élément champs d'utilisateur obligatoire*/
  }
```

---

#### 3.1.4/ Champs sélectionné

Applique du style aux cases à cocher quand elle sont cochées:

```css
a:checked {
  /*Règles à appliquer aux cases à cocher quand elle sont cochées*/
  }
```

---

#### 3.1.5/ Champs désactivé

Applique du style champs utilisateur possedant l'attribut ```disabled```:

```css
a:diabled {
  /*Règles à appliquer aux champs désactivé*/
  }
```

---

### 3.2/ Position

On peut ajouter des pseudo-classe aux sélecteurs afin de préciser leurs postition relativement au parent:

#### 3.2.1/ Premier enfant

Applique le style aux éléments qui sont premier enfant d'un contenant:

```css
a:first-child {
  /*Règles à appliquer à tous les élément a à la premiere position*/
  }
```

Resultat:

![Graphique Sélecteur CSS Premier enfant](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-pseudo-first.svg)

---

#### 3.2.2/ Dernier enfant

Applique le style aux éléments qui sont dernier enfant d'un contenant:

```css
a:last-child {
  /*Règles à appliquer à tous les élément a à la derniere position*/
  }
```

Resultat:

![Graphique Sélecteur CSS Dernier enfant](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-pseudo-last.svg)

---

#### 3.2.3/ Enfant à la position

Applique le style aux éléments enfant aillant pour position la formule mentionnée entre parenthèses ```()``` dans un contenant:

```css
a:nth-child(2n) {
  /*Règles à appliquer à tous les élément a dont la position est un nombre pair*/
  }
```

Resultat:

![Graphique Sélecteur CSS Enfant à la position](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/2.css-selectors/css-selector-pseudo-nth.svg)

---

## Conclusion

Le CSS offre une grande flexibilité pour sélectionner et ciblé les éléments HTM voulus.

Dans le prochain chapitre, nous verrons en détails le Modèle de Boîtes CSS, son fonctionnement ainsi que sa terminologie, pour vous permettre de réaliser des mises en pages plus complexes.

## Aller plus loin

[Précédent: CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)

[Suivant: CSS: Les Boites](https://djemai-samy.com/posts/3.css-box.article)
