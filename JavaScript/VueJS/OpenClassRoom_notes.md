# Introduction
## What is VueJS?
It is a JavaScript front-end framework. The disadvantages of the front-end web development that it aims to fix are:
- long development time
- difficult bug fixes and updates
- slow page rendering

Vue is a SPA (Single Page application) framework.
-  a web page is downloaded only once
-  the content of the web page is updated accordinlgy to the user needs instead of downloading the content of a new page again
-  no more refresh of the page 

### Load VueJS
```HTML
<script src="https://cdn.jsdelivr.net/npm/vue>"></script>
```

### Check if there is no errors
```Javascript
console.log(Vue)
```

### VueJS configuration
``` Javascript
const app = new Vue({
	el: '#app'
})
```

- `el`: element abreviation, needs a CSS selector

Do not use functions with arrows because it can reset the context `this`.  `this` should always point towards the Vue instance.

## Storing data
-`data`: accepts pairs of key/value, excepts an object 
```javascript
const app = new Vue({
 	el: '#app',
	data: {
		key1: value1,
		key2: {
			key2.1: value 2.1,
			key2.2: value 2.2
		}
	}
 })
```

To render data in HTML, you need to use `{{}}`
``` HTML
<li>Pommes: {{ costOfApples }}€</li>
```

`{{}}` can also be used to render basic Javascript expressions such as
``` Javascript
<!-- Réaliser le calcul -->
{{ (2 + 8) * 10 }}

<!-- Appeler des méthodes de string -->
{{ "alexia".toUpperCase() }}

<!-- Opérateurs ternaires -->
{{ 2 > 0 ? 'Deux est plus grand que zéro' : 'Vous ne verrez jamais cette phrase' }}
```

### Computations
```Javascript
const app = new Vue({
  el: '#app',
  data: {
    costOfApples: 6,
    costOfBananas: 2,
    costOfCoconuts: 8
  },
  computed: {
    totalAmount() {
      return this.costOfApples + this.costOfBananas + this.costOfCoconuts
    },
	copyright(){
		const currentYear = new Date().getFullYear()
		return 'Copyright ${this.restaurantName} ${currentYear}'
	}
  }
})
```

## Conditions
- Helpful when you need to show/hide some content depending on a user's role (admin, user...)

### v-if, v-else-if, v-else
``` HTML
<div id="app">
    <!-- Si (if) l'utilisateur a les autorisations par défaut, afficher ce qui suit -->
    <section v-if="userPermission === 'default'">...</section>
    <!-- Sinon et si l'utilisateur a les autorisations administrateur, afficher ce qui suit -->
    <section v-else-if="userPermission === 'admin'">...</section>
    <!-- Si l'utilisateur n'a aucune autorisation afficher ce qui suit -->
    <section v-else>...</section>
</div>
```

### v-show
- Used when there is a need to control the visibility of a toggle element
``` HTML
<div id="app">
    <button @click="showModal = !showModal">Display Modal</button>
    <div v-show="showModal" class="modal">...</div>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            showModal: false
        }
    })
</script>
```

### loops: v-for
``` HTML
<div id="app">
    <h1>Vue Mart</h1>
    <h2>Shopping Cart</h2>
    <ul>
        <li v-for="item in shoppingCart">
            {{ item.label }} : {{ item.cost }}€
        </li>
    </ul>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            shoppingCart: [
                { label: 'Pommes', cost: 6 },
                { label: 'Bananes', cost: 2 },
                { label: 'Noix de coco', cost: 8 }
            ]
        }
    })
</script>
```

### v-bind
- links two items together

```HTML
<div id="app">
    <ul>
        <li v-for="item in apiResponse">
            <a v-bind:href="item.url">{{ item.name }}</a>
        </li>
    </ul>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            apiResponse: [
                { name: 'GitHub', url: 'https://www.github.com' },
                { name: 'Twitter', url: 'https://www.twitter.com' },
                { name: 'Netlify', url: 'https://www.netlify.com' }
            ]
        }
    })
</script>
```

### v-on
- Allows to listen to events on an element
- `methods` key in the vue instance allows to write methods callable by v-on events.

### v-model
- allows to update a data store field related to a form field. 
``` HTML
<div id="app">
    <label for="username">Nom d'utilisateur</label>
    <input id="username" type="text" v-model="username" />
    <label for="pw">Mot de passe</label>
    <input id="pw" type="password" v-model="password" />
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            username: '',
            password: ''
        }
    })
</script>
```

#VueJS #Code
