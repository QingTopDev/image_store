<template>
  <div>
    <img width="75%" :src="item.image.source" />
    <div>
      <h2>{{ item.name }}</h2>
      <h4 v-if="item.new" class="tag">Nouveauté</h4>
      <h4 v-else-if="item.coomingSoon" class="tag">Prochainement</h4>
      <h4 v-else class="tag">Vanha</h4>
      <div v-if="item.coomingSoon != true">
        <h2>Price: {{ item.price }} € <button>Acheter</button></h2>
        <h2 style="display: flex; justify-content: center; align-item: center">
          Loan Price: {{ item.loan_price }} €
          <div class="form-group" style="margin-left: 10px; margin-right: 10px">
            <label for="bid"></label>
            <input
              name="bid"
              type="text"
              class="odd_input"
              style="margin: 0px"
            />
          </div>
          <div class="alert-3">
            <button v-on:click="say(item.loan_price)">Prix du prêt</button>
          </div>
        </h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "videoItem",
  props: ["item"],
  el: ".alert-3",
  methods: {
    say: function (message) {
      alert("prix du prêt:" + message);
    },
  },
};
</script>

<style lang="scss">
button {
  border: none;
  margin: 2%;
  background-color: orange;
  padding-left: 10px;
  padding-right: 10px;
  font-size: 20px;
  cursor: pointer;
  transition: background 0.5s;
}

.odd_input {
  width: 50px !important;
}
</style>
