<template>
  <div class="repositoriesArea">
    <div class="repo" v-for="(repo, index) in repositories" :key="index">
      <h3>{{ repo.name }}</h3>

      <p class="repo-description">{{ repo.description }}</p>

      <div class="repo-stats">
        <p>
          <strong>Main language:</strong>
          {{ repo.language }}
        </p>
        <p>
          <i class="fas fa-star"></i>
          Stars: {{ repo.stargazers_count }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "user-repositories",
  props: {
    repositories: Array
  }
};
</script>

<style>
div.repositoriesArea {
  border-radius: 42px;
  width: 40%;
  height: 100%;
  background-color: var(--light-color);
  box-shadow: 0 0 12px rgba(255, 255, 255, 0.2);
  display: grid;
  grid-template-columns: 100%;
  grid-template-rows: repeat(4, 25%);
  grid-row-gap: 6px;
  padding: 26px;
}

.repo {
  padding: 4px;
  width: 100%;
  margin-top: 6px;
  display: grid;
  grid-template-columns: 100%;
  grid-template-rows: 1fr 1fr 1fr;
  grid-row-gap: -3px;
}

.repo h3 {
  font-size: 0.95rem;
  font-weight: 600;
  grid-column: 1/2;
  grid-row: 1/2;
}

.repo p {
  font-size: 0.8rem;
}

.repo .repo-description {
  grid-column: 1/2;
  grid-row: 2/3;
}

.repo .repo-stats {
  margin-top: -5px;
  grid-column: 1/2;
  grid-row: 3/4;

  display: flex;
  justify-content: flex-start;
  height: 50%;
}

.repo .repo-stats p:first-of-type {
  margin-right: 12px;
}

div.repositoriesArea div.repo:nth-child(1) {
  grid-column: 1/2;
  grid-row: 1/2;
}

div.repositoriesArea div.repo:nth-child(2) {
  grid-column: 1/2;
  grid-row: 2/3;
}

div.repositoriesArea div.repo:nth-child(3) {
  grid-column: 1/2;
  grid-row: 3/4;
}

div.repositoriesArea div.repo:nth-child(4) {
  grid-column: 1/2;
  grid-row: 4/5;
}
</style>