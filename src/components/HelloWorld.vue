<template>
  <div class="hello-world">
    <link
      v-for="(cssUrl, index) in cssUrls"
      :key="index"
      :href="cssUrl"
      rel="stylesheet"
    />
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      default: 'Hello World!',
    },
    cssUrls: {
      type: Array,
      default: () => [],
    },
  },
  mounted() {
    this.cssUrls.forEach((cssUrl) => {
      let link = document.createElement('link');
      link.rel = 'stylesheet';
      link.href = cssUrl;
      this.$el.appendChild(link);
    });
  },
};
</script>
