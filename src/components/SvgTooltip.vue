<template>
  <svg viewBox="0 0 100 100" class="tooltip" xmlns="http://www.w3.org/2000/svg">
    <g class="root" transform="translate(50, 50)">
      <path :d="d" />
      <text text-anchor="middle" x="0" y="-12">12800</text>
    </g>
  </svg>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: 'SvgTooltip',
  computed: {
    d () {
      const width: number = this.width || 60,
        height: number = this.height || 24,
        offset: number = this.offset || 6,
        corner: number = this.corner || 10,
        left = -width / 2,
        right = width / 2,
        top = -offset - height,
        bottom = -offset
      return [
        'M0,0',
        `L${-offset},${bottom}`,
        `H${left + corner}`,
        `Q${left},${bottom} ${left},${bottom - corner}`,
        `V${top + corner}`,
        `Q${left},${top} ${left + corner},${top}`,
        `H${right - corner}`,
        `Q${right},${top} ${right},${top + corner}`,
        `V${bottom - corner}`,
        `Q${right},${bottom} ${right - corner},${bottom}`,
        `H${offset}`,
        'L0,0 z',
      ].join(' ')
    },
  },
  props: {
    width: {
      type: Number,
      required: false,
    },
    height: {
      type: Number,
      required: false,
    },
    offset: {
      type: Number,
      required: false,
    },
    corner: {
      type: Number,
      required: false,
    },
  },
})
</script>

<style lang="scss">
.tooltip {
  width: 100px;
  height: 100px;
  .root {
    fill: none;
    stroke: #fff;
  }
  text {
    stroke-width: 0;
    fill: #fff;
  }
}
</style>
