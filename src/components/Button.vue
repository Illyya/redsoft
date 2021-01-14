<template>
  <button 
    class="btn" 
    :class="{ 'in-basket' : inBasket, 'loading' : loading }"
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
      inBasketRow: 'В корзине',
      axios: require('axios'),
      loading: false,
    }
  },
  methods: {
    addToCart() {
      if (!this.inBasket) {
        this.loading = true;
        const url = "https://jsonplaceholder.typicode.com/posts/1";
      
        this.axios
          .get(url)
          .then(response => {
            response.status === 200 ? this.$emit('addToCart') : null;
          })
          .catch(error => {
            console.log(error);
          })
          .finally(() => (this.loading = false));
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

  &.loading::after {
    content: '';
    position: absolute;
    display: inline-block;
    width: 20px;
    height: 20px;
    top: 25%;
    left: 45%;
    border: 3px dotted rgb(0, 255, 21);
    border-radius: 50%;
    animation: loading 1s infinite;
    @keyframes loading {
      50% {
        transform: rotate(180deg) scale(1.2);
      }
      100% {
        transform: rotate(360deg) scale(1);
      }
    }
  }
}
</style>