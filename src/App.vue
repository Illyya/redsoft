<template>
  <div id="app" class="app">
    <Header class="app__header" />
    <main class="app__main main">
      <div class="container">
        <div class="main__content">
          <h1 class="main__title-1 title-1">Картины эпохи Возрождения</h1>
          <div class="main__paintings paintings">
            <Painting
              class="paintings__painting"
              :class="{ active : !painting.inStock }"
              v-for="(painting, index) in paintings" :key="index"
              :pictureName="painting.pictureName"
              :oldPriceShow="painting.oldPriceShow"
              :oldPrice="painting.oldPrice"
              :newPrice="painting.newPrice"
              :ButtonMsg="ButtonMsg"
              :pictureAddress="painting.pictureAddress"
              :inStock="painting.inStock"
              :inBasket='painting.inBasket'
              @addToCart='addToCart(painting, index)'
            />
          </div>
        </div>
      </div>
    </main>
    <Footer class="app__footer" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
import Painting from "./components/Painting";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Painting,
  },
  data() {
    return {
      ButtonMsg: "Купить",
      paintings: [
        {
          pictureName: "«Рождение Венеры» Сандро Боттичелли",
          oldPriceShow: true,
          oldPrice: "2 000 000",
          newPrice: "1 000 000",
          pictureAddress: require("./assets/painting-1.png"),
          inStock: true,
          inBasket: Boolean(localStorage.getItem('0'))
        },
        {
          pictureName: "«Тайная вечеря»  Леонардо да Винчи",
          oldPriceShow: false,
          oldPrice: "2 000 000",
          newPrice: "3 000 000",
          pictureAddress: require("./assets/painting-2.png"),
          inStock: true,
          inBasket: Boolean(localStorage.getItem('1'))
        },
        {
          pictureName: "«Сотворение Адама» Микеланджело",
          oldPriceShow: true,
          oldPrice: "6 000 000",
          newPrice: "5 000 000",
          pictureAddress: require("./assets/painting-3.png"),
          inStock: true,
          inBasket: Boolean(localStorage.getItem('2'))
        },
        {
          pictureName: "«Урок анатомии»  Рембрандт",
          oldPriceShow: false,
          oldPrice: "2 000 000",
          newPrice: "1 000 000",
          pictureAddress: require("./assets/painting-4.png"),
          inStock: false,
          inBasket: Boolean(localStorage.getItem('3'))
        },
      ],      
    };
  },
  methods: {
    addToCart(painting, index) {
      painting.inBasket = true;
      localStorage.setItem(index, 'true')
    }
  },
};
</script>

<style lang="scss">
////////////////////////////////////////////////////////////////////////
//resets
////////////////////////////////////////////////////////////////////////

* {
  padding: 0;
  margin: 0;
  border: 0;
}
*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
:focus,
:active {
  outline: none;
}
a:focus,
a:active {
  outline: none;
}

nav,
footer,
header,
aside {
  display: block;
}

html,
body {
  height: 100%;
  width: 100%;
  font-size: 100%;
  line-height: 1.2;
  -ms-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
input,
button,
textarea {
  font-family: inherit;
  font-size: inherit;
}

input::-ms-clear {
  display: none;
}
button {
  cursor: pointer;
}
button::-moz-focus-inner {
  padding: 0;
  border: 0;
}
a {
  color: inherit;
}
a,
a:visited,
a:hover {
  text-decoration: none;
}
ul li {
  list-style: none;
}
img {
  max-width: 100%;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: 400;
}

///////////////////////////////////////////////////////////////////////////////////

$color-1: #f6f3f3;
$color-2: #343030;

body {
  font-family: "Merriweather", "Arial", serif;
  color: $color-2;
  background-color: $color-1;
}

.app {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  &__header {
  }

  &__main {
    flex: 1;
  }

  &__footer {
  }
}

.container {
  max-width: 1216px;
  margin: 0 auto;
}

.title-1 {
  font-weight: 700;
  font-size: 1.5rem;
}

.title-3 {
  font-size: 1.125rem;
}

.main {
  padding: 45px 0;
  &__content {
  }

  &__title-1 {
    margin-bottom: 39px;
  }

  &__paintings {
  }
}

.paintings {
  display: flex;
  justify-content: space-between;

  &__painting {
  }
}
</style>
