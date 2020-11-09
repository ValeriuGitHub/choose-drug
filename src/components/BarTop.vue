<template>
  <div class="bar-top">
    <ButtonControl
      href="#"
      to="/"
      :className="'circle'"
    >
      <Icon name='union' />
    </ButtonControl>
    <ButtonControl
      :className="'circle button'"
      :functionCall="reload"
    >
      <Icon name='group' />
    </ButtonControl>
  </div>
</template>

<script>
import Icon from '@/components/Icon.vue'
import ButtonControl from '@/components/ButtonControl.vue'

export default {
  components: {
    Icon,
    ButtonControl
  },
  methods: {
    reload () {
      this.$emit('reload')
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";

.bar-top {
  margin-top: 70px;
  margin-left: 50px;
  display: flex;
  @include laptops {
    margin-left: 30px;
    margin-top: 30px;
  }
}
.button {
  outline: none;
  border: none;
  cursor: pointer;
}
</style>
