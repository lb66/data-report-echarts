<template>
  <div>
    <commom-card title="累计订单量" value="2,456,789">
      <template>
        <v-chart :options="getOptions()"/>
      </template>
      <template v-slot:footer>
        <span>昨日订单量</span>
        <span class="emphasis">30,000</span>
      </template>
    </commom-card>
  </div>
</template>

<script>
import CommomCard from "./CommomCard.vue";

export default {
  components: { CommomCard },
  methods: {
    getOptions(){
      return {
        xAxis: {
          type: "category",
          show: false,
          boundaryGap:false //使x轴左右无间距
        },
        yAxis: {
          show: false,
        },
        series: [
          {
            type: "line",
            data: [522,565, 343, 434, 343, 202, 326, 120, 102, 202],
            areaStyle: {
              color: "purple",
            },
            lineStyle: {
              width: 0,
            },
            itemStyle: {
              opacity: 0,
            },
            smooth: true,//光滑曲线
          },
        ],
        grid: {
          bottom: 0,
          top: 0,
          right: 0,
          left: 0,
        },
      }
    }
  },
};
</script>

<style lang="scss" scoped>

</style>