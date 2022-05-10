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
  methods: {
    cwcIsUserAccept() {
      const response = window.cwcIsUserAccept('analytics')
      this.isAccept = response 
    },
  },
};
</script>
