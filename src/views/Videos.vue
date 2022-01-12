<template>
  <div class="app">
    <h1>VideoStore</h1>
    <button v-on:click="setViewType(0)">Tout</button>
    <button v-on:click="setViewType(1)">Nouvelle</button>
    <button v-on:click="setViewType(2)">Bientôt disponible</button>
    <div style="width: 100%; display: flex; flex-wrap: wrap">
      <section v-for="item in realList" :key="item.name" style="width: 50%">
        <br width="20%" />
        <VideoItem :item="item" :type="viewType" />
      </section>
    </div>
    <br width="20%" />

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
    const viewType = 0;
    const currentDate = new Date();
    const dateAgo = new Date().setDate(currentDate.getDate() - 30);
    return {
      viewType: viewType,
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
          new: true,
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
          new: true,
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
          new: false,
          coomingSoon: true,
        },
        {
          id: "5",
          name: "Revenge (CREEPER AWW MEN)",
          price: 999.99,

          loan_price: 128,

          image: {
            source: "assets/creeper.jpg",
          },
          new: false,
          coomingSoon: false,
        },
        {
          id: "6",
          name: "Bebou",
          price: 9500,

          loan_price: 2000,
          image: {
            source: "assets/bebou.jpg",
          },
          new: true,
          coomingSoon: false,
        },
      ],
    };
  },
  mounted() {},
  computed: {
    realList() {
      if (this.viewType == 0) return this.videoList;
      else if (this.viewType == 1)
        return this.videoList.filter((video) => video.new == true);
      else return this.videoList.filter((video) => video.coomingSoon == true);
    },
    copyright() {
      this.videoList.forEach((item) => {
        if (this.dateBefore < item.date) {
          item.new = true;
        }
        if (new Date() < item.date) {
          item.new = false;
          item.coomingSoon = true;
        }
      });
      const currentYear = new Date().getFullYear();
      return `Copyright VideoStore ${currentYear}`;
    },
  },
  methods: {
    setViewType(type) {
      this.viewType = type;
    },
  },
};
</script>

<style lang="scss"></style>
