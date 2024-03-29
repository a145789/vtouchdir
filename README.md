<p align="center">
  <a href="https://www.npmjs.com/package/vtouchdir" target="_blank" rel="noopener noreferrer"><img src="https://badgen.net/npm/v/vtouchdir" alt="NPM Version" /></a>
  <a href="https://www.npmjs.com/package/vtouchdir" target="_blank" rel="noopener noreferrer"><img src="https://badgen.net/npm/dt/vtouchdir" alt="NPM Downloads" /></a>
  <a href="https://github.com/a145789/vtouchdir/blob/main/LICENSE" target="_blank" rel="noopener noreferrer"><img src="https://badgen.net/github/license/a145789/vtouchdir" alt="License" /></a>
</p>

<p align="center">
  <a href="https://github.com/a145789/vtouchdir/blob/main/README_zh-CN.md" target="_blank" rel="noopener noreferrer">中文</a>
</p>

# vtouchdir

A mobile vue3 touch api custom directive for swipe direction

## Installation

### npm

```bash
npm install --save-dev vtouchdir
```

### pnpm

```bash
pnpm add vtouchdir -D
```

## Docs

### touchDir

**Description**

A function can be passed in, which will be called after the element slides, and can receive three parameters.

**Usage**

```vue
<script setup lang="ts">
import vTouchdir from "vtouchdir"

const handler = (
  direction: Direction,
  e: TouchEvent,
  rangeParams: {
    startPageX: number
    startPageY: number
    endPageX: number
    endPageY: number
    deltaX: number
    deltaY: number
  }
) => {}
</script>

<template>
  <div v-touchdir="handler" />
</template>
```

Supports the same [event modifiers](https://v3.vuejs.org/guide/essentials/event-handling.html#event-modifiers) as `vue` except for `passive`, `.self` has the highest priority

```vue
<script setup lang="ts">
import vTouchdir from "vtouchdir"

function handler(dir: "left" | "right" | "up" | "down") {}
</script>

<template>
  <div v-touchdir.once.stop.prevent="handler" />
</template>
```

The default swipe range is **10**, and the `handler` will be triggered only when the swipe exceeds **10**. You can specify a `range` parameter to customize the range

```vue
<script setup lang="ts">
import vTouchdir from "vtouchdir"

function handler(dir: "left" | "right" | "up" | "down") {}
</script>

<template>
  <div v-touchdir.once.stop.prevent="{ handler, range: 0 }" />
</template>
```

**Typescript**

If you use `ts`, you can export the `Direction` enum

```ts
// vtouchdir
export enum Direction {
  LEFT = "left",
  RIGHT = "right",
  UP = "up",
  DOWN = "down",
}

// use
import vTouchdir, { Direction } from "vtouchdir"
```
