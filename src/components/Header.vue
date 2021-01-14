<template>
  <header class="header">
    <div class="container">
      <div class="header__content">
        <Logo class="header__logo" />
        <Menu class="header__menu" />
        <PaintingSearch class="header__form-painting-search " />
      </div>
    </div>
  </header>
</template>

<script>
import Logo from '@/components/Logo'
import Menu from '@/components/Menu'
import PaintingSearch from '@/components/PaintingSearch'

export default {
  name: "Header",
  components: {
    Logo,
    Menu,
    PaintingSearch
  }
};
</script>

<style lang='scss'>

.header {
  padding: 24px 0;
  border-bottom: 1px solid #E1E1E1;

  &__content {
    display: flex;
    align-items: center;
  }

  &__logo {
    margin-right: 48px;
  }

  &__menu {
  }

  &__form-painting-search {
    flex: 1;
    justify-content: flex-end;
  }

}
</style>