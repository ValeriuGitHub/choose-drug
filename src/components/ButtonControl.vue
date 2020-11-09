<template>
  <component
    :is="type"
    :href="href"
    @click="functionCall"
    :to="to"
    :class="className"
  >
    <slot/>
  </component>
</template>

<script>
export default {
  props: {
    href: {
      type: String
    },
    to: {
      type: String
    },
    className: {
      type: String
    },
    functionCall: {
      type: Function,
      default: () => null
    }
  },
  computed: {
    type () {
      if (this.href) {
        return 'router-link'
      } else {
        return 'button'
      }
    }
  }
}
</script>
