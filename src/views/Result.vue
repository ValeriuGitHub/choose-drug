<template>
  <div class="result">
    <div class="result-left">
      <ButtonControl
        href="#"
        to="/"
        :className="'circle green'"
      >
        <Icon name="union-white" />
      </ButtonControl>
      <div class="result-info">
        <ul class="result-info__list">
          <li
            class="result-info__item"
            v-for="result in results"
            :key="result.id"
          >
            <div class="result-info__percent">{{ drugPercent(result.drugCount) }}</div>
            <div class="result-info__drug">{{ result.drugName}}</div>
          </li>
        </ul>
        <div class="result__pre-title">Ваш результат:</div>
        <h1 class="result__title">«Что я здесь делаю?»</h1>
        <div class="result__text">Это тестовое задание, так что не будем углубляться в глубины проблем фармацевтов.</div>
        <ButtonControl
          href="#"
          to="/main"
          :className="'gray result__link'"
        >
          Попробовать еще
        </ButtonControl>
      </div>
    </div>
    <div class="result-right">
      <img src="../assets/image.png" alt="image" class="result-right__image">
    </div>
  </div>
</template>

<script>
import Icon from '@/components/Icon.vue'
import ButtonControl from '@/components/ButtonControl.vue'

export default {
  props: {
    results: {
      type: Array
    },
    total: {
      type: Number
    }
  },
  components: {
    Icon,
    ButtonControl
  },
  methods: {
    drugPercent (drugCount) {
      return Math.round(drugCount / this.total * 100) + '%'
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/variables.scss";
@import "@/scss/misc.scss";

.gray {
  background: linear-gradient(90deg, #D9D9D9 0%, #A1A1A1 100%);
}
.result {
  min-height: 100vh;
  display: flex;
  padding: 0px 0px 84px 50px;
  overflow: hidden;
  @include bigLaptops {
    padding: 0px 0px 40px 30px;
  }
  &-left {
    display: flex;
    flex-direction: column;
    flex: 1;
    padding-top: 70px;
  }
  &-right {
    flex: 1.2;
    display: flex;
    justify-content: flex-end;
    @include bigLaptops {
      flex: 1;
    }
    &__image {
      height: 81%;
      width: 100%;
      max-width: 820px;
      margin-left: 20px;
      object-fit: cover;
      object-position: top right;
      @include desktops {
        display: block;
        max-width: 700px;
        height: 100%;
        object-fit: contain;
      }
      @include bigLaptops {
        height: 65%;
        object-fit: contain;
      }
    }
  }
  &-info {
    margin-top: 120px;
    padding-left: 80px;
    display: flex;
    flex-direction: column;
    flex: 1;
    @include laptops {
      margin-top: 50px;
      padding-left: 0px;
    }
    &__list {
      display: flex;
      border-bottom: 2px solid #D9D9D9;
      padding-bottom: 50px;
      margin-bottom: 40px;
      justify-content: center;
    }
    &__item {
      margin-right: 20px;
      flex-basis: 180px;
    }
    &__percent {
      font-size: 48px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: $gray;
    }
    &__drug {
      font-size: 16px;
      line-height: 20px;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      color: $gray;
      font-weight: bold;
      margin: 15px 0px 10px;
    }
  }
  &__pre-title {
    color: $blue;
    font-size: 32px;
    font-weight: 500;
    @include bigLaptops {
      font-size: 28px;
    }
  }
  &__text {
    font-size: 24px;
    line-height: 29px;
    color: $gray;
    max-width: 580px;
    margin-bottom: 20px;
    @include bigLaptops {
      font-size: 20px;
    }
  }
  &__title {
    color: $blue;
    font-size: 40px;
    font-weight: 900;
    margin-top: 0px;
    margin-bottom: 20px;
    @include bigLaptops {
      font-size: 34px;
    }
  }
  &__link {
    font-size: 24px;
    font-weight: bold;
    text-align: center;
    color: #fff;
    width: auto;
    max-width: 270px;
    margin-bottom: 0px;
    margin-top: auto;
    height: auto;
    padding: 15.2px 16px;
    flex: none;
    text-decoration: none;
    border-radius: 100px;
    &:hover {
      opacity: 0.8;
    }
  }
}
</style>
