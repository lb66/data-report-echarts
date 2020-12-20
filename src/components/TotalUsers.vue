<template>
  <div>
    <commom-card title="累计用户数" value="32,456,789">
      <template>
        <v-chart :options="getOptions()" />
      </template>
      <template v-slot:footer>
        <span>日同比</span>
        <span class="emphasis">154% </span>
        <span :style="{ marginLeft: '16px' }"> 月同比</span>
        <span class="emphasis">154%</span>
      </template>
    </commom-card>
  </div>
</template>

<script>
import CommomCard from "./CommomCard.vue";

export default {
  components: { CommomCard },
  methods: {
    getOptions() {
      return {
        grid: {
          bottom: 0,
          top: 0,
          right: 0,
          left: 0,
        },
        xAxis: {
          type: "value",
          show: false,
        },
        yAxis: {
          type: "category",
          show: false,
        },
        series: [
          {
            type: "bar",
            data: [100],
            barWidth: "12px",
            itemStyle: {
              color: "#45c946",
            },
            stack: "x", //堆叠
          },
          {
            type: "bar",
            data: [250],
            barWidth: "12px",
            itemStyle: {
              color: "#eee",
            },
            stack: "x",
          },
        ],
      };
    },
  },
};
</script>

<style lang="scss" scoped>
</style>