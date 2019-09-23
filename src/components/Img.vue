<template>
  <div>
    <vl-feature>
      <vl-geom-point :coordinates="[6.438020467758174, 44.89833741865752]"></vl-geom-point>
      <vl-style-box>
         <vl-style-icon src="@/assets/marker.png" :scale="0.07"></vl-style-icon>
      </vl-style-box>
    </vl-feature>

  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import VueLayers from 'vuelayers';

Vue.use(VueLayers);

@Component
export default class Img extends Vue {}
</script>
