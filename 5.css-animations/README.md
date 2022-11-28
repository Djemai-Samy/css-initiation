# CSS: Les animations

Apprendre à styliser vos pages web en utilisant le CSS.

Dans cet article nous allons voir comment créer des animation afin de rendre nos pages web plus vivantes.

[Suivre tous les tutoriels sur mon site:](https://djemai-samy.com/posts/0.css-initiation)

- [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)
- [CSS: Sélécteurs](https://djemai-samy.com/posts/2.css-selectors.article)
- [CSS: Boites](https://djemai-samy.com/posts/3.css-box.article)
- [CSS: Transformations](https://djemai-samy.com/posts/4.css-transformations.article)
- [CSS: Animations](https://djemai-samy.com/posts/5.css-animations.article)

---

## Prérequis

Il est conseillé d'avoir suivi la première parti de ce tutoriel: [CSS: Introduction](https://djemai-samy.com/posts/1.css-introduction.article)

---

## 1/ Comprendre les animations

Les animations CSS permettent de créer des transitions entre plusieurs états de mise en forme.

Une animation est décrite par deux choses :

- Des propriétés propres à l'animation afin de la configurer la durée, le minutage et d'autres détails à propos de l'animation.
- Un ensemble d'étapes (```keyframes```) qui indiquent l'état initial, final et éventuellement des états intermédiaires.

## 2/ Les étapes d'une animation

Afin de créer une animation en CSS, on utilise la règle ```@keyframes``` suivi par le nom de l'animation et des accolades ```{}```.

Puis entre les accolades, nous précisons les étapes exprimées en pourcentage.

- ```0%``` indique l'état initial de l'animation.
- ```100%``` indique l'état final.

Pour l'exemple nous allons créer une animation qui changera la couleur d'un carré representé dans notre HTML par une div:

```html
<div class="square" id="change-color"></div>
```

puis dnas notre CSS:

```css
.square{
    height:200px;
    width:200px;
}

@keyframes changeColorAnimations{
    0%{
        background-color:red;
    }
    100%{
        background-color:blue;
    }
}
```

---

## 3/ Paramétrer l'animation

Maintenant que notre animation est déclarée, nous devons la lier avec l'élément HTML à animer. Dans notre cas, il s'agit de la div possédant l'identifiant ```#change-color```:

```css
#change-color{
    animation-name:changeColorAnimation;
    animation-duration: 2s;
    animation-iteration-count:infinite;
}
```

![La timeline de l'animation](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/5.css-animations/2.changeColor.svg)

Toutes les paramètres possible sont :

- ```animation-name```: Cette propriété permet de déclarer un nom qui pourra être utilisé comme référence à l'animation pour la règle ```@keyframes```.

- ```animation-duration```: Cette propriété définit la durée d'un cycle de l'animation.

- ```animation-iteration-count```: Cette propriété détermine le nombre de fois que l'animation est répétée. On peut utiliser le mot-clé ```infinite``` afin de répéter une animation infiniment.

- ```animation-delay```: Cette propriété définit le délai entre le moment où l'élément est chargé et le moment où l'animation commence.

- ```animation-direction```: Cette propriété indique si l'animation doit alterner entre deux directions de progressions (faire des allers-retours) ou recommencer au début à chaque cycle de répétition.

- ```animation-fill-mode```: Cette propriété indique les valeurs qui doivent être appliquées aux propriétés avant et après l'exécution de l'animation.

- ```animation-play-state```: Cette propriété permet d'interrompre (« pause ») ou de reprendre l'exécution d'une animation.

- ```animation-timing-function```: Cette propriété configure la fonction de minutage d'une animation, autrement dit comment celle-ci accélère entre l'état initial et l'état final notamment grâce à des fonctions décrivant des courbes d'accélération.

---

### 3.1/ Etapes intermédiaires

Afin d'ajouter des étapes intermédiaires, il suffit d'ajouter des ```keyframes``` entre ```0%``` et ```100%```:

```css
@keyframes changeColorAnimations{
    0%{
        background-color:red;
    }
    50%{
        background-color:green;
    }
    100%{
        background-color:blue;
    }
}
```

![La timeline de l'animation avec 3 étapes](https://djemai-samy.com/blog/2.programmation/1.web/2.css/1.css-initiation/5.css-animations/4.changeColor3key.svg)

---

### 3.2/ Direction d'une animation

Pour illustrer notre exemple, nous allons ajouter une nouvelle ```div```:

```html
<div class="square" id="move"></div>
```

Puis dans le CSS, ajoutons une nouvelle animations:

```css
#move{
    background-color:purple;
    animation-name: moveAnimation;
    animation-duration: 2s;
    animation-iteration-count:infinite;
}
@keyframes moveAnimation{
    0%{
        transform: translateX(0) rotate(0deg) scale(1);
        border-radius: 5px;
    }
    100%{
        transform: translateX(100%) rotate(180deg) scale(0.5);
        border-radius: 50%;
    }
}
```

On a donc une animation qui se répète mais on obtient un résultat étrange, l'animation redémarre à chaque fois depuis l'état initial.

Si on veut que l'élément aille de droite à gauche puis de gauche à droite, on pourra utiliser la propriété ```animation-direction``` avec la valeur ```alternate```.

---

### 3.2/ Accélération d'une animation

Nous avons la possibilité de modifié l'accélération de l'élément entre l'état initial et l'état final notamment grâce aux courbes de bézier. (Par défaut, l'accélération est lineaire).

- ```animation-timing-function:linear```.
- ```animation-timing-function:ease-in-out```.
- ```animation-timing-function: cubic-bezier(.77,-0.02,.16,1.01)```.

il existe plusieurs site permettant de configurer et générer les coordonnés tout en visualisant la courbe, voici un exemple de site:
[www.cubic-bezier.com](https://cubic-bezier.com/#.17,.67,.83,.67)

---

## 5/ Raccoucie

La propriété raccourcie animation permet d'économiser de l'espace. Par exemple, si on prend cette règle :

```css
#move{
    background-color:purple;
    animation-name: moveAnimation;
    animation-duration: 2s;
    animation-iteration-count:infinite;
    animation-direction: alternate;
    animation-timing-function: cubic-bezier(.77,-0.02,.16,1.01);
}
        ```
On peut la réécrire de façon plus concise :

```css
#move{
    background-color:purple;
    animation: moveAnimation 2s infinite cubic-bezier(.77,-0.02,.16,1.01) alternate;
}
```

---

## Conclusion

Dans cet article nous avons vu comment animer n'importe quel propriété de n'importe quel élément HTML.

Dans la partie suivante, nous allons utiliser tous ce que nous avons vu pendant cette serie de tutoriels, dans un cas concret, pour créer une page web.

---

## Aller plus loin

[Précédent: CSS: Les Boîtes](https://djemai-samy.com/posts/4.css-transformations.article)

[Suivant: CSS: Styliser une page](https://djemai-samy.com/posts/6.css-page.article)
