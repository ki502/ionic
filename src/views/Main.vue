<template>
  <div id="korea-map" style="height:100%"></div>
</template>

<script>
//lang="ts"를 지웠다. Typescript에서 Vue의 this.$refs를 인식하지 못하여 지움(추후 확인 필요)
//import { IonContent } from '@ionic/vue';
import { ellipse, square, triangle } from 'ionicons/icons';
import * as d3 from 'd3';
import * as topojson from 'topojson';
import * as korea from '@/modules/korea.json';

export default {
  name: 'Main',
  //components: { IonContent },
  setup() {
    return {
      ellipse, 
      square, 
      triangle,
    }
  },
  data() {
    return {
      svg: null
    }
  },
  mounted() {
    //mounted가 된 상태에서도 element가 생성되지 않아 clientWidth, clientHeight을 구하기 위해 Delay를 주었다.(추후 확인 필요)
    setTimeout(() => {
      this.$nextTick(() => {
        const projection = d3.geoMercator()
        .center([128, 36])
        .scale(this.$el.offsetHeight * 6.8)
        .translate([this.$el.clientWidth / 4, this.$el.offsetHeight / 2]);

        const path = d3.geoPath(projection);

        this.svg = d3
            .select('#korea-map')
            .append('svg')
            .attr('width', this.$el.clientWidth + 'px')
            .attr('height', this.$el.offsetHeight + 'px');

        console.log(this.$el.clientWidth);
        console.log(this.$el.offsetHeight);

        const g = this.svg.append('g');

        console.log(korea.default);
        console.log(korea.default.features);

        const states = g.append('g')
          .attr('fill', '#ffffff')
          .attr('cursor', 'pointer')
          .selectAll('path')
          .data(korea.default.features)
          .attr('fill', '#ffffff')
          .join("path")
          .attr("d", path);

      });
    }, 500);
  }
}
</script>