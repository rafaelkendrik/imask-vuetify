<template>
  <v-text-field
    ref="field"
    :value="value"
    @input="input"
    @blur="checkNormalize"
    v-bind="$attrs"
  ></v-text-field>
</template>

<script>
  import Imask from 'imask'

  const EVENT = 'input'

  let element = {}
  let masked = {}

  export default {
    name: 'ImaskField',

    model: {
      prop: 'value',
      event: EVENT
    },

    props: {
      value: {
        type: [String, Number],
        required: false,
        default: String()
      },

      mask: {
        type: Object,
        required: true
      }
    },

    methods: {
      init () {
        element = this.$refs.field.$el.querySelector('input')
        masked = Imask(element, this.mask)
      },

      input (value) {
        this.$emit(EVENT, value)
      },

      checkNormalize () {
        const isNormalized = (element.value === masked.value)

        if (!isNormalized) {
          element.value = masked.value
          element.dispatchEvent(new Event(EVENT))
        }
      }
    },

    mounted () {
      this.init()
    }
  }
</script>
