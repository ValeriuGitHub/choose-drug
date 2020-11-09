<template>
  <div class="bar">
    <BarTop
      @reload="reload"
    />
    <Parameters
      :sadDrug="sadDrug"
      :happyDrug="happyDrug"
      :heartDrug="heartDrug"
    />
    <Queue
      :total="total"
      :current="current"
    />
  </div>
</template>

<script>
import BarTop from '@/components/BarTop.vue'
import Parameters from '@/components/Parameters.vue'
import Queue from '@/components/Queue.vue'

export default {
  components: {
    BarTop,
    Parameters,
    Queue
  },
  props: {
    sadDrug: {
      type: Number
    },
    happyDrug: {
      type: Number
    },
    heartDrug: {
      type: Number
    },
    total: {
      type: Number
    },
    current: {
      type: Number
    }
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

.bar {
  display: flex;
  flex-direction: column;
  flex: 0.5;
  max-width: 470px;
  background: linear-gradient(63.53deg, rgba(#2D8550, 0.7) 16.62%, rgba(#5E6EC2, 0.7) 83.38%);
  min-height: 100vh;
  @include bigLaptops {
    flex: 0.3;
  }
}
</style>
