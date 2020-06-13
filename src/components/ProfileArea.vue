<template>
  <div class="profileArea">
    <img :src="userContent.avatar_url" alt="User profile picture" />
    <h3 class="mt-1 mb-1">{{ userContent.name }}</h3>

    <div id="userBio">
      <p>{{ userContent.bio }}</p>
    </div>

    <div id="userStats">
      <p>
        <i class="fas fa-archive"></i>
        Repositories: {{userContent.public_repos}}
      </p>
      <p>
        <i class="fas fa-user-friends"></i>
        Followers: {{userContent.followers}}
      </p>
    </div>

    <a target="_blank" :href="userContent.html_url">VIEW PROFILE</a>
  </div>
</template>

<script>
export default {
  props: {
    userContent: Object
  }
};
</script>

<style>
div.profileArea {
  border-radius: 42px;
  width: 35%;
  height: 95%;
  background-color: var(--light-color);
  box-shadow: 0 0 12px rgba(255, 255, 255, 0.2);

  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  padding: 20px;
}

div.profileArea img {
  width: 135px;
  height: 135px;
  border-radius: 50%;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
}

div.profileArea #userBio {
  display: flex;
  justify-content: center;
  padding: 6px;
}

div.profileArea #userStats {
  width: 100%;
  padding: 6px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  font-size: 0.8rem;
}

div.profileArea #userStats i {
  color: var(--secondary-color);
}

div.profileArea a {
  background: #4b6cb7; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to right,
    #182848,
    #4b6cb7
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to right,
    #182848,
    #4b6cb7
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  padding: 8px;
  width: 100%;
  color: #fff;
  border-radius: 6px;
  font-weight: 600;
  text-align: center;
  text-decoration: none;
}

div.profileArea a:hover {
  background: #4b6cb7; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to left,
    #182848,
    #4b6cb7
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to left,
    #182848,
    #4b6cb7
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

div.profileArea a:active {
  box-shadow: 0 0 8px #4b6cb7;
}
</style>