<template>
  <div>
    <v-container v-if="show" style="height: 100vh;">
      <v-img class="logo" src="../../public/img/logo.png"></v-img>

      <h1>PayUKT</h1>
    </v-container>
  </div>
</template>
<script>
export default {
  name: 'SplashScreen',
  data() {
    return {
      show: true,
    }
  },
  mounted() {
    this.showToggle()
  },
  methods: {
    showToggle() {
      setTimeout(() => {
        this.show = false
      }, 2000)
    },
  },
}
</script>

<style scoped>
div {
  justify-content: center;
}
div img {
  width: 100%;
}

h1 {
  font-weight: 700;
  font-size: 40px;
  line-height: 48px;
  /* identical to box height */

  text-align: center;
  letter-spacing: 0.01em;

  color: #14684e;
}

.logo {
  width: 189px;
  height: 185px;
  margin: 0 auto;
  margin-top: 50%;
}
</style>
