<template>
  <button 
    class="btn" 
    :class="{ 'in-basket' : inBasket }"
    @click="addToCart"
  >
    {{ !inBasket ? msg : inBasketRow}}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    msg: String,
    inBasket: Boolean
  },
  data() {
    return {
      inBasketRow: 'В корзине'
    }
  },
  methods: {
    addToCart() {
      if (this.msg === "Купить") {
        const url = "https://jsonplaceholder.typicode.com/posts/1";

        fetch(url).then((response) => {
          response.ok ? this.$emit('addToCart') : null;          
        });
      }
    },
  },
};
</script>

<style lang='scss'>
.btn {
  position: relative;
  padding: 13px 27px;
  font-size: 0.875rem;
  color: #ffffff;
  background-color: #403432;
  transition: 0.2s ease-out;

  &:hover {
    background-color: #776763;
  }

  &:disabled {
    background-color: #c1b4b1;
  }

  &.in-basket {
    padding: 13px 9px 13px 32px;
    background-color: #5b3a32;

    &::before {
      content: '';
      position: absolute;
      display: inline-block;
      width: 20px;
      height: 20px;
      top: 15px;
      left: 10px;
      background: url('./../assets/arrow.svg') no-repeat;
    }
  }
}
</style>