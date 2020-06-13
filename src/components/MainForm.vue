<template>
  <div class="form">
    <div class="form-header">
      <img src="../assets/images/GitHub-Mark-64px.png" alt="Github Logo" />
      <h2>Github Overview</h2>
    </div>
    <div class="input-area">
      <input
        @keyup.enter="fetchUser"
        v-model="githubUsername"
        type="text"
        placeholder="Github Username"
      />
      <button @click="fetchUser">SEND</button>
    </div>
  </div>
</template>

<script>
import swal from "sweetalert";

export default {
  name: "main-form",
  data: () => ({
    githubUsername: "",
    userContent: {}
  }),

  methods: {
    fetchUser() {
      const url = `https://api.github.com/users/${this.githubUsername}`;
      fetch(url)
        .then(response => response.json())
        .then(data => {
          if (data.message && data.message === "Not Found") {
            swal({
              title: "Ops...",
              text: "We haven't found any user with this username",
              icon: "error",
              button: "Okay"
            });
          } else {
            this.userContent = data;
            swal({
              title: "Good job",
              text: "We have found an user with this username",
              icon: "success",
              button: "Nice, thanks"
            });

            this.$emit("userHasBeenFound", this.userContent);
          }
        });
    }
  }
};
</script>

<style scoped>
.form {
  padding: 24px;
  margin-top: 24px;
  width: 40%;
  min-width: 350px;
  height: 180px;
  background-color: var(--light-color);
  border-radius: 40px;
  box-shadow: 0 0 12px rgba(255, 255, 255, 0.2);
  grid-column: 2/3;
  grid-row: 1/2;
}

.form .form-header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 6px;
}

.form .form-header img {
  width: 50px;
  margin-right: 12px;
  opacity: 0.7;
}

.form .form-header h2 {
  font-size: 1.7rem;
  font-weight: 600;
}

.form .input-area {
  padding: 16px;
  display: flex;
  justify-content: space-between;
}

.form .input-area input {
  padding: 6px;
  border-radius: 6px;
  outline: 0;
  border: none;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.3);
  width: 70%;
  transition: box-shadow 0.1s;
}

.form .input-area input:focus {
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
}

.form .input-area button {
  padding: 8px;
  border: none;
  outline: 0;
  border: 1px solid var(--primary-color);
  background-color: var(--primary-color);
  border-radius: 6px;
  color: var(--light-color);
  width: 25%;
  transition: filter 0.15s;
}

.form .input-area button:hover {
  filter: brightness(0.95);
  cursor: pointer;
}

.form .input-area button:active {
  box-shadow: 0 0 5px rgba(27, 38, 49, 0.4);
  cursor: pointer;
}
</style>