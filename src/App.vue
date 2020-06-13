<template>
  <div id="app">
    <MainForm @userHasBeenFound="userContent = $event" />
  </div>
</template>

<script>
import MainForm from "./components/MainForm.vue";

export default {
  name: "App",

  data: () => ({
    userContent: {}
  }),

  components: { MainForm }
};
</script>

<style>
#app {
  width: 60%;
  height: 400px;
  background-color: #aaa;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
