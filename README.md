# Imask-Vuetify

A simple component that integrates Vuetify TextField component with Imask.
Available in pug and html templates.

# Usage

## HTML Template

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

## Pug Template
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
