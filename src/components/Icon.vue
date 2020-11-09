<template>
  <img :src="require(`@/assets/icons/${name}.svg`)" />
</template>

<script>
export default {
  props: {
    name: {
      type: String
    }
  }
}
</script>
