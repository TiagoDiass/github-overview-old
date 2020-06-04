<template>
  <div class="FormCard">
    <div class="row d-flex justify-content-center mb-2">
      <img src="../assets/GitHub-Mark/PNG/GitHub-Mark-32px.png" alt="Github Logo" />
      <h4 class="ml-2">Github Overvue</h4>
    </div>
    <form class="form-inline">
      <input v-model="username" class="mr-1" type="text" placeholder="Github Username" />
      <input @click="getUser" class="btn" type="button" value="SEND" />
    </form>
  </div>
</template>

<script>
export default {
  name: "FormCard",
  data: () => ({
    username: ""
  }),
  methods: {
    getUser() {
      const url = `https://api.github.com/users/${this.username}`;
      fetch(url)
        .then(resp => resp.json())
        .then(data => {
          if (data.message === "Not Found") {
            return console.log("Nenhum usuário foi encontrado com este ID");
          }

          //CHAMAR AS FUNÇÕES COM OS DADOS RECEBIDOS AQUI
        });
    }
  }
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