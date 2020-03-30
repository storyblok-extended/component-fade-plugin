<template>
  <div class="container">
    {{ title }}
    </div>
</template>

<script>
export default {
  mixins: [window.Storyblok.plugin],
  data: function() {
    return {
      title: "fading plugin"
    };
  },
  methods: {
    initWith() {
      return {
        // needs to be equal to your storyblok plugin name
        plugin: "ef-component-fade-plugin",
        effect: 'fade'
      };
    },
    pluginCreated() {
      // eslint-disable-next-line
      console.log(
        "View source and customize: https://github.com/storyblok/storyblok-fieldtype"
      );
      console.log("fade plugin created");
    }
  },
  mounted() {
    console.log(this);
  },
  watch: {
    model: {
      handler: function(value) {
        this.$emit("changed-model", value);
      },
      deep: true
    }
  }
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
}
</style>
