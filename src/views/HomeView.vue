<template>
  <div class="home">
    <div
      v-for="item in dataList"
      :key="item.id"
      style="width: 500px; height: 500px"
    >
      <div>{{ item.message }}</div>
      <div class="block-image">
        <img :src="item.full_picture" style="width: 100%; height: 100%" />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
  created() {
    this.onGetFeeds();
  },

  data: () => ({
    url: "https://graph.facebook.com/v13.0/1752077728363529/feed?fields=full_picture%2Cmessage%2Cpermalink_url&access_token=EAAHu6zfIL28BAFBMcozYFLmFLYJOS40kH1fwFOOSyjyMvh5bBe4oNWcg1ZCZBZAIDx1GvcGCfzUWl8J9qoAPSvEbtZA81bqnGNJwCZCpNnmcRvPcSD6o63ZACP4HL9kpDLGNy2NLwzR5kyhjwIFsE3ZCzYzAppKuQbjFiosRqOWkZBisRGnwXZAPjUubTx2KyXQ7ZBn7EJZAi2Ncatpqb4bGsFz",
    dataList: [],
  }),
  methods: {
    async onGetFeeds() {
      const response = await fetch(this.url);
      const data = await response.json();
      this.dataList = data.data;
    },
  },
};
</script>

<style scoped>
.block-image {
  width: 500px;
  height: 300px;
}
</style>
