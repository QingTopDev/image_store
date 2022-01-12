<template>
  <div style="display: flex">
    <div>
      <h4 v-if="dateBefore">{{ dateBefore }}</h4>
      <h4 v-if="item.new" class="tag">Nouveauté</h4>
      <h4 v-else-if="item.coomingSoon" class="tag">Prochainement</h4>
      <h4 v-else class="tag">Vanha</h4>
      <br />
      <h3>
        <router-link
          :to="{ name: 'Video', params: { name: item.id } }"
          :item="item"
          ><img width="80%" :src="item.image.source" />
        </router-link
        >
      </h3>
      <h3>{{ item.name }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "videoItem",
  props: ["item"],
};
</script>
