<template>
  <div class="container">
    <div class="uk-margin">
      <label
        ><input v-model="model.enabled" class="uk-checkbox" type="checkbox" />
        Enable transition</label
      >
    </div>
    <template v-if="model.enabled">
      <h5 class="transition-settings__heading">Transition settings</h5>
      <div class="transition-settings">
        <div class="uk-margin">
          <div>
            <label for="duration">Duration (ms)</label>
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
            <label for="delay">Delay (ms)</label>
          </div>
          <input
            v-model="model.transitionConfig.delay"
            class="uk-input"
            type="number"
            id="delay"
            name="delay"
          />
        </div>
        <div class="uk-margin">
              <label
                ><input
                  v-model="model.enabledOnMobile"
                  class="uk-checkbox"
                  type="checkbox"
                  checked
                />
                Enabled on mobile</label
              >
            </div>
        <div>
          <button class="uk-button" @click="toggleMoreOptions">
            {{ moreOptions ? "Less options..." : "More options..." }}
          </button>
        </div>
        <template v-if="moreOptions">
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
          <h5 class="intersection-observer-settings__heading">
            Intersection observer settings
          </h5>
          <div class="intersection-observer-settings">
            <div class="uk-margin">
              <div>
                <label for="threshold">Threshold</label>
              </div>
              <input
                class="uk-range"
                type="range"
                v-model="model.config.threshold"
                min="0"
                max="1"
                step="0.1"
              />
              <span class="uk-range--label">{{ model.config.threshold }}</span>
            </div>
            <div class="uk-margin">
              <label
                ><input
                  v-model="model.config.triggerOnce"
                  class="uk-checkbox"
                  type="checkbox"
                />
                Trigger once</label
              >
            </div>
          </div>
        </template>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  mixins: [window.Storyblok.plugin],
  data: function() {
    return {
      moreOptions: false,
      title: "fading plugin",
    };
  },
  methods: {
    toggleMoreOptions() {
      this.moreOptions = !this.moreOptions;
    },
    initWith() {
      return {
        // needs to be equal to your storyblok plugin name
        plugin: "component-fade-plugin",
        classNames: {
          before: `before-fade`,
          after: `after-fade`,
        },
        transitionConfig: {
          duration: 500,
          transitionProperty: "opacity", // HIDE
          transitionTimingFunction: "ease", // HIDE
          delay: 200,
        },
        config: {
          triggerOnce: true, // HIDE
          threshold: 0.3, // HIDE
          // rootMargin: `0px 0px 0px 0px`
        },
        effect: "fade",
        enabledOnMobile: true,
        enabled: false,
      };
    },
    pluginCreated() {
      // eslint-disable-next-line
      console.log(
        "View source and customize: https://github.com/storyblok/storyblok-fieldtype"
      );
    },
  },
  watch: {
    model: {
      handler: function(value) {
        this.$emit("changed-model", value);
      },
      deep: true,
    },
    // rootMargin: {
    //   handler: function(value) {
    //     console.log(value);
    //     this.model.config.rootMargin = `${value[0]}px ${value[1]}px ${value[2]}px ${value[3]}px`
    //   }
    // }
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
}

.link:hover {
  color: #09b3af;
}

.uk-range--label {
  margin-left: 16px;
}

.intersection-observer-settings__heading {
  margin: 16px 0 0 0;
  padding: 0;
}

.intersection-observer-settings {
  border: 1px outset #e9e9e9;
  padding: 16px;
}

.transition-settings__heading {
  margin: 16px 0 0 0;
  padding: 0;
}

.transition-settings {
  border: 1px outset #e9e9e9;
  padding: 16px;
}
</style>
