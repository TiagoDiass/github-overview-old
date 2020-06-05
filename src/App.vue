<template>
  <div id="app">
    <div id="appAre" class="container">
      <FormCard />
    </div>
  </div>
</template>

<script>
import FormCard from "./components/FormCard";

export default {
  name: "App",
  components: {
    FormCard
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;400;700&display=swap");

* {
  box-sizing: border-box;
}

:root {
  --primary-color: #1b2631;
}

#app {
  font-family: "Source Sans Pro", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: var(--primary-color);
  text-align: center;
  height: 100vh;
  width: 100%;
  color: var(--primary-color);
}

.container {
  padding: 40px;
  display: flex;
  justify-content: center;
}
</style>
