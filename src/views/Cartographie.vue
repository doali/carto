<template>
  <div class="home">
    <Carto/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Carto from '@/components/Carto.vue'; // @ is an alias to /src

@Component({
  components: {
    Carto,
  },
})
export default class Cartographie extends Vue {}
</script>
