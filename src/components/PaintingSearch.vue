<template>
  <form class="form-painting-search" action="#" method="get">
    <input
      class="form-painting-search__input-painting-search"
      type="search"
      name="painting-search"
      id="painting-search"
      placeholder="Поиск по названию картины"
    />
    <Button 
      class="form-painting-search__btn" 
      :msg='ButtonMsg'
    />    
  </form>
</template>

<script>
import Button from '@/components/Button';

export default {
  name: "PaintingSearch",
  components: {
    Button
  },
  data() {
    return {
      ButtonMsg: 'Найти'
    }
  }
};
</script>

<style lang='scss'>
.form-painting-search {
  display: flex;

  &__input-painting-search {
    padding: 13px 60px 14px 16px;
    border: 1px solid #E1E1E1;
    background-color: transparent;
    transition: 0.2s ease-out;

    &:active,
    &:focus {
      border: 1px solid #B5B5B5;
    }

    &::placeholder {
      font-size: 0.875rem;
    }
  }

  &__btn {
    padding: 13px 36px;
  }
}
</style>