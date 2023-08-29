<script >
import TheHeader from "./components/TheHeader.vue";
import TheMain from "./components/TheMain.vue";


export default {
  components: {
    TheHeader,
    TheMain,
  }

}


</script>

<template>
  <header>
    <TheHeader></TheHeader>
  </header>
  <main class="main-section">
    <TheMain></TheMain>
  </main>
</template>

<style lang="scss">
.main-section {
  margin-top: 100px;

}

body {
  background-color: #1B1B1B;
}
</style>
