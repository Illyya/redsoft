<template>
  <div class="logo">
    <div class="logo__img">
      <img src="./../assets/logo.png" alt="The Famous" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Logo'
};
</script>

<style lang='scss'>

.logo {

	&__img {
    max-width: 48px;
    max-height: 48px;
  }
}
</style>