<template>
  <div class="param">
    <h2 class="param__title">Параметри:</h2>
    <ul class="param__list">
      <li
        class="param__item"
        v-for="param in params"
        :key=param.id
      >
        <Icon :name="`${param.iconName}`" />
        <div class="param__count">{{ count(param.countType) }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
import Icon from '@/components/Icon.vue'

export default {
  components: {
    Icon
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
    }
  },
  data () {
    return {
      params: [
        {
          id: 1,
          iconName: 'sad-icon',
          countType: 'sadDrug'
        },
        {
          id: 2,
          iconName: 'happy-icon',
          countType: 'happyDrug'
        },
        {
          id: 3,
          iconName: 'heart-icon',
          countType: 'heartDrug'
        }
      ]
    }
  },
  methods: {
    count (countType) {
      switch (countType) {
        case 'sadDrug':
          return this.sadDrug
        case 'happyDrug':
          return this.happyDrug
        case 'heartDrug':
          return this.heartDrug
      }
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";
@import "@/scss/variables.scss";

.param {
  padding-left: 40px;
  padding-right: 20px;
  margin-top: auto;
  margin-bottom: auto;
  @include laptops {
    padding-left: 20px;
  }
  &__title {
    font-size: 36px;
    color: #fff;
  }
  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  &__item {
    width: 185px;
    padding: 10px;
    min-height: 80px;
    background-color: #fff;
    margin-right: 20px;
    margin-bottom: 37px;
    display: flex;
    box-shadow: 0px 0px 50px rgba(131, 42, 64, 0.4);
    border-radius: 40px;
    align-items: center;
    justify-content: space-between;
    @include bigLaptops {
      margin-bottom: 20px;
    }
  }
  &__count {
    font-size: 48px;
    margin-right: 40px;
    font-weight: bold;
    display: flex;
    align-items: center;
    text-align: center;
    color: $gray;
  }
}
</style>
