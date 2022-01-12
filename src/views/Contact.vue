<template>
  <div class="contact_app">
    <h1>VideoStore</h1>

    <h3>{{ address }}</h3>
    <h3>{{ email }}</h3>
    <h3>{{ phone }}</h3>

    <form action="" @submit="checkForm">
      <div class="container">
        <div class="label_container">
          <label for="name">Votre nom</label>
        </div>
        <div class="input_container">
          <input id="name" v-model="name" type="text" name="name" />
        </div>
      </div>
      <div class="container">
        <div class="label_container">
          <label for="first_name">Votre prénom</label>
        </div>
        <div class="input_container">
          <input id="first_name" v-model="first_name" type="text" name="firstname" />
        </div>
      </div>
      <div class="container">
        <div class="label_container">
          <label for="mail">Votre Email</label>
        </div>
        <div class="input_container">
          <input id="mail" v-model="mail" type="mail" name="mail" />
        </div>
      </div>

      <div class="container">
        <div class="label_container">
          <label for="message">Votre Message</label>
        </div>
        <div class="input_container">
          <textarea
            id="message"
            v-model="message"
            name="message"
            rows="5"
          ></textarea>
        </div>
      </div>
      <button>Envoyer</button>
    </form>

    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "contact",
  data() {
    return {
      name: null,
      mail: null,
      message: null,
      address: "325 route de la buse, Avignon, France",
      email: "contact@video-store.com",
      phone: "01 32 84 32 00",
    };
  },
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear();
      return `Copyright VideoStore ${currentYear}`;
    },
  },
  methods: {
    checkForm: function (e) {
      if (this.name && this.mail && this.message) {
        alert("Message envoyé");
        return true;
      }
      if (!this.firstname) {
        alert("Nom prénom valide");
      }
      if (!this.name) {
        alert("Nom non valide");
      }
      if (!this.mail) {
        alert("Email non valide");
      }
      if (!this.message) {
        alert("Message non valide");
      }
      e.preventDefault();
    },
  },
};
</script>.

<style lang="scss">
input,
textarea {
  width: 100%;
  border-color: orange;
  border-radius: 5px;
  text-align: center;
}
.container {
  display: flex;
  width: 100%;
  margin-top: 30px;
  text-align: center;
}
.label_container {
  width: 30%;
  text-align: right;
  margin-right: 30px;
}
.input_container {
  width: 40%;
  margin-right: 50px;
}

label {
  font-size: 20px;
}

input {
  font-size: 20px;
}

textarea {
  font-size: 18px;
}

button {
  width: 150px;
  margin-top: 20px;
  padding: 5px  !important;
  background-color: orangered !important;
  color: #ffffff;
}
</style>
