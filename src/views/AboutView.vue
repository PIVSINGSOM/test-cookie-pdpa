<template>
  <div class="about">
    <h1>{{ isAccept ? "Analytics is approve" : "Not approve" }}</h1>
  </div>
</template>

<script>
export default {
  data: () => ({
    isAccept: false,
  }),
  mounted() {
    const self = this;
    setInterval(() => {
      self.cwcIsUserAccept();
    }, 100);
  },
  methods: {
    cwcIsUserAccept() {
      const response = window.cwcIsUserAccept("analytics");
      this.isAccept = response;
    },
  },
};
</script>
