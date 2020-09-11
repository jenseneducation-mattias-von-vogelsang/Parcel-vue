<template>
  <div>
    <div v-if="!checkNodeEnv" class="square"><h1>Dev mode</h1></div>
    <img v-if="checkNodeEnv" :src="imageBytes" alt="cat" />
    <h1 v-if="checkNodeEnv == null">You're doing something wrong, pal</h1>
  </div>
</template>
<script>
export default {
  name: 'Gif',
  data() {
    return {
      imageBytes: '',
    };
  },
  computed: {
    checkNodeEnv() {
      if (process.env.NODE_ENV == 'production') {
        return true;
      } else if (process.env.NODE_ENV == 'development') {
        return false;
      } else {
        return null;
      }
    },
  },
  methods: {
    async fetchAPI() {
      let self = this;
      await fetch('https://placekitten.com/g/100/100')
        .then((response) => response.blob())
        .then((blob) => {
          const reader = new FileReader();
          reader.onload = function() {
            self.imageBytes = this.result; // <--- `this.result` contains a base64 data URI
          };
          reader.readAsDataURL(blob);
        });
    },
  },
  created() {
    console.log(process.env.NODE_ENV);
  },
  mounted() {
    this.fetchAPI();
  },
};
</script>
<style scoped>
.square {
  height: 100px;
  width: 100px;
  background: salmon;
}
</style>
