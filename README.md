# Imask-Vuetify

A simple component that integrates Vuetify TextField component with Imask.
Available in pug and html templates.

## Motivation
This component contains few simple rules that have solved some common side effects when Imask is integrated with native inputs inside Vuetify TextField.
This side effects are common even while using [vue-imask](https://github.com/uNmAnNeR/imaskjs/tree/master/packages/vue-imask).

## Dependencies

- [Vuetify](https://github.com/vuetifyjs/vuetify)
- [Imask](https://imask.js.org/)

## Usage

**HTML Template**

```vue
<template>
  <imask-field label="Name" v-model="name" :mask="nameMask" required>
</template>

<script>
  export default {
    data: () => ({
      name: 'My Name',

      nameMask: {
        mask: /^([a-zA-Z]+ ?)*$/
      }
    })
  }
</script>
```

**Pug Template**
```vue
<template lang="pug">
  imask-field(
    label="Name"
    v-model="name"
    :mask="nameMask"
    required
  )
</template>

<script>
  export default {
    data: () => ({
      name: 'My Name',

      nameMask: {
        mask: /^([a-zA-Z]+ ?)*$/
      }
    })
  }
</script>
```
