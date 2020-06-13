<template>
  <div id="app">
    <MainForm @userHasBeenFound="userContent = $event" />

    <div id="userContent" v-if="userContent">
      <ProfileArea :userContent="userContent" />

      <UserRepositories :repositories="userBestRepos" />
    </div>
  </div>
</template>

<script>
import MainForm from "./components/MainForm.vue";
import ProfileArea from "./components/ProfileArea.vue";
import UserRepositories from "./components/UserRepositories.vue";

export default {
  name: "App",

  components: { MainForm, ProfileArea, UserRepositories },

  data: () => ({
    userContent: "",
    userBestRepos: []
  }),

  methods: {
    setUserBestRepos() {
      fetch(this.userContent.repos_url)
        .then(response => response.json())
        .then(repositories => {
          //That's gonna sort our array based on the amount of the stars of each repository
          repositories.sort((repo1, repo2) => {
            if (repo1.stargazers_count < repo2.stargazers_count) return 1;

            if (repo1.stargazers_count > repo2.stargazers_count) return -1;

            return 0;
          });

          //We're gonna take the top 4 repos of the user, the ones that have more stars than the other ones
          for (let i = 0; i <= 3; i++) {
            this.userBestRepos.push(repositories[i]);
          }
        });
    }
  },

  watch: {
    userContent() {
      if (this.userContent) {
        this.userBestRepos = [];
        this.setUserBestRepos();
      }
    }
  }
};
</script>

<style>
#app {
  width: 70%;
  height: 700px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: repeat(3, 33%);
}

#app i {
  color: var(--secondary-color);
}

div#userContent {
  width: 100%;
  height: 100%;
  grid-column: 1/4;
  grid-row: 2/4;

  display: flex;
  justify-content: space-evenly;
}
</style>
