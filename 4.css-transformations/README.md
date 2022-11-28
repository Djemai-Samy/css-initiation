# CSS: Les transformations

Apprendre à styliser vos pages web en utilisant le CSS.

Dans cet article nous allons nous voir les transformations en CSS, afin d'apprendre à déplacer, faire des rotations ou changer la taille des éléments.

[Suivre tous les tutoriels sur mon site:](https://djemai-samy.com/posts/0.css-initiation)

- [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)
- [CSS: Sélécteurs](https://djemai-samy.com/posts/2.css-selectors.article)
- [CSS: Boites](https://djemai-samy.com/posts/3.css-box.article)
- [CSS: Transformations](https://djemai-samy.com/posts/4.css-transformations.article)

---

## Prérequis

Il est conseillé d'avoir suivi la première parti de ce tutoriel: [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)

---

## 1/ Les ransformations en 2D

### 1.1/ Les axes de transformations

Un écran est representé par deux axes:

![Axe de transformations CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-1.2d-axes.svg)

1. Sur l’axe X, les valeurs augmentent de gauche à droite.

2. Sur l’axe Y, les valeurs augmentent de haut en bas.

---

### 1.2/ Le point d'origine

chaque élément du DOM possède un point d'origine. Ce point est par défaut situé au centre l'objet.

La propriété ```transform-origin``` permet de modifier le point d'origine d'un objet HTML.

Elle accepte comme valeur le X et le Y de l'origine souhaité séparés par un espace.

Ces deux informations peuvent être spécifiées en pourcentage, en pixel, ou par les mots clé ```left```, ```right```, ```top```, ```bottom``` et ```center```.

Par exemple:

- ```transform-origin: 0 0;```: le point d'origine est dans le coin haut gauche.
- ```transform-origin: 100% 100%;```: le point d'origine est dans le coin bas droite.

---

### 1.3/ Les transformations

Toutes les transformations sont appliqué par rapport au point d'origine.

Prenons pour exemple une ```div```:

```html
<div class='square'>
    <h2>un carré</h2>
</div>
```

Puis grâce au style, nous allons en faire un carré avec une hauteur et une largeur de ```100px```:

```css
.square{
    background-color:green;
    width: 100px;
    height:100px;
}
```

afin d'appliquer des transformations en CSS, nous utilisons la propriété ```transform```, qui prend en valeurs toutes les transformations possibles.

#### La rotation

En ajoutant la déclaration ```transfrom: rotate(45deg)```, nous appliquons une rotation de 45° dans le sens des aiguilles d'une montre:

![La rotation en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.rotate-2d.svg)

---

#### La translation

Pour déplacer un élément horizontalement (Sur l'axe X), on utilise la déclaration ```transfrom: translateX(100px)```

![La translation sur l'axe X en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.translateX-2d.svg)

---

Pour déplacer un élément verticalement (Sur l'axe Y), on utilise la déclaration ```transfrom: translateY(50px)```

![La translation sur l'axe Y en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.translateY-2d.svg)

---

On peut aussi déplacer un élément sur les deux axes avec la déclaration ```transfrom: translate(100px, 50px)``` ou ```transfrom: translateX(100px) translateY(50px)```

![La translation sur l'axe X et Y en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.translate-2d.svg)

---

#### La taille

Pour changer la taille  d'un élément horizontalement (Sur l'axe X), on utilise la déclaration ```transfrom: scaleX(2)```

![La taille sur l'axe X en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.scaleX-2d.svg)

---

Pour changer la taille  d'un élément horizontalement (Sur l'axe Y), on utilise la déclaration ```transfrom: scaleY(1.5)```

![La taille sur l'axe Y en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.scaleY-2d.svg)

---

On peut aussi changer la taille d'un élément sur les deux axes avec la déclaration ```transfrom: scale(1.5)```:

![La taille sur l'axe x et Y en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.scale-2d.svg)

---

Pour changer la taille d'un élément sur les deux axes de manière indépendante, nous pouvons utiliser cette syntaxe: ```transform: scaleX(2) scaleY(1.5)```:

![La taille sur l'axe x et Y indépendament en CSS](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/1-3.scaleXY-2d.svg)

---

---

## 2/ Les transformation en 3D

### La perspective

La propriété CSS ```perspective``` permet d'activer la perspective 3D et l'axe Z.

![La perspective 3D en CSS ](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/css-axeZ.png)

La valeur donnée modifie la distance entre l'observateur/camera, et le point d'origine ```z=0``` sur l'axe de perspective Z.

```perspective:800px```:

![La perspective a 800px en CSS ](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/css-perspective800.png)

```perspective:400px```:

![La perspective a 400px en CSS ](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/css-perspective400.png)

---

### Le point de fuite:

La propriété CSS perspective-origin, permet de spécifier la position du point de fuite sur l'axe X et Y dans le contexte 3D. 

Par défaut la valeur est au centre (50% 50%)

```perspective-origin: 50% 50%```:

![Point de fuite par défaut en CSS ](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/2-1.pointfuitecentre-3d.svg)

```perspective-origin: 100% 50%```:

![Point de fuite à droite en CSS ](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/4.css-transformations/2-1.pointfuitedroite-3d.svg)

---

### Les transformations en 3D

Afin de pouvoir visualiser la perspective 3D en CSS, il faut appliquer la perspective au parent des éléments placé dans un environnement 3D:

```html
<div class="wrap3D">
    <div class="face">
    </div>
</div>
```

Puis en CSS:

```css
.wrap3D{
    perspective: 800px;
    display:flex;
    justify-content:center;
    align-items:center;
}

.face{
    height: 150px;
    width: 150px;
    background-color: green;
}
```

---

#### La rotation

En 3D, nous pouvons appliquer deux nouvelles rotation:

Par exemple:

- ```transform:rotateX(45deg)```: rotation sur l'axe X (De haut en bas).
- ```transform:rotateY(45deg)```: rotation sur l'axe Y (De gauche à droite).

---

#### La translation

La 3D, ouvre aussi la possibilité de déplacer les élément sur l'axe Z:

- ```transform:translateZ(100px)```: translation sur l'axe z (Se rapproche de l'observateur)

La translation sur l'axe Z donne l'impression d'augmenter et de diminuer la taille de l'élément, mais en réalité il y'a bien un déplacement. Comme dans la vraie vie, les objets paraissent plus petit quand ils s'éloignent de l'observateur/camera, et plus gros si ils se rapprochent.

---

### Exemple: Créer un cube

Dans cet exemple, nous allons utiliser les transformations sur des ```div``` pour reconstituer un cube à quatre face:

```html
<div class="wrap3D">
    <div class="cube">
        <div class="face" id="front">Front</div>
        <div class="face" id="right">Right</div>
        <div class="face" id="back">Back</div>
        <div class="face" id="left">Left</div>
    </div>
</div>
```

Puis en CSS:

```css
.cube{
    position:relative;
    width:200px;
    height:200px;
    transform-style:preserve-3d;
    transform:rotateY(45deg);
}

.cube > face {
    width: 200px;
    height: 200px;
    position: absolute;
}

#front{
    transform: translateZ(100px);
}

#right{
    transform: rotateY(90deg) translateX(100px);
    transform-origin:"center right";
}
#rightback{
    transform: rotateY(180deg) translateZ(100px);
}
#left{
    transform: rotateY(-90deg) translateX(-100px);
    transform-origin:"center left";
}
```

## Conclusion

Maintenant que nous avons vu comment transformer les éléments, dans la chapitre suivant nous allons apprendre à créer des transitions et animations orchestrées afin de rendre nos pages web plus vivantes.

## Aller plus loin

[Précédent: CSS: Les Boîtes](https://djemai-samy.com/posts/3.css-box.article)

[Suivant: CSS: Les animations](https://djemai-samy.com/posts/5.css-animations.article)
