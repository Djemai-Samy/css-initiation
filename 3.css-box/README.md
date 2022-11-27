# CSS: Les boites

Apprendre à styliser vos pages web en utilisant le CSS.

Dans cet article nous verrons en détails le Modèle de Boîtes CSS - son fonctionnement ainsi que sa terminologie - pour vous permettre de réaliser des mises en pages plus complexes.

[Suivre tous les tutoriels sur mon site:](https://djemai-samy.com/posts/0.css-initiation)

- [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)
- [CSS: Sélécteurs](https://djemai-samy.com/posts/2.css-selectors.article)
- [CSS: Boites](https://djemai-samy.com/posts/3.css-box.article)

---

## Prérequis

Il est conseillé d'avoir suivi la première parti de ce tutoriel: [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)

---

## 1/ Le modèle de boîte

En CSS, tout élément est inclus dans une boîte ("box" en anglais).

Comprendre le fonctionnement de ces boîtes est essentiel pour maîtriser la mise en page CSS ainsi que le positionement des éléments d'une page HTML.

![Image du modèle de boite CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/3.css-box/1.box-model.svg)

- Le contenu: Il s'agit de la zone où sont affichés les éléments contenus par notre boîte, qui peut être dimensionnée en utilisant les propriétés CSS ```width``` et ```height```.
- Le ```padding``` (marge intérieure) : est une zone vierge qui se présente comme un espacement encadrant le contenu; sa taille peut être contrôlée sur chaque côté en utilisant la propriété padding et ses autres propriétés connexes.
- La bordure : La bordure englobe le contenu et le padding pour former une bordure. Sa taille et son style sont paramétrés par la propriété ```border``` et ses propriétés sous-jacentes.
- La marge : est la couche la plus à l'extérieur, englobant le contenu, le padding et la bordure. Comme le padding , il s'agit d'une zone vierge d'espacement mais qui est cette fois située à l'extérieur de l'élément, séparant l'élément des autres éléments de la page. sa taille peut être contrôlée sur chaque côté en utilisant la propriété margin et ses autres propriétés connexes.

---

On remarque que la largeur finale de l'élément sera la largeur du contenu donnée avec la propriété CSS ```width``` et de l'addition de la taille du padding, de la bordure et du margin.

Il existe une propriété CSS, appelée ```box-sizing: border-box;```, permettant de dire au navigateur que la largeur et la hauteur de l'élement doit inclure la largeur et la hauteur du padding et de la bordure:

![Image du modèle de boite CSS avec box-sizing](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/3.css-box/1-2.box-size.svg)

---

### Exemple

Dans l'exemple ci-dessous, se trouvent deux boîtes (```<div>```). Les deux boîtes possèdent la classe ```.box```, et la deuxiemme possèdent en plus la classe ```alternate```.

```html
<div class="box">Boîte standard.</div>
<div class="box alternate">Boîte aletrnative.</div>
```

Puis en CSS nous allons ajouter à la classe .box les proprietés width, height, padding et margin.

Pour le deuxiemme boite, avec la classe ```.alternate```, nous allons préciser au navigateur de prendre en compte le ```padding``` et la bordure dans la taille de l'élément grâce a la propriété ```box-sing: border-box;```:

```css
.box {
    border: 5px solid rebeccapurple;
    background-color: lightgray;
    padding: 40px;
    margin: 40px;
    width: 300px;
    height: 150px;
}

.alternate {
    box-sizing: border-box;
}
```

---

## 2/ Les types de boîte

En CSS, il existe deux type de boîtes :

les boîtes en bloc ("block boxes" en anglais) et les boîtes en ligne ("inline boxes" en anglais).

Ces deux qualifications renvoient au comportement de la boîte au sein de la page et vis-à-vis des autres boîtes :

---

### 2.1/ Les boîtes en bloc

Si une boîte est définie en bloc, elle suivra alors les règles suivantes :

- La boîte s'étend en largeur pour remplir totalement l'espace offert par son conteneur. Dans la plupart des cas, la boîte devient alors aussi large que son conteneur, occupant 100% de l'espace disponible.
- La boîte occupe sa propre nouvelle ligne et crée un retour à la ligne, faisant ainsi passer les éléments suivants à la ligne d'après.
- Les propriétés de largeur ```width``` et de hauteur ```height``` sont toujours respectées.
- Les propriétés ```padding```, ```margin``` et ```border``` auront pour effet de repousser les autres éléments.

À moins que l'on ne décide de changer le type de positionnement de la boîte en "en ligne", certains éléments tels que les titres (```<h1>```, ```<h2>```, etc.), les paragraphes ```<p>```, les ```div``` et pleins d'autresn utilisent le mode "bloc" comme propriété de positionnement extérieur par défaut.

---

### 2.2/ Les boîtes en ligne

Si une boîte est positionnée en ligne, alors :

- La boîte ne crée pas de retour à la ligne, les autres éléments se suivent donc en ligne.
- Les propriétés de largeur (width) et de hauteur (height) ne s'appliquent pas.
- Le padding , les marges et les bordures verticales (en haut et en bas) seront appliquées mais ne provoqueront pas de déplacement des éléments alentours.
- Le padding , les marges et les bordures horizontales (à gauche et à droite) seront appliquées et provoqueront le déplacement des éléments alentours.

Les éléments ```<a>```, utilisés pour les liens, ou encore ```<span>```, ```<em>``` et ```<strong>``` sont tous des éléments qui s'affichent "en ligne" par défaut.

Le type de boîte appliqué à un élément est défini par la propriété CSS ```display``` avec la valeur ```block``` ou ```inline```.

---

## 3/ Positionnement intérieur

Comme nous l'avons évoqué, les boîtes en CSS possèdent un type de positionnement extérieur qui détermine si la boîte est "en ligne" ou bien "en bloc".

Cependant, les boîtes ont aussi un type de positionnement intérieur, qui décrit le comportement de mise en page des éléments contenus dans la boîte.

---

Par défaut, les éléments contenus dans la boîte sont affichés dans la disposition normale, ce qui signifie qu'ils se comportent exactement comme n'importe quel autre élément "en bloc" ou "en ligne" (comme décrit auparavant).

Nous pouvons modifier le positionnement intérieur  en utilisant la valeur ```flex``` de la propriété ```display```.

---

Si on donne la propriété ```display: flex;``` à un élément, son type de positionnement extérieur est "en bloc" (block), mais son type de positionnement intérieur est modifié en flex.
Ce type de positionement interne nous donne beaucoup de controle sur la mise en page des éléments enfants.

Nous pourrons les arrangés selon un axe principal, permettant de disposer des éléments en ligne ou en colonne. Les éléments se dilatent ou se rétractent pour occuper l'espace disponible ect...

Prenons pour exemple une boîte avec la classe ```.parent```, contenant d'autre boites avec la class ```.child```:

```html
<div class="parent">
  <div class="child">
    Enfant 1
  </div>
  <div class="child">
    Enfant 2
  </div>
  <div class="child">
    Enfant 3
  </div>
  <div class="child">
    Enfant 4
  </div>
</div>
```

Puis dans notre CSS, nous allons attribuer une bordure et un ```display:flex;``` à la class ```.parent```, et une bordure pour la classe ```.child``` pour mieux visualiser ce qu'il se passe:

```css
.parent{
  border: 2px solid blue;
  display:flex;
}
.child{
  border: 2px solid red;
  margin:20px;
  padding:20px;
  width:100px;
}
```

On remarque que les éléments sont placés en ligne, et leur taille s'ajustent quand la taille du parent change.

On remarque aussi que pour petit largeur d'écran, les élément restent en ligne ajoutant un scroll horizontale.

---

### Retour à la ligne

Afin de permettre aux enfants du parent de faire une retour à la ligne quand il n'y a plus de place, nous pouvons ajouter la classe ```.parent```, la propriété ```flex-wrap:wrap;```.
Le CSS offre une grande flexibilité pour sélectionner et ciblé les éléments HTM voulus.

Dans le prochain chapitre, nous verrons en détails le Modèle de Boîtes CSS, son fonctionnement ainsi que sa terminologie, pour vous permettre de réaliser des mises en pages plus complexes.

On remarque maintenant que les élements forment une seule ligne quand il y'a de l'espace, et permet un retour à la ligne quand l'espace manque.

Cette méthode est très utile pour construire des sites qui s'adaptent au différentes tailles d'écrans.

---

### Direction

Avant de parler de direction, il faut comprendre que les boites ```flex```, possèdent deux axes:

- Axe principale, est l'axe de la direction dans laquelle sont disposés les éléments flex. Le début et la fin de cet axe sont appelés l'origine principale (main start) et la fin principale (main end). Par défaut horizontale allant de gauche à droite.
- Axe croisé (cross axis) est l'axe perpendiculaire à l'axe principal. Le début et la fin de cet axe sont appelés le début (cross start) et la fin (cross end) de l'axe croisé.

![Representation de l'axe principal et croisé](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/3.css-box/1-2.css-box-axes.svg)

On peut modifier la direction de l'axe principal, (horizontale ou verticale), en utilisant la propriété ```flex-direction```, qui peut prendre plusieurs valeurs:

- ```row```: Pour mettre les éléments en ligne (valeur par défaut).
- ```row-reverse```: Pour mettre les éléments en ligne avec ordre inversé (Axe pricipale horizontale de droite à gauche).
- ```column```: Pour mettre les éléments en colonne (Axe principal horizontale de haut en bas).
- ```column-reverse```: Pour mettre les éléments en colonne avec ordre inversé (Axe principal horizontale de bas en haut)

---

### Disposition

On remarque dans l'exemple précedent, que les éléments sont toujours placé au début de l'axe principal.

Par défaut, en direction ```row```, les éléments se sont placés à gauche du parent, au début de l'axe principal.

Avec la disposition ```row-reverse```, les éléments ce sont positionnés à droite du parent, toujours au début de l'axe pricipal.

Il existe deux propriétés CSS permettant de placer les éléments au début, au centre ou à la fin de l'axe pricipal et croisé:

- ```justify-content```: permettant de positionner les éléments sur l'axe principal, et peut prendre 5 valeurs:
- ```flex-start``` (par défaut) tous les éléments sont disposés vers l'origine de l'axe principal:
- ```center```: les éléments flex sont placés vers le centre de l'axe principal:
- ```end```: tous les éléments sont disposés à la fin de l'axe principal:
- ```space-around```: distribue régulièrement tous les éléments le long de l'axe principal, en laissant autant d'espace à chaque extrémité et entre chacun des éléments:
- ```space-between```: est semblable à space-around, mais elle ne laisse pas d'espace aux extrémités:
- ```align-items```: Suit le meme principe, permettant de positionner les éléments sur l'axe croisé, et peut prendre ausii 3 valeurs (```start```,```center```, ```end```).

---

### Taille modulable

Avec la propriété ```flex```, on peut decider d'une valeur de proportion, sans unité, définissant la quantité d'espace disponible que chaque élément flex prendra le long de l'axe principal.

Par défaut la veleur est de 1, mais si nous ajoutons cette règles à notre css:

```css
.child:nth-child(2){
  flex:2;
}
```

L'élément enfant às la position 2 aura deux fois la taille des autres éléments quand la place le permet.

---

## Aller plus loin avec les Flexbox

La méthode de mise en page en utilisant le positionnement ```flex``` est très flexible et complexe.

Nous avons couvert la partie essentiel, mais il reste beaucoup de choses à voire. Nous allons les introduire plus tard dans le tutoriel, mais si vous voulez aller plus loin sur les techniques et utilisation, je vous conseille:

- [La documentation MDN sur les flexbox.](https://developer.mozilla.org/fr/docs/Learn/CSS/CSS_layout/Flexbox)

- [Flexbox Froggy: Un jeu permettant d'apprendre de manière ludique.](https://flexboxfroggy.com/#fr)

---

## Conclusion

Dans cet article nous avons vu les bases de la mise en page d'éléments en CSS. nous allons plus tard, à travers un exemple concret et complet approfondir ces notions et en introduire d'autres.

Mais avant, dans le prochain article, nous allons nous voir les transformations en CSS, et comment déplacer, faire des rotation ou changer la taille des éléments.

## Aller plus loin

[Précédent: CSS: Les selecteurs](https://djemai-samy.com/posts/2.css-selectors.article)

[Suivant: CSS: Les transfromations](https://djemai-samy.com/posts/4.css-transformations.article)
