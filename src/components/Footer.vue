<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__content">
        <Logo class="footer__logo" /> 
        <Menu class="footer__menu" />          
        <div class="footer__contact-number">
          <a href="tel:+74955555555">+7 (495) 555-55-55</a>
        </div>
        <div class="footer__address">
          <p>г. Москва, ул. Расплетина, 24</p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import Logo from '@/components/Logo';
import Menu from '@/components/Menu';

export default {
  name: "Footer",
  components: {
    Logo,
    Menu
  }
};
</script>

<style lang='scss'>
.footer {
  padding: 24px 0;
  font-size: 0.875rem;
  background-color: #ECE9E9;

  &__content {
    display: flex;
    align-items: center;
}

  &__logo {
    margin-right: 48px;
  }

  &__menu {
  }

  &__contact-number {
    display: flex;
    align-items: center;
    margin-left: auto;
    margin-right: 51px;

    &::before {
      content: '';
      width: 14px;
      height: 14px;
      display: inline-block;
      margin-right: 9px;
      background: url(./../assets/phone.svg);
    }
  }

  &__address {
    display: flex;
    align-items: center;

    &::before {
      content: '';
      width: 10.14px;
      height: 14px;
      display: inline-block;
      margin-right: 9px;
      background: url(./../assets/address.svg);
    }
  }
}
</style>