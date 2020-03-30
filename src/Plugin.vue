<template>
  <div class="container">
    <div class="button-group">
      <button :class="{ active: breakpoint === 's' }" v-on:click="setBreakpoint('s')">All (s)</button>
      <button :class="{ active: breakpoint === 'm' }" v-on:click="setBreakpoint('m')">Medium</button>
      <button :class="{ active: breakpoint === 'l' }" v-on:click="setBreakpoint('l')">Large</button>
    </div>
    <div v-if="breakpoint === 's'" class="box-model s">
      <div class="box-model__margin relative">
        <span class="box-model__title">margin</span>
        <div class="box-model__margin-top">
          <select class="select-breakpoint" v-if="model.s" v-model="model.s.mt">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-bottom">
          <select class="select-breakpoint" v-if="model.s" v-model="model.s.mb">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-left">
          <select class="select-breakpoint" v-if="model.s" v-model="model.s.ml">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-right">
          <select class="select-breakpoint" v-if="model.s" v-model="model.s.mr">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__padding relative">
          <span class="box-model__title">padding</span>
          <div class="box-model__padding-top">
            <select class="select-breakpoint" v-if="model.s" v-model="model.s.pt">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-bottom">
            <select class="select-breakpoint" v-if="model.s" v-model="model.s.pb">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-left">
            <select class="select-breakpoint" v-if="model.s" v-model="model.s.pl">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-right">
            <select class="select-breakpoint" v-if="model.s" v-model="model.s.pr">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__dimensions relative">
            content
          </div>
        </div>
      </div>
    </div>

    <div v-if="breakpoint === 'l'" class="box-model l">
      <div class="box-model__margin relative">
        <span class="box-model__title">margin</span>
        <div class="box-model__margin-top">
          <select class="select-breakpoint" v-if="model.l" v-model="model.l.mt">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-bottom">
          <select class="select-breakpoint" v-if="model.l" v-model="model.l.mb">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-left">
          <select class="select-breakpoint" v-if="model.l" v-model="model.l.ml">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-right">
          <select class="select-breakpoint" v-if="model.l" v-model="model.l.mr">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__padding relative">
          <span class="box-model__title">padding</span>
          <div class="box-model__padding-top">
            <select class="select-breakpoint" v-if="model.l" v-model="model.l.pt">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-bottom">
            <select class="select-breakpoint" v-if="model.l" v-model="model.l.pb">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-left">
            <select class="select-breakpoint" v-if="model.l" v-model="model.l.pl">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-right">
            <select class="select-breakpoint" v-if="model.l" v-model="model.l.pr">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__dimensions relative">
            content
          </div>
        </div>
      </div>
    </div>

    <div v-if="breakpoint === 'm'" class="box-model m">
      <div class="box-model__margin relative">
        <span class="box-model__title">margin</span>
        <div class="box-model__margin-top">
          <select class="select-breakpoint" v-if="model.m" v-model="model.m.mt">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-bottom">
          <select class="select-breakpoint" v-if="model.m" v-model="model.m.mb">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-left">
          <select class="select-breakpoint" v-if="model.m" v-model="model.m.ml">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__margin-right">
          <select class="select-breakpoint" v-if="model.m" v-model="model.m.mr">
            <option :key="option" v-for="option in options" :value="option">{{
              option
            }}</option>
          </select>
        </div>
        <div class="box-model__padding relative">
          <span class="box-model__title">padding</span>
          <div class="box-model__padding-top">
            <select class="select-breakpoint" v-if="model.m" v-model="model.m.pt">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-bottom">
            <select class="select-breakpoint" v-if="model.m" v-model="model.m.pb">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-left">
            <select class="select-breakpoint" v-if="model.m" v-model="model.m.pl">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__padding-right">
            <select class="select-breakpoint" v-if="model.m" v-model="model.m.pr">
              <option :key="option" v-for="option in options" :value="option">{{
                option
              }}</option>
            </select>
          </div>
          <div class="box-model__dimensions relative">
            content
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mixins: [window.Storyblok.plugin],
  data: function() {
    return {
      options: ["-", "0", "xs", "s", "m", "l", "xl", "xxl"],
      breakpoint: 's',
    };
  },
  methods: {
    initWith() {
      return {
        // needs to be equal to your storyblok plugin name
        plugin: "spacing-plugin",
        s: {
          pt: "-",
          pb: "-",
          pl: "-",
          pr: "-",
          mt: "-",
          mb: "-",
          ml: "-",
          mr: "-"
        },
        m: {
          pt: "-",
          pb: "-",
          pl: "-",
          pr: "-",
          mt: "-",
          mb: "-",
          ml: "-",
          mr: "-"
        },
        l: {
          pt: "-",
          pb: "-",
          pl: "-",
          pr: "-",
          mt: "-",
          mb: "-",
          ml: "-",
          mr: "-"
        }
      };
    },
    setBreakpoint(bp) {
      this.breakpoint = bp;
    },
    pluginCreated() {
      // eslint-disable-next-line
      console.log(
        "View source and customize: https://github.com/storyblok/storyblok-fieldtype"
      );
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
select {
  text-align: center;
  text-align-last: center;
}
option {
  text-align: left;
}


.active {
  background-color: #efefef;
}

.container {
  display: flex;
  flex-direction: column;
}

.button-group {
  margin: 8px 0;
  display: flex;
  align-self: flex-end;
}

.input-number {
  text-align: center;
  width: 24px !important;
  height: 20px !important;
  font-size: 10px !important;
  padding: 0 !important;
}

.select-breakpoint {
  text-align: center !important;
  width: 24px !important;
  height: 20px !important;
  font-size: 10px !important;
  padding: 0 !important;
  background-image: none !important;
}

.box-model {
  background-color: #efefef;
  text-align: center;
  font-size: 12px;
  margin-bottom: 8px;
}

.box-model .relative {
  position: relative;
  padding: 24px 32px;
}

.box-model__margin {
  background-color: #efefef;
}

.box-model__border {
  background-color: #dfdfdf;
}

.box-model__padding {
  background-color: #cfcfcf;
}

.box-model .box-model__dimensions {
  background-color: #efefef;
  padding: 8px 0px;
}

.box-model__title {
  position: absolute;
  line-height: 8px;
  font-size: 8px;
  top: 2px;
  left: 2px;
}

/* margin */
.box-model__margin-top {
  position: absolute;
  z-index: 1;
  top: 2px;
  left: 50%;
  transform: translateX(-50%);
}

.box-model__margin-bottom {
  position: absolute;
  z-index: 1;
  bottom: 2px;
  left: 50%;
  transform: translateX(-50%);
}

.box-model__margin-left {
  position: absolute;
  z-index: 1;
  top: 50%;
  left: 2px;
  transform: translateY(-50%);
}

.box-model__margin-right {
  position: absolute;
  z-index: 1;
  top: 50%;
  right: 2px;
  transform: translateY(-50%);
}

/* border */
.box-model__border-top {
  position: absolute;
  z-index: 1;
  top: 2px;
  left: 50%;
  transform: translateX(-50%);
}

.box-model__border-bottom {
  position: absolute;
  z-index: 1;
  bottom: 2px;
  left: 50%;
  transform: translateX(-50%);
}

.box-model__border-left {
  position: absolute;
  z-index: 1;
  top: 50%;
  left: 2px;
  transform: translateY(-50%);
}

.box-model__border-right {
  position: absolute;
  z-index: 1;
  top: 50%;
  right: 2px;
  transform: translateY(-50%);
}

/* padding */
.box-model__padding-top {
  position: absolute;
  z-index: 1;
  top: 2px;
  left: 50%;
  transform: translateX(-50%);
}

.box-model__padding-bottom {
  position: absolute;
  z-index: 1;
  bottom: 2px;
  left: 50%;
  transform: translateX(-50%);
}

.box-model__padding-left {
  position: absolute;
  z-index: 1;
  top: 50%;
  left: 2px;
  transform: translateY(-50%);
}

.box-model__padding-right {
  position: absolute;
  z-index: 1;
  top: 50%;
  right: 2px;
  transform: translateY(-50%);
}
</style>
