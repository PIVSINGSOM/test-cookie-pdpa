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
    url: "https://graph.facebook.com/v13.0/1752077728363529/feed?fields=full_picture%2Cmessage%2Cpermalink_url&access_token=EAAHu6zfIL28BALJnG2PkEVTuZAF8EMSclPj3mDtoIiZAQb6xiqxgXOPmVsyLGdD0m9I961K7rZA66HzZBDZCg2lLuAZCZAEaS38TjNLoYZAplesJuEeZAZAatKk1wdwLgZAMHZCyS0FwZC1ButnWM3AmiS0GZBxtZAFlfEbzLqPdfsR8fZBnSyF1x5ytdkpjZAYkQ6jJsKCMUzEWvKArsVAZDZD",
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
