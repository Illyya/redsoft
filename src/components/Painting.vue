<template>
  <div class="painting">
    <div class="painting__top">
      <div class="painting__img">
        <img :src="pictureAddress" alt="Рождение Венеры" />
      </div>
    </div>
    <div class="painting__bottom">
      <h3 class="painting__title-3 title-3">
        {{ pictureName }}<br />        
      </h3>
      <template v-if="inStock">
        <div class="painting__price-and-purchase">
          <div class="painting__price">
            <span
              v-show="oldPriceShow" 
              class="painting__old-price"
            >
            {{ oldPrice }} $
            </span>
            <span class="painting__new-price">
              {{ newPrice }} $</span>
          </div>
          <Button 
            class="painting__btn" 
            :msg='ButtonMsg'
            :inBasket='inBasket'
            @addToCart='addToCart'
          />
        </div>
      </template>
      <p 
        v-else 
        class="painting__sold-out"
      >
      Продана на аукционе
      </p>
    </div>
  </div>
</template>

<script>
import Button from '@/components/Button';

export default {
  name: "Painting",
  components: {
    Button
  },
  props: {
    ButtonMsg: String,
    pictureName: String,
    oldPriceShow: Boolean,
    oldPrice: String,
    newPrice: String,
    pictureAddress: String,    
    inStock: Boolean,
    inBasket: Boolean
  },
  methods: {
    addToCart() {
      this.$emit('addToCart')
    }
  }
};
</script>

<style lang='scss'>
.painting {
  position: relative;
  border: 1px solid #e1e1e1;
  display: flex;
  flex-direction: column;

  &.active::before {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: #e5e5e571;
    z-index: 100;
  }

  &__top {}
  
  &__bottom {
    padding: 20px 24px 24px 24px;
    display: flex;
    flex-direction: column;
  }

  &__img {
    max-width: 280px;
    max-height: 160px;
  }

  &__title-3 {
    max-width: 220px;
    margin-bottom: 23px;
  }

  &__price-and-purchase {
    display: flex;
    justify-content: space-between;
  }

  &__price {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }

  &__old-price {
    font-weight: 300;
    font-size: 0.875rem;
    color: #A0A0A0;
    text-decoration: line-through;
  }

  &__new-price {
    font-weight: 700;
  }

  &__btn {
  }

  &__sold-out {
    margin-top: 15px;
  }
}
</style>