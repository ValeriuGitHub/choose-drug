<template>
  <div class="bg-img">
    <div class="bg green-transparent"></div>
    <div class="circle green">
      <div class="circle__welcome">Добро пожаловать в игру</div>
      <h1 class="circle__title">Помоги <span class="uppercase">Фармацевту</span></h1>
      <ButtonControl
        href="#"
        to="/main"
        :className="'circle__link'"
      >
        Начать
      </ButtonControl>
    </div>
  </div>
</template>

<script>
import ButtonControl from '@/components/ButtonControl.vue'

export default {
  components: {
    ButtonControl
  }
}
</script>

<style scoped lang="scss">
@import "@/scss/misc.scss";
@import "@/scss/variables.scss";

.bg {
  width: 100%;
  height: 100vh;
  &-img {
    position: relative;
    background: url("../assets/cover-img.jpg") center / cover no-repeat;
    overflow: hidden;
  }
}
.uppercase {
  text-transform: uppercase;
}
.green-transparent {
  background: linear-gradient(63.53deg, rgba(#2D8550, 0.35) 16.62%, rgba(#5E6EC2, 0.35) 83.38%);
}
.circle {
  position: absolute;
  width: 84vh;
  height: 84vh;
  left: 110px;
  top: -30px;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #fff;
  max-width: 860px;
  max-height: 860px;
  @include laptops {
    left: 50px;
    width: 80vh;
    height: 80vh;
  }
  &__welcome {
    font-size: 35px;
    text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    font-weight: 300;
    width: 50vh;
    text-align: left;
    margin-top: auto;
    opacity: 0.9;
    letter-spacing: 1px;
    @include desktops {
      width: 70%;
      margin-top: 25vh;
      letter-spacing: 0px;
    }
    @include laptops {
      font-size: 28px;
      margin-top: 20vh;
      width: 60vh;
    }
  }
  &__title {
    font-size: 60px;
    width: 50vh;
    text-align: left;
    margin-top: 29px;
    margin-bottom: 11.5vh;
    letter-spacing: 2px;
    @include desktops {
      margin-bottom: 60px;
      width: 70%;
    }
    @include laptops {
      font-size: 50px;
      width: 60vh;
      margin-bottom: 7.5vh;
    }
  }
  &__link {
    color: $blue;
    text-decoration: none;
    outline: none;
    border: none;
    padding: 0px;
    background-color: #fff;
    border-radius: 50px;
    width: 44.18%;
    padding: 23px 0px;
    font-family: Montserrat;
    font-weight: bold;
    font-size: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: 0.5s;
    margin-bottom: 15vh;
    @include laptops {
      margin-bottom: 10vh;
      padding: 15px 70px;
      width: auto;
      font-size: 28px;
    }
    &:hover {
      background-color: rgba(#fff, 0.9);
    }
  }
}
</style>
