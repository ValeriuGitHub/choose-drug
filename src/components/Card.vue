<template>
  <div :class="`card isAnimating ${isMoveUp ? 'transformed' : ''}`">
    <div class="card__item">
      <img
        class="card__image"
        :src="require(`@/assets/${user.image}`)"
      />
      <div class="card-under">
        <div
          v-if="drug && isShowing"
          :class="`card-drug ${drug.color}`">
          {{ drug.name }}
        </div>
        <div class="card-under__title">{{ user.name }}, {{ user.age }} років</div>
        <div class="card-under__desc">{{ user.desc }}</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    user: {
      type: Object
    },
    drug: {
      type: Object
    },
    isShowing: {
      type: Boolean
    },
    isMoveUp: {
      type: Boolean
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";
@import "@/scss/variables.scss";

.purple {
  border: 8px solid $purple;
  color: $purple;
  transform: rotate(-30deg);
}
.blue {
  color: $blue-light;
  border: 8px solid $blue-light;
  transform: rotate(-30deg);
}
.yellow {
  color: $yellow;
  border: 8px solid $yellow;
  transform: rotate(30deg);
}
.transformed {
  transform: rotate(-15deg);
}
.card {
  display: flex;
  flex: 1;
  @include laptops {
    justify-content: center;
  }
  &-drug {
    font-size: 52px;
    line-height: 51px;
    display: flex;
    font-weight: bold;
    padding: 0px 30px;
    align-items: center;
    text-align: center;
    height: 120px;
    position: absolute;
    right: 85px;
    bottom: 210px;
    display: flex;
    justify-content: center;
  }
  &__item {
    background: #FFFFFF;
    max-width: 540px;
    box-shadow: 0px 0px 40px rgba(127, 127, 127, 0.4);
    border-radius: 40px;
    margin: auto;
    overflow: hidden;
    will-change: transform, opacity;
    @include desktops {
      max-width: 450px;
    }
    @include laptops {
      width: 500px;
    }
    @include tablets {
      max-width: 400px;
      margin: 0px 30px 20px;
      margin-top: auto;
      margin-bottom: auto;
    }
  }
  &__image {
    width: 100%;
  }
  &-under {
    padding: 15px 50px 30px;
    min-height: 240px;
    @include laptops {
      min-height: 180px;
      padding: 15px 35px 20px;
    }
    &__title {
      font-size: 32px;
      color: $blue;
      font-weight: bold;
      margin-bottom: 10px;
      @include laptops {
        font-size: 26px;
      }
    }
    &__desc {
      font-size: 24px;
      color: $gray;
      @include desktops {
        font-size: 20px;
      }
      @include laptops {
        font-size: 18px;
      }
    }
  }
}
</style>
