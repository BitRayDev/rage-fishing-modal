<template>
  <div class="fishing-modal">
    <div class="fishing-modal__header">
      <p class="fishing-modal__title" :style="{color: titleColor}">{{ title }}</p>
      <div class="fishing-modal__close-button fishing-close-button">
        <img class="fishing-close-button__icon" src="@/assets/fishing-modal/img/icons/close.svg"/>
      </div>
    </div>
    <div class="fishing-modal__row">
      <div class="fishing-modal__image-container">
        <img class="fishing-modal__image" :src="image"/>
      </div>
      <div class="fishing-modal__properties">
        <p class="fishing-modal__property fishing-modal-property">
          <img class="fishing-modal-property__icon" src="@/assets/fishing-modal/img/icons/weight.svg"/>
          {{ weight }} КГ
        </p>
        <p class="fishing-modal__property fishing-modal-property fishing-modal-property_theme_green">
          {{ price }}$
        </p>
      </div>
    </div>
    <p class="fishing-modal__description">{{ description }}</p>
    <div class="fisning-modal__amount-container">
      <p class="fishing-modal__amount-label">Количество</p>
      <div class="fishing-modal__amount-input fishing-amount-input">
        <p class="fishing-amount-input__button" @click="decrementAmount">-</p>
        <input class="fishing-amount-input__input" type="number" v-model="amount"/>
        <p class="fishing-amount-input__button" @click="incrementAmount">+</p>
      </div>
    </div>
    <div class="fishing-modal__buttons">
      <button class="fishing-modal__button fishing-modal__button_theme_blue" @click="payByCashClick">Оплатить наличными</button>
      <button class="fishing-modal__button fishing-modal__button_theme_green" @click="payByCardClick">Оплатить картой</button>
    </div>
  </div>
</template>

<script>
import fishingRod1 from '@/assets/fishing-modal/img/fishing-rods/1.png'

export default {
  name: "FishingModal",
  props: {
    title: String,
    titleColor: String,
    image: String,
    weight: Number,
    price: Number,
    description: String,
  },
  data: function () {
    return {
      amount: 1,
    }
  },
  methods: {
    incrementAmount: function() {
      this.amount++;
    },
    decrementAmount: function() {
      if(this.amount == 0)
        return;

      this.amount--;
    },
    payByCardClick: function() {
      // TODO: Add handler
    },
    payByCashClick: function() {
      // TODO: Add handler
    }
  }
}
</script>

<style lang="scss" scoped>
.fishing-modal {
  display: flex;
  flex-direction: column;
  gap: .5vw;

  width: 16vw;

  box-sizing: border-box;
  padding: 1vw 1vw;

  background: linear-gradient(180deg, rgba(20, 27, 35, 0.98) 0%, rgba(20, 34, 47, 0.98) 100%);

  border: .1vw solid rgba(255, 255, 255, 0.1);
  border-radius: 1vw;

  box-shadow: 0px 0px 1.75vw rgba(0, 164, 255, 0.05);

  * {
    user-select: none;
    -webkit-user-drag: none;
  }

  &__header {
    display: flex;
    justify-content: space-between;
  }

  &__title {
    color: #0A9CFB;

    font-size: .9vw;
    font-weight: 600;
  }

  &__row {
    display: flex;
    gap: .5vw;
  }

  &__image-container {
    display: flex;
    flex-grow: 1;
    align-items: center;
    justify-content: center;

    width: 70%;
    height: 5vw;

    padding: .5vw .75vw;

    background-color: rgba(55, 176, 255, 0.1);

    border-radius: .3vw;

    box-shadow: 0px 0px 32px rgba(0, 164, 255, 0.05);
  }

  &__image {
    height: 100%;
  }

  &__properties {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: .25vw;
  }

  &__description {
    color: #D2D2D6;

    font-size: .75vw;
    font-weight: 700;
  }

  &__amount-label {
    color: #D2D2D6;

    font-size: .75vw;
    font-weight: 700;
  }

  &__buttons {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    gap: .25vw;
  }

  &__button {
    padding: .5vw .75vw;

    color: white;

    font-size: .75vw;
    font-weight: 600;

    border-radius: .5vw;

    border: none;
    outline: none;

    transition: box-shadow 100ms ease-out;

    &_theme {
      &_green {
        background-color: #01C909;

        &:hover {
          box-shadow: 0 0 .5vw #01C909;
        }
      }

      &_blue {
        background-color: #109FFC;

        &:hover {
          box-shadow: 0 0 .5vw #109FFC;
        }
      }
    }
  }
}

.fishing-close-button {
  display: flex;
  align-items: center;
  justify-content: center;

  padding: .2vw;

  background: rgba(55, 176, 255, 0.1);

  border: .1vw solid rgba(255, 255, 255, 0.05);
  border-radius: 6px;

  transition: box-shadow 100ms ease-out;
  &:hover {
    box-shadow: 0 0 .5vw rgba(55, 176, 255, 0.1);
  }

  &__icon {
    height: .75vw;
  }
}

.fishing-modal-property {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: .25vw;

  width: 3vw;

  padding: .4vw;

  color: white;

  font-size: .6vw;
  font-weight: 700;
  letter-spacing: .025vw;

  background: rgba(55, 176, 255, 0.1);
  border-radius: .3vw;

  &__icon {
    height: .6vw;
  }

  &_theme {
    &_green {
      color: #01C909;
      background-color: #173227;
    }
  }
}

.fishing-amount-input {
  display: flex;
  gap: .25vw;

  width: 100%;

  box-sizing: border-box;
  padding: .2vw .4vw;

  background: radial-gradient(50% 50% at 50% 50%, rgba(55, 176, 255, 0.02) 0%, rgba(10, 156, 251, 0.02) 100%);
  border-radius: .5vw;

  &__button {
    display: flex;
    flex-shrink: 0;
    align-items: center;
    justify-content: center;

    width: 1.5vw;
    height: 1.1vw;

    color: white;

    font-size: 1vw;

    border: .1vw solid #D2D2D6;
    border-radius: .3vw;

    cursor: pointer;
  }

  &__input {
    min-width: 0;

    color: white;
    text-align: center;

    font-size: 1vw;

    -webkit-appearance: none;
    background: none;
    border: none;
    outline: none;

    &::-webkit-outer-spin-button, &::-webkit-inner-spin-button {
      -webkit-appearance: none;
    }
  }
}

</style>