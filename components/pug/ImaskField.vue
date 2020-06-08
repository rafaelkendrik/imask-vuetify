<template lang="pug">
  v-text-field(
    ref="field"
    :value="value"
    @input="input"
    @blur="checkNormalize"
    v-bind="$attrs"
  )
</template>

<script>
  import Imask from 'imask'

  const INPUT_EVENT = 'input'

  export default {
    name: 'ImaskField',

    model: {
      prop: 'value',
      event: INPUT_EVENT
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

    data: () => ({
      element: {},
      masked: {}
    }),

    methods: {
      init () {
        this.element = this.$refs.field.$el.querySelector('input')
        this.masked = Imask(this.element, this.mask)
      },

      input (value) {
        this.$emit(INPUT_EVENT, value)
      },

      checkNormalize () {
        const isNormalized = (this.element.value === this.masked.value)

        if (!isNormalized) {
          this.element.value = this.masked.value
          this.element.dispatchEvent(new Event(INPUT_EVENT))
        }
      }
    },

    mounted () {
      this.init()
    }
  }
</script>
