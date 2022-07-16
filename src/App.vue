<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@100;300;400&family=Roboto:wght@400;500;700;900&display=swap");
/* reset css */
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}

*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

h1,
h2,
h3,
h4,
h5,
h6,
p {
  margin: 0px;
  padding: 0px;
}

ul,
ol,
li {
  list-style: none;
  margin: 0px;
  padding: 0px;
}

a,
a:hover,
a:focus {
  text-decoration: none;
  outline: none;
}

input {
  padding: 0;
}

img {
  width: 100%;
  height: 100%;
  display: block;
}
#app {
  font-family: "Noto Sans TC", sans-serif;
  font-family: "Roboto", sans-serif;
}
</style>
