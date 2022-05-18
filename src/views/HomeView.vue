<template>
  <div class="home">
    <a
      v-for="item in dataList"
      :key="item.id"
      :href="item.permalink_url"
      target="blank"
    >
      <div style="width: 500px; height: 500px">
        <div style="width: 100%">{{ item.message }}</div>
        <div class="block-image">
          <img :src="item.full_picture" style="width: 100%; height: 100%" />
        </div>
      </div>
    </a>
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
    url: "https://graph.facebook.com/v13.0/1752077728363529/feed?fields=full_picture%2Cmessage%2Cpermalink_url&access_token=",
    token:
      "EAAHu6zfIL28BALJnG2PkEVTuZAF8EMSclPj3mDtoIiZAQb6xiqxgXOPmVsyLGdD0m9I961K7rZA66HzZBDZCg2lLuAZCZAEaS38TjNLoYZAplesJuEeZAZAatKk1wdwLgZAMHZCyS0FwZC1ButnWM3AmiS0GZBxtZAFlfEbzLqPdfsR8fZBnSyF1x5ytdkpjZAYkQ6jJsKCMUzEWvKArsVAZDZD",
    dataList: [],
  }),
  mounted() {
    document.cookie = "name=oeschger; SameSite=None; Secure";
  },
  methods: {
    async onGetFeeds() {
      const { token } = this.$route.query;
      console.log(token);
      const response = await fetch(
        token ? `${this.url}${token}` : `${this.url}${this.token}`
      );
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
