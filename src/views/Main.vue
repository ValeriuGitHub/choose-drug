<template>
  <div class="wrap">
    <Bar
      :sadDrug="sadDrug"
      :happyDrug="happyDrug"
      :heartDrug="heartDrug"
      :current="current"
      :total="total"
      @reload='onReload'
    />
    <main class="main">
      <DraggableCard
        :isMoveUp="isMoveUp"
        :isShowing="isShowing"
        :drugs="drugs"
        :currentDrug="currentDrug"
        :users="users"
        :interactEventBus="interactEventBus"
        :current="current"
        :onGiveSadDrug="onGiveSadDrug"
        :onGiveHappyDrug="onGiveHappyDrug"
        :onGiveHeartDrug="onGiveHeartDrug"
        :hideCard="hideCard"
        :moveUp="moveUp"
      />
      <Drugs
        :drugs="drugs"
        :sadDrug="sadDrug"
        :happyDrug="happyDrug"
        :heartDrug="heartDrug"
        :current="current"
        @giveSadDrug='giveSadDrug'
        @giveHappyDrug='giveHappyDrug'
        @giveHeartDrug='giveHeartDrug'
      />
    </main>
  </div>
</template>

<script>
import users from '@/users.json'
import Bar from '@/components/Bar.vue'
import DraggableCard from '@/components/DraggableCard.vue'
import Drugs from '@/components/Drugs.vue'
import { InteractEventBus } from 'vue2-interact'

const EVENTS = {
  GIVE_SAD_DRUG: 'giveSadDrug',
  GIVE_HAPPY_DRUG: 'giveHappyDrug',
  GIVE_HEART_DRUG: 'giveHeartDrug'
}

export default {
  components: {
    Bar,
    Drugs,
    DraggableCard
  },
  data () {
    return {
      users: users,
      total: users.length,
      current: 0,
      sadDrug: 0,
      happyDrug: 0,
      heartDrug: 0,
      drugs: [
        {
          id: 1,
          color: 'purple',
          name: 'Препарат 1',
          functionName: this.giveSadDrug
        },
        {
          id: 2,
          color: 'blue',
          name: 'Препарат 2',
          functionName: this.giveHappyDrug
        },
        {
          id: 3,
          color: 'yellow',
          name: 'Препарат 3',
          functionName: this.giveHeartDrug
        }
      ],
      currentDrug: null,
      isMoveUp: false,
      isShowing: true,
      interactEventBus: {
        draggedLeft: EVENTS.GIVE_SAD_DRUG,
        draggedUp: EVENTS.GIVE_HAPPY_DRUG,
        draggedRight: EVENTS.GIVE_HEART_DRUG
      }
    }
  },
  watch: {
    current: function (newVal, oldVal) {
      if (newVal >= this.users.length) {
        const data = [
          {
            id: 1,
            drugName: 'Препарат 1',
            drugCount: this.sadDrug
          },
          {
            id: 2,
            drugName: 'Препарат 2',
            drugCount: this.happyDrug
          },
          {
            id: 3,
            drugName: 'Препарат 3',
            drugCount: this.heartDrug
          }
        ]
        this.$router.push({ name: 'Result', params: { results: data, total: this.total } })
      }
    }
  },
  methods: {
    onGiveSadDrug () {
      this.sadDrug++
    },
    onGiveHappyDrug () {
      this.happyDrug++
    },
    onGiveHeartDrug () {
      this.heartDrug++
    },
    onReload () {
      this.current = 0
      this.happyDrug = 0
      this.heartDrug = 0
      this.sadDrug = 0
    },
    giveSadDrug (index) {
      this.currentDrug = index
      InteractEventBus.$emit(EVENTS.GIVE_SAD_DRUG)
    },
    giveHappyDrug (index) {
      this.currentDrug = index
      InteractEventBus.$emit(EVENTS.GIVE_HAPPY_DRUG)
    },
    giveHeartDrug (index) {
      this.currentDrug = index
      InteractEventBus.$emit(EVENTS.GIVE_HEART_DRUG)
    },
    hideCard () {
      setTimeout(() => {
        this.isShowing = false
        this.isMoveUp = false
        this.currentDrug = null
        this.current++
      }, 300)
      setTimeout(() => {
        this.isShowing = true
      }, 400)
    },
    moveUp () {
      this.isMoveUp = true
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";

.wrap {
  display: flex;
  flex: 1;
}
.main {
  display: flex;
  flex: 1;
  flex-direction: column;
  overflow: hidden;
}
</style>
