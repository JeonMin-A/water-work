<template>
  <!-- 3. 끌어오기 -->
  <Nav/>
  <Main/>
  <Notice/>
  <Content />
  <Footer />
</template>

<script>
import './assets/css/material-design-iconic-font.css';
// 1. 가져오기
import Nav from './components/Nav.vue'
import Main from './components/Main.vue'
import Notice from './components/Notice.vue'
import Content from './components/Content.vue'
import Footer from './components/Footer.vue'

export default {

  name: 'App',
  components: {
    // 2. 등록
    Nav,
    Main,
    Notice,
    Content,
    Footer
  }
}
</script>

<style>
/* #app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
*{
  font-family: 'NanumSquareNeo-Variable';
}
</style>
