<template lang="html">
  <input v-if="!isTextarea" class="v-tag-input" type="text" v-model="editableValue">
  <textarea v-if="isTextarea" class="v-tag-input" type="text" v-model="editableValue">
</template>

<script>
export default {
  name: 'v-tag-input',
  props: {
    value: {
      type: Array,
      default: () => [] // factory function
    },
    separator: {
      type: String,
      default: ' '
    },
    isTextarea: {
      type: Boolean,
      default: false,
    }
  },
  computed: {
    editableValue: {
      get () {
        return (this.value || []).join(this.separator)
      },
      set (newValue) {
        newValue = newValue.trim() ? newValue.split(this.separator) : []
        this.$emit('input', newValue)
      }
    }
  }
}
</script>
