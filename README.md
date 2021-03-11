# Vue HeightCollapsible

Collapsible component with CSS transition for elements with variable and dynamic height.

[![npm version](https://img.shields.io/npm/v/vue-height-collapsible.svg?style=flat-square)](https://www.npmjs.com/package/vue-height-collapsible)
[![gzip](https://img.shields.io/bundlephobia/minzip/vue-height-collapsible.svg)](https://bundlephobia.com/result?p=vue-height-collapsible)
[![license](https://img.shields.io/github/license/kunukn/vue-height-collapsible.svg)](https://github.com/kunukn/vue-height-collapsible/blob/master/LICENSE)

Vue HeightCollapsible

![logo](logo/collapsible.svg "logo")

## Supported versions

### Vue 2

```bash
npm install vue-height-collapsible
// or yarn install vue-height-collapsible
```

### Vue 3

```bash
npm install vue-height-collapsible/vue3
// or yarn install vue-height-collapsible/vue3
```

Or the source file could be copied. It is only this file.<br/>
`vue-height-collapsible.vue`

## Usage example

### Simple

```vue
<template>
  <div class="my-component">
    <button @click="isOpen = !isOpen">
      Toggle
    </button>
    <HeightCollapsible :isOpen="isOpen">
      <p>Paragraph of text.</p>
      <p>Another paragraph is also OK.</p>
    </HeightCollapsible>
  </div>
</template>

<script>
import HeightCollapsible from "vue-height-collapsible";

export default {
  name: "MyComponent",
  components: {
    HeightCollapsible,
  },
  data() {
    return {
      isOpen: true,
    };
  },
};
</script>
```

### Using Aria and scoped slots

```vue
<template>
  <div class="my-component">
    <button
      @click="isOpen = !isOpen"
      :aria-expanded="isOpen"
      aria-controls="my-collapsible-1"
    >
      <span>Toggle {{ collapseState }}</span>
    </button>
    <HeightCollapsible
      :isOpen="isOpen"
      @update="onUpdate"
      v-slot="{ state }"
      id="my-collapsible-1"
    >
      <p>I know the collapse state: {{ state }}</p>
      <p>Paragraph of text.</p>
      <p>Another paragraph is also OK.</p>
      <p>Images and any other content are ok too.</p>
    </HeightCollapsible>
  </div>
</template>

<script>
import HeightCollapsible from "vue-height-collapsible";

export default {
  name: "MyComponent",
  components: {
    HeightCollapsible,
  },
  data() {
    return {
      isOpen: true,
      collapseState: "",
    };
  },
  methods: {
    onUpdate({ state }) {
      this.collapseState = state;
    },
  },
};
</script>
```

## Properties

| Prop               | Type    | Default |
| ------------------ | ------- | ------- |
| isOpen             | boolean | true    |
| transition         | string  |         |
| tag                | string  | div     |
| overflowOnExpanded | boolean | false   |

<br/>

#### `isOpen` : boolean

Expands or collapses content.

#### `transition` : string

You can also specify a CSS transition inline by using the `transition` prop.

```html
<HeightCollapsible
  transition="height 300ms cubic-bezier(.4, 0, .2, 1)"
  :isOpen="isOpen"
>
  <p>Paragraph of text</p>
</HeightCollapsible>
```

#### `tag` : string

You can specify the HTML element type for the collapse component. By default the element type is a `div` element.

```html
<HeightCollapsible tag="article" :isOpen="isOpen">
  <p>Paragraph of text</p>
</HeightCollapsible>
```

#### `overflowOnExpanded` : boolean

If added, then `overflow: hidden` inline style will not be added when the state is `expanded`.

<br>

# npm

https://www.npmjs.com/package/vue-height-collapsible
