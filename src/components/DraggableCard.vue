<template>
  <div class="wrap">
    <Vue2InteractDraggable
      v-if="isShowing"
      @draggedLeft="draggedLeft"
      @draggedRight="draggedRight"
      @draggedUp="draggedUp"
      :interact-event-bus-events="interactEventBus"
      :interact-max-rotation="15"
      :interact-out-of-sight-x-coordinate="500"
      :interact-x-threshold="200"
      :interact-y-threshold="200"
      :interact-lock-swipe-down="true"
      class="draggable-card isCurrent"
    >
      <Card
        :isMoveUp="isMoveUp"
        :isShowing="isShowing"
        :drug="drugs[currentDrug]"
        :user="users[current]" />
    </Vue2InteractDraggable>
  </div>
</template>

<script>
import Card from '@/components/Card.vue'
import { Vue2InteractDraggable } from 'vue2-interact'

export default {
  props: {
    onGiveSadDrug: {
      type: Function
    },
    onGiveHappyDrug: {
      type: Function
    },
    onGiveHeartDrug: {
      type: Function
    },
    hideCard: {
      type: Function
    },
    moveUp: {
      type: Function
    },
    user: {
      type: Object
    },
    interactEventBus: {
      type: Object
    },
    drugs: {
      type: Array
    },
    users: {
      type: Array
    },
    isShowing: {
      type: Boolean
    },
    isMoveUp: {
      type: Boolean
    },
    currentDrug: {
      type: Number
    },
    current: {
      type: Number
    }
  },
  components: {
    Card,
    Vue2InteractDraggable
  },
  methods: {
    draggedLeft () {
      this.onGiveSadDrug()
      this.hideCard()
    },
    draggedUp () {
      this.onGiveHappyDrug()
      this.moveUp()
      this.hideCard()
    },
    draggedRight () {
      this.onGiveHeartDrug()
      this.hideCard()
    }
  }
}

</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";

.draggable-card {
  flex: 1;
  display: flex;
  user-select: none;
  pointer-events: none;
  will-change: transform, opacity;
  &.isCurrent {
    pointer-events: auto;
  }
  &.isAnimating {
    transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }
}
.wrap {
  padding-top: 50px;
  min-height: 520px;
  display: flex;
  flex: 1;
  @include desktops {
    padding-bottom: 30px;
  }
}
</style>
