<template>
  <div>
    <commom-card title="今日交易用户数" value="2,456,789">
      <template>
        <v-chart :options="getOptions()"/>
      </template>
      <template v-slot:footer>
        <span>退货率</span>
        <span class="emphasis">5.7%</span>
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
      return{
        xAxis: {
          type: "category",
          show: false,
          data: [522,565, 343, 434, 343, 202, 326, 120, 102, 202],
        },
        yAxis: {
          show: false,
        },
        color:['#3398DB'],
        series: [
          {
            type: "bar",
            data: [522,565, 343, 434, 343, 202, 326, 120, 102, 202],
            barWidth:'60%'
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