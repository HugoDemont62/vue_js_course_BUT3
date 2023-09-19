# Cours du framework VueJs

*Avec Nicolas PARIS*

*Cours dans vuejs.html*

### Présentation

VueJs est un framework Javascript permettant de créer des interfaces utilisateurs.
C'est un framework incremental, c'est-à-dire qu'il peut être utilisé pour créer des interfaces utilisateurs simples et
complexes et être incrémenté dans un projet déjà existant.

Il est très simple à prendre en main et permet de créer des applications web complexes.
Vue ne supporte pas IE8 et les versions antérieures, car il utilise les fonctions ECMAScript 5 qui ne sont pas
supportées par IE8.

#### Rapide rappelle sur Javascript

DOM et les Events :

- Le DOM est une interface de programmation pour les documents HTML, XML et SVG.
    - Le DOM (view) est lié via le dataBinding aux données de l'application (model) dans laquelle on trouve la data et
      la
      logique de l'application.
- Les Events sont des actions de l'utilisateur sur la page web (click, scroll, etc.).

Qui dit application VueJs dit une manipulation du DOM et des Events.

### VueJs

Framework javascript frontend et opensource
et le dev d'applications web complexes fluide et modulaire et reactive.

SPA : Single Page Application.

*Exemple :*

- Gmail
- Google Drive
- Google Maps
- Twitter
- Facebook
- ...

SCRUM : méthodo de gestion de projet de manière agile (itérative et incrémentale)

### Le dataBinding

Le dataBinding est un lien entre le DOM et les données de l'application.
Il fonctionne dans les deux sens et permet de mettre à jour les données de l'application en fonction des actions de l'
utilisateur et inversement.

### Les composants

Les composants sont des éléments réutilisables dans l'application.
Ils permettent de découper l'application en plusieurs parties et de les réutiliser dans d'autres applications.

### Modèle MVVM

Le modèle MVVM est un modèle de conception de logiciel qui sépare les données de la logique de présentation.
Il est composé de trois parties :

- Le modèle : les données de l'application
- La vue : la présentation des données
- Le ViewModel : la logique de présentation
- Le dataBinding : le lien entre le modèle et la vue

Magento lui est un modèle MVVMV (Model View ViewModel View) car il y a une vue pour le client et une vue pour l'admin.

### Les directives

Les directives sont des attributs HTML qui permettent d'ajouter des comportements à un élément HTML.
Elles sont préfixées par `v-` et peuvent être utilisées sur les éléments HTML, les composants et les commentaires.

Par exemple :

- `v-if` : permet d'afficher ou non un élément HTML en fonction d'une condition
- `v-for` : permet de parcourir un tableau et d'afficher un élément HTML pour chaque élément du tableau
    - `v-for` : permet de parcourir un tableau
        - par exemple : `v-for="item in items"`
        - `item` : nom de la variable qui contient l'élément du tableau
        - `items` : nom du tableau (dans les data du composant)
- `v-on` : permet d'ajouter un événement à un élément HTML
- `v-bind` : permet de lier une propriété HTML à une propriété de l'application
- `v-model` : permet de lier une propriété HTML à une propriété de l'application et d'ajouter un événement sur l'élément
  HTML
- `v-text` : permet d'ajouter du texte dans un élément HTML
- `v-html` : permet d'ajouter du code HTML dans un élément HTML
- `v-show` : permet d'afficher ou non un élément HTML en fonction d'une condition
- `v-cloak` : permet de cacher un élément HTML en attendant que l'application soit chargée
- `v-pre` : permet d'afficher le contenu d'un élément HTML sans interpréter les directives
- `v-once` : permet d'afficher le contenu d'un élément HTML une seule fois
- ...

Différence entre instance et class :

- Une instance est un objet créé à partir d'une classe. Elle possède les mêmes propriétés et méthodes que la classe.
- Une classe est un modèle qui permet de créer des objets. Elle possède des propriétés et des méthodes.

### Vue conditionnelle

Les directives `v-if` et `v-else` permettent d'afficher ou non un élément HTML en fonction d'une condition.

````html

<div id="app2">
    <span v-if="conditional === 0">Test Conditional v-if {{ conditional }}</span>
    <span v-else-if="conditional === 1">Test conditional v-else-if {{ conditional }}</span>
    <span v-else>Tes conditional v-else {{ conditional }}</span>
</div>
````

````javascript
const app2 = new Vue({
  el: '#app2',
  data: {
    conditional: 0, // affichera le premier span
  },
});
````

Exercices :

````html

<div id="app">
    <span v-if="conditional === 'H'">Sexe => {{ conditional }} <br> Je suis un homme</span>
    <span v-else-if="conditional === 'F'">Sexe => {{ conditional }}  <br> Je suis une femme</span>
    <span v-else>Sexe => Autres</span>
    
    <br>
    <input type="text" v-model="conditional">
</div>


<div id="app2">Mon rang est {{ conditional }},
    <span v-if="conditional === '1'"> ma médaille : Or</span>
    <span v-else-if="conditional === '2'">ma médaille : Argent</span>
    <span v-else-if="conditional === '3'"> ma médaille : Bronze</span>
    <span v-else>ma médaille : Pas de médaille</span>
    <br>
    <input type="text" v-model="conditional">
</div>

<script>
let app = new Vue({
    el: '#app',
    data: {
        conditional: 'H',
    },
});

let app2 = new Vue({
    el: '#app2',
    data: {
        conditional: '4',
    },
});

</script>
````

````HTML

<div id="app3">
    <ul>
        <li v-for="item in items">
            <span v-if="item % 2 === 0">Pair : {{ item }}</span>
            <span v-else>Impair : {{ item }}</span>
        </li>
    </ul>
</div>
````

````javascript
let app3 = new Vue({
  el: '#app3',
  data: {
    items: [1, 2, 3, 4, 5, 6, 7],
  },
});
````

```HTML

<div id="app">
    <p v-bind:style="{ color: maxSize ? 'red' : 'black' }">{{ reversedMessage }}</p>
    <input type="text" v-model="message">
</div>
```

```javascript
let app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!',
    max: 40,
  },
  computed: {
    reversedMessage: function() {
      return this.message.split('').reverse().join('');
    },
    maxSize: function() {
      return this.message.length > this.max;
    },
  },
  watch: {
    message: function(val) {
      this.c = val.length;
    },
  },
});
```

### Les événements

Les directives `v-on` et `v-bind` permettent d'ajouter des événements à un élément HTML.

````html

<div id="app">
    <button v-on:click="increment">Incrémenter</button>
    <button v-on:click="decrement">Décrémenter</button>
    <p>{{ counter }}</p>
</div>
````

````javascript
let app = new Vue({
  el: '#app',
  data: {
    counter: 0,
  },
  methods: {
    increment: function() {
      this.counter++;
    },
    decrement: function() {
      this.counter--;
    },
  },
});
````

## Props et Emit

Les props permettent de passer des données d'un composant parent à un composant enfant.

````html

<div id="app">
    <child-component v-bind:prop1="message"></child-component>
</div>

<script>
Vue.component('child-component', {
    props: ['prop1'],
    template: '<p>{{ prop1 }}</p>',
});

let app = new Vue({
    el: '#app',
    data: {
        message: 'Hello World',
    },
});
</script>
````
