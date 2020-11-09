<template>
  <div class="drug">
    <ul class="drug__list">
      <li
        class="drug__item"
        v-for="(drug, index) in drugs"
        :key="drug.id"
      >
        <button
          :class="`drug__button ${drug.color}`"
          @click="`${drug.functionName(index)}`"
        >
          <div class="drug__text">{{ drug.name }}</div>
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    current: {
      type: Number
    },
    sadDrug: {
      type: Number
    },
    happyDrug: {
      type: Number
    },
    heartDrug: {
      type: Number
    },
    drugs: {
      type: Array
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";

.purple {
  background: linear-gradient(266.19deg, #8049C7 0%, #CA57FD 100%);
}
.blue {
  background: linear-gradient(266.19deg, #169AE4 0%, #0CC4FA 100%);
}
.yellow {
  background: linear-gradient(90deg, #FFD748 0.02%, rgba(195, 199, 11, 0.96) 99.97%, #CAC6AB 99.98%, #D3E9E1 99.99%);
}
.drug {
  &__list {
    margin-bottom: 24px;
    display: flex;
    padding-left: 30px;
    padding-right: 20px;
    margin-top: 24px;
    flex-wrap: wrap;
    justify-content: center;
    @include desktops {
      margin-bottom: 0px;
    }
    @include bigLaptops {
      margin-bottom: 0px;
    }
    @include tablets {
      margin-right: -20px;
    }
  }
  &__item {
    margin-bottom: 30px;
    margin-right: 40px;
    display: flex;
    flex: 1;
    justify-content: center;
    &:last-child {
      margin-right: 0px;
      @include tablets {
        margin-right: 40px;
      }
    }
  }
  &__button {
    padding: 27.8px 30px;
    border-radius: 100px;
    min-width: 240px;
    max-width: 300px;
    flex: 1;
    @include bigLaptops {
      padding: 20px 25px;
      max-width: 320px;
    }
    &:hover {
      opacity: 0.9;
    }
  }
  &__text {
    font-size: 28px;
    font-weight: bold;
    color: #fff;
  }
}
</style>
