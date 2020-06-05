<template>
  <div class="FormCard">
    <div class="row d-flex justify-content-center mb-2">
      <img
        src="../assets/GitHub-Mark/PNG/GitHub-Mark-32px.png"
        alt="Github Logo"
      />
      <h4 class="ml-2">Github Overvue</h4>
    </div>
    <form class="form-inline">
      <input
        v-model="username"
        class="mr-1"
        type="text"
        placeholder="Github Username"
      />
      <input @click="getUser" class="btn" type="button" value="SEND" />
    </form>
  </div>
</template>

<script>
import swal from "sweetalert";

export default {
  name: "FormCard",
  data: () => ({
    username: "",
    user: {},
  }),
  methods: {
    renderUserData(response) {
      if (response.message === "Not Found") {
        return swal({
          icon: "error",
          title: "User not found",
          text: "Sorry, we haven't found any user with this username",
        });
      }

      swal({
        icon: "success",
        title: "User has been found",
        text: "Success, we have found an user with this username",
      });

      const {
        name,
        login,
        avatar_url,
        followers,
        following,
        bio,
        repos_url,
      } = response;

      this.user = {
        name,
        login,
        avatar_url,
        followers,
        following,
        bio,
        repos_url,
      };
    },

    getUser() {
      const url = `https://api.github.com/users/${this.username}`;
      fetch(url)
        .then((resp) => resp.json())
        .then((data) => this.renderUserData(data));
    },
  },
};
</script>

<style>
.FormCard {
  padding: 15px;
  background: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 310px;
  border-radius: 24px;
  box-shadow: 1px 1px 1px 1px;
}

.FormCard img {
  width: 28px;
  height: 28px;
}

.FormCard form input[type="text"] {
  padding: 6px;
  border-radius: 4px;
  outline: none;
  border: 1px solid #ccc;
  transition: box-shadow 0.15s;
}

.FormCard form input[type="text"]:focus {
  box-shadow: 0px 0px 2px 0.4px #000;
}

.FormCard input[type="button"] {
  color: #fff;
  background-color: var(--primary-color);
  transition: background 0.2s, color 0.2s;
}

.FormCard input[type="button"]:hover {
  filter: brightness(0.85);
}
</style>
