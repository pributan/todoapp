# todoapp

## Project setup

```
yarn install
```

## Install FontAwesome 5

```
$ yarn add @fortawesome/fontawesome-free -D
```

## Import FontAwesome in src/plugins/vuetify.js

Note : You have to change some PRO's font if you use the free version of FA

```
import '@fortawesome/fontawesome-free/css/all.css' // Ensure you are using css-loader
import Vue from 'vue'
import Vuetify from 'vuetify/lib'

Vue.use(Vuetify)

export default new Vuetify({
  icons: {
    iconfont: 'fa',
  },
})
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
