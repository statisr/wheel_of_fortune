<template>
  <transition name="spin" enter-active-class="SpinWheel">
    <div v-if="spin" class="wheel">
      <div class="wheel__inner" v-for="el in content" :key="el">
        <div class="wheel__content">
          {{ el.discont }}
        </div>
      </div>
      <div class="separator">
        <div class="line"></div>
        <div class="line"></div>
        <div class="line"></div>
      </div>
    </div>
  </transition>
  <div class="wheel__circle">
    <div class="wheel__circle-rhombus"></div>
    <span class="wheel__circle-header">Крути, чтобы забрать свой бонус</span>
    <h1 class="wheel__circle-info">Акцион Clan VI</h1>
    <button type="button" @click="spin = !spin" class="wheel__circle-btn">
      Крутить колесо
    </button>
    <span class="wheel__circle-esc" @click="wheelState">Нет, спасибо</span>
    <span v-if="spin">победа</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      spin: true,
      content: [
        { discont: "Бесплатная доставка", deg: "30deg" },
        { discont: "Скидка 15%", deg: "90deg" },
        { discont: "Скидка 10%", deg: "150deg" },
        { discont: "Бесплатная доставка", deg: "210deg" },
        { discont: "Скидка 15%", deg: "270deg" },
        { discont: "Скидка 10%", deg: "330deg" },
      ],
    };
  },
};
</script>

<style  lang="scss">
:root {
  --spin-deg: 3000deg;
}

@keyframes SpinWheel {
  0% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(var(--spin-deg));
  }
}

.wheel {
  animation: SpinWheel 4s forwards;

  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 480px;
  height: 480px;
  background: url(@/assets/Ellipse.svg);
  border-radius: 50%;

  &__inner {
    position: absolute;
    left: 50%;
    bottom: 50%;
    transform-origin: 0 100%;
    width: 0;

    z-index: 999;
    padding-bottom: 174px;
    &:nth-child(1) {
      transform: rotate(0deg);
    }
    &:nth-child(2) {
      transform: rotate(60deg);
    }
    &:nth-child(3) {
      transform: rotate(120deg);
    }
    &:nth-child(4) {
      transform: rotate(180deg);
    }
    &:nth-child(5) {
      transform: rotate(240deg);
    }
    &:nth-child(6) {
      transform: rotate(300deg);
    }
  }
  &__content {
    position: relative;
    right: 30px;

    font-family: Trajan Pro 3;
    font-size: 17px;
    line-height: 22px;
    text-align: center;

    color: #333333;
  }

  .separator {
    position: absolute;
    .line {
      height: 2px;
      width: 480px;
      background: #ecd9da;
      &:nth-child(1) {
        transform: rotate(0deg);
      }
      &:nth-child(2) {
        transform: rotate(125deg);
      }
      &:nth-child(3) {
        transform: rotate(235deg);
      }
      z-index: 1;
    }
  }
}
.wheel__circle {
  position: absolute;
  display: flex;
  justify-content: center;
  flex-direction: column;
  width: 312px;
  height: 312px;
  box-sizing: border-box;
  padding: 0 50px;

  background: #ecd9da;
  border-radius: 50%;
  z-index: 2;
  text-align: center;
  &-rhombus {
    position: absolute;
    left: 143px;
    top: -13px;

    background: inherit;

    height: 26px;
    width: 26px;

    transform: rotate(45deg);
  }
  &-header {
    font-weight: 300;
    font-size: 14px;
    line-height: 18px;
  }
  &-info {
    font-family: Trajan Pro 3;
    font-size: 31.4262px;
    line-height: 40px;
  }
  &-btn {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #333333;
    border-radius: 50px;
    height: 40px;

    font-size: 15px;
    line-height: 18px;

    color: #ffffff;
    border: none;
    outline: none;
  }
  &-esc {
    font-size: 14px;
    line-height: 20px;
    text-decoration-line: underline;

    cursor: pointer;
  }
}
</style>
