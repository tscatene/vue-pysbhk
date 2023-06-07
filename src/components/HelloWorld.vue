<template>
  <div class="hello-world">
    <h2 class="comment-status">{{ msg }}</h2>
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
      type: String,
      default: '',
    },
  },
  data() {
    return {
      parsedCssUrls: [],
    };
  },
  watch: {
    cssUrls: {
      immediate: true,
      handler(newValue) {
        if (newValue) {
          try {
            console.log(newValue);
            this.parsedCssUrls = JSON.parse(newValue);
          } catch (e) {
            this.parsedCssUrls = [];
          }
        }
      },
    },
  },
  mounted() {
    console.log('test', this);
    this.parsedCssUrls.forEach((cssUrl) => {
      let link = document.createElement('link');
      link.rel = 'stylesheet';
      link.href = cssUrl;

      this.$el.appendChild(link);
    });
  },
};
</script>
