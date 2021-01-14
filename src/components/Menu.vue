<template>
  <nav class="menu">
    <ul class="menu__list">
      <li class="menu__li"><a href="#">Каталог</a></li>
      <li class="menu__li"><a href="#">Доставка</a></li>
      <li class="menu__li"><a href="#">Оплата</a></li>
      <li class="menu__li"><a href="#">Контакты</a></li>
      <li class="menu__li"><a href="#">О галерее</a></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Menu",
};
</script>

<style lang='scss'>
.menu {

  &__list {
    display: flex;
    font-size: 0.875rem;
  }

  &__li:not(:last-of-type) {
    margin-right: 48px;
  }
}
</style>