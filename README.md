# Storyblok EF Component Fade plugin

## Installing the plugin in your storyblok space 
To use EF Component Fade plugin you need to compile and minify the plugin. But first you need to change name of the plugin.
Go to `./src/` and open `Plugin.vue`.
You need to prefix plugin name, with for example name of your department:
```
initWith() {
      return {
        // needs to be equal to your storyblok plugin name
        plugin: "department_name-ef-component-fade"
      };
    },
```


#### Compiles and minifies for production
Go to root folder and run:
```
npm install
npm run build
```

After running the build you should get a folder `/dist` with an `export.js` file inside. 
Create a new plugin in storyblok (it has to have exact name as in first step) and paste the content of `export.js` and publish it.  
The plugin will be available in your storyblok component schemas. 


##### More info on storyblok plugin usage/implementation: 
https://www.storyblok.com/docs/Guides/Creating-a-field-type-plugin

---

## Using the plugin output in your components
The output of the plugin has following structure:

```
{
  "plugin": "ef-component-fade-plugin",
  "classNames": {
    "before": "before-fade",
    "after": "after-fade"
  },
  "transitionConfig": {
    "duration": 500,
    "transitionProperty": "opacity",
    "transitionTimingFunction": "ease"
  },
  "config": {
    "threshold": "0.4"
  },
  "type": "classnames",
  "effect": "fade",
  "_uid": "78dba965-6c4e-42cc-9eb8-f04a50c8215e"
}
```
* `classNames.before` - className which will be applied before intersection observer will be triggered (it is always before-*), where * is set up on plugin consumer
* `classNames.after` - className which will be applied after inntersection observer will be triggered (it is always after-*), where * is set up on plugin consumer
* `transitionConfig` - this is configuration object fot transition
* `config` - this is configuration object which is passed to `IntersectionObserver`
* `type` - type of animation supoported. Right now it's only transition with classnames (roadmap: support js animations)
* `effect` - effect for the transition, this is mostly to for `classNames.before` and `after`

