<template>
  <div>
    <vl-map
      :load-tiles-while-animating="true"
      :load-tiles-while-interacting="true"
      data-projection="EPSG:4326"
      style="height: 700px">

      <vl-view :zoom.sync="zoom" :center.sync="center" :rotation.sync="rotation"></vl-view>

      <!--
      <vl-layer-tile id="osm">
        <vl-source-osm></vl-source-osm>
      </vl-layer-tile>
      -->

      <vl-layer-tile id="bingmaps">
          <vl-source-bingmaps :api-key="apiKey" :imagery-set="imagerySet"></vl-source-bingmaps>
      </vl-layer-tile>

    <Img/>

    <vl-feature>
      <vl-geom-point :coordinates="center"></vl-geom-point>
    </vl-feature>

    </vl-map>
    <div style="padding: 20px">
      Zoom: {{ zoom }}
      <br />
      Center: {{ center }}
      <br />
      Rotation: {{ rotation }}
    </div>
  </div>  
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

import VueLayers from 'vuelayers';
// import 'vuelayers/lib/style.css';



Vue.use(VueLayers);

import Img from '@/components/Img.vue';

@Component({
  components: {
    Img,
  },
})
export default class Carto extends Vue {
  @Prop({ type: String, default: 'Cartographie' }) private msg!: string;

  @Prop({
    type: [Number, Number],
    default: [6.447522008166061, 44.88623180247297],
  })
  private coordoCentreCarte!: [number, number];

  @Prop({ type: Number, default: 12 }) private zoomCarte!: number;

  private apiKey: string = 'ArbsA9NX-AZmebC6VyXAnDqjXk6mo2wGCmeYM8EwyDaxKfQhUYyk0jtx6hX5fpMn';
  private imagerySet: string = 'AerialWithLabels';

  private zoom: number = this.zoomCarte;
  private center: [number, number] = this.coordoCentreCarte;
  private rotation: number = 0;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
