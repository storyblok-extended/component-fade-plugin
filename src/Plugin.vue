<template>
  <div class="container">
    <h5>intersection observer settings</h5>
    <div class="uk-margin">
      <div>
        <label for="threshold">Threshold</label>
      </div>
      <input class="uk-range" type="range" v-model="model.config.threshold" min="0" max="1" step="0.1">
      <span class="uk-range--label">{{ model.config.threshold }}</span>
    </div>
    <div class="uk-margin">
      <select class="uk-select" v-model="model.type">
        <option disabled value="">Please select one</option>
        <option>classnames</option>
        <option>inline styles</option>
      </select>
    </div>
    <div v-if="model.type === 'classnames'">
      <div>
        <div>
          <label for="effects">Effect name</label>
        </div>
        <input
          class="uk-input"
          type="text"
          @change="onEffectChange"
          id="effects"
          name="effects"
        />
        <p v-if="model.classNames">
          Now you have to create classes: <br />
          <strong>.{{ model.classNames.before }}</strong> <br />
          <strong>.{{ model.classNames.after }} </strong><br />
          with your custom transitions
        </p>
        <h5>here you can define simple transition variables</h5>
        <div class="uk-margin">
          <div>
            <label for="duration">duration (ms)</label>
          </div>
          <input
            v-model="model.transitionConfig.duration"
            class="uk-input"
            type="number"
            id="duration"
            name="duration"
          />
        </div>
        <div class="uk-margin">
          <div>
            <label for="transitionTimingFunction"
              >Transition timing function</label
            >
          </div>
          <select
            class="uk-select"
            v-model="model.transitionConfig.transitionTimingFunction"
            id="transitionTimingFunction"
            name="transitionTimingFunction"
          >
            <option value="ease">ease</option>
            <option>ease-in</option>
            <option>ease-out</option>
            <option>ease-in-out</option>
            <option>linear</option>
          </select>
        </div>
        <div class="uk-margin">
          <div>
            <label for="transitionProperty">Transition property</label>
          </div>
          <input
            disabled
            v-model="model.transitionConfig.transitionProperty"
            class="uk-input"
            type="text"
            id="transitionProperty"
            name="transitionProperty"
          />
        </div>
      </div>
    </div>
    <div v-else-if="model.type === 'inline styles'">
      Here inline styles
    </div>
    <div v-else>
      Choose animation strategy
    </div>
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
        classNames: {
          before: `before-effect-name`,
          after: `after-effect-name`
        },
        transitionConfig: {
          duration: 500,
          transitionProperty: "opacity",
          transitionTimingFunction: "ease"
        },
        config: {
          threshold: 0
        },
        type: "",
        effect: "fade"
      };
    },
    pluginCreated() {
      // eslint-disable-next-line
      console.log(
        "View source and customize: https://github.com/storyblok/storyblok-fieldtype"
      );
      console.log("fade plugin created");
    },
    onEffectChange(event) {
      this.classNames = {
        before: `before-${event.target.value}`,
        after: `after-${event.target.value}`
      };
      this.$emit("changed-model", {
        ...this.model,
        classNames: this.classNames
      });
    }
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

.uk-range--label {
  margin-left: 16px;
}
</style>
