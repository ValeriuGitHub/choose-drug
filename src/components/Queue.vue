<template>
  <div class="queue">
    <div class="queue__text">
      Осталось в очереди:
      <div><b>{{ current }}</b>/{{ total }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    current: {
      type: Number
    },
    total: {
      type: Number
    }
  }
}
</script>

<style scoped lang="scss">
.queue {
  background: rgba(#FFFFFF, 0.15);
  padding: 23px 0px;
  &__text {
    font-size: 36px;
    font-weight: 300;
    padding: 0px 10px;
    letter-spacing: 2px;
    color: #fff;
    text-align: center;
  }
}
</style>
