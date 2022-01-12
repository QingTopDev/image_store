<template>
  <div class="app">
    <h1>VideoStore</h1>
    <p class="description">
      Bienvenue dans le VideoStore ! Nous vous proposons une liste de divers
      vidéos, avec des nouveautées tout les jours.
    </p>

    <div style="display: flex;">
      <div style="max-width: 50%;">
        <h2>Nouveauté</h2>
        <section v-for="item in videoList" :key="item.name">
          <br v-if="item.new === true" />
          <VideoItem v-if="item.new === true" :item="item"/>
        </section>
        <br/>

        <br />
      </div>
      <div style="max-width: 50%;">
        <h2>Prochainement</h2>
        <section v-for="item in videoList" :key="item.name">
          <br v-if="item.coomingSoon === true" />
          <VideoItem v-if="item.coomingSoon === true" :item="item" style="height: 100%" />
        </section>
        <br/>
      </div>
    </div>

    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import VideoItem from "../components/VideoItem.vue";

export default {
  name: "app",
  components: {
    VideoItem,
  },
  data() {
    const currentDate = new Date();
    const dateAgo = new Date().setDate(currentDate.getDate() - 30);
    return {
      currentDate: new Date(),
      dateBefore: new Date(dateAgo),
      videoList: [
        {
          id: "0",
          name: "Vidéo de chat",
          price: 25,
          loan_price: 12,
          image: {
            source: "assets/cat.jpg",
          },
          date: new Date(2013, 10, 7),
          new: false,
          coomingSoon: false,
        },
        {
          id: "1",
          name: "Test",
          price: 0.45,
          loan_price: 0.1,
          image: {
            source: "assets/NeonDrive.jpg",
          },
          date: new Date(2022, 0, 1),
          new: false,
          coomingSoon: false,
        },
        {
          id: "2",
          name: "How to make money when you are student in 2021",
          price: 5.99,
          loan_price: 2.3,
          image: {
            source: "assets/joris.jpg",
          },
          date: new Date(2021, 10, 3),
          new: false,
          coomingSoon: false,
        },
        {
          id: "3",
          name: "Social Game",
          price: 15,
          loan_price: 3,
          image: {
            source: "assets/nico.jpg",
          },
          date: new Date(2021, 11, 15),
          new: false,
          coomingSoon: false,
        },
        {
          id: "4",
          name: "YouTube rewind 2021",
          price: 80,
          loan_price: 22,
          image: {
            source: "assets/yt.jpg",
          },
          date: new Date(2022, 0, 31),
          new: false,
          coomingSoon: false,
        },
        {
          id: "5",
          name: "Revenge (CREEPER AWW MEN)",
          price: 999.99,
          loan_price: 128,
          image: {
            source: "assets/creeper.jpg",
          },
          date: new Date(2018, 4, 21),
          new: false,
          coomingSoon: false,
        },
        {
          id: "6",
          name: "Bebou 🥺 ?",
          price: 9500,
          loan_price: 2000,
          image: {
            source: "assets/bebou.jpg",
          },
          date: new Date(2015, 5, 13),
          new: false,
          coomingSoon: false,
        },
      ],
    };
  },
  computed: {
    copyright() {
      this.videoList.forEach((item) => {
        if (this.dateBefore < item.date) {
          item.new = true;
        }
        if (new Date() < item.date) {
          console.log(this.currentDate + "//" + item.date);
          item.new = false;
          item.coomingSoon = true;
        }
      });
      const currentYear = new Date().getFullYear();
      return `Copyright VideoStore ${currentYear}`;
    },
  },
  methods: {},
};
</script>

<style lang="scss"></style>
