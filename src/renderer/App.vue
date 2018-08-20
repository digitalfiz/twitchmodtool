<template>
  <div id='app'>
    <grid-layout
            :layout='layout'
            :col-num='12'
            :row-height='30'
            :is-draggable='true'
            :is-resizable='true'
            :is-mirrored='false'
            :vertical-compact='true'
            :margin='[10, 10]'
            :use-css-transforms='true'
            @layout-updated="layoutUpdatedEvent"

    >

        <grid-item v-for="item in layout" :x="item.x" :y="item.y" :w="item.w" :h="item.h" :i="item.i" drag-allow-from=".vue-draggable-handle" drag-ignore-from=".no-drag">
            <div class="title vue-draggable-handle">{{item.t}}</div>
            <div class="inner no-drag">

            </div>
        </grid-item>
    </grid-layout>
  </div>
</template>

<script>
import { GridLayout, GridItem } from 'vue-grid-layout'
import VideoPlayer from 'vue-grid-layout'

let testLayout = [
  { x: 0, y: 0, w: 6, h: 10, i: '0', t: 'Stream', },
  { x: 6, y: 0, w: 2, h: 4, i: '1', t: 'Chat', },
  { x: 8, y: 0, w: 2, h: 5, i: '2', t: 'Mod Room', }
];

export default {
  name: 'tmt',
  components: {
    GridLayout,
    GridItem
  },
  data: () => {
    return {
      layout: testLayout,
      layoutUpdatedEvent: (newLayout) => {
        console.log("Updated layout: ", newLayout)
      }

    }
  },
};
</script>

<style>

.vue-grid-item {
  background-color: #6441a5;
  padding: 4px;
}

.vue-grid-item .title {
  color: #ffffff;
}
.vue-grid-item .inner {
  background-color: #442d6b;
  position: absolute;
  top: 25px;
  bottom: 5px;
  left: 5px;
  right: 5px;
}

</style>
